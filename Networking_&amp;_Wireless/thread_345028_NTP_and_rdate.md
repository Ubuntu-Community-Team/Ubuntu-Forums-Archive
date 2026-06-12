---
title: "NTP and rdate"
date: 2007-01-23
forum: Networking &amp; Wireless
---

### Post by russianbandit on 2007-01-23
So I'm running a npt-server service on my EdgyBox. I need to update the time on GenericBox that only knows about my Edgy1. GenericBox only has access to rdate command. Therefore when I run:

rdate -s EdgyBox

I get:

rdate: EdgyBox: Connection refused

Is rdate able to talk to npt-server? Am i running the right server? Help is appreciated.

---

### Post by TerryHowe on 2008-05-01
The RFC 868 time server is supported by xinetd.  You'll probably need to install it and configure it.

sudo apt-get install xinetd
vi /etc/xinetd.d/time
# Set the diable to "no"
sudo /etc/init.d/xinetd restart

rdate away!

---

