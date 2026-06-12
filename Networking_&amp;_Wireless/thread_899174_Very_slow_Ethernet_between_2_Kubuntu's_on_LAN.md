---
title: "Very slow Ethernet between 2 Kubuntu's on LAN"
date: 2008-08-24
forum: Networking &amp; Wireless
---

### Post by mibadt on 2008-08-24
Hi,
I try to share**** files Using Samba)  between 2 Kubuntu 8.04 (fully updated) on a physical (not wireless) Ethernet LAN. Unfortunately, while copying files between these two my **Max speed is only 7 Mib/Sec**. Why can't I get a higher speed?

PCs configuration (each): On board Gigabyte Ethernet card (works fine while surfing). Local firewall temporarily disabled.

Both PC are the only active ones connected via a 100Mbit.Sec 8 port Edimax switch.

Please Advise!
Thanks

Miki Badt

---

### Post by ilrudie on 2008-08-25
Don't know for sure but samba could just be a real chatty protocol.  Try using scp or nfs instead since these are Linux native and windows is not involved.

---

### Post by mibadt on 2008-08-30
Thanks, I'll try.

---

