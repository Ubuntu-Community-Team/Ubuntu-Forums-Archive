---
title: "Ubuntu Server"
date: 2005-09-12
forum: Networking &amp; Wireless
---

### Post by benson on 2005-09-12
how can i configure Ubuntu to work as a dial-in server? I have already a generic modem installed in /dev/ttyS1. :) is there a how to for this? I search the internet and its quite technical. Can someone explain it in just simple words. :D Thanks!

---

### Post by debenham on 2005-09-13
A quick-n-dirty way is the following:

1. Install "mgetty" (ie apt-get install mgetty, or via synaptic)
2. Edit your /etc/inittab, adding a line like "s0:23:respawn:/sbin/mgetty ttyS0" (this is for modem on /dev/ttyS0, change as needed)
3. restart init (kill -HUP 1)
4. there is no 4

If you also install "mgetty-docs" there is a really simple file to help you at /usr/share/doc/mgetty/examples/inittab.DEBIAN

---

