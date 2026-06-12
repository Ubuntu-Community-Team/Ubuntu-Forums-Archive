---
title: "logitech trackman marble (mouse)"
date: 2009-02-11
forum: New to Ubuntu
---

### Post by techno-mole on 2009-02-11
Hello

i have just bought a logitech trackman marble mouse, it has 4 buttons,
 now i have already managed to get the small left button to work as a scroll button (meaning if you hold it down and move the ball the page etc will scroll)

but i want to have the small right button act as a middle click button but im not sure how, i followed a guide to change the small left button, it mentions changing the right button, but im a tad confused as im not sure what xmodmap is, or where to find it.

heres where the guide is - [https://help.ubuntu.com/community/Logitech_Marblemouse_USB](https://help.ubuntu.com/community/Logitech_Marblemouse_USB)

does it mean i need to create the xmodmap file ?

cheers

---

### Post by Tim Sharitt on 2009-02-11
You will need to create an .Xmodmap file (in your home folder). For the small right button, I think you will need something like;

```
pointer = 1 9 3 4 5 6 7 8 2
```

---

### Post by techno-mole on 2009-02-12
cheers for the help.

many thanks

---

### Post by amr2205 on 2010-09-21
> **techno-mole said:**
> Hello

i have just bought a logitech trackman marble mouse, it has 4 buttons,
 now i have already managed to get the small left button to work as a scroll button (meaning if you hold it down and move the ball the page etc will scroll)

but i want to have the small right button act as a middle click button but im not sure how, i followed a guide to change the small left button, it mentions changing the right button, but im a tad confused as im not sure what xmodmap is, or where to find it.

heres where the guide is - [https://help.ubuntu.com/community/Logitech_Marblemouse_USB](https://help.ubuntu.com/community/Logitech_Marblemouse_USB)

does it mean i need to create the xmodmap file ?

cheers

Thanks! This fix my problem with the trackball!

---

### Post by techno-mole on 2010-09-22
Glad it helped, I used to use this method, but found after karmic I think it was this method stopped working, for me anyway.
Now I use gpointing device settings (It's in the repo's) here's a link to the site - [gpoiting device settings]("http://live.gnome.org/GPointingDeviceSettings")

It works well for my logitech one, it may work with other track balls, give it a try, it's easy to configure, in the case of my mouse I have to select button 8 so I can scroll.

---

