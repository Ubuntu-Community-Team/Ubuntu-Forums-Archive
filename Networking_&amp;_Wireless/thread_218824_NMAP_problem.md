---
title: "NMAP problem"
date: 2006-07-19
forum: Networking &amp; Wireless
---

### Post by ding.iitk on 2006-07-19
Hi,
When I start the netcat server a host by the command "nc -l -p 4000" and I run the port scan for that particular host on itself by using the command "nmap -sT -p 3999-4001 10.1.0.2" to scan the ports 3999, 4000, 4001, the result I get is that port 4000 is open and other 2 closed. This is expected result but this result doesn't come when I do the same using UDP i.e. when I run "nc -l -p 4000 -u" and then do a port scan by "nmap -sU -p 3999-4001 10.1.0.2". In this case it shows all three ports closed. I also checked the file /proc/net/udp file and it shows a socket being created with port 4000. But I don't know why is it not showing up in nmap. Can anyone please help me out in this?? 
Thanx in advance.

---

