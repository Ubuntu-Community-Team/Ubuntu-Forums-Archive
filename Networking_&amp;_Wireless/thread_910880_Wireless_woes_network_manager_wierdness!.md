---
title: "Wireless woes network manager wierdness!"
date: 2008-09-05
forum: Networking &amp; Wireless
---

### Post by jbarby on 2008-09-05
Hi,

I am currently running Ubuntu 8.04

When I installed the distribution i had 3 network cards.

Onboard Nvidia MCP73V
Realtek 8139 chipset nic
Wireless Ralink chipset card

The Onboard Nvidia card works mostly I do have dropped packets and it seems to max out at 30-40k per sec while a windows box on the same network can easily hit 300k.

The Realtek card was recognized but could never pickup DHCP when I moved the cable from the onboard to this card the card has since been removed.

The Wireless Ralink chipset card has a linux driver that I installed and I can see the wireless networks. 

I tried to connect to the wep open to no avail so I went into the settings and changed it to wpa-psk the best available on the wireless router. 

I seemed to connect the first time grabbed an ip but no dns or gateway and has since not picked up dhcp at all. 

I have selected the ssid of my network then went down to the command line and typed iwconfig and found that the essid is NETGEAR another AP with a weak signal and not the one I want to connect to. 

I tried to set the connection manually through network manager verified it with iwconfig reset the network via /etc/init.d/networking restart then looked at ifconfig saw that i am getting a valid 192.x.x.x address but I am not able to ping anything I cannot even ping the router. 

My resolv.conf has the ip of the router.

I have a pretty vanilla install of ubuntu is there something that could be blocking my wireless. iptables -L shows the following:

> Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

Output of lspci:

> 00:00.0 Host bridge: nVidia Corporation Unknown device 07c3 (rev a2)
00:00.1 RAM memory: nVidia Corporation nForce 630i memory controller (rev a2)
00:01.0 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.1 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.2 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.3 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.4 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.5 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.6 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:02.0 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:03.0 ISA bridge: nVidia Corporation MCP73 LPC Bridge (rev a2)
00:03.1 SMBus: nVidia Corporation MCP73 SMBus (rev a1)
00:03.2 RAM memory: nVidia Corporation MCP73 Memory Controller (rev a1)
00:03.4 RAM memory: nVidia Corporation MCP73 Memory Controller (rev a1)
00:04.0 USB Controller: nVidia Corporation GeForce 7100/nForce 630i (rev a1)
00:04.1 USB Controller: nVidia Corporation GeForce 7100/nForce 630i (rev a1)
00:08.0 IDE interface: nVidia Corporation MCP73 IDE (rev a1)
00:09.0 Audio device: nVidia Corporation MCP73 High Definition Audio (rev a1)
00:0a.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0b.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0c.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0d.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0e.0 SATA controller: nVidia Corporation Unknown device 0584 (rev a2)
00:0f.0 Ethernet controller: nVidia Corporation MCP73 Ethernet (rev a2)
01:06.0 Network controller: RaLink Unknown device 0601
02:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GT (rev a1)

If you need any more information I'll be happy to provide.
Please help!!

---

### Post by Crafty Kisses on 2008-09-05
Post the results of this command: ```
lshw -C network
```

---

### Post by jbarby on 2008-09-05
> **Codename said:**
> Post the results of this command: ```
lshw -C network
```

Sure thing!

> 
  *-network               
       description: Wireless interface
       product: RaLink
       vendor: RaLink
       physical id: 6
       bus info: pci@0000:01:06.0
       logical name: ra0
       version: 00
       serial: 00:0e:2e:ea:88:37
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2860 latency=64 maxlatency=4 mingnt=2 module=rt2860sta multicast=yes wireless=RT2860 Wireless
  *-network
       description: Ethernet interface
       product: MCP73 Ethernet
       vendor: nVidia Corporation
       physical id: f
       bus info: pci@0000:00:0f.0
       logical name: eth1
       version: a2
       serial: 00:1e:90:ee:36:35
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 duplex=full ip=192.168.1.91 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s



---

