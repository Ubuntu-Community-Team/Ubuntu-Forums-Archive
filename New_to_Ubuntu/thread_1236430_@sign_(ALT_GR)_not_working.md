---
title: "@sign (ALT GR) not working"
date: 2009-08-10
forum: New to Ubuntu
---

### Post by swappa on 2009-08-10
Weird issue on Jaunty x64.
My "at sign" stops working after I have been using a remote desktop session on a different server. When I press AltGr + 2 (Norwegian keyboard) nothing happens. The same "at sign" is working on my virtual Vista workstation (virtualized using vmware workstation).

My Device section in xorg.conf looks like this;

Section "InputDevice"
# generated from default
Identifier "Keyboard0"
Driver "kbd"
Option "XkbModel" "pc105"
Option "XkbLayout" "no"

My keyboard is a standard wired logitech keyboard attached to my Lenovo T61 laptop.
The same thing happens if I bypass the logitech keyboard and use the keys on my laptop so it is not related to the keyboard. 

Any ideas?

Thanks

---

### Post by arochester on 2009-08-10
Check your region. In in the UK. Whan this happens for me I usually find that I have the US keyboard installed - and have to change it.

---

### Post by swappa on 2009-08-11
> **arochester said:**
> Check your region. In in the UK. Whan this happens for me I usually find that I have the US keyboard installed - and have to change it.

I have checked that and according to my keyboard layout it is still NO (Norwegian) when this happens.

---

