---
title: "VPNC and DNS"
date: 2006-12-20
forum: Networking &amp; Wireless
---

### Post by diesel4555 on 2006-12-20
Folks,

I am a newbie at this but have benefitted from this fourm so I wanted to give back.   

I installed VPNC and got it working, with the help of this fourm of course.  The only problem was that the DNS info would not be correct once the tunnel was started.  Basicly resolve.conf would not get updated when a tunnel would be created by VPNC.

So I went to /etc/network/interface and edit that file and added...
BTW, I use DHCP and my wireless connection.

auto tun0
iface tun0 inet dhcp


This way whenever I will run VPNC the tunnel tun0 would get created and would run DCHP and hence get the correct DNS info.

When I disconnect from VPNC it will remove the tunnel and hence only my existing eth1 will be available with it's DNS info :p 

Hope that helps.

-Diesel

---

