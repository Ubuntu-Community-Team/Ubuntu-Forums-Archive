---
title: "3d box platform in ubuntu"
date: 2010-12-21
forum: New to Ubuntu
---

### Post by lorantjakab on 2010-12-21
hi, what do i need to do or download to get the 3d box platform in ubuntu as it would be super useful. thank you

---

### Post by Elfy on 2010-12-21
What is a 3d box platform?

---

### Post by lorantjakab on 2010-12-21
some guy posted it on youtube and it looks real handy, where you spin the box u work with.[http://www.youtube.com/watch?v=cy-4hVGR5Vk](http://www.youtube.com/watch?v=cy-4hVGR5Vk)
[http://www.youtube.com/watch?v=kYgV2GlsufI](http://www.youtube.com/watch?v=kYgV2GlsufI)
thanks

---

### Post by theozzlives on 2010-12-21
> **lorantjakab said:**
> some guy posted it on youtube and it looks real handy, where you spin the box u work with.[http://www.youtube.com/watch?v=cy-4hVGR5Vk](http://www.youtube.com/watch?v=cy-4hVGR5Vk)
[http://www.youtube.com/watch?v=kYgV2GlsufI](http://www.youtube.com/watch?v=kYgV2GlsufI)
thanks

If your talking about the cube just install:
```
sudo apt-get install compizconfig-settings-manager
```
you set it up under System/Preferances.

Hit Alt+F2 and type compiz --replace

If that works, put it in your startup applications.

edit: Make sure your number of desktops is set to 4. Oh, you rotate the cube with CTRL+ATL+Left Click.

---

### Post by lorantjakab on 2010-12-21
Can I get some step by step instructions on how to get this box working. I got a window pop up when i hit alt f, but then on i was lost. thank you

---

### Post by theozzlives on 2010-12-21
Write this down:

1. Go to Applications > Accessories > Terminal
2. At the prompt type:
```
sudo apt-get install compizconfig-settings-manager
```
3. Right-click on your workspace switcher and select properties
4. change the # of workspaces to 4
5. go to System > Properties > compizconfig settings manager
6. select cube, rotate cube and if you want, 3d Windows
7. Hit ALT+F2 at the same time and type in the box:
```
compiz --replace
```
8. do an ALT+CTRL+Left-click and see if it works.

It's a **CUBE**, not box.

If it works:
1. go to System > preferances > Startup Manager
2. click add
3. name should be: Compiz
4. command should be: compiz --replace

---

### Post by lorantjakab on 2010-12-21
thank you that worked
you guys are awesome!

---

### Post by theozzlives on 2010-12-21
> **lorantjakab said:**
> thank you that worked
you guys are awesome!

You're quite welcome from both of me.

---

### Post by lorantjakab on 2010-12-21
LOL sure, twice the thanks is better than one=D>

---

### Post by sammiev on 2010-12-22
Hi lorantjakab, Thought you may like [THIS]("http://ubuntuguide.net/how-to-install-compiz-fusion-desktop-effects-in-ubuntu-810") as well. :)

---

