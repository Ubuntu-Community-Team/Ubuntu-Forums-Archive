---
title: "Scroll Lock"
date: 2009-01-31
forum: New to Ubuntu
---

### Post by EGLF24 on 2009-01-31
I have a KVM switch to switch between my Windows and Ubuntu PCs. The hotkey sequence for switching between them is the standard double press of Scroll Lock. The thing is, the scroll lock button doesn't seem to work in Ubuntu. I have tried the following but it didn't help:

gksudo gedit /etc/X11/Xmodmap

add mod3 = Scroll_Lock


Any ideas? Thanks.

---

### Post by mjheagle8 on 2009-01-31
that shouldnt matter, the keypress signals the kvm to switch where it is sending your input. the os doesnt tell the switch to change computers.

---

### Post by EGLF24 on 2009-01-31
I see what you mean. I don't understand though why it works fine when switching from Windows to Linux but not the other way around. The rest of the keyboard functionality seems to work OK.

The odd thing is that I have just tried plugging another USB keyboard directly into the Linux machine and a double press of Scroll Lock works fine. I guess that proves your point about the OS. Still leaves me rather confused though.

---

### Post by nmcfarb on 2009-02-02
I have this same issue. Bypassing the KVM did not fix the issue, scroll lock still does not work.  Furthermore it appears to work (scroll light comes on at least) before the system boots and then stops working when GRUB loads.  So it does not appear to be the KVM, perhaps a Keyboard/OS compatibility issue - Mine is a "Comfort Ergoflex" keyboard.

---

### Post by mjheagle8 on 2009-02-02
try this:
[http://linuxtechie.wordpress.com/2008/04/07/getting-scroll-lock-to-work-in-ubuntu/](http://linuxtechie.wordpress.com/2008/04/07/getting-scroll-lock-to-work-in-ubuntu/)

---

### Post by nmcfarb on 2009-02-04
Thanks - 

That worked great!
:D

---

### Post by mjheagle8 on 2009-02-04
glad i could help! :)

---

