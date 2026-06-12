---
title: "DHCP problem"
date: 2007-03-08
forum: Networking &amp; Wireless
---

### Post by kgn on 2007-03-08
Hi,


When using dhcp on Edgy i receive an IP with incorrect netmask (/28 instead of /24). Because the default-gateway is out of the /28 space, kernel doesn't install the default into the routing table. There is no difference when using wire/wireless connection. Windows XP works as it should, and netmask is correct.

If any of You have some ideas i'd be more than thankfull for any hints.

All the best,

kgn

---

### Post by Mr. C. on 2007-03-08
If you are using DHCP, it is the responsibility of the DHCP server to hand out the netmask.  If it is incorrect, then there is a misconfiguration of the DHCP service.  Where is your DHCP server?  Your ISP?  Your own Router?

Show output from :

ifconfig -a
route -rn

MrC

---

### Post by kgn on 2007-03-09
> **Mr. C. said:**
> If you are using DHCP, it is the responsibility of the DHCP server to hand out the netmask.  If it is incorrect, then there is a misconfiguration of the DHCP service.  Where is your DHCP server?  Your ISP?  Your own Router?

MrC

Hi,

I know that, the problem is i have no access to this server. Actually i don't think that there is a bug in Edgy, but something wrong with DHCP config on the server. The problem is that XP behaves correctly on the same PC and the same link to ISP. I'll try contact with the ISP.
I have no access to the mentioned dhcp-client computer, but afair there was only one entry in routing table (assgined_ip_network/28) and interface has only assgined_ip/28.
As I say, will contact with ISP and probably the problem dissapear.

Thnks,

---

### Post by kgn on 2007-03-09
Hi,

Yeap, the problem was related to dhcp-server config. Sorry for making unnecessary noise.

All the best,
kgn

---

