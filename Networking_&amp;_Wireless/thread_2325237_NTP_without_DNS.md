---
title: "NTP without DNS"
date: 2016-05-20
forum: Networking &amp; Wireless
---

### Post by wales2 on 2016-05-20
I have a box running ubuntu 10.04 x86 & it's isolated by necessity from a lot of the network.
It is blocked from DNS.

I'd like it to keep accurate time, so I've configured NTP with several servers, all IP addresses.  It's got the IP address, so it won't need to do DNS lookups, riiiight?

Here's the error I get when I try to update time:


date before sync:
Fri May 20 08:03:32 PDT 2016
 * Stopping NTP server ntpd
   ...done.
Name server cannot be used, exiting20 May 08:03:32 ntpdate[26887]: name server cannot be used, reason: Temporary failure in name resolution

 * Starting NTP server ntpd
   ...done.
COMMAND FAILED: /usr/sbin/ntpdate -u 216.228.192.69 prefer	#S2Platform-Server1 131.107.13.100 prefer	#S2Platform-Server2 192.43.244.18 prefer	#S2Platform-Server3
date after sync:
Fri May 20 08:03:32 PDT 2016
Sync failed

My question:  is this ever going to work or does NTP just flat-out require DNS?
I've done a lot of googling but I can't find any info about this.


Thank you

---

### Post by TheFu on 2016-05-20
welcome to the forums.
Support for 10.04 ended in 2015 for servers and 2013 for desktop releases. Please upgrade to a currently supported OS. There have been many bugs addressed in the NTP system over these years.

---

