---
title: "Broadcom Wireless Hell"
date: 2006-09-02
forum: Networking &amp; Wireless
---

### Post by bostonjeremy on 2006-09-02
I finally got my broadcom 43xx working, then wham! next restart, it isn't working any more! 

this is my interfaces file:

auto lo
iface lo inet loopback

auto wlan0

iface eth1 inet dhcp

iface eth0 inet dhcp

what other files are involved? any ideas?

---

### Post by K.Mandla on 2006-09-02
I'm not an expert on this, but I'm willing to take a guess, in the interest of science.

Make sure your cueing the right interface. Use *sudo iwconfig* to get the name of your wireless card and use it in your interfaces file. (I don't know if wlan0 will help you at all; I've never run into an Ubuntu install that used wlan0.)

I'm trying to think what my interfaces file looks like with the 4318 I used (I'm at work now). Maybe something like this ... ?

```
iface eth1 inet dhcp # this is my wireless connection
iface eth0 inet dhcp # this is my wired connection

auto eth1
```
Hope that helps. :roll:

---

