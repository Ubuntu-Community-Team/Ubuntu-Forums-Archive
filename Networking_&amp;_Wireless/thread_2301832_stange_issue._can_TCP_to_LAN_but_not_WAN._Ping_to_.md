---
title: "stange issue. can TCP to LAN but not WAN. Ping to external is good"
date: 2015-11-05
forum: Networking &amp; Wireless
---

### Post by sapient007 on 2015-11-05
did some updates and rebooted today to this strange problem. The ips/gateway/dns server seems to be good as I can reach my router browser interface and other pages within my home network. What's hosed up is all traffic over tcp outside of LAN. Strangely I'm able to ping 8.8.8.8 but not google.com

it seems like my tcp traffic is all getting trapped somewhere but I'm not sure where to look. 

other workstations on the same router goes to WAN just fine. any suggestions?

---

### Post by TheFu on 2015-11-05
Check the DNS settings.

---

### Post by sapient007 on 2015-11-05
DNS looks okay. I us nm-tool and see the following on wlan0

IPv4 Settings:
Address: 192.168.0.169
Prefix: 24
Gateway: 192.168.0.1
DNS: 192.168.0.1

so it looks correct and identical (aside from Address) to my working laptop.


edit: also have disabled dnsmasq without any success. it seems like something holding on to the DNS service... anywhere else I can look?

---

### Post by TheFu on 2015-11-05
If you can ping internet IPs, but cannot resolve internet domainnames, the problem is DNS.

I don't use network manager or dnsmasq, so can't help with those. Sorry.

---

### Post by sapient007 on 2015-11-05
i've updated my resolve.conf and works. it's dns per your initial assessment. 

what confused me was that I was able to ping google ip fine but was not able to get there with wget. what i found out afterwards was the google ip is actually issuing a redirect and consequent dnslookup that caused the hang. 

anyhow, something added a invalid entry to my long resolv.conf file and that casued a hose up. I've since cleaned it up and it's now working.

---

### Post by TheFu on 2015-11-05
resolv.conf will be recreated every time networking is restarted. Changes will be lost.

---

