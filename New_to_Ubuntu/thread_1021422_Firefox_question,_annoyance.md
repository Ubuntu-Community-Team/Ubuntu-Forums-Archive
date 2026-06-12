---
title: "Firefox question, annoyance"
date: 2008-12-25
forum: New to Ubuntu
---

### Post by Steve05TSX on 2008-12-25
Maybe someone will have an idea, on Windows when I single click on the address bar it will select all, but on here I have to double click.  Anyone know if this is changable?  I have FF3 installed on here

---

### Post by zzHanks on 2008-12-25
Type ```
about:config
``` in the url bar and change to these values (by double-clicking)  ```
browser.urlbar.clickSelectsAll;true
```and 
```
browser.urlbar.doubleClickSelectsAll;false
```

---

### Post by DouglasK on 2008-12-25
Also in the About:Config window, change:

```
browser.urlbar.doubleClickSelectsAll=true
```

to 

```
browser.urlbar.doubleClickSelectsAll=false
```

Just so that you can select single words in the url bar with a double click like in Windows.

~~Douglas

---

