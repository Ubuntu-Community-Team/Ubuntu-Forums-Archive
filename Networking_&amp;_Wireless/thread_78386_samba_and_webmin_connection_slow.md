---
title: "samba and webmin connection slow"
date: 2005-10-18
forum: Networking &amp; Wireless
---

### Post by LongLife on 2005-10-18
Hello,

Here's my network :

- Ubuntu server 5.04 on Pentium 200, 128Mo RAM
Samba server
Webmin
Squid 
Dansguardian
permanent ip address (class C)
100mb Ethernet


- Netgear ADSL DG834 router modem 
Dhcp activated  (Class C) but some ip addresses are permanent
ADSL gateway
Firewall
2 hubs


Clients :
10 XP home workstations (700-3000mhz, 256Mo RAM)
100mb Ethernet

Both server and test client have permanent addresses declared in hosts.conf and hosts.ini

Problems :
- First connection to samba shares via explorer are slow (4-6secs), but after that, browsing shares is fast
- Each connection to Webmin is slow :it takes 4-6 secs to load each page. I use Firefox and disabled IPv6 in about:config. Same problem with I.E.

It could be worse, but it's annoying anyway and I'd like to solve the problem

Thanks

---

### Post by supergrapeman on 2005-10-23
[QUOTE=LongLife]Hello,

Here's my network :

- Ubuntu server 5.04 on Pentium 200, 128Mo RAM
Samba server
Webmin
Squid 
Dansguardian
permanent ip address (class C)
100mb Ethernet


- Netgear ADSL DG834 router modem 
Dhcp activated  (Class C) but some ip addresses are permanent
ADSL gateway
Firewall
2 hubs


Clients :
10 XP home workstations (700-3000mhz, 256Mo RAM)
100mb Ethernet

Both server and test client have permanent addresses declared in hosts.conf and hosts.ini

Problems :
- First connection to samba shares via explorer are slow (4-6secs), but after that, browsing shares is fast
- Each connection to Webmin is slow :it takes 4-6 secs to load each page. I use Firefox and disabled IPv6 in about:config. Same problem with I.E.

It could be worse, but it's annoying anyway and I'd like to solve the problem

Thanks[/QUOTE]

I've found this kind of slowness is often DNS related.

You mention adding hosts to the hosts.conf and hosts.ini files. I have never heard of such files, either under Linux or Windows.

Try adding the machine name and IP address pairs for your clients and your server to the appropriate hosts file (/etc/hosts under linux, something like c:\windows\system32\etc\drivers\hosts under windows).

---

