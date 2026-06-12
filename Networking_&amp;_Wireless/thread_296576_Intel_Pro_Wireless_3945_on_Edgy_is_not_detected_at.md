---
title: "Intel Pro Wireless 3945 on Edgy is not detected at all"
date: 2006-11-09
forum: Networking &amp; Wireless
---

### Post by Dead_$partan on 2006-11-09
Hi All,

Just updated to edgy from Dapper (via format and re-install).  My WiFi card doesnt appear to be detcted at all.

In Dapper all I had to do was to goto system>admin>networking.  My wireless card was listed, I enabled it,turned on DHCP and boom, it worked.  In edgy the card is not listed here ate all.  I also ran iwconfig and got the following info...

> iain@ARAGORN:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.


Does anyone have any suggestions to get the card at least detected by the OS?

Thanks for any hlp.

Regards
Iain

---

### Post by kappo9000 on 2006-11-09
Does ifconfig eth1 show anything?

---

### Post by Dead_$partan on 2006-11-09
Hi,

Doest look like it, please see below...

> iain@ARAGORN:~$ ifconfig eth1
eth1: error fetching interface information: Device not found

Cheers

---

### Post by emdeem on 2006-11-09
Install the linux-restricted-modules for your kernel.

---

### Post by Dead_$partan on 2006-11-09
Yay that workeed, fantastic - thank you all very much.

I wonder why this wasnt added as defaulr like it was in dapper.

Manay thanks.
Iain

---

### Post by GabrieisWings on 2008-02-12
Just what might those be? Got a E1505 with the same problem. Any way you can direct me in the proper direction? Cause I am quite lost.

Please. I need my wifi back. I am lost with out it.

-S

---

