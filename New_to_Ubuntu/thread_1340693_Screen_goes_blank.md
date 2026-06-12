---
title: "Screen goes blank"
date: 2009-11-28
forum: New to Ubuntu
---

### Post by halovivek on 2009-11-28
Hi
I have installed all the updates in ubuntu 9.04.
I have given upgrade to ubuntu 9.10
after reboot my screen gone blank.
I dont know what to do. how to recover?
thanks

---

### Post by zkriesse on 2009-11-28
Not sure exactly but you can try to stick in your Ubuntu cd and choose "Repair System" from the boot menu of the cd.

---

### Post by u.b.u.n.t.u on 2009-11-29
> **halovivek said:**
> Hi
I have installed all the updates in ubuntu 9.04.
I have given upgrade to ubuntu 9.10
after reboot my screen gone blank.
I dont know what to do. how to recover?
thanks

The problem may relate to your GPU driver. One solution to at least get you back into Ubuntu is to delete the xorg.conf file.

To do this start Ubuntu in recovery mode and get to a command prompt. There enter the following:

rm /etc/X11/xorg.conf

Please understand that this will delete your xorg.conf file.

The error I see, is after the white Ubuntu logo, the screen goes black and a cold boot is required. If this is exactly what you are seeing then my assessment may be correct and it your GPU driver.

---

