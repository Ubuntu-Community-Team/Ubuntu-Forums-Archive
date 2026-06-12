---
title: "Ubuntu Server 12.04LTS - Specific ports aren't &quot;working&quot; - Hosting Valve Game Server"
date: 2014-10-28
forum: Networking &amp; Wireless
---

### Post by owena1337 on 2014-10-28
Hi,

So I have a home server running Ubuntu Server 12.04LTS connected directly to the Virgin Media SuperHub. The server has an IP reserved (192.168.0.100) and is also set to be in a DMZ. I can access the server from over the internet completely fine - SSH, Web/Mail Server etc, however when running a Valve Game Server for the Game "Team Fortress 2", I cannot access it when using the default port the server is running on - 27015. Instead, I have to use another port range such as from Minecraft - 25592, 25593 etc. 

Any ideas? I've never been able to get my head around it. It's always been like this even if I do a full clean install of Ubuntu Server.

Thanks,
Owen.

---

### Post by TheFu on 2014-10-28
Does your ISP filter ports?  Run a scan from outside.  Many residential ISPs **absolutely** filter inbound requests.

Of course, you realize that running a normal, non-hardened, linux machine directly on the internet is dangerous, right?

---

### Post by owena1337 on 2014-10-28
The server is pretty secure. No one can gain SSH access without accessing the VPN. It's just the port issue which is bothering me. I've isolated the issue that it is definitely something to do with the Ubuntu Server since I ran the same game server from my Windows machine and it was accessible via the internet.

---

### Post by TheFu on 2014-10-28
> **owena1337 said:**
> The server is pretty secure. No one can gain SSH access without accessing the VPN. It's just the port issue which is bothering me. I've isolated the issue that it is definitely something to do with the Ubuntu Server since I ran the same game server from my Windows machine and it was accessible via the internet.

Not really worried about ssh - THAT is the most secure service in your list - with **fail2ban** running and not allowing passwords for authentication,  pretty much bullet proof. All the other stuff is scary. Perhaps my limited idea of DMZ is outdated?

Could a firewall have been enabled on the box?  **sudo iptables -L** will dump any rules.  Could the edge router rules have changed? Could the edge router have been dynamically updated through non-secure UPnP methods?

---

