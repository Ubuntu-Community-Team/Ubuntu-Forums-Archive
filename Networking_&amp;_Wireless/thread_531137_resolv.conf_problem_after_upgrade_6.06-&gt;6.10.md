---
title: "resolv.conf problem after upgrade 6.06-&gt;6.10"
date: 2007-08-21
forum: Networking &amp; Wireless
---

### Post by h0r0n on 2007-08-21
Hi! I used inet via pptpcinfig with OpenDNS hack :) :[http://ubuntuforums.org/showthread.php?t=323747&highlight=Internet+works+sorta%3F](http://ubuntuforums.org/showthread.php?t=323747&highlight=Internet+works+sorta%3F)

But after upgrade 6.06->6.10 in /etc/resolv.conf appear line SEARCH NAME.SERVER.COM, I tryed to delete it but after network restart it apear again... :(

---

### Post by h0r0n on 2007-08-21
I tryed **sudo chattr +i /etc/resolv.conf** command but pptpconfig stil freeze, it's write 
[I]Using interface ppp0pptpconfig: monitoring interface ppp0

Connect: ppp0 <--> /dev/pts/1
CHAP authentication succeeded
MPPE 128-bit stateless compression enabled
Cannot determine ethernet address for proxy ARP
local  IP address 172.16.106.32 [/I] :(
I also tryed to change my **prepend domain-name-servers 208.67.222.222, 208.67.220.220;** on **supersede domain-name-servers 208.67.222.222, 208.67.220.220;** in /etc/dhcp3/dhclient.conf. It didn't have effect :(

---

