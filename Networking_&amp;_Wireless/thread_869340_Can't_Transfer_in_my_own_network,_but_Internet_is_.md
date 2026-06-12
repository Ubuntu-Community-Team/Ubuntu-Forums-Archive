---
title: "Can't Transfer in my own network, but Internet is fine!"
date: 2008-07-24
forum: Networking &amp; Wireless
---

### Post by puredoxyk on 2008-07-24
Hi all...I'm having the WEIRDEST problem, and trying to determine what the cause of it is.  Hopefully you can help me.

Running Hardy on a 64-bit Athalon box with 1.2Gb RAM; my wireless card is a RT2561/RT61 802.11g PCI by RaLink.

Here's what it's doing:

I can surf just fine.  I can download four torrents while surfing and listening to streaming radio; just fine.  I can pull my whole website down over FTP; no problems.  But if I try to transfer anything of any real bulk -- over 100MB or so -- over the network to my media box or my husband's box (both also Ubuntu Hardy boxen), my whole computer grinds to a halt.  It doesn't seem to matter whether I use SMB, FTP, etc. to do the transfer.

The first thing that happens, oddly enough, is that my mouse stops working -- it stutters to a halt immediately as soon as the transfer starts.  (I'm using a Rocketfish wireless mouse, that works fine otherwise.)  Then the transfer, which starts normally and at about 1.5 MB per second, starts to slllloooowwwwllly drop in speed.  When it reaches zero -- if I can't find a way to cancel it before then -- it will lock my whole machine, requiring a hard reboot.  (After which, everything will work fine again).

So...my guess is that something is hanging *only* when the pipe is really full.  Any ideas why this might happen??

Thanks!
PureDoxyk

---

### Post by puredoxyk on 2008-07-30
Bump...anybody?  Any guesses where to look or what to try?

Thanks!

---

### Post by brujoand on 2008-07-30
can you dump your syslog her, just after you get the computer working again after the failed transfer.

to get the syslog do:
gedit /var/log/syslog

---

