---
title: "Wired ethernet connexion not recognized Lucid Lynx"
date: 2010-05-01
forum: New to Ubuntu
---

### Post by Unbearable_bear on 2010-05-01
Hi everyone !
I'm quite a complete beginner with Ubuntu Lucid Lynx, and I managed to find a problem as soon as I started using it, I must have a gift for that...
I'm on dual boot with Windows Seven, on which I use a wired Ethernet connexion. On Seven, as soon as I plug the cable in, my connexion is immediately recognized and works fine, without any static setting.So I assume DHCP works fine too.
The problem is that it is supposed to do the same on ubuntu with NetworkManager, while it's not :x
In fact, I also have a wireless connexion, and as weird as it seems, it works without any problems (and I'm actually using this one).
Even if I disable the wireless connexion, there is just no way to get the wired connexion :
"Wired Network
    disconnected"
I tried a lot things to solve the problem:
-Reinstall NetworkManager
-Apply a static connexion
-Disable ipV6 (in fact it was already disabled)
None of them worked :o

Here is are some of my configs, hope it'll help:
ifconfig :
eth0      Link encap:Ethernet  HWaddr 00:23:5a:ff:71:e9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:29 Base address:0x8000 

eth0:avahi Link encap:Ethernet  HWaddr 00:23:5a:ff:71:e9  
          inet addr:169.254.11.38  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:29 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:32 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2144 (2.1 KB)  TX bytes:2144 (2.1 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1e:65:65:6a:1a  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:65ff:fe65:6a1a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10802 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9946 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11782512 (11.7 MB)  TX bytes:1854006 (1.8 MB)

route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0

my hosts file :
127.0.0.1    localhost
127.0.1.1    unbearablebear-laptop

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

my interface file :
auto lo
iface lo inet loopback

And I have no wired connexion configured in the NetworkManager

Merci d'avance ! (french :) )

---

### Post by firesock on 2010-05-10
Same problem here :(

Wireless works perfect but wired isn't detected, nothing happens when i plug the cable.

Any idea? 


THANK YOU!!

---

### Post by alphacrucis2 on 2010-05-10
> **firesock said:**
> Same problem here :(

Wireless works perfect but wired isn't detected, nothing happens when i plug the cable.

Any idea? 


THANK YOU!!

Could be the ethernet card isn't being recognised. What does:

```
lspci -k
```

display for your ethernet controller?

Also what does:

```
sudo ethtool eth0
```

say?

---

### Post by awilkin on 2010-05-10
Have the same issue. Not sure is this is the correct cure but I edited /etc/network/interfaces to: -

auto lo eth0
iface lo inet loopback
iface eth0 inet dhcp

Now get a wired connection but Network Manager still states unmanaged. Right click brings up 2 options, New wired connection and Manage Connections. Doesn't seem to matter what I add to the Wired Connection tab, Network Manager states unmanaged.

Andrew

---

### Post by firesock on 2010-05-14
hi!!

Magically it was solved with an update...

Some day I plugged the Ethernet cable and it worked. Maybe it was a bug, but now for me it's solved.

Thank you very much ;)

---

### Post by Rewarp on 2010-06-02
Good day to all.

I recently did a fresh installation of Lucid Lynx after three successful years of Ubuntu on my Compaq F762AU. Never before has a distro given me so much trouble on the wired connection out of the box.

During the installation, updates could be retrieved via the wired connection, and when Lucid loaded, I downloaded the nVidia drivers and ran Update Manager - after which I did a reboot.

The wired connection could be seen attempting to connect, but fails to do so. Thinking this could be an issue with the updates, I loaded the Live CD and still couldn't get a connection.

I did another fresh installation and it still wouldn't recognise my wired connection.

Using Karmic Koala's Live CD yielded the same results.

As I do not have a wireless router, and am connected directly to the Internet via my modem, it is not yet possible to verify whether or not the wireless connection works.

Here are some readouts:
```
rewarp@Enceladus:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 4a:bf:69:8f:99:59  
          inet6 addr: fe80::48bf:69ff:fe8f:9959/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:2222 (2.2 KB)
          Interrupt:27 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:76 errors:0 dropped:0 overruns:0 frame:0
          TX packets:76 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5840 (5.8 KB)  TX bytes:5840 (5.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3a:8f:5e:88  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

```
rewarp@Enceladus:~$ lspci -k
00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
	Kernel driver in use: nForce2_smbus
	Kernel modules: i2c-nforce2
00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.3 Co-processor: nVidia Corporation MCP67 Co-processor (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
	Kernel driver in use: ohci_hcd
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
	Kernel driver in use: ehci_hcd
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
	Kernel driver in use: ohci_hcd
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
	Kernel driver in use: ehci_hcd
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
	Kernel driver in use: pata_amd
	Kernel modules: pata_amd
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
	Kernel driver in use: ahci
	Kernel modules: ahci
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
	Kernel driver in use: forcedeth
	Kernel modules: forcedeth
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:12.0 VGA compatible controller: nVidia Corporation C67 [GeForce 7000M / nForce 610M] (rev a2)
	Kernel driver in use: nouveau
	Kernel modules: nvidiafb, nouveau
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
	Kernel modules: amd64_edac_mod
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
	Kernel driver in use: k8temp
	Kernel modules: k8temp
02:05.0 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci
02:05.1 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
	Kernel modules: ricoh_mmc
02:05.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:05.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
03:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
	Kernel driver in use: ath5k
	Kernel modules: ath5k
```

```
rewarp@Enceladus:~$ sudo ethtool eth0
[sudo] password for rewarp: 
Settings for eth0:
	Supported ports: [ MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Advertised pause frame use: No
	Advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: MII
	PHYAD: 1
	Transceiver: external
	Auto-negotiation: on
	Supports Wake-on: g
	Wake-on: d
	Link detected: yes
```

This problem is quite frustrating, but I trust the Ubuntu community will pull through for me as usual. :)

---

