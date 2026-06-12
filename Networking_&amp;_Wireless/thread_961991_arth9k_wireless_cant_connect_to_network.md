---
title: "arth9k wireless cant connect to network"
date: 2008-10-28
forum: Networking &amp; Wireless
---

### Post by biphtec on 2008-10-28
I have downloaded the lastest drivers and everything installed without a hitch, but I can't connect to my network. I have tried IPv4 mode, DHCP, and Static IP configs and it always ends with no errors, but not connected.

Here is ifconfig output:
[FONT="Courier New"]eth0      Link encap:Ethernet  HWaddr 00:1e:33:46:a3:85  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:18102117365 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:251 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2036 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2036 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:107684 (105.1 KB)  TX bytes:107684 (105.1 KB)

wlan0     Link encap:Ethernet  HWaddr 00:22:68:af:a6:0d  
          inet addr:192.168.0.217  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-22-68-AF-A6-0D-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)[/FONT]

---

### Post by pytheas22 on 2008-10-28
It may help to connecting using [wicd]("http://wicd.sourceforge.net") instead of Network Manager.  There are installation instructions on wicd's site.  You could also try disabling security on your router to see if it makes a difference.

If that doesn't help, please post the output of:
```

lspci -nn | grep -i atheros
lshw -C Network
modinfo ath9k
```

---

### Post by Abdul Haqq on 2008-10-28
I have a similar problem which makes it difficult as to access the internet I have to go to another computer in another area for doing dumps etc.

For what it's worth this driver according to madwifi in installed in  the EEEPC so it must work.

I have just installed 8.04 'Hardy' onto my Asus X50RL laptop. This uses the Atheros AR5007 WiFi chipset. I followed the directiond dor installing the MadWifi driver in an earlier howto post. This driver has been superced by the new HAL madwifi-hal-0.10.5.6-r3861-20080903.

I have got it up and running and if finds my AP which has WEP 64bit encription. I have entered this in both ASCII and HEX but it refuses to accept it.

Where do I go from here?

---

### Post by pytheas22 on 2008-10-28
Abdul Haqq: I would also recommend that you give wicd a try.  You can install it offline by downloading the [Debian package]("http://downloads.sourceforge.net/wicd/wicd_1.5.4_all.deb?modtime=1225050059&big_mirror=0"), transferring it to Ubuntu, and double-clicking it to install.

If you still can't connect under wicd, it would be good to know the PCI ID of your wireless card.  This is a string in the form of XXXX:XXXX.  You can find it by running the command 'lspci -nn'.  For example, here's the appropriate line for my Atheros card, with the PCI ID in bold:
```

01:01.0 Ethernet controller [0200]: Atheros Communications Inc. AR2413 802.11bg NIC [**168c:001a**] (rev 01)
```

If we know the PCI ID we can google around to see if others are having the same problem with your particular chipset and how they solved it.

---

### Post by Abdul Haqq on 2008-10-28
Thanks for your reply. I will give WiCd a go probable tomorrow. The fact it can find the AP is something. I have been at this on and off since April what I bought my laptop.

There is a problem with 'Hardy identifying the AR5007 and this is well documented both here and on the net. 

The problem seems to be that whatever key is transmitted to the AP it has been corrupted in some way. Certainly looking as ifconfig results packets are TX and RX. I can't turn the security off to see what would happen.

Luckily I have Vista on one HDD and 'Hardy' on another so for today back to Vista to catch up on things.

BTW Why have you chose to run WiCd? :confused::confused:

---

### Post by pytheas22 on 2008-10-28
I run Network Manager because it works fine with my card, plus I like the VPN plugin which makes it easy to connect to my university VPN when necessary.  But wicd is a very good connection manager.

The ar5007 chip should definitely work on 8.04 once you install the latest madwifi.  I'm aware of the issues with Ubuntu incorrectly identifying certain Atheros cards, but 'lspci -nn' should give the correct PCI ID even if it otherwise misidentifies the card, so please post your PCI ID if you continue to have trouble.  If you really don't believe lspci, you can look in Vista, which should tell you the PCI ID somewhere.

---

### Post by biphtec on 2008-10-29
lspci | grep -i ath spits out:
03:00.0 Network controller: Atheros Communications Inc. Unknown device 002a (rev 01)

and modinfo ath9k says:
filename:       /lib/modules/2.6.24-19-generic/updates/drivers/net/wireless/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     A4910585605A4EEF935C41B
alias:          pci:v0000168Cd0000002Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000029sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000027sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000024sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000023sv*sd*bc*sc*i*
depends:        led-class,mac80211
vermagic:       2.6.24-19-generic SMP mod_unload

NetworkManager barfs with:
03:00.0 Network controller: Atheros Communications Inc. Unknown device 002a (rev 01)

So I'm guessing that even though the device shows up in the System>Administration>Network tool, my wifi isn't actually loaded...

---

### Post by Abdul Haqq on 2008-10-29
I have spent hours at this thing searching the internet trying different approaches.
Hardy I find too unstable. Things working and then not working. I had a copy of Debian 5 Beta. Installed it with the Madwifi drivers network detected and WEP Key accepted. As much as I love Ubuntu I now have a pure Debian system on my Laptop.

---

### Post by pytheas22 on 2008-10-29
Abdul: I'm glad you found a solution, even if it was Debian.  You may have had better luck with your card under Ubuntu 8.10, by the way.  8.04 does come up a bit short in the wireless department.

biphtec: please post the output of:
```

lspci -nn | grep -i atheros
```

The 'nn' is important.

---

### Post by biphtec on 2008-10-29
> **pytheas22 said:**
> Abdul: I'm glad you found a solution, even if it was Debian.  You may have had better luck with your card under Ubuntu 8.10, by the way.  8.04 does come up a bit short in the wireless department.

biphtec: please post the output of:
```

lspci -nn | grep -i atheros
```

The 'nn' is important.

yeah I missed that the first time, here it is:
lspci -nn | grep -i ath:
03:00.0 Network controller [0280]: Atheros Communications Inc. Unknown device [168c:002a] (rev 01)

---

### Post by pytheas22 on 2008-10-30
biphtec: my apologies for the tardy reply.

I was involved in [another thread]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=930155&page=5") a few weeks back where someone with the same exact wireless card (PCI ID 168c:002a) had what sounded like the same problem as yours--the driver was installed correctly, but he couldn't manage to connect.  However, things worked for him in Intrepid out-of-the-box (see the last page of the thread).  Can you upgrade to Intrepid?  You can do it by gyping:
```

sudo update-manager -d
```

and clicking the appropriate button.

If you can't or don't want to upgrade, let me know and we can keep trying to solve the problem on Hardy.  In that case, you should first try using [wicd]("http://wicd.sourceforge.net") instead of Network Manager to connect.

---

