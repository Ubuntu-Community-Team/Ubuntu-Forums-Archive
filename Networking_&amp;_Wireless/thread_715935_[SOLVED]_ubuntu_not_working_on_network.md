---
title: "[SOLVED] ubuntu not working on network"
date: 2008-03-05
forum: Networking &amp; Wireless
---

### Post by tocleora on 2008-03-05
We just recently set up an ubuntu server with linux firewall, dhcp and nat (gateway?).  We tested all the windows computers and they are all working.  I have ubuntu on my desktop (as my primary os) and it was working yesterday, but today I can't get it to work.  With a static ip I can ping the ubuntu server, I can access webmin on the server, but I can't ping an external web site or visit an external web site from the browser.  If I try to do dhcp with it, it never gets an ip address.  I can switch to Windows from the same machine and everything works fine (on it now).  

In case it's nat related, here are the settings we have set up (eth0 is the one going to the internet, eth1 is the one going to our internal network):

prerouting
> 
Accept 	If input interface is eth1 		
Accept 	If input interface is lo 		
Accept 	If protocol is TCP and source and destination ports are 80 		
Destination NAT 	If protocol is TCP and input interface is eth0 and destination port is 8000 		
Destination NAT 	If protocol is TCP and input interface is eth0 and destination port is 8001 		
Destination NAT 	If protocol is TCP and input interface is eth0 and destination port is 8002


input
> 
Accept 	If input interface is eth1 		
Accept 	If input interface is lo 		
Accept 	If input interface is eth0 and state of connection is ESTABLISHED,RELATED


postrouting
> 
Masquerade 	If output interface is eth0


Anyone see anything in there that might cause windows to work but not ubuntu?  tia...

---

### Post by tocleora on 2008-03-05
Alright, I've narrowed it down to dns related because I can navigate via ip. originally my dns was set to the ubuntu server (which seems to work for our windows machines), so I changed it to the dns's of our isp, but it still doesn't work.  I assumed because a special port needed to be open on the nat, so I created an entry that looks just like the 80 one in prerouting, but is 53 instead.  still doesn't work.  Am I getting close?

---

### Post by tocleora on 2008-03-06
Don't know if this will ever be of benefit to anyone since the solution really doesn't relate to the problem, but I found out that me installing winbind on my machine was what caused it.  I uninstalled winbind and everything works now.

---

