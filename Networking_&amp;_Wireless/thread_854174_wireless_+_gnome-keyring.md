---
title: "wireless + gnome-keyring ???"
date: 2008-07-09
forum: Networking &amp; Wireless
---

### Post by pogacsa on 2008-07-09
hi,

i am new to ubuntu. I found ubuntu live-cd working fine, so i decided to install over my opensuse, but after installation having difficulties to connect my wireless network. Ideal solution would be having user logged in automatically (solved), and connecting to my wireless (not working). 

Having problems leading me to gnome-keyring from several ways. The /etc/network/interfaces configured to have auto wlan0. It seems to be working if i have doing the next steps:
 - right click on nm-applet and open my wireless setting at editing (do not need to enter password of root. this has been fixed by seahorse)
 - system/admin/network and unlock by typing the password of root
 - at termnial windows, do su, then /etc/init.d/networking restart.
then it is connecting to my wireless.

i have issues with gedit from terminal window, as do su, then trying to edit anything with gedit filename. It is not starting up due to missing priviledges.

=> therefore i found gnome-keyring is not working as i expect or misunderstood it.
There is some reading: [http://magicrobotmonkey.blogspot.com/2008/02/chaging-your-password-on-gnome-keyring.html](http://magicrobotmonkey.blogspot.com/2008/02/chaging-your-password-on-gnome-keyring.html)
which i tried to follow to setup keyring.

i hope any of you will have ideas for next steps.... thx

---

