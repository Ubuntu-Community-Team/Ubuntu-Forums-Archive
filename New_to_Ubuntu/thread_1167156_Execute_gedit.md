---
title: "Execute gedit"
date: 2009-05-22
forum: New to Ubuntu
---

### Post by petermadd on 2009-05-22
I need to use gedit. Found out that I need execute gedit to get started. How please. If you are kind enough to answer please remember I am really really new to this. Thanks

---

### Post by taurus on 2009-05-22
Applications -> Accessories -> Terminal
```
gedit
```

---

### Post by Mornedhel on 2009-05-22
Applications > Accessories > Text Editor ?

gedit is the default text editor in Ubuntu.

---

### Post by Don1500 on 2009-05-22
> **taurus said:**
> Applications -> Accessories -> Terminal
```
gedit
```


OR, if you need to edit document in other than your accessable locations.


Applications -> Accessories -> Terminal
```
sudo gedit (/path/file name)
```

---

### Post by Tibuda on 2009-05-22
> **Mornedhel said:**
> Applications > Accessories > Text Editor ?

gedit is the default text editor in Ubuntu.

That's the easier way, but you can also press Alt+F2, type gedit and hit Enter.

---

### Post by Cheesemill on 2009-05-22
> **Don1500 said:**
> OR, if you need to edit document in other than your accessable locations.


Applications -> Accessories -> Terminal
```
sudo gedit (/path/file name)
```

You really shouldn't do this, you should do
```
gksudo gedit (/path/file name)
```
instead.

Cheesemill

---

