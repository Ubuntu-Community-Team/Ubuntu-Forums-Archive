---
title: "network interface disabled"
date: 2014-06-03
forum: Networking &amp; Wireless
---

### Post by jimmy-jad on 2014-06-03
my realtek gigabyte card for some reason is disabled on my Ubuntu 14.04 server, unless i choose it as the primary during OS installation. I need it enabled to manage my cluster nodes.

Outputs: [COLOR=#333333][FONT=UbuntuRegular]lshw(networking): [/FONT][/COLOR][http://paste.ubuntu.com/7580772/](http://paste.ubuntu.com/7580772/)[COLOR=#333333][FONT=UbuntuRegular] dmseg: [/FONT][/COLOR][http://paste.ubuntu.com/7580750/](http://paste.ubuntu.com/7580750/)

Thanks for any help!

---

### Post by jimmy-jad on 2014-06-03
Close, i managed to get it to work!

---

### Post by Iowan on 2014-06-03
Perhaps you could share your secret...
then mark it [[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")

---

### Post by jimmy-jad on 2014-06-04
After multiple reboots and network restarts..... For some reason adding eth1 to the network interface worked, now im just working on getting MAAS to use the interface to accept PXE using the DHCP & DNS management.

---

