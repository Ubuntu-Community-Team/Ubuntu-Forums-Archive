---
title: "A weird DNS issue"
date: 2016-04-09
forum: Networking &amp; Wireless
---

### Post by neogarfield on 2016-04-09
Hello all,

I'm facing a rather quaint internet issue, which I think is a DNS issue. I'll narrate the problem, but I'm not very proficient with behind the scenes operations, so I request you to bear with me.

I'm using Kubuntu 15.10 on my laptop (Plasma 5.4.2). I'm on a university network. I'm able to access internet fine from my dorm room, where I've hooked up a wireless router to the university network ethernet port, but not anywhere else on campus - all on the same campus local network - regardless of whether I connect using a wireless or wired network. The issue persists even when I plug in the same cable from my wifi router to my laptop.

When I access through my wireless router, everything is fine - I can access all websites. When I access from elsewhere on campus, the connection is established, I get assigned an IP, the DNS addresses are given with the DHCP leash, and pinging IP addresses work, but pinging hostnames or trying to access a website through a browser does not work. For example, pinging 8.8.8.8 works, but pinging google.com times out. Accessing my university website IP address - hosted on the intranet - works, but not if I use the hostname. Accessing one of the google IPs through a website redirects me to google.com and times out. I put in the IP address of stackexchange, and I get at least a stackexchange error page (thus hinting that if I give IP addresses of websites, the connection goes through, but not if I give the hostnames). I tried manually configuring DNS addresses (given by campus network support, and the same ones which my laptop and other computers seem to connect to when plugged in via ethernet) using Network Manager, but the results were the same.

What makes it so weird is that everything works when I connect via my wireless router. I think it's a problem with my installation because I booted from an elementary OS usb stick, and everything worked fine when I connected outside of my router - I could access all websites using hostnames.

Here are outputs from "nmcli dev show" for various instances-

From Kubuntu, connecting through my wireless router (everything works) - [http://paste.ubuntu.com/15703658/](http://paste.ubuntu.com/15703658/)
From elementary OS, connecting through ethernet (everything works) - [http://paste.ubuntu.com/15703670/](http://paste.ubuntu.com/15703670/)
From Kubuntu, connecting through ethernet (problem listed above - cannot access hostnames, can ping ips) - [http://paste.ubuntu.com/15703678/](http://paste.ubuntu.com/15703678/)
(the results are similar to the last, no matter where else I connect on campus)

This is info from my wireless router-
Connection Type 	Dynamic
WAN IP 	10.8.16.173
Subnet Mask 	255.255.254.0
Default Gateway 	10.8.16.1
DNS Address 	10.1.2.61

I spent a lot of time with my campus network support, but they weren't able to figure it out. They did check and guarantee that there were no blocks in place, and that the network does not discriminate against Linux or any OSes. I have installed Kubuntu 15.10 on a friend's laptop and another friend's PC, and both those installations are working fine connecting directly to ethernet ports on the campus network.

I did do an initial search, and as suggested [here]("http://askubuntu.com/questions/368435/how-do-i-fix-dns-resolving-which-doesnt-work-after-upgrading-to-ubuntu-13-10-s"), commented out "dns=dnsmasq" in /etc/NetworkManager/NetworkManager.conf . Did not help, results were the same.

Any help would be very much appreciated! Thank you for your time and patience.

---

### Post by neogarfield on 2016-04-13
Sorry to bump this up, but anyone? Any help on how to proceed or what to check?

---

### Post by apohal9 on 2016-04-13
When the problem occurs, try to ping 10.1.2.61 and if it responding, "dig www.google.com" as well as "dig @10.1.2.61 www.google.com".
What's the output then?

---

### Post by neogarfield on 2016-04-14
Thank you for the response!

When the problem occurs, a ping to 10.1.2.61 goes through.
Dig [www.google.com](www.google.com) returns no result, it times out.
Dig @10.1.2.61 [www.google.com](www.google.com) returned the following result-
> 
; <<>> DiG 9.9.5-11ubuntu1.2-Ubuntu <<>> @10.1.2.61 [www.google.com](www.google.com)
; (1 server found)
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 27587
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 4000
;; QUESTION SECTION:
;[www.google.com](www.google.com).			IN	A

;; ANSWER SECTION:
[www.google.com](www.google.com).		167	IN	A	216.58.220.36

;; Query time: 1 msec
;; SERVER: 10.1.2.61#53(10.1.2.61)
;; WHEN: Thu Apr 14 15:39:41 IST 2016
;; MSG SIZE  rcvd: 59



---

