---
title: "Wireless network lasts about 5 minutes after a reboot"
date: 2005-06-16
forum: Networking &amp; Wireless
---

### Post by shane98 on 2005-06-16
Im a newbie and I just loaded Ubuntu.  I was trying to get the wireless on my laptop working.  iwlist would list my ap, but I could never connect to it (AP mac always read zeros).  I saw on another post that someone updated their /etc/network/interfaces file (what I added is listed below) so I tried that.  And it worked...  for about 5 minutes.  After about 5 minutes (not always exactly 5 minutes so I dont think it is an actual timeout set somewhere) I lose connectivity and iwconfig is back to listing all zeros for the AP mac.  I am less than 5 feet from the AP and windows xp does not lose connection so I do not believe it to be a hardware problem or me losing the signal from being too far away.



Router:  Dlink-520
Wireless card:  Intel B2200

interfaces file additions:
iface eth0 inet dhcp
wireless-essid shanesnetwork
wireless-keymode restricted
wireless-key (I list the key, its hex so I just type in the numbers)
wireless-mode managed


As I said after about 5 minutes I lose connectivity.  If I reboot then it is fine and works for about 5 minutes again.  Any Ideas on how to keep connectivity?  If you need more information let me know.

Thanks,

Shane

---

