---
title: "Configure DNS Server"
date: 2014-04-13
forum: Networking &amp; Wireless
---

### Post by alfredo3 on 2014-04-13
I want to create a DNS Server. The first step is create the eth0 interface with IP. I have used these commands: 
[HTML]auto eth0
iface eth0 inet static
address 192.168.1.5
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1
# dns-nameservers[/HTML]

The issue is when apply the changes then lose wifi connection (wlan0). These wlan0 and eth0 interfaces are in the same subnet (192.168.1.0). I sould change the subnet in the eth0 interface??  What subnet would can to use??

Thanks,

---

### Post by SeijiSensei on 2014-04-14
If you are setting up a server on a wired network, you should simply disable the wifi adapter and rely on Ethernet.  You might be able to disable it from NetworkManager, or you could turn it off in the BIOS.

---

