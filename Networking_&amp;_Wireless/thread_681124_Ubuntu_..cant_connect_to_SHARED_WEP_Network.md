---
title: "Ubuntu ..cant connect to SHARED WEP Network"
date: 2008-01-28
forum: Networking &amp; Wireless
---

### Post by alinux-lb22 on 2008-01-28
Hi All

I am running Ubuntu 7.04 on my toshiba laptop with an IPW3945 card. At home I do have an access point with OPEN WPE security and it connects fine.

At work we do have a CISCO AP without MAC filtering and with WEP and security set to SHARED, my system is a dual boot system and it works with VISTA but it does not work with my Ubuntu system.

The password is hexadecimal when I try to connect using Wireless Assistant it crashes and the farest I get is the following:


root@alinux-laptop:/home/alinux# iwconfig eth1
eth1 unassociated ESSID:"BLABLABLA"
Mode:Managed Frequency=2.437 GHz Access Point: 00:CCD:EE:FF:AA
Bit Rate:0 kb/s Tx-Power:16 dBm
Retry limit:15 RTS thrff Fragment thrff
Encryption key:1111-2222-33 Security mode:restricted
Power Managementff
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:1615 Missed beacon:0


Has anyone had problems with SHARED WEP using Ubuntu ?

Thanks

---

### Post by UpsideDownFace on 2008-01-28
I have just had to replace my wireless router,and now have a Netgear DG834PN, and couldn't get my MacBook to link wirelessly, it was OK with ethernet cable.
The System>Administration>Network kept telling my the network it was detecting needed a WEP password and that I might have entered it wrongly.
So I googled "NETGEAR WEP" and found a forum that said this router needs $ typed in before the password !!!
So I typed $ followed immediately by the password I had already typed in lots of times.
It worked straight away.

So it might not be an obvious fault, and this solution certainly isn't obvious.

Sorry this isn't a very direct help, but keep trying.

---

### Post by alinux-lb22 on 2008-01-29
Indeed not obvious at all I will try that..keep your fingers crossed for me..but if it is correct then #$#A$%#$#$@#% ...!! Well but it would at least work :)

---

