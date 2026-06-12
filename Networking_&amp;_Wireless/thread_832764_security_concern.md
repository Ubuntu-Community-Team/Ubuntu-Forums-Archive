---
title: "security concern"
date: 2008-06-18
forum: Networking &amp; Wireless
---

### Post by sandman2600 on 2008-06-18
I'm new to Ubuntu.  I just configured a pcmcia wireless card on my laptop to use my home wireless gateway.  In the Network Settings tool, there are four tabs:  connections, general, DNS, hosts.  When I click on the "hosts" tab there is a long list of hosts.  Here are some examples:
127.0.0.1  localhost
127.0.1.1  jimmy-laptop  (my computer name)
::1        ip6-localhost ip6-loopback
fe00::0    ip6-localne"
ff00::0    ip6-mcastprefix

the list goes on...

Other than my computer name, what are these other entries???  Are they other users who are using my bandwidth?

---

### Post by maddog39 on 2008-06-18
Ummm... no those other entries are IPv6 addresses to things on the local machine. Other things that may be in that list are the names and associated IP addresses of other computer on your local network. Nothing in there will ever be a security risk as they are just human readable aliases to IP addresses. Unless of course someone is able to change one in such a way as to either deny you service to network functionality or take advantage of it in order to infect your system with say a rootkit. However you should never have to worry about that as it would require direct access to the machine (most likely) and other attack vectors are far more affective. If anyone were to even want to go to that length.

---

### Post by sandman2600 on 2008-06-18
> **maddog39 said:**
> Ummm... no those other entries are IPv6 addresses to things on the local machine. Other things that may be in that list are the names and associated IP addresses of other computer on your local network. Nothing in there will ever be a security risk as they are just human readable aliases to IP addresses. Unless of course someone is able to change one in such a way as to either deny you service to network functionality or take advantage of it in order to infect your system with say a rootkit. However you should never have to worry about that as it would require direct access to the machine (most likely) and other attack vectors are far more affective. If anyone were to even want to go to that length.

much appreciated....At least I can relax now while I learn how to use liux, without worries

---

