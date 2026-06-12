---
title: "Gutsy: Can ping internet but not router"
date: 2007-10-28
forum: Networking &amp; Wireless
---

### Post by Skyes0402 on 2007-10-28
Dear experts,

I work on a laptop (HP nx7010) with a clean install of 7.10. The laptop's wireless interface eth1 works perfect (internet and windows shared drive access). 
The trouble starts when I switch of eth1 and try to work wired. Then I can access the internet (eth0 has received a DHCP address), ping e.g. "http://ubuntuforums.org" but I can't ping my router (192.168.0.1). With eth1 I can, as well as with my other Windows PC which works also wired. There is also no chance to ping the windows computer or access the shared drive via Samba.

Any ideas?

Gunter

---

### Post by Sunforge on 2007-10-28
Do your wireless card and wired ethernet card get the same DHCP address assigned by the router?

*If* that is the case - then it's worth clearing the arp cache on your other computers and your router. If you waited long enough, sometimes up to 1/2 an hour arp cache problems clear themselves when computers refresh their cache.

---

