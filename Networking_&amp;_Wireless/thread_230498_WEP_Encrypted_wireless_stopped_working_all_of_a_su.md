---
title: "WEP Encrypted wireless stopped working all of a sudden"
date: 2006-08-06
forum: Networking &amp; Wireless
---

### Post by ltmon on 2006-08-06
Hi All,
 
I have been happily running Dapper on my laptop with an Intel ipw3945 card for a couple of months now.
 
Suddenly this morning I can't get anything working with my wireless card at all. This happened after waking up from being suspended.
 
Both with NetworkManager and just standard iwconfig I can see my wireless network, get a link up to it but not get an IP address.
 
DHCPDISCOVER just keeps timing out each time.
 
I have another PC I am using right now with a different wireless card. It works fine with the same settings on the same network.
 
I have tried rebooting into another kernel (i.e. the one before the most recent update) but there was no joy there.
 
Once I disable WEP encryption on the access point it starts working again just fine.

Any help?
 
L.

---

### Post by Mr. Electric Wizard on 2006-08-06
Interesting...
I am having the same problem with my Broadcom card...
Hopefully somebody can give some direction.

---

### Post by ltmon on 2006-08-06
Well I found out today that WPA works fine also.

It is simply WEP that times out when trying to get an IP address.  The timeout is 45s, so I think if it's still not getting an IP after that long then it isn't going to get one at all.

L.

---

### Post by luglug on 2006-08-06
You've brought me out of lurking for this one...

But I'm having the same problem. WPA works fine with NetworkManager but can't seem to connect to any WEP networks. Hoping someone has the solution.

---

### Post by riverpaddler on 2006-12-30
My wireless D-Link Airplus G stopped working correctly also ...after some recent update to the system. It works to connect to Ubuntu.com and mozilla but can't connect to anywhere else. I remember when I first set up this system I had to put in some script to stop something... had to do with the number 6 but I can't remember what it was and be darned if I can find it now. As you can tell I am a COMPLETE BEGINNGER!!!

---

