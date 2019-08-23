# JavaScript viewport checker

[demo](https://tltary.github.io/ch_view/index.html)

### IMPORTANT: Checking the first hit of an element in the viewport

copy ch_view.js file in you site, or copy this code

``` js
const chView = (i) => {
    const isInViewport = (elem) => {
        let bounding = elem.getBoundingClientRect();
        return (bounding.top >= 0 && 
                bounding.left >= 0 && 
                bounding.bottom <= 
                (window.innerHeight || 
                document.documentElement.clientHeight) && 
                bounding.right <= 
                (window.innerWidth || 
                document.documentElement.clientWidth)
        );
    };

    const el = document.querySelectorAll(i);
    document.addEventListener('scroll', () => {
        for (let i = 0; i < el.length; i = i + 1) {
            if (isInViewport(el[i]) && !el[i].classList.contains('active')) {
                alert(`view element - ${el[i].innerText}`);
                el[i].classList.add('active');
            }
        }
    }, true);
}
```

and use like
``` js
chView('<your-element>');
```