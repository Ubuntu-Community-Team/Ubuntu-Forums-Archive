---
title: "is 915resolution no longer available?"
date: 2009-08-10
forum: New to Ubuntu
---

### Post by unfolding on 2009-08-10
I think i need it to gain the proper resolution for my monitor.

I tried synaptic and terminal commands to no avail.

im trying to install a driver for 'Intel Corporation 82Q963/Q965 Integrated Graphics Controller (rev 02)'

to gain higher resolutions.   

dis sucks!


is it still available or what should i do instead?

---

### Post by unfolding on 2009-08-10
* i did try the modeline stuff but just ended up pulling my hair out. i am using linux mint by the way.

---

### Post by kerry_s on 2009-08-11
it should already be using the intel driver, look in your /var/log/Xorg.0.log

if your not getting the right resolution than you'll probably have to do it manually.

first, you need to get a good xorg.conf for your hardware.
boot in to the failsafe mode & run-> **X -configure**
that will scan your system and create a xorg.conf.new that you can copy and use later.
type "reboot" to get back to your regular system.

now copy that new xorg.conf to the old one.
**cat /root/xorg.conf.new > /etc/X11/xorg.conf**

now that xorg.conf can be modified and will work.
post a copy of that and tell us what resolution you need.

---

### Post by unfolding on 2009-08-11
thank you for responding kerry,

i did everything except the last command responded with:

billy@billy-desktop ~ $ cat /root/xorg.conf.new > /etc/X11/xorg.conf
bash: /etc/X11/xorg.conf: Permission denied

---

### Post by kerry_s on 2009-08-11
> **unfolding said:**
> thank you for responding kerry,

i did everything except the last command responded with:

billy@billy-desktop ~ $ cat /root/xorg.conf.new > /etc/X11/xorg.conf
bash: /etc/X11/xorg.conf: Permission denied

my bag, "sudo" it. :P

**sudo cat /root/xorg.conf.new > /etc/X11/xorg.conf**

---

