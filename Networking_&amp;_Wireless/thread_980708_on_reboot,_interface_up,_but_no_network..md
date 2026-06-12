---
title: "on reboot, interface up, but no network."
date: 2008-11-13
forum: Networking &amp; Wireless
---

### Post by dutler on 2008-11-13
On reboot - no network.
Ubuntu Server 8.04.1 w/ kubuntu-desktop 2.6.24-19-server

I have been using a bridge for weeks with out any problems. I installed bridge-utils and configured /etc/network/interfaces as such:
```
auto eth0
iface eth0 inet manual

auto br0
iface br0 inet dhcp
    bridge_ports eth0 vbox0 vbox1 vbox2 vbox3
```

I did this so my virtualbox guest could have a host interface. Two days ago, I had to powercycle my machine. On reboot kdm crashed (nvida twinview) - couldnt fix it and finally realized I had booted 2.6.24-19-virtual (a mistake installing vbox???). I uninstalled 2.6.24-19-virtual and rebooted to -server, Now no prob with kdm, but still problems with the network.

br0 is present and shows as being up, but does not find any dhcp offers. I have tried to static assign an ip, still acts like its a layer0 issue... have also tried removing the bridge and have restarted network service and reconfigured dhcp3-client.

Im not worried about saving my bridge functionally nor the vbox guest. At the moment I only care about restoring network functionality to the host. 

Can I "factory restore" the network services, riding my system off any bugger'd config files and what not?

-tom

---

### Post by dutler on 2008-11-20
I managed to get intermittent partial network access, but it became time to restore service rather than figure it out and I reinstalled the OS.

---

