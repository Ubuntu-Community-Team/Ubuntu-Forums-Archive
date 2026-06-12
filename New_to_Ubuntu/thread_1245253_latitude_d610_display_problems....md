---
title: "latitude d610 display problems..."
date: 2009-08-20
forum: New to Ubuntu
---

### Post by mbaucco on 2009-08-20
Hello,

I installed Ubuntu 9.04 today and I am having trouble with the display, it is very slow and the monitor shows up as "unknown" in the display control panel. I have a few questions:

Is there something like the windows device manager so I can see what video card I have?

How do I make sure I am using the right driver or try a different one?

Also, does anyone know which driver to use with a Dell Latitude d610?

Thanks!
Matt

---

### Post by chalex on 2009-08-20
You can use 'lspci' to list the devices in your system.  E.g. 'lspci|grep VGA' will look for a line with "VGA" in it, so it will tell you your exact graphics card.

E.g. on my machine:
```

alex@pgfi-chekh-d1:~$ lspci |grep VGA
01:00.0 VGA compatible controller: nVidia Corporation GeForce 9500 GT (rev a1)

```

---

### Post by mbaucco on 2009-08-20
Thanks! Looks like I have the following:

00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)

How do I make sure I have the right driver for this and get it to recognize my laptop's display?

Thanks again,
Matt

---

### Post by LewRockwell on 2009-08-20
[https://bugs.launchpad.net/ubuntu-mobile/+bug/366601](https://bugs.launchpad.net/ubuntu-mobile/+bug/366601)

.

---

### Post by LewRockwell on 2009-08-20
[http://www.geekology.co.za/blog/2009/05/widescreen-resolutions-ubuntu-904-acer-al1916w-with-intel-915gm-910gml/](http://www.geekology.co.za/blog/2009/05/widescreen-resolutions-ubuntu-904-acer-al1916w-with-intel-915gm-910gml/)

.

---

### Post by LewRockwell on 2009-08-20
sometimes when laptop and netbook screens are goofy we just hook them up to an external monitor and then they function ok after that

we're convinced that the process to identify the external monitor must also re-confirm the internal as well

mostly we just know it works more often than not in those situations

.

---

### Post by mbaucco on 2009-08-20
I tried hooking it up to an external monitor with no luck. I looked at the web page you linked but it is for an Acer. Is it safe to use the same numbers on my Dell?

Thanks,
Matt

---

### Post by mbaucco on 2009-08-21
I think I may just try 8.10 and see if that works better, thanks for trying though!

---

