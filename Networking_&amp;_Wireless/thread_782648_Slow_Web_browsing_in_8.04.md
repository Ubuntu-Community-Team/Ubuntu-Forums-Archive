---
title: "Slow Web browsing in 8.04"
date: 2008-05-05
forum: Networking &amp; Wireless
---

### Post by Jonagon on 2008-05-05
Hi guys,

I've had Ubuntu 8.0.4 installed for about a week now, and have been having a problem.

To put it in short: 

My web browsing is slow in both firefox and opera but file downloads are fine. By slow.. 20+ secs to load [http://news.bbc.co.uk](http://news.bbc.co.uk) .. i'm dual booting Win XP which is much faster (<2secs)

details:

I'm connecting using a ethernet cable, via network manager and a router
after googling this a bit, I found a problem that seemed to affect dapper (?) with IPv6 compatibility, disabling this in firefox and using some terminal commands on the web didn't seem to have any effect.

Does anyone have any ideas?

---

### Post by subzero316 on 2008-05-05
Try the Add-on FasterFox... Here`s the [<<-----Link------>>.]("https://addons.mozilla.org/en-US/firefox/addon/1269")

---

### Post by superprash2003 on 2008-05-05
try changing DNS servers top opendns - [http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html)

---

### Post by Jonagon on 2008-05-07
> **superprash2003 said:**
> try changing DNS servers top opendns - [http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html)

Thanks guys, I've changed my DNS servers to no effect, though I get the impression that the DNS is the problem (the firefox status bar pasuses for ages at the looking up *site name* bit)

Any more tips?


As far as isntalled fasterfox goes, i'm not sure this will make the difference will it? since it only caches things to get the speed increase + I'm using firefox 3 and there's no fasterfox version for it yet. I tried installing firefox 2 as well, but it wasn't having it.

---

### Post by pgdave on 2008-05-07
I have a similar problem - I have an Ubuntu machine, and a Windows XP machine both with wireless connections to the router. The Windows machine gets 3.7Mb/s throughput on the internet, while the Ubunto 8.04 machine gets 350Kb/s max. File downloads start at 1Mb/s, and rapidly slow to 10kps - dialup speeds!

This started immediately after upgrade to Hardy. Under Gutsy, I got the same speed as the windows machine. Copying files from Windows to Ubuntu machine is also painfully slow at 10kps. A file that downloaded off the internet in less than 10 minutes on the Windows XP machine threatens to take 6 hours to copy across...

EDIT: now fixed by sudo iwconfig wlan0 rate 54M

Thanks to [http://ubuntuforums.org/showthread.php?p=4902804#post4902804](http://ubuntuforums.org/showthread.php?p=4902804#post4902804)

---

