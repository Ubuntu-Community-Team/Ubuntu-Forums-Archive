---
title: "Display problem MSI wind U115 with GMA 500"
date: 2010-09-02
forum: New to Ubuntu
---

### Post by telllos on 2010-09-02
Hello,

I'm having a display problem with the icons in netbook edition.

I installed the poulsbo driver for the GMA 500.

Everything was working ok, (no 3d or compiz), but it was working

Today when I started my computer after logging in the icons in netbook remix are all messed up? Any window I open is displayed well, same thing for the top menu bar. Here is a screen:

[IMG]http://imgur.com/XUVVx.png[/IMG]

Here is a screen with the icon problem:

[IMG]http://imgur.com/yB84Z.png[/IMG]

I'm not sure if I did any update of my computer yesterday. Also didn't install any new software recently.

If I log in using normal gnome in the log in screen it works fine.

I installed gnome shell a while ago, but can't logging that way, because I have the same kind of problem. So I'm just logging normally

I'm not sure if it is a problem with poulsbo drivers.

Here is my xorg if it can help:


```
Section "DRI"
    Mode    0666
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    Driver    "psb"
EndSection
```If anyone coult tell me what is the problem, I would really love the help.

thank you.

---

