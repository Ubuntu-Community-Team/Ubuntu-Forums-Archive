---
title: "Xubuntu: cannot connect to wireless network after restart until key is re-entered"
date: 2007-12-09
forum: Networking &amp; Wireless
---

### Post by Manad on 2007-12-09
Hi,

I'm having a problem with Xubuntu network-admin (I think). I'll give as much details as I can in case something is relevant.

1) I installed Xubuntu, set up the wireless connection. Things worked fine.
2) I decided to change the wireless key on the router to something smaller/simpler (an 8-digit ASCII string).
3) I changed the wireless key in Network-admin, it took the changes and I was able to reconnect to the network.
4) I reset the computer using the Restart option at the Quit menu. When it came back, the computer could not connect to the network. I could not ping google OR the router's IP.
5) I went back to network-admin, there was a very long network password (presumably the encrypted copy of the key). I deleted all the *'s and put my 8-digit key again.
6) After submitting changes, I could now ping google/the network. 
7) Repeat after every reboot

Troubleshooting steps attempted (couldn't do more as I am a linux newbie):

1) Entered the key a ton of times, reset a ton of times, same result.

2) Through googling, found out that the network config file is kept in /etc/network/interfaces. I deleted that file to force it to generate a new one in case a bug left it using the old key. Didn't change anything.

Could it be that my regular login does not have the rights to access the wireless interface, and that changing the key (which requires me to enter my sudo password) gives me said rights?

In any case, my network connection is broken, and I need help fixing it. Thank you.

---

### Post by walkerk on 2007-12-09
Give [WICD]("http://wicd.sourceforge.net") a try :)

---

### Post by Manad on 2007-12-09
> **walkerk said:**
> Give [WICD]("http://wicd.sourceforge.net") a try :)

Thanks, this worked perfectly. Your thread with installation instructions was most helpful.

I'm still left wondering why Xubuntu's network-admin couldn't do something this basic. You'd expect a program handling the most important aspect of a modern OS (networking) to do this kind of thing without problems. Oh well...

---

