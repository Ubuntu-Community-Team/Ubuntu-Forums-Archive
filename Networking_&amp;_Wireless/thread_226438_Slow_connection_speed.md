---
title: "Slow connection speed"
date: 2006-07-31
forum: Networking &amp; Wireless
---

### Post by Ahma on 2006-07-31
First of all, I'd like to point out that I just recently installed Ubuntu so please be as specific as possible if you decide to reply, thank you.

For some reason I seem to have very slow connection speed on Ubuntu. I have a 3M/512kb cable connection which just crawls. I've read these forums and tried a couple of things to fix this, to no avail. Is the following accurate?
> One thing you can try is, with IPv6 enabled, to launch a terminal, and
type 'host www.google.com'. If the command succeeds quickly, listing
Google's IPs, then you're not having general network connectivity
trouble, and you can start filing bug reports against whichever specific
applications are being slow.Sometimes on Firefox when a page is almost loaded I get a message stating that the connection was reset. My download speed on "software updates" is less than 1kb! I tried disabling IPv6, but didn't see any change in my connection speed. I changed the IPv6 part in "sudo gedit /etc/modprobe.d/aliases", I changed it in Firefox's "about:config", rebooted and then tried ip a | grep inet6 to verify that it was disabled.

:::.. Download Stats ..:::
Download Connection is:: 155 Kbps about 0.16 Mbps (tested with 386 kB)
Download Speed is:: 19 kB/s
Tested From:: [http://testmy.net/](http://testmy.net/) (Server 2)
Test Time:: 2006/07/31 - 7:13am 
Bottom Line:: 3X faster than 56K 1MB Download in 53.89 sec 
Tested from a 386 kB file and took 20.467 seconds to complete
Download Diagnosis:: May need help : running at only 5.71 % of your hosts average (elisa-laajakaista.fi) 
D-Validation Link:: [http://testmy.net/stats/id-TODI7FHBR](http://testmy.net/stats/id-TODI7FHBR)
User Agent:: Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.0.5) Gecko/20060727 Ubuntu/dapper-security Firefox/1.5.0.5 [!]

---

### Post by mips on 2006-07-31
Maybe have a look at your DNS settings resolv.conf file.

---

### Post by Ahma on 2006-07-31
It contains: search elisa-laajakaista.fi and two nameserver parts with different IP addresses.

---

### Post by mips on 2006-07-31
See if there is anything in here that can help you, [http://www.ubuntuforums.org/showthread.php?t=225734](http://www.ubuntuforums.org/showthread.php?t=225734)

I'm outa here for now.

---

