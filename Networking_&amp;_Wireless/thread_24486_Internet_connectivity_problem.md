---
title: "Internet connectivity problem"
date: 2005-04-07
forum: Networking &amp; Wireless
---

### Post by peeterge on 2005-04-07
Hello, 

I'm very new in the linux world. Worked already several years on Solaris at office. So I do know the basics of unix. 

Yesterday I installed ubuntu from a CD I got from a collegue. Ubuntu runs fine on my PC but I cannot access internet.
I configured PPPoE with pppoeconf which is OK.

I checked if PPPoE session was set up by linux. OK. running with IP address got form ISP.

DNS server IP addresses are forwarded by ISP. checked in network GUI.

But I cannot ping any site on the web
ping [www.google.be](www.google.be) was unsuccessful.

Can this be a firewall isssue? 
As far as I understood, there is a firewall installed during initial installation.


Does anyone know how I can monitor if incoming packets on eth0 are blocked by a firewall? 
I think one can see if packets are coming on on eth0 with snoop.
I didn't check this yet.

any suggestions or debug scenario's are welcome

kind regards

Geert

---

### Post by dataw0lf on 2005-04-08
What's the exact error you're getting from your ping?
Can you post your ifconfig of eth0 here?
Can you give me the output of 'route'?
FYI, tcpdump can be used to monitor specific interfaces.  Very useful tool to learn.

---

### Post by KoJ on 2005-04-11
[QUOTE=dataw0lf]What's the exact error you're getting from your ping?
Can you post your ifconfig of eth0 here?
Can you give me the output of 'route'?
FYI, tcpdump can be used to monitor specific interfaces.  Very useful tool to learn.[/QUOTE]
 I'm also having the same problem peeterge, I typed in "sudo pon dsl-provider" then DNS server and IP addresses are forwarded by ISP as seen on "plog" but i cant seem to ping any sites even the sites ip address. also when i typed in "plog" i get these results:

PAP athentication suceeded
Peer from calling number [mac address] 
not replacing default route to eth0
cannot determine ethernet address proxy arp
local ip: 210.xx.xxx.xxx
remote ip: 210.xx.xxx.xxx
Primary DNS: 203.xxx.xx.xxx
Secondary DNS: 203.xxx.xx.xxx

any inputs?

---

