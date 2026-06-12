---
title: "Connecting to public Wifi"
date: 2006-12-11
forum: Networking &amp; Wireless
---

### Post by hbj on 2006-12-11
Hello,

I am having a problem connecting to public wifi hotspots with my laptop.  In Linux I am using ndiswrapper with the bcmwl5 driver.  I am currently running Edgy but have had this problem with Dapper too.  I can connect to private WEP access points just fine and experience no problems at all.  I can connect to open wifi access points if they don't have any strange authentication steps.

Many of the public wifi hotspots that I connect to (hotels, coffee shops, etc.) require that you first open your web bowser and accept some agreement before they allow you to access the internet.  As far as I recall, I have not been able to get this to work using only Linux.  I am unable to get an IP address from the wifi hotspot DHCP server.

What does work is first to boot Windows, get and IP address and accept the agreement, and then reboot into Linux, and everything is fine.  I assume that it is adding my MAC address to a control list somehow.  This sucks because I have having to boot into Windows just so that I can get online.

Any suggestions?

---

### Post by mhallowes on 2006-12-20
I am having the exact same problem.  Even at home, sometimes I have to boot into windows first, then boot into Ubuntu, or the boot will hang waiting for the network.

Can anyone shed any light on this problem?

Thanks.

---

