---
title: "Had to clean install Ubuntu 8.04 dual boot wxp"
date: 2009-07-26
forum: New to Ubuntu
---

### Post by altkon on 2009-07-26
Hi to all Community members,
After a clean Install of Ubuntu 8.04 dual boot with WXP everything works fine.
My main problem is that I cant switch from EN to Greek typing both on Firefox and 0.0.Org Word processor.
I have found and installed already from myspelling in Synaptic the Greek language.
Can someone assist me please??:(
Tanks
AA
PS. The same problem on evolution

---

### Post by altkon on 2009-07-26
My keyboard is Microsoft Internet Keyboard and I have no problem in Typing the Greek letters with WXP OS.
Also previously when I had installed Ubuntu I had no problem in Greek typing with the same Keyboard.
AA

---

### Post by TeoBigusGeekus on 2009-07-26
[http://ubuntuforums.org/showthread.php?t=798555]("http://ubuntuforums.org/showthread.php?t=798555")

---

### Post by altkon on 2009-07-26
Intending to apply following quotation:
 Re: Change keyboard layout problem
You can edit /etc/X11/xorg.conf by hand. Here's what to do:
- Open /etc/X11/xorg.conf . Please note that you need administrator privileges. Otherwise you will not be able to write any changes.
- Find your keyboard config. It should look somewhat like this:
Unquote
But I dont know how??
I tried from terminal but I cannot find it..
Can someone be a little bit more specific as to how to apply:
 edit /etc/X11/xorg.conf by hand
Thanks a lot.

---

### Post by Liolikas on 2009-07-26
sudo gedit /etc/X11/xorg.conf

If you have 9.04 it may be almost empty so you have to find examples in forum and copy-paste contents.

---

### Post by oldfred on 2009-07-26
minor point it should be gksudo gedit /etc/X11/xorg.conf 
They say you should use gksudo for all graphical applications and sudo for terminal applications.
In 9.04  top panel system preferences keyboard tab for layouts is a chooser for keyboard.

---

### Post by altkon on 2009-07-28
Finally I resolved the issue as follows:
I hit System>Preferences>Keyboard>Layouts.
Then I added "Greece" layout below "USA" layout.(No default)
From Layout options>layout switching.....
Checked both boxes for "both shift keys together change layout",
and "both alt keys together change layout".
And voila now everything works fine even after reboot.
But I use all the time only the "both alt keys together" setup.
Grateful for all your help and assistance...:)
Regards,
AA

---

