---
title: "Switching the Alt and Ctrl keys"
date: 2011-06-15
forum: New to Ubuntu
---

### Post by cgroza on 2011-06-15
Hello,
I am feeling uncomfortable with the Ctrl key far to my left and I almost never use my Alt key.
So I was wondering if there is any way to reverse them?
I heard about xmodmap but I an sure how to use it.

Thank you.

---

### Post by pqwoerituytrueiwoq on 2011-06-15
maybe system -> preferences -> keyboard -> click options button

---

### Post by cgroza on 2011-06-15
I go to Ctrl key position and all I see is Right Ctrl as Right Alt.

I need the left ones or both sides.

---

### Post by idoitprone on 2011-06-16
save the file
use
```
xmodmap filename

``````

! left
remove Control = Control_L
remove Mod1 = Alt_L
keysym Control_L = Alt_L
keysym Alt_L = Control_L
add Control = Control_L
add Mod1 = Alt_L

! right
remove Control = Control_R
remove Mod1 = Alt_R
keysym Control_R = Alt_R
keysym Alt_R = Control_R
add Control = Control_R
add Mod1 = Alt_R
```

this is just a quick solution. If keep swapping keys when you log out and loggin.

 if you want a more perment solution 

post the output of 
```
xmodmap -pke | grep -i "alt\|control"

xmodmap
```

---

### Post by cgroza on 2011-06-16
Thank you. It was exactly what I needed.

---

### Post by idoitprone on 2011-06-16
there always a problem with loggin out and loggin in, unless you only run it manually

---

### Post by cgroza on 2011-06-17
I will put it in my .xsession to be run every time my computer boots...

---

