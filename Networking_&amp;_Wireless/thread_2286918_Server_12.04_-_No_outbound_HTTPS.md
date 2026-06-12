---
title: "Server 12.04 - No outbound HTTPS"
date: 2015-07-15
forum: Networking &amp; Wireless
---

### Post by dtsmith1984 on 2015-07-15
I have a server hosted by Softlayer running Ubuntu Server 12.04.  

I have recently noticed that I cannot make any connection to an HTTPS site from this server.  I am utilizing iptables, however I have no rules applied to OUTPUT and the default policy is to ACCEPT.

I have used lynx, elinks, curl, and telnet to test.  Any website running HTTP will load quickly.  However if I point to an HTTPS site, it just hangs and eventually times out.  
I have not noticed any other protocols being blocked. 

Could anyone point me in the right direction in determining what could be blocking outbound https connections? Any help would be greatly appreciated.

Thanks in advance,
David

---

