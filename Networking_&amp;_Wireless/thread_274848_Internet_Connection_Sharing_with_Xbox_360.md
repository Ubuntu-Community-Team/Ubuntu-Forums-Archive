---
title: "Internet Connection Sharing with Xbox 360"
date: 2006-10-10
forum: Networking &amp; Wireless
---

### Post by Xecuter on 2006-10-10
I know there are tons of threads about this out there, but I find some of them inconclusive or just to difficult. So please don't link me to some other guide.

I need to share my internet connection with my xbox 360. To this point I've followed [this]("https://help.ubuntu.com/community/InternetConnectionSharing") guide. But it only helps so far.

Anyhow. My internet connection is eth1 configured to receave IP from modem.
IP: 10.0.0.4
Mask: 255.255.255.0
Gateway: (modem) 10.0.0.1

My network connection is eth0. What settings do I need here?
And what settings do I need on my x360?

---

### Post by mips on 2006-10-10
[http://ubuntuforums.org/showthread.php?t=269235](http://ubuntuforums.org/showthread.php?t=269235)

I'm linking as I'm not gonna type it out again just to please you.

---

### Post by Xecuter on 2006-10-11
Thanks. But Firestarter says there's an error when I enable DHCP for the local network. What to do?

It says that eth0 is not ready. I have eth0 set for DHCP in network-admin.

---

### Post by mips on 2006-10-12
Try and configure it statically. It's only one device so dhcp is not really required.

---

### Post by Xecuter on 2006-10-12
I've also got vmnet1 and vmnet8, from VMWare. Anyways. I've been fiddeling around with a DHCP server, and finally got it running. My x360 now gets an IP, but it fails on DNS. On automatic it uses 10.0.0.1, witch is my modems adress. What is wrong then?

---

### Post by Xecuter on 2006-10-13
Got it working! Thanks! :D Had to configure the DHCP server, and set up the correct settings on the x360. Works like a charm!

---

### Post by Oen386 on 2007-03-24
How did you get the DNS working?

---

