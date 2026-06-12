---
title: "wifi drops connection, but only when I'm not looking"
date: 2007-08-26
forum: Networking &amp; Wireless
---

### Post by nikkkko on 2007-08-26
Hi,

I use a Netgear WG121 with ndiswrapper,(Kubuntu 7.04), and have no problems except when downloading large files, and even then only when I leave the computer unattended. 

This is not really that annoying as I am usually using the machine, but if I leave it for more than, say, 20 minutes, there is a 50/50 chance the connection will be dropped.

Connection also often gets dropped if I use Skype for a call longer than about 20 min.  Again, not a show stopper, but I'd love to iron out this wrinkle.

Any pointers gratefully received.

---

### Post by be4truth on 2007-08-26
Check your screen saver. If it is on 20 mins ....

---

### Post by nikkkko on 2007-08-27
This only happens when I am downloading or talking on Skype.  In other words, if the screensaver cuts in when there is low or no wifi traffic, the connection is not dropped.

It seems to be ndiswrapper related. Yesterday, when I noticed the connection had dropped, I did ndiswrapper -l just to see if the device was still alive, and hey presto it woke up and reconnected.

---

