---
title: "Help with slow samba tranfers"
date: 2007-07-10
forum: Networking &amp; Wireless
---

### Post by brent113 on 2007-07-10
Hi, I've set samba up on ubuntu feisty server on a gigabit network, and I'm getting surprisingly slow speeds.  I am using saidar to monitor the network traffic along with other info, and it's saying i'm getting around 7Mb/s transmit and 1.6Mb/s receive.

In my smb.conf file i've got 

socket options = TCP_NODELAY

and i've also tried using

socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192

but both get *exactly* the same speed.

I'm transferring to another ubuntu feisty computer while I set it up, but ultimately the server is joining a Microsoft collection, so I need to stick with smb, (I can't install nfs or others on all the computers).

Any ideas how to speed this up or where to start looking?  Any help is appreciated!

--
Brent

---

### Post by brent113 on 2007-07-10
Update:  When I use smbclient, I get full transfer speeds (around 30MByte/s down, 20 up).

Why is nautilus so much slower?

---

### Post by gangolli on 2007-07-24
I also find Nautilus Samba to be very slow.  With smbget / smbclient, I get approximately 500mbps transfers on my lan (gigabit, jumbo frames) , and about 700mbps with plain ftp.  Nautilus still operates at about 100mbps. I have some notes on my own study [here]("http://www.busybuddha.org/blog/anil/entry/notes_on_gigabit_ethernet_ubuntu")

---

