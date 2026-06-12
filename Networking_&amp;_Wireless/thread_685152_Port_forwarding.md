---
title: "Port forwarding"
date: 2008-02-01
forum: Networking &amp; Wireless
---

### Post by satimis on 2008-02-01
Hi folks,


VMWare Server

Ubuntu 7.04 server amd64 (Host)
Internal IP addr 192.168.0.10
Port forwarded  80, 443


CentOS 5 x56_64 (Guest)
Internal IP addr 192.168.0.20
Port forwarded 8080


Router - Linksys Ethernet Fast Cable/DSL 4-way switch
(on load from ISP with password locked by ISP)


On Internet [https://public_ip:8080](https://public_ip:8080) can visit the Default Apache page on CentOS (webpage not established).  Now I expect to run [https://public_ip](https://public_ip) instead (w/o 8080.  This is a test. Apache on Ubuntu will be stopped)


I googled a while coming up with following steps to re-set the router;


Applications & Gaming:

Port Range Forwarding```


Application	Start	End	Protocol	IP Addr		Enabled
web		80	80	Both		192.168.0.20	check
				(TCP/UDP)

```

Port Triggering```

Application	Triggered Range		Forwarded Range
Web		Start Port End Port	Start Port End Port
		80         80 		8080	   8080

```

Edit httpd.conf on CentOS

Change;
Listen 8080

to;
Listen 80


Please shed me some light before I call ISP to reset the router.  Whether the above setting will cater my need.  TIA



Shall I do anything on "UPnP Forwarding"


B.R.
satimis

---

