---
title: "Inconsistent Network"
date: 2007-06-27
forum: Networking &amp; Wireless
---

### Post by gogira on 2007-06-27
My machine seems to have an inconsistent network connection. The internet connection routinely freezes, when downloading packets it stops and wont start again. When accessed from other computers on the network it's speed is random and printing large documents routinely fails. 

When ping-ed it reports 5 to 30 ok replies then 1-10 "request timed out" and just continues to alternate like that at random. I have looked at ifconfig and ethtool and as far as I can tell everything seems OK. Although, ethtool -S eth0 reports "no stats available".

I let the ping run for a while -- stats:
Packets: Sent = 1870, Rec = 1318, Lost = 552 (29% loss) !!!!!!!
roundtrip in ms -- Min = 0, Max = 261, Avg = 7

Here is what I am working with:
xubuntu (fiesty fawn), samba and cups have been configured so that works as a file/print server, not very well tho because of the randomness. It is connected via wire to linksys wrt54g router.

I looked at new drivers for the sis onboard card but the latest drivers available are already installed. So at this point I'm stuck, If anyone has any ideas or could point me in the right direction it would be appreciated.

---

