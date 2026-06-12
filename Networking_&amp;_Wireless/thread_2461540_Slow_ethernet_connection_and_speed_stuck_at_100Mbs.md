---
title: "Slow ethernet connection and speed stuck at 100Mb/s"
date: 2021-05-02
forum: Networking &amp; Wireless
---

### Post by drcid98 on 2021-05-02
A while ago I updated my internet plan to a 5g connection, while the wifi speed reaches up to 500Mb/s on my cellphone and my laptop, the ethernet speed is  as low as 60Mb/s on my machine (running ubuntu 20.04). I've tried solving this changing the ethernet (now I'm using a cat 6e and I've tried with a cat 5e) and the speed remains unchanged. This and the fact that my ps4, which is connected with ethernet, reaches up to 600Mb/s has made realize that the problem I'm facing is linnux-related. I've searched for answers in this and other forums but nothing seems to work. ethloot gives me
```
 sudo ethtool enp3s0 
Settings for enp3s0:
	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Supported pause frame use: Symmetric Receive-only
	Supports auto-negotiation: Yes
	Supported FEC modes: Not reported
	Advertised link modes:  100baseT/Full 
	Advertised pause frame use: No
	Advertised auto-negotiation: Yes
	Advertised FEC modes: Not reported
	Link partner advertised link modes:  10baseT/Half 10baseT/Full 
	                                     100baseT/Half 100baseT/Full 
	                                     1000baseT/Full 
	Link partner advertised pause frame use: No
	Link partner advertised auto-negotiation: Yes
	Link partner advertised FEC modes: Not reported
	Speed: 100Mb/s
	Duplex: Full
	Port: Twisted Pair
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	MDI-X: Unknown
	Supports Wake-on: pumbg
	Wake-on: g
	Current message level: 0x00000033 (51)
			       drv probe ifdown ifup
	Link detected: yes
 
```

As it's shown above, the speed is stuck at 100Mb/s while a 1000 is allowed. lspci gives me

```

sudo lspci
00:00.0 Host bridge: Intel Corporation Device 9b53 (rev 03)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor PCIe Controller (x16) (rev 03)
00:14.0 USB controller: Intel Corporation Comet Lake USB 3.1 xHCI Host Controller
00:14.2 RAM memory: Intel Corporation Comet Lake PCH Shared SRAM
00:15.0 Serial bus controller [0c80]: Intel Corporation Comet Lake PCH Serial IO I2C Controller #0
00:15.1 Serial bus controller [0c80]: Intel Corporation Comet Lake PCH Serial IO I2C Controller #1
00:16.0 Communication controller: Intel Corporation Comet Lake HECI Controller
00:17.0 SATA controller: Intel Corporation Device 06d2
00:1d.0 PCI bridge: Intel Corporation Comet Lake PCI Express Root Port #9 (rev f0)
00:1d.3 PCI bridge: Intel Corporation Device 06b3 (rev f0)
00:1f.0 ISA bridge: Intel Corporation Device 0684
00:1f.3 Audio device: Intel Corporation Comet Lake PCH cAVS
00:1f.4 SMBus: Intel Corporation Comet Lake PCH SMBus Controller
00:1f.5 Serial bus controller [0c80]: Intel Corporation Comet Lake PCH SPI Controller
01:00.0 VGA compatible controller: NVIDIA Corporation GK208B [GeForce GT 730] (rev a1)
01:00.1 Audio device: NVIDIA Corporation GK208 HDMI/DP Audio Controller (rev a1)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 15)

```

Besides trying with different cables and testing them in different devices, I've tried some "solutions" in this forum like [this]("https://ubuntuforums.org/archive/index.php/t-1048267.html") and nothing seems to work, I ran ```
sudo ethtool -s enp3s0 speed 1000 duplex full autoneg on 
``` and after that I lose connection and ethtool gives me
```

sudo ethtool enp3s0 
Settings for enp3s0:
	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Supported pause frame use: Symmetric Receive-only
	Supports auto-negotiation: Yes
	Supported FEC modes: Not reported
	Advertised link modes:  1000baseT/Full 
	Advertised pause frame use: No
	Advertised auto-negotiation: Yes
	Advertised FEC modes: Not reported
	Speed: Unknown!
	Duplex: Unknown! (255)
	Port: Twisted Pair
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	MDI-X: Unknown
	Supports Wake-on: pumbg
	Wake-on: g
	Current message level: 0x00000033 (51)
			       drv probe ifdown ifup
	Link detected: no

```

I've also tried solving it [this way]("https://askubuntu.com/questions/1236926/how-do-i-set-ethernet-speed-for-ubuntu-20-04-permanently") and I get the same problem as before. I really don't know what to do anymore so if someone could please help me I'd be grateful. If more information is needed please let me know.

---

### Post by praseodym on 2021-05-02
Which driver is it? Please show
```

lsmod | grep r8
```
If r8169 is shown, then run
```

sudo apt install r8168-dkms
echo "blacklist r8169" | sudo tee /etc/modprobe.d/blacklist-r8169.conf
```
and reboot

---

### Post by The Cog on 2021-05-02
It may be worth trying turning auto-negotiation off at both ends and configuring them for a fixed 1000 Mb/S.

---

### Post by drcid98 on 2021-05-02
[**[COLOR=#000000]praseodym[/COLOR]**]("https://ubuntuforums.org/member.php?u=1411497"), It shows
```

lsmod | grep r8
r8168                 548864  0

```

---

### Post by drcid98 on 2021-05-02
[**[COLOR=#DD4814][B]The Cog**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=437760"), I tried that and I get the same problem I described when i ran  sudo ethtool -s enp3s0 speed 1000 duplex full autoneg on

---

