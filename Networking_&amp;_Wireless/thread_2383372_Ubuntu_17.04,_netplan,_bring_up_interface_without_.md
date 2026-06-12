---
title: "Ubuntu 17.04, netplan, bring up interface without ip"
date: 2018-01-24
forum: Networking &amp; Wireless
---

### Post by 0x19xx on 2018-01-24
Hello everyone,


I'm having difficulties with this new netplan in just bringing up a network interface with no IP.


I'm running 17.04 and have noticed that /etc/network/interfaces is completely ignored and I now have to use /etc/netplan/01-netcfg.yaml instead.


Problem is, I could not find the syntax to just bring up an interface with no IP assigned.


I tried "dhcp: no" but it didn't work. 


How can I simply up the interface?

---

### Post by chili555 on 2018-01-24
May we see the contents, please?```
cat /etc/netplan/01-netcfg.yaml 
```If you simply boot the computer and then run:```
ifconfig
```If the interface doesn't show as up automatically, then something else  is wrong:```
chili@T440p:~$ ifconfig
enp0s25: flags=4099<[COLOR="#FF0000"]UP[/COLOR],BROADCAST,MULTICAST>  mtu 1500
        ether 68:f7:28:ae:83:47  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 20  memory 0xe0600000-e0620000  
```Let's track down what's happening first.

Which interface is it? Let's start by checking the log for any clues:```
dmesg | grep enp0s25
```Of course, substitute your actual interface if not enp0s25.

---

