---
title: "Share internet connection over wireless"
date: 2008-11-14
forum: Networking &amp; Wireless
---

### Post by mad_max0204 on 2008-11-14
Hi,
there are some threads about sharing internet over wireless and making ad-hoc connections but none helped me.
I installed Gigabyte Wireless PCI adapter and I use Gbit onboard LAN adapter for my internet. How do I share my internet connection from my LAN to Wireless and how do I make access point out of my wireless card ?

Thanks

---

### Post by superprash2003 on 2008-11-15
For internet connection sharing, you could use firestarter ( type sudo apt-get install firestarter in the terminal) or if firestarter doesnt work, you could do it the command line way

1)Sharing Internet connection - [http://www.ubuntugeek.com/sharing-internet-connection-in-ubuntu.html](http://www.ubuntugeek.com/sharing-internet-connection-in-ubuntu.html)
2)creating ad hoc network - [http://prash-babu.blogspot.com/2008/08/how-to-createjoin-adhoc-network-in.html](http://prash-babu.blogspot.com/2008/08/how-to-createjoin-adhoc-network-in.html)

---

### Post by iponeverything on 2008-11-15
If your wireless driver support ap mode your in luck.

What driver is using? Just post the correct line from the output of lspci.

BTW -- ad-hoc only supports up to 10Mb

---

