---
title: "laptop freezes"
date: 2009-05-16
forum: New to Ubuntu
---

### Post by Mr.Kuchinawa on 2009-05-16
Hi.

I have an Asus m2400n with ubuntu 9.04 installed. The problem is that it sometimes (I can't point out why) completely freezes. I can move the mouse, but nothing responds, not even ctrl+alt+backspace (I have enabled it), which leads me to think that this is something more than gnome... I did not have this problem with 8.04 on the same machine. 

Oh, and it's a fresh install. Any help would be great!

---

### Post by Bölvaður on 2009-05-16
From the following website


> 0000:00:02.0 VGA compatible controller: Intel Corp. 82852/855GM Integrated Graphics Device (rev 02)

If you want 2D/3D acceleration (use GLX or DRI), you must activate
Intel AGP, AGPGART and i830 support in kernel (CONFIG_AGP_INTEL,
CONFIG_AGP, CONFIG_DRM_I830 options). If you choose to compile Intel
AGP as module, be sure to load module before to start XFree86.


Verify that you have a "DRI" section in your XF86Config file:

[http://people.easter-eggs.org/~valos/Asus_M2400N/Asus_M2400N.html]("http://people.easter-eggs.org/%7Evalos/Asus_M2400N/Asus_M2400N.html")


you probably already know intel video cards are having trouble in jaunty.

---

### Post by Mr.Kuchinawa on 2009-05-16
Nope I didn't. But besides, I have absolutely no fancy effects enabled, not even compositing..

EDIT: wait a second..I did not ask for beta!

---

### Post by mapes12 on 2009-05-17
I have read that Jaunty utilises a new Xorg configuration that has been causing problems. I went back to 8.04LTS and have no problems anymore.

---

### Post by Mr.Kuchinawa on 2009-05-18
> **mapes12 said:**
> I have read that Jaunty utilises a new Xorg configuration that has been causing problems. I went back to 8.04LTS and have no problems anymore.

Does anyone know if it's possible to use the "old" xorg with 9.04?

---

### Post by mapes12 on 2009-05-19
> Does anyone know if it's possible to use the "old" xorg with 9.04?I don't think so. Others have tried to copy their /etc/X11/xorg.conf in 8.04 then paste it into 9.04 but this doesn't work because the xorg.conf file in 9.04 is almost redundant.This is because 9.04 uses something called Jockey to replace what the xorg.conf file used to do. I don't know how this Jockey configuration works though. From what I've read you can't edit it, unlike the xorg.conf file.

This is only what I've read on this Forum. Others may have other info to help you out.

---

