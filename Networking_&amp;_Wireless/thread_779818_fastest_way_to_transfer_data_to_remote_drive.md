---
title: "fastest way to transfer data to remote drive"
date: 2008-05-03
forum: Networking &amp; Wireless
---

### Post by applegrew on 2008-05-03
I have a 500GB Maxtor SATA drive attached to my Desktop computer. It has an ext3 partition that I need to access over the network (Wifi). When I transfer data to the drive by the direct connection to it (over USB), the transfer rate is on average 10MBps, but when I transfer data to the drive over the network the transfer rate is dismal (about 1.3MBps)!

I am accessing the drive using samba. What other ways exists to access my drive over the network, and which is the fastest one?

---

### Post by tamoneya on 2008-05-03
1.3 MBps is pretty fast for a wifi connection.  As for networks you are not going to be able to acheive anywhere near the speeds you get if it is just a local harddrive to harddrive transfer,

---

### Post by applegrew on 2008-05-03
Isn't wifi have capacity for 54Mbps? That translates to 6.75MBps. Full bandwidth is never utilized but 1.3MBps is nowhere near 6MBps. BTW I tried accessing the drive via proftpd but the trasfer rate was around only 30KBps!

---

### Post by tamoneya on 2008-05-03
that is the theoretical maximum.  It is rarely if ever acheived.  You would probably have to be directly next to the router for that to happen.  I don't think that you are doing anything wrong with your transfer so just keep it the way it is.  I would be content with those transfer rates.

---

### Post by applegrew on 2008-05-04
ok. Now I am arranging for a longer power extension cord, so that I can bring my external HDD next to my laptop.

---

