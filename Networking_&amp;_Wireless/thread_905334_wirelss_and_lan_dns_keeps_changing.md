---
title: "wirelss and lan dns keeps changing"
date: 2008-08-30
forum: Networking &amp; Wireless
---

### Post by talktorishav on 2008-08-30
Hey guys,

In my laptop I use wireless at office and LAN at home. ISP of office and home are different. In office I use DHCP and in home I have static public IP.

My problem is when I'm at home I have to change the nameserver back to home's ISP from office's ISP when I reach home. So each day I reach home I have to manually chage my nameserver to the ISP of my home.

Though for now I have written a script that updates the namserver based on IP, is there any easy solution?

---

### Post by talktorishav on 2008-09-03
bump
This scenario seems to be very common to me.

---

### Post by Iowan on 2008-09-03
**dhclient.conf** retrieves DNS information from DHCP Server by default.  DHCP at home would compliment the DHCP at work and (hopefully) change nameserver for you.

---

