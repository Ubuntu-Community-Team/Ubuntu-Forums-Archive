---
title: "IP MASQ Bottleneck"
date: 2007-08-06
forum: Networking &amp; Wireless
---

### Post by ShOrTwAvE on 2007-08-06
I'm having some throughput issues with my MASQ'd clients. I set up everything via tutorial posted here:
hxxp://ubuntuforums.org/showthread.php?t=91370

Everything is up and working on server and client side. But, after some bandwidth tests I notice a degrade in performance on my clients. Tests done on the MASQ server give results of 1.5Mb connections to the internet. While my clients only show results varying from 400-500kb.

Is there anything that can be done to optimize this? Anyone know of why I would be having these issues? I have 2 clients set-up and both are connected @ 11Mb to my router. I'll try and portray my network set-up for you below:

Internet => WRT54G =>(wirelessly via atheros) Ubuntu MASQ server => (wired) BEFW11S4 => (wirelessly) MASQ'd clients

IP settings are as followed:
WRT54G: 192.168.1.1
Ubuntu atheros card: 192.168.1.1 (connected to WRT54g wirelessly)
Ubuntu 3com: 192.168.100.10 (connected to BEFW11S4 wired)
BEFW11S4: 192.168.100.1 (MASQ's clients connect here wirelessly)
Other clients: 192.168.100.* range

All clients are set-up as MASQ server being thier gateway. The BEFW11S4 does no routing or filtering. It just gives me a connection to my MASQ server. My MASQ'd clients are all configured staticly. Any help or input here would be great. 

Thanks in advanced!

Some added info:
MASQ server is a PIII 733Mhz w/320MB
Also my uploads seem to stay pretty consistant. Varying around 800-1000kb p/s
Changing my MASQ servers connection to WRT54G from 11Mb => 5Mb doesn't change anything really

Would it be better for me to connect my eth0 interface up to my WAN port of my internal BEFW11S4 router?

---

