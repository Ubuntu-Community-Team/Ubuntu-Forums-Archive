---
title: "Super windows key and Applications menu"
date: 2010-02-14
forum: New to Ubuntu
---

### Post by GL541 on 2010-02-14
Hi,

Is there any way to set the Super/Windows key as hot-key for the Applications menu? You know, just like on Windows with the Start menu.

I've tried doing this in System > Preferences > Keyboard Shortcuts, but when I hit the Super key nothing happens. I know the key works though, because I've used it to "grab" windows with the cursor.

Thanks in advance for replies. :)

---

### Post by HermanAB on 2010-02-14
Yes, you can do it with xmodmap, but I cannot remember the details. Some googling will find a guide for you though.

I use it to map the Menu key on my Eee PC to a right hand Control key.  

Here is my ~/.Xmodmap file as an example:
remove Control = Control_R
keycode 135 = Control_R
add Control = Control_R

From then on, the Menu key 135 acts like a Control key.

---

### Post by bumanie on 2010-02-14
I also think it can be done via gconf-editor --> apps --> metacity --> global keybinding

---

### Post by GL541 on 2010-02-19
> **bumanie said:**
> I also think it can be done via gconf-editor --> apps --> metacity --> global keybinding
Thanks both for your replies. I tried bumanie's suggestion, and got the same problem. When I go to edit the Key, I hit the super key and nothing happens. Does anyone know what it's actually called? Because I can type in things like "<Alt>F1" etc.

---

### Post by fualad on 2010-02-19
> **GL541 said:**
> Thanks both for your replies. I tried bumanie's suggestion, and got the same problem. When I go to edit the Key, I hit the super key and nothing happens. Does anyone know what it's actually called? Because I can type in things like "<Alt>F1" etc.

**Super_L** ;)

---

### Post by GL541 on 2010-02-19
> **fualad said:**
> **Super_L** ;)

And it works! Fantastic!

Thank you all :)

---

