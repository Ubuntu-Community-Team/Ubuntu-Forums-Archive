---
title: "Blank Scree after i log in.."
date: 2009-06-23
forum: New to Ubuntu
---

### Post by koyakishore on 2009-06-23
dear all..

yeaterday..i upgraded ubuntu latest version 9.04..

but the prob is..
after i enter my username,password..
it is just showing the blank display..:(
now i'm not in a position to open terminal even...

help me out of this...

---

### Post by fugaki on 2009-06-23
press ctrl+alt+f1

this will bring you to a prompt
log in

you can then begin looking thorugh logfiles for errors.

---

### Post by koyakishore on 2009-06-23
ok..thats fine..

as i'm new to ubuntu..
i dono how to look for those logfiles..
will u plz help me..??

---

### Post by magh-87 on 2009-06-23
Can you give us some details about your computer? Does it meet the minimum or recommended requirements for 9.04?

---

### Post by koyakishore on 2009-06-23
yes...it do meet..

2.6ghz..RAM 512MB..120MB harddisk..

---

### Post by 3rdalbum on 2009-06-23
What do you mean by a blank screen? Like, is the monitor's backlight still on, or is it like the monitor has turned off? Do you have a cursor on the screen?

If you've got a cursor on the screen, reboot and try using the Failsafe Gnome session (at the login screen, press Options and then Sessions and choose Failsafe Gnome.

---

### Post by koyakishore on 2009-06-23
thanks friends...

the actual prob is with xserver configuaration...
I checked it by using..

sudo dpkg-reconfigure xserver-xorg

then it got displayed xserver file is broken..

then i solved itt..

sudo dpkg --configure -a

now its working for me...:D

thanks for ur support too..:)

---

### Post by magh-87 on 2009-06-23
Grats, welcome to ubuntu.

---

