---
title: "Cannot connect to a wired network after migration to Linux"
date: 2014-11-06
forum: Networking &amp; Wireless
---

### Post by kevin122 on 2014-11-06
I just downloaded and installed Ubuntu 14.04.1 and cannot get connected to my wired network.

I used to run exclusively Linux (primarily Ubuntu), but I never really got that good at it (I tried, it just wasn't a priority). I just used it because it ran better and with fewer problems than Windows, and because I agree with the open source mentality. A little over a year ago I purchased a new machine and had MAJOR issues when trying to install Linux. I tried several flavors, but nothing would successfully install. I got frustrated, gave up, and installed Windows 8. I again find myself wanting to move back to Linux and become more productive with it, but I am having an issue with networking. I have been trying to solve it for a few days, but I cannot figure it out and I need help

The Mobo I have is [GIGABYTE GA-990FXA-UD5 AM3+ AMD 990FX SATA 6Gb/s USB 3.0 ATX AMD Motherboard]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813128509") and has a Realtek RTL8111e

The OS is installed (Ubuntu 14.04.1), but it will not connect to the router.

I powercycled the desktop and the router, no effect.
I unplugged the network cable from the desktop and plugged it into my laptop (running Windows 8) and it connected without issue.
I found a few posts regarding problems with the r8169 driver, so I followed the instructions to replace the driver with the r8168, no effect. (I later read a post from Varunendra saying that the driver issue was no longer a problem)
Following directions from Varunendra's post in the thread at [http://ubuntuforums.org/showthread.php?t=2237120](http://ubuntuforums.org/showthread.php?t=2237120), I used```
sudo ifconfig eth0 192.168.1.60
```it still will not connect.
I used the GUI to set the IP, as well as the subnet and gateway, Linux claims that the connection is active, but the router cannot see the device, not can I ping anything on the network.
I uninstalled Linux and reinstalled Windows to confirm that the onboard NIC didn't coincidentally break while I was making this transition. It hadn't, Windows connected to the router without issue. 
I installed LXLE, same problem. I installed Scientific Linux 7, same problem. I reinstalled Ubuntu, and the problem (obviously) is persisting.
I tried manually setting the IP info again, still no luck. Linux reports that it is connected, but the router doesn't see it (I am accessing the router from my laptop) and the desktop cannot ping anything on the network (nor can anything ping it)

At first I thought it was a hardware incompatibility, but lots of people appear to be using this NIC. I hoped it was the driver. Then I thought it was my router (AT&T U-Verse provided Arris NVG589), but I found other people using the router without issue. Then I hoped it was DHCP settings, but they are good, and a manually ip address didn't work. Now I don't know how to proceed.

lspci shows the NIC as
```
05:00.0 Ethernet controller: Realtek Semconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)
```

nm-tool returns
```
NetworkManager Tool

State: connected (global)

- Device: eth0 [Wired connection 1]--------------------
Type:      Wired
Driver:     r8169
State:     connected
Default:    yes
HW Address:           94:DE:80:6A:83:2F

Capabilities:
Carrier Detect:     yes
Speed:        1000 Mb/s

Wired Properties
Carrier:       on

IPv4 Settings:
Address:      192.168.1.60
Prefix:         24 (255.255.255.0)
Gateway:       192.168.1.254

```

ethtool eth0 returns
```
Settings for eth0:
Supported ports: [ TP MII ]
Supported link modes: 10baseT/Half 10baseT/Full
                               100baseT/Half 100baseT/Full
                               1000baseT/Half 1000baseT/Full
Supported pause frame use: No
Supports auto-negotiation: Yes
Advertised link modes:  10baseT/Half 10baseT/Full
                               100baseT/Half 100baseT/Full
                               1000baseT/Half 1000baseT/Full
Advertised pause frame use: Symmetric Receive-only
Advertised auto-negotiation: Yes
Link partner advertised link modes:  10baseT/Half 10baseT/Full
                               100baseT/Half 100baseT/Full
                               1000baseT/Half 1000baseT/Full
Link partner advertised pause frame use: Transmit-only
Link partner advertised auto-negotiation: Yes
Speed: 1000Mb/s
Duplex: Full
Port: MII
PHYAD: 0
Transceiver: internal
Auto-negotiation: on
Cannot get wake-on-lan settings: Operation not permitted
Current message level: 0x00000033 (51)
drv probe ifdown ifup
Link detected:yes

```

I am very confused by the fact that Linux claims to be connected to the network, but nothing else on the network recognizes this. I am also confused because, to my understanding from the previous thread, assigning the IP, even without the gateway, should have put me on the network, but it does not.

I am at a loss, please help.

---

### Post by kevin122 on 2014-11-06
It never fails that asking for help causes one to find oversights. I searched for my problem and referenced the board and not the NIC. I found in a Red Hat thread that there is a setting in the BIOS on my mobo called IOMMU Controller. It is disabled by default, but needs to be enabled to get the networking working in Linux. I enabled it and now the NIC works like a charm.

---

