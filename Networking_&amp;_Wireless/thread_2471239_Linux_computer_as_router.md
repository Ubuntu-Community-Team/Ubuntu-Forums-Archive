---
title: "Linux computer as router"
date: 2022-01-24
forum: Networking &amp; Wireless
---

### Post by cazz on 2022-01-24
Wondering if anyone here runs linux on a computer as a router. One that has NAT, Firewall and VPN in one but is still easy to handle. 
Right now I have a router that I am quite happy with but am a little curious to try connecting a linux computer that handles firewall, port forward, VPN and DHCP.
A computer that has two network connections for WAN and LAN.

VPN may not be that important, you can add another computer to it but it would be nice if it had it built in anyway.

---

### Post by ajgreeny on 2022-01-24
I have no personal experience of anything related to this but a google search of ***linux router distro*** came up with this site and many other useful links which you may find useful.
[https://teklager.se/en/best-free-linux-router-firewall-software-2019/](https://teklager.se/en/best-free-linux-router-firewall-software-2019/)

---

### Post by rsteinmetz70112 on 2022-01-25
I have a computer that does limited routing, NAT and firewall. It doesn't have a VPN but I assume it could it I wanted to set it up.
I have it set up using iptables mostly to handle the public  satatic ips for our company.

---

### Post by morrownr on 2022-01-25
I use a Raspberry Pi 4B. The 4B has some horsepower to move data and is very flexible.

Here is a link if you want router software:

[https://openwrt.org/toh/raspberry_pi_foundation/raspberry_pi](https://openwrt.org/toh/raspberry_pi_foundation/raspberry_pi)

If you prefer to tinker more:

[https://github.com/morrownr/7612u/blob/main/AP_Mode-Bridged_Wireless_Access_Point.md](https://github.com/morrownr/7612u/blob/main/AP_Mode-Bridged_Wireless_Access_Point.md)

That is a guide to an access point setup but with a little tweaking it can do what you want.

If going this direction, you will want one or more USB WiFi adapters:

[https://github.com/morrownr/USB-WiFi](https://github.com/morrownr/USB-WiFi)

---

### Post by The Cog on 2022-01-25
I have set up an Ubuntu PC as a router in the past. It only had 4 (I think) interfaces, but it did a lot of policy routing and NAT work, with several thousand NAT entries. It dipped into a database server and updated its NAT rules every 5 minutes according to current requirements. The database dipping and logic to work out the required NAT entries were the reason we went for Linux. It worked very nicely. We were always surprised at how low the CPU and memory usage was. We also also took maybe 20 VPN clients (remote laptop users) and authenticated them against an LDAP server, but I don't remember if that was the same PC or not. We didn't do any DHCP, it was all static addresses.
There is quite a learning curve to get through, but it's all possible and works well when set up. I enjoyed doing it.

---

### Post by cazz on 2022-01-25
Thanks for all information.

Right now I'm curious about OPNsense or OpenWrt

I have a proxmox server already running with some VM on and I was thinking maybe add a NIC with two ethernet connection and use OPNsense or
maybe use a Raspberry Pi with OPenWrt-

I have a Raspberry Pi 3 already at home and also a USB-Ethernet adapter so maybe try that first, not sure yet.

---

### Post by him610 on 2022-01-25
You might want to check out this ... [https://openwrt.org/toh/raspberry_pi_foundation/raspberry_pi]("https://openwrt.org/toh/raspberry_pi_foundation/raspberry_pi")

---

### Post by daniellemil on 2022-02-03
I also wanted Linux computer as router! But somehow it is written in this article too complicated![ https://teklager.se/en/best-free-lin...software-2019/]("https://teklager.se/en/best-free-linux-router-firewall-software-2019/") I would like to find an easier solution!

---

### Post by morrownr on 2022-02-04
[https://www.raspberrypi.com/documentation/computers/configuration.html#setting-up-a-routed-wireless-access-point](https://www.raspberrypi.com/documentation/computers/configuration.html#setting-up-a-routed-wireless-access-point)

---

### Post by Tadaen_Sylvermane on 2022-02-04
I wrote a script that can auto configure a router. In my case I was trying to do a dual wan. The dual wan didn't work out so well but a single wan it seems to do just fine. It's a bit of a mess though. The machine was running a squid proxy with docker. wouldn't be too much to add a vpn to the machine.

[https://gitlab.com/jmgibson1981/homescripts/-/blob/master/router/homerouter.sh](https://gitlab.com/jmgibson1981/homescripts/-/blob/master/router/homerouter.sh)

---

