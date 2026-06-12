---
title: "SIOCSIFFLAGS: No such device"
date: 2008-11-18
forum: Networking &amp; Wireless
---

### Post by TheLunticIsInMyHead on 2008-11-18
Hi all,

Just wondering if I could get some help, I'm fairly new to Linux, on Hardy I had my wireless working fine, now on intrepid, the nm-applet doesn't allow me "enable wireless".

lspci recognises my card
Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

iwlist scanning reveals
wlan0     No scan results

sudo iwlist wlan0 scan gives
wlan0     Interface doesn't support scanning : Network is down

and so here is the bigy, I try
sudo ifconfig wlan0 up
and get
SIOCSIFFLAGS: No such device
But there is such a device, it appears in the lspci right?

Any help would be great. Cheers,

Mike

---

### Post by hofa on 2009-02-04
I would really like some help too with this (same problem)

---

### Post by Iowan on 2009-02-04
Check **lshw -C network** to see if the wireless card is actually aliased as wlan0.

---

