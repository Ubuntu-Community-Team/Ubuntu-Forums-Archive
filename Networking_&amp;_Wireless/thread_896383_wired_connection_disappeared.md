---
title: "wired connection disappeared"
date: 2008-08-21
forum: Networking &amp; Wireless
---

### Post by sandclock on 2008-08-21
Hi
I have a small network with some pcs on ubuntu 7.10 and some on win xp. here are events that happened today
1. suddenly all ubuntu boxes stopped internet browsing.
2. To fix this i just restarted my switch.
3. everything was back on track but one box in particular suddenly lost its wired connection. 
4. Now it doesnt show up wired connection in networking at all.
facts
1. I am using wired connection and not wireless
2. I did not install any updates.
3. I did not change any settings.
any idea whats wrong here?
Regards
Nik

---

### Post by sdide on 2008-08-21
Hi, 
How are your ubuntu boxes configured?

Do they get their ip information from DHCP or are they staticly configured?

and what does 

$ ip a s

output on the machine not working?

---

### Post by sandclock on 2008-08-23
> **sdide said:**
> Hi, 
How are your ubuntu boxes configured?

Do they get their ip information from DHCP or are they staticly configured?

and what does 

$ ip a s

output on the machine not working?

Ip addresses are configured automatically DHCP 
are you sure ip a s is right command? its says a s is unknown
thanks for help
Regards
Nik

---

### Post by sandclock on 2008-08-23
Just to update this now i have some other problems.
1. internet is not accessible on any of ubuntu boxes but works fine on xp pcs on same network. 
2. when i ping ubuntu.com or yahoo.com i get reply as unknown hostname. 
hell this is driving me crazy.

---

### Post by sandclock on 2008-08-23
update:
i restarted the switch and modem and internet started working again. But problem with one pc remains where its not detecting network card at all.

---

### Post by Iowan on 2008-08-23
> **sandclock said:**
> Ip addresses are configured automatically DHCP 
are you sure ip a s is right command? its says a s is unknown
thanks for help
Regards
Nik
**ip a** works (or **ip -s a**).  That's a new one for me - similar to **ifconfig**
Try **lshw** or **lspci** to see if the NIC shows up.

---

