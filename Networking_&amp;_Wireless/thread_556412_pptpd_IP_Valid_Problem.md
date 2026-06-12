---
title: "pptpd IP Valid Problem"
date: 2007-09-21
forum: Networking &amp; Wireless
---

### Post by FiFtHeLeMeNt on 2007-09-21
Hi,
I have installed pptpd on Feitsy , but I am facing a strange problem. I have assigned 192.168.10.1 to pptpd as localip and 192.168.10.10-100 as remoteips. I have done all of ip forwarding and masquerade and it is working great for these clients who have non valid IPs.
I have assigned Valid IPs to some of my users and sometimes they can not access the internet through my VPN server , it seems like an arp problem , because when they can not access the net , I just set their IP on my NIC and then I remove it and then when they connect it works fine !
it seems to me pptpd doent advertise their address on the net. I have proxyarp in my pptpd-options.
does anyone have any idea about it ?
Regards

---

