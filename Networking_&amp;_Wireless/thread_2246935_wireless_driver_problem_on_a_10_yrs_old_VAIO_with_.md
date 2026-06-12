---
title: "wireless driver problem on a 10 yrs old VAIO with Linksys WMP54GX"
date: 2014-10-04
forum: Networking &amp; Wireless
---

### Post by hugoo2 on 2014-10-04
Hello, 

I've failed to make the wireless connection (with WPA key) work on a ten years old VAIO RS-502 working with Pentium 4 ([http://www.ciao.fr/Sony_VAIO_PCV_RS502__584035#productdetail](http://www.ciao.fr/Sony_VAIO_PCV_RS502__584035#productdetail)) and a LINKSYS WIRELESSG PCI ADAPTER WITH SRX WMP54GX ([http://support.linksys.com/en-us/support/adapters/WMP54GX](http://support.linksys.com/en-us/support/adapters/WMP54GX)) working with a Broadcomm chip. 

In Driver Manager, I get the message 'No proprietary drivers are in use'. Linksys has never delivered any Linux driver for the WMP54GX. 

After long searches on the web, I've tried this: 
- I've installed the STA driver for a Broadcomm chip. No change.
- I've executed Ndiswrapper so that Linux can use the Windows drivers. But I've been unable to go further than the launch. 


Any solution, preferably using graphical tools (I'm new to Linux) ? 

I've also tried Linux Mint 16 and 17 with the same failure. 

The card and antenna work correctly on Windows XP on the same computer.

Thanks in advance.

---

### Post by varunendra on 2014-10-05
I don't know of any GUI tools other than the "Additional Drivers" program for driver troubleshooting, and you already found out that it has nothing to offer. For the extra information that we usually need to troubleshoot such problems, I'm afraid I only know of command line ways, although it shouldn't be difficult to follow as we have very clear instructions for that.

Please follow the instructions in this post to download and run 'wireless_script' (alternative version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

Of course, run it when the adapter is plugged in.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

### Post by hugoo2 on 2014-10-09
Here is the log. Thank you in advance for your diagnosis. 

```



	======== Wireless-Info START ========


System-Info ~~~~~~~~~~~~~~~~~~~~~~~~


raheel-PCV-RS502-CE 3.13.0-32-generic i686,  Ubuntu 14.04.1 LTS, trusty


CPU    : Intel(R) Pentium(R) 4 CPU 3.00GHz
Memory : 495 MB
Uptime : 14:20:24 up 8 min,  2 users,  load average: 0,58, 0,84, 0,55




lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


02:08.0 Ethernet controller [0200]: Intel Corporation 82562EZ 10/100 Ethernet Controller [8086:1050] (rev 02)
	Subsystem: Sony Corporation Device [104d:815c]
	Kernel driver in use: e100
02:09.0 Ethernet controller [0200]: Airgo Networks, Inc. AGN100 802.11 a/b/g True MIMO Wireless Card [17cb:0001] (rev 03)
	Subsystem: Linksys WMP54GX v1 802.11g Wireless-G PCI Adapter with SRX [1737:0045]
02:0a.0 Multimedia video controller [0400]: Internext Compression Inc iTVC16 (CX23416) Video Decoder [4444:0016] (rev 01)




lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 054c:0174 Sony Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub




PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~






iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~






rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~








lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~








module parameters ~~~~~~~~~~~~~~~~~~




nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


State: connected (global)
=============================o=======o========o===========o=========o===========o==============o===========
 Interface & ID              | Type  | Driver | State     | Default | Speed     | Support      | HW Addr   
=============================o=======o========o===========o=========o===========o==============o===========
 eth0  [Connexion filaire 1] | Wired | e100   | connected | yes     | 100 Mb/s  |              | <MAC eth0>


    Address:         192.168.0.4
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1
    DNS:             109.88.203.3
    DNS:             62.197.111.140


    Address:         2a02:2788:64:e15::5
    Prefix:          128
    Gateway:         fe80::6a1:51ff:fec6:7624


    Address:         2a02:2788:64:e15:cc8c:46b2:1194:5fc6
    Prefix:          64
    Gateway:         fe80::6a1:51ff:fec6:7624


    Address:         2a02:2788:64:e15:20e:a6ff:fe8c:fb36
    Prefix:          64
    Gateway:         fe80::6a1:51ff:fec6:7624


    Address:         fe80::20e:a6ff:fe8c:fb36
    Prefix:          64
    Gateway:         fe80::6a1:51ff:fec6:7624


    Address:         2a02:2788:64:e15::5
    Prefix:          128
    Gateway:         ::
    DNS:             2a02:2788:fff0:7::3
    DNS:             2a02:2788:fff0:5::140
-----------------------------+-------+--------+-----------+---------+-----------+--------------+-----------




NetworkManager.state ~~~~~~~~~~~~~~~
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true




NetworkManager.conf ~~~~~~~~~~~~~~~~


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false




NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~
 




interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~


nameserver 127.0.1.1
search voo.be




Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~


Table de routage IP du noyau
Destination     Passerelle      Genmask         Indic Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0


--- 192.168.0.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 0.424/0.974/1.525/0.551 ms


--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.040/0.042/0.045/0.007 ms




iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~


(Region : "fr_BE.UTF-8")
country 00:
	(2402 - 2472 @ 40), (6, 20)
	(2457 - 2482 @ 40), (6, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (6, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 160), (6, 20), PASSIVE-SCAN, NO-IBSS
	(5250 - 5330 @ 160), (6, 20), DFS, PASSIVE-SCAN, NO-IBSS
	(5490 - 5730 @ 160), (6, 20), DFS, PASSIVE-SCAN, NO-IBSS




iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~


           - 




iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~






blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci




modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~




udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~


# PCI device 0x8086:0x1050 (e100)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"




Custom files/entries ~~~~~~~~~~~~~~~


/etc/modules        : Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default


[/etc/modprobe.d]
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en




Kernel boot line ~~~~~~~~~~~~~~~~~~~


BOOT_IMAGE=/boot/vmlinuz-3.13.0-32-generic root=UUID=cc99ea73-bfb9-4b1f-9e46-483c1bb5264e ro quiet splash vt.handoff=7




dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[    0.711851] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.712334] audit: initializing netlink socket (disabled)
[   12.757823] ivtv0: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
[   13.076921] cx25840 0-0044: firmware load i2c failure
[   15.463117] Bluetooth: BNEP (Ethernet Emulation) ver 1.3


	======== Done ========

```

---

### Post by varunendra on 2014-10-09
The [driver]("http://git.sipsolutions.net/?p=agnx.git") for your card was last updated on 3 Nov, 2008, and is no more included in the kernel. And since the laptop has only USB 1.1 interface, I believe a USB wifi adapter won't work either.

As such, I can see only two options with this laptop -

1) Use a different card, internal or an external PCMCIA one (if the machine has a PCMCIA slot available), that is supported by current kernels.
2) Try Windows XP driver with 'Ndiswrapper'.

