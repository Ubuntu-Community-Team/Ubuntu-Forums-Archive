---
title: "Pptp Dns/wins"
date: 2007-05-02
forum: Networking &amp; Wireless
---

### Post by skiani on 2007-05-02
Hi,

I've got the my VPN connection work (PPTP) except for one minor problem. I can't find systems on the other side of the VPN. I can find internet addresses just fine, but when I try to ping a server on the network I'm connecting to it can't find the address. If I know the address I can ping, RDC, SMB whatever. The PPTP host is MS small business server. Also, the DNS on my network settings gets reconfigured to my corporate DNS when I connect. Typically on our network I just ping "servername" and it finds it. When I ping from computer inside will list the address as "servername.OurDomain.local" (it's a private IP set). So I try to pin "servername.OurDomain.local" from my VPN client, it thinks for minute then says unknown host.  I also have an linux box inside the net and to get it to properly find addresses I had to set up WINS client in samba, now it can ping addresses inside the domain. I tried setting up my VPN client the same with no luck.

Any suggestions?

Thanks,
SK

---

