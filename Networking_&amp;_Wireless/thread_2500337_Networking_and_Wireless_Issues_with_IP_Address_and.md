---
title: "Networking and Wireless Issues with IP Address and Router"
date: 2024-08-30
forum: Networking &amp; Wireless
---

### Post by sofiasovel on 2024-08-30
Hi community ,I&#8217;m having trouble with my network and wireless setup. My router is assigned an IP address [[SIZE=1]192.168.0.1[/SIZE]]("https://19216801.pro/")but devices connected to it are experiencing connectivity issues. Some devices can't connect to the network, while others frequently lose connection or show IP address conflicts. I&#8217;ve checked the router settings and ensured the DHCP server is working correctly, but the problems repeats. this is the kind of issue iam facing. give me any solution to solve my problem .Thank you .

---

### Post by TheFu on 2024-08-30
Sometimes the default settings of wifi-routers aren't good with all different wifi-adapters.  At one client, they had an expensive Netgear wifi router that was constantly dropping connections from Linux, but it all worked fine for MS-Window and Apple equipment.  I spent 5 hours trying to figure out what the issue was, but a my hourly rate, it became stupid, so I got them a Ubiquiti AP, plugged that into the Netgear and never looked back.  In addition to rock solid wifi connections, about 10x more clients could connect than the standard home-router wifi handled.

The new AP was just that, only for wifi and only an AP.  We kept using the Netgear for DHCP and LAN stuff.

BTW, if you ever hope to run a VPN and connect back home, it would be smart to change the router subnet from 192.168.0.1/24 to something less popular.  It is a routing tissue.  Something like 192.168.12.1/24 would be better - different enough to likely work from anywhere, but not so different as to confuse anyone.

As for IP address collisions, that is something you need to manage.  The way I do it is to split the DHCP subnet into about 3x more "guests" than I think I'll ever have.  Then setup the rest of the network for static IPs.  So, if I have 3 guests at home, they might need 9 DHCP IPs, so my DHCP range is x.x.x.245 - x.x.x.255 (10 IPs). More than enough.  x.x.x.1 - x.x.x.244 are all for static IPs.

Every device that isn't portable or isn't impossible to set to a static IP is setup on the LAN using .2 - .30.  That includes desktops, servers, VoIP equipment, printers.

Portable devices and those that cannot be manually set to static IPs get "reserved DHCP addresses".  That includes laptops using wired connections, network TV tuners, I think that's it. The key is to choose IPs from the static side of the router IP range, not the DHCP-side.  So IPs between .31 and .200 would work. Just be certain they don't conflict.

WiFi devices aren't trusted here, so they are placed onto an IoT (really IoSxxx) subnet, that is upstream from my main router.  I've learned that wifi is quite hackable in all the current and past standards, so wifi devices like phones, tablets aren't trusted until they connect to my VPN server. Some consider this overly paranoid.  Additionally, I put all guest devices on this subnet which is actually a 10.0.9.1/24 subnet.  Without connecting to my VPN, they only have internet access. No access to any trusted devices.  If we had any IoT cams, game consoles, or appliance devices, they'd be on this IoT network too.  From inside the secure LAN, the wifi LAN devices can be accessed.

You can look up how to setup DHCP reservations on your router.  Each router is a little different, but the overall idea is the same.  Usually, the MAC address for the eithernet card are used to determine which IP will be provided.  Both wired ethernet and wifi have MAC addresses. **ip neigh** is the command to see the different MAC addresses on a subnet. It will pull that information from the ARP table for any actively known devices.

You can look up how to setup static IPs for your desktops - it is in the OS/networking tool.  [https://help.ubuntu.com/stable/ubuntu-help/net-fixed-ip-address.html.en](https://help.ubuntu.com/stable/ubuntu-help/net-fixed-ip-address.html.en)

---

### Post by currentshaft on 2024-08-30
Does your router run Ubuntu? If not, why are you posting this here?

---

### Post by TheFu on 2024-08-30
> **currentshaft said:**
> Does your router run Ubuntu? If not, why are you posting this here?

I assume because the client systems are Ubuntu?

---

