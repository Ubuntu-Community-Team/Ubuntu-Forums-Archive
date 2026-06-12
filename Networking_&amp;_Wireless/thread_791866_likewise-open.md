---
title: "likewise-open"
date: 2008-05-12
forum: Networking &amp; Wireless
---

### Post by redmansk8 on 2008-05-12
Hello I recently upgraded to 8.04 on my laptop. I was reading some of the features on 8.04 and I read about likewise-open. I thought I would try it out. In my office I have a win2000 server running a domain with active directory. When I try to connect to the domain from my laptop with ubuntu 8.04 using likewise-open I get this message
The configuration stage 'open ports to DC' cannot be completed automatically. Please manually perform the following steps and rerun the domain join:

Some required ports on the domain controller could not be contacted. Please update your firewall settings to ensure that the following ports are open to 'prodvana.local':
	88  UDP
	137 UDP
	389 UDP
	464 UDP
	123 UDP
	88 TCP
	139 TCP
	389 TCP
	445 TCP
	464 TCP

My laptop does not have a firewall and the server's firewall is set up to accept those ports. I even turned the firewall off on the server and still get the same thing. I was wondering does anyone know what can be causing this problem? thanks in advance for any help.

---

### Post by npallett on 2008-05-12
> **redmansk8 said:**
> Hello I recently upgraded to 8.04 on my laptop. I was reading some of the features on 8.04 and I read about likewise-open. I thought I would try it out. In my office I have a win2000 server running a domain with active directory. When I try to connect to the domain from my laptop with ubuntu 8.04 using likewise-open I get this message
The configuration stage 'open ports to DC' cannot be completed automatically. Please manually perform the following steps and rerun the domain join:

Some required ports on the domain controller could not be contacted. Please update your firewall settings to ensure that the following ports are open to 'prodvana.local':
	88  UDP
	137 UDP
	389 UDP
	464 UDP
	123 UDP
	88 TCP
	139 TCP
	389 TCP
	445 TCP
	464 TCP

My laptop does not have a firewall and the server's firewall is set up to accept those ports. I even turned the firewall off on the server and still get the same thing. I was wondering does anyone know what can be causing this problem? thanks in advance for any help.

I experienced the same problem with likewise-open when I tried to join to our AD Domain. I turned off my machine's firewall and checked that the required ports were accessible on the AD Domain Controller. I eventually discovered that the problem was DNS related. I am running a DNS Server on my machine and it was resoling the AD Domain name as the IP Address of my machine. When I set my machine to use the DNS Server of the AD Domain Controller, I was able to successfully join to the AD Domain using likewise-open.


Hope this helps.

---