Installing ndiswrapper and the windows driver should be easy, but unfortunately I have absolutely no experience with that, so may not be able to offer the best kind of help with that.

Please search the forums or the net to find a suitable guide to install the latest version of ndiswrapper, as the steps to install windows xp driver over it should be same as for any other card (of course the driver would differ).

The community maintained official guide is [here]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper"), but someone has flagged it an NOT up-to-date, so not sure if it is the best one. Please take a look at it if you can't find an easier and more suitable guide, and post back if you need help with that.

---

### Post by hugoo2 on 2014-10-10
The wifi connection now works perfectly after using ndiswrapper. 

install the graphical version of ndiswrapper
sudo apt-get install ndisgtk ndiswrapper-dkms dkms linux-headers-generic build-essential
It all downloads fine, then
sudo ndisgtk
Select install new driver from the graphical version and select the .inf file from the drivers you have downloaded and see how it goes. 

Thank you for your help!

---

### Post by varunendra on 2014-10-10
I'm super happy you made it! I was biting nails thinking of 'what if you asked for help with ndiswrapper'.. :p

Thanks for the precise and concise instructions for installing and making ndiswrapper work. I'm sure it'll help many others like you. :)

---

### Post by jeremy31 on 2014-10-10
> **varunendra said:**
> I'm super happy you made it! I was biting nails thinking of 'what if you asked for help with ndiswrapper'.. :p

Thanks for the precise and concise instructions for installing and making ndiswrapper work. I'm sure it'll help many others like you. :)

The ndiswrapper GUI makes it simple once installed and have the correct .inf file

I just hope it works better for Hugoo2 than it has for me but I was trying to use a different device

---

