---
title: "Kubuntu 18.04 name resolution problem"
date: 2018-06-20
forum: Networking &amp; Wireless
---

### Post by gus_zernial on 2018-06-20
I just upgraded to Kubuntu 18.04. My primary wired ethernet adapter is configured for static ip using Kubuntu "System Settings/Connections/Edit your Network Connections". Upon boot, ifconfig shows the adapter up, and I can ping a site successfully by IP address but not by name, the latter showing "temporary failure in name resolution"

I'm using a Pi-Hole ad blocker on my LAN, which provides DNS services in conjunction with it's filtering function. Thus in "Edit your Network Connections" I specify the address of the Pi-Hole (192.168.X.X) under "Other DNS Servers". On boot I have no DNS resolution in my 18.04 box, see above, but if I edit /etc/resolv.conf and replace 127.0.0.1 by the same Pi-Hole box IP address, name resolution thereafter works. Of course that solution is not persistent across boots.

I note that the Pi Hole server correctly provides name resolution for other Windows and Mac boxes on the LAN, and provided name resolution to the Kubuntu box prior to upgrading to 18.04.

I've tried to track down the problem, and admit I'm thorougly confused by the relationship between "Kubuntu System Settings/Connections/Edit your Network Connections", NetworkManager, NetPlan/YAML files, resolvconf, /etc/resolv.conf, and the change from /etc/network/interfaces to whatever is the current method of network adapter configuration. I haven't been able to find Kubuntu documentation on this stuff, and my google searching hasn't bought me to enlightenment either. 

Would appreciate recommendations how to diagnose/fix the problem.

Thx, Gus

-------------------------- Update:

Per other posts I tried to configure the static adapter using my yaml file/etc /netplan/01-systemd-networkd-eth.yaml, as follows:

network:
  version: 2
  renderer: networkd
  ethernets:
    enp0s31f6:
     dhcp4: no
     dhcp6: no
     addresses: [192.168.1.17/24]
     gateway4: 192.168.1.1
     nameservers:
       addresses: [192.168.1.51]

After enjoying a series of misleading yaml syntax errors, I was able to get it thru # netplan generate && netplan apply without errors (the indents may not appear in this
forum post, but they're there and now produce no errors). But - same result "temporary failure in name resolution" after rebooting the 18.04 box.

---

