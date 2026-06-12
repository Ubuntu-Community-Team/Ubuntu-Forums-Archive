---
title: "How to get a Belkin AC wi-fi Dualband USB Adapter working"
date: 2015-04-26
forum: Networking &amp; Wireless
---

### Post by will_s2 on 2015-04-26
Its not on the list of supported devices ( F9L1106 )but then maybe its out since the list last updated ??????. Now the problem is basically I dont have a clue on what I am doing and how to set wireless up or install the drivers for the USB device and even when installed how to configure the bloody thing...........was going to paste this in the new users forum but then decided maybe this forum may be a better place.  Actually was asking about which wifi to buy and I stumbled upon this USB device that I purchased last year  .... looked and looked and couldnt find it but soon as I stopped looking it comes out of hiding.......anyway, back to the subject, I did try once before to install this device but gave up . But now I want this PC to be wireless......it works great on the Windows boot ( dual boot win7 and Ubuntu 14.04 on different SSD's ). So anyone can they help me in getting this working or does this device not work with Ubuntu ?
edit : found this at  *List of 802.11ac Hardware*  
[h=4][Belkin F9L1106 v1]("https://wikidevi.com/wiki/Belkin_F9L1106_v1")[/h] 
[LIST]
[*]USB 2.0
[*]2x2:2 802.11ac / 802.11bgn
[*]**Broadcom** BCM43526 based
[/LIST]
also had the V2 with different but my one clearly has V1 marked on iy




```

########## wireless info START ##########

Report from: 26 Apr 2015 16:11 AEST +1000

Booted last: 26 Apr 2015 16:08 AEST +1000

Script from: 06 Apr 2015 17:23 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-49-generic #83-Ubuntu SMP Fri Apr 10 20:11:33 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

00:19.0 Ethernet controller [0200]: Intel Corporation 82579V Gigabit Network Connection [8086:1503] (rev 04)
    Subsystem: Gigabyte Technology Co., Ltd Device [1458:e000]
    Kernel driver in use: e1000e

06:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8151 v2.0 Gigabit Ethernet [1969:1083] (rev c0)
    Subsystem: Gigabyte Technology Co., Ltd Device [1458:e000]
    Kernel driver in use: atl1c

##### lsusb #############################

Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 007: ID 2109:0810  
Bus 001 Device 006: ID 2109:0810  
Bus 001 Device 005: ID 050d:1106 Belkin Components 
Bus 001 Device 004: ID 045e:0750 Microsoft Corp. Wired Keyboard 600
Bus 001 Device 009: ID 046d:c051 Logitech, Inc. G3 (MX518) Optical Mouse
Bus 001 Device 010: ID 0424:4063 Standard Microsystems Corp. 
Bus 001 Device 008: ID 0424:2640 Standard Microsystems Corp. USB 2.0 Hub
Bus 001 Device 003: ID 0424:2514 Standard Microsystems Corp. USB 2.0 Hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID 2109:0810  
Bus 004 Device 002: ID 2109:0810  
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### lsmod #############################

mxm_wmi                13021  0 
wmi                    19177  1 mxm_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth1      Link encap:Ethernet  HWaddr <MAC 'eth1' [IF]>  
          inet addr:192.168.2.86  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::52e5:49ff:feef:9ea0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1161 errors:0 dropped:0 overruns:0 frame:0
          TX packets:989 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1048060 (1.0 MB)  TX bytes:112004 (112.0 KB)
          Interrupt:20 Memory:f7f00000-f7f20000 

##### iwconfig ##########################

eth0      no wireless extensions.

eth1      no wireless extensions.

lo        no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 eth1
192.168.2.0     0.0.0.0         255.255.255.0   U     1      0        0 eth1

##### resolv.conf #######################

nameserver 127.0.1.1
search Belkin

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

- Device: eth1  [Ethernet connection 1] ----------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth1' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.2.86
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1

    DNS:             192.168.2.1

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

no-auto-default=<MAC 'eth1' [IF]>,<MAC 'eth0' [IF]>,

[ifupdown]
managed=false

##### NetworkManager profiles ###########

##### iw reg get ########################

Region: Australia/Sydney (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (6, 20)
    (2457 - 2482 @ 40), (6, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (6, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 160), (6, 20), PASSIVE-SCAN, NO-IBSS
    (5250 - 5330 @ 160), (6, 20), DFS, PASSIVE-SCAN, NO-IBSS
    (5490 - 5730 @ 160), (6, 20), DFS, PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

eth0      no frequency information.

eth1      no frequency information.

lo        no frequency information.

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

##### module infos ######################

##### module parameters #################

##### /etc/modules ######################

lp
rtc

##### modprobe options ##################

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:19.0 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth1' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"
# PCI device 0x1969:/sys/devices/pci0000:00/0000:00:1c.6/0000:05:00.0 (atl1c)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.4/0000:0a:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth2"
# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.5/0000:0b:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth3"

##### dmesg #############################

[   10.544403] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready (repeated 2 times)
[   14.013809] e1000e: eth1 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
[   14.013841] IPv6: ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready

########## wireless info END ############


```

---

### Post by kurt18947 on 2015-04-26
This is very much a long shot but it should be simple to try. Devices using Broadcom wifi chipsets typically don't 'just work', they require additional firmware/software. On this flavor of Ubuntu - Ubuntu-gnome, it's found under 'Software & Updates -> additional drivers'.  You'll need either a wired connection or temporary connection with a wifi adapter that is working. You can see if anything appears but I'm pretty doubtful. Wikidevi is useful for things wireless. They list only F9L1106 v.1 and the news there is not good.

[https://wikidevi.com/wiki/Belkin_F9L1106_v1](https://wikidevi.com/wiki/Belkin_F9L1106_v1)
**Probable Linux driver**
none
**[USB ID not yet observed in any mainline kernel / this list]("https://wikidevi.com/wiki/List_of_Wi-Fi_Device_IDs_in_Linux")**

I'm a little surprised given that this device has been around since 2012 but there we are. Are you able to return it for something known to work?

---

### Post by chili555 on 2015-04-26
I am writing my reply for the benefit of you, will_s2, but also for the benefit of the searchers out there who wonder how to find the details that will get the device working, or not. First, we see the device enumerated here:> Bus 001 Device 005: ID 050d:1106 Belkin Components A Google search for the usb.id of 050d:1106 finds this: [https://wikidevi.com/wiki/Belkin_F9L1106_v1](https://wikidevi.com/wiki/Belkin_F9L1106_v1)> Probable Linux driver
noneAnd this: [http://ubuntuforums.org/showthread.php?t=2167526](http://ubuntuforums.org/showthread.php?t=2167526)> Looks like you'll be better in investing in a device that actually works. ndiswrapper is mentioned in the thread. It is a system to use the Windows XP drivers appropriate to your architecture; either 32- or 64-bit. It is tricky to get going. If you have or can get the XP parts, we'll be happy to help. I give fair warning; ndiswrapper is challenging and sometimes just won't work at all. 

If you have the option to return the device for one that's fully supported, I'd take it.

---

### Post by will_s2 on 2015-04-26
thankyou, returning is not an option
Had a look at a lot of pages , actually have spent way to much time on this and I think the simplest solution is to back all the stuff on to another drive and remove Ununtu and use that drive as an external plug and go ( case lets me plug drives in externally at the top ). I just dont know enough about Linux and as my age increases my brain power decreases. I have another option, move Linux to my main PC that is NOT wireless  ..... I am ticked off at component manufactureres, are they on a kickback arrangement with Microshot ?  ( there is a spelling error but not the one you think )


btw: chili, that was me back in 2013, lost my details in an upgrade , anyway.........put it away for a while and only found again recently and thought I would give it another go

---

### Post by kurt18947 on 2015-04-27
> **will_s2 said:**
> thankyou, returning is not an option
Had a look at a lot of pages , actually have spent way to much time on this and I think the simplest solution is to back all the stuff on to another drive and remove Ununtu and use that drive as an external plug and go ( case lets me plug drives in externally at the top ). I just dont know enough about Linux and as my age increases my brain power decreases. I have another option, move Linux to my main PC that is NOT wireless  ..... I am ticked off at component manufactureres, are they on a kickback arrangement with Microshot ?  ( there is a spelling error but not the one you think )


btw: chili, that was me back in 2013, lost my details in an upgrade , anyway.........put it away for a while and only found again recently and thought I would give it another go

Too bad about returning not being an option. I don't know that component manufacturers are in cahoots with Microsoft, exactly. I think they devote the most resources to developing for the O.S. that they believe will be used most often with their wares. Also I think with Windows there is work done before a device is released to the market so that when it goes on sale the O.S. support is there. Any open source driver development work STARTS when the device reaches store shelves. And Microsoft licensing models may make it easier to protect intellectual property vs. Linux - or at least that's the perception. 

Installing a second network adapter is not difficult or particularly expensive. I presume the latest whiz-bang AC routers also support N speed devices. There are quite a few devices that are known to be plug -n- play. Get one of those :D. Given that *buntu seems oblivious to the existence of your Broadcom device, there certainly wouldn't be any conflicts. 

Since I've been using various flavors of linux the vast majority of the time, one of my first steps when considering a new hardware purchase is to go the to manufacturer's website and check on linux support. If they don't (support linux) I don't (buy their product). And if I'm in a grumpy mood, I'll write to the manufacturer's senior management type and tell him/her why their product is still on a store shelf instead of in my home. May not help but it makes me feel better O:).

---

### Post by Bill_Sutton on 2015-04-27
Having Ubuntu on a separate hard drive and using it mainly for banking and other secure transactions gives me a nice sense of security but the effort to find a device that works is painful. Nowadays a lot of manufacturers don't even list what chipset they use . Originally I asked something along the lines of "what USB wireless adapter works ....." and I could purchase another one and sell my current one along with the AC1200 router/modem  ( fibre is coming in July and the funny thing is if I had both the latest models of both devices I wouldn't have to sell them as they would do what I want....but that's another story ) 
The sad thing is a lot of manufacturers mention only windows ready and don't mention Linux ..... I don't hate Windows or anything like that and I should really make more of an effort to learn more then the basics of Ubuntu. 
The first thing I have to do is record my Ubuntu forums account and stop opening different ones from different computers.......am actually using wireless on my windows to type this rambling reply that wont make much sense.

---

### Post by chili555 on 2015-04-27
> the effort to find a device that works is painful.There are threads here and on askubuntu.com about recommending fully supported devices pretty regularly.

---

### Post by Bill_Sutton on 2015-04-28
Have found the Asus USB AC56 has drivers for Linux AT [http://support.asus.com/Download.aspx?SLanguage=en&m=USB-AC56](http://support.asus.com/Download.aspx?SLanguage=en&m=USB-AC56)      AND  [http://wikidevi.com/wiki/ASUS_USB-AC56](http://wikidevi.com/wiki/ASUS_USB-AC56) so will most probabley order that

---

### Post by chili555 on 2015-04-28
The driver on Asus' site is a little too old to compile on recent Ubuntu versions. When the time comes, I suggest this: [http://ubuntuforums.org/showthread.php?t=2228244](http://ubuntuforums.org/showthread.php?t=2228244)

---

### Post by Bill_Sutton on 2015-04-28
well after reading that post I will order it next week and the only remaining post on this subject will be me saying thankyou again

btw: totally off topic but I see in your sig you have 15.04   .... is it worthwhile to get ?

---

### Post by chili555 on 2015-04-28
I have installed 15.04 primarily because I answer questions on this and other forums. Questions start on the day of the release and sometimes a bit earlier than that! I want to be equipped to answer them. Between Mrs. Chili and I, we have computers with 14.04, 14.10 and 15.04 around. If needed, I can run a live session DVD of 12.04 LTS!

Frankly, for my limited needs, they all work perfectly well. I'm not in love or hate with any release.

If you have a particular piece of hardware that gained or lost support in 15.04, then it could be significant. In my case, my daily driver is an older laptop with an i3 processor, 8 GB of RAM and a 256 GB SSD. 15.04 with the default Unity desktop runs beautifully.

---

### Post by Bill_Sutton on 2015-04-28
well I see the Asus USB device advertised with broadcom chipset so contacted them to ask if they had it wrong and got a great reply 

> Hi Bill, thanks for your email,
 
Unfortunately I am unable to confirm compatibilities as I have not handled the products personally,
 
I would recommend confirming with the manufacturer if you have concerns regarding compatability,
 
 
Regards,
---
Jack Hall -
---
Customer Service Representative


---

### Post by mole84 on 2015-09-24
All,

I was able to get my Belkin AC Dual-Band Wi-Fi USB Adapter F9L1109-TG working on Ubuntu 14.04.1 x86_64 using the following instructions.

Reference:
[https://wikidevi.com/wiki/Belkin_F9L1109_v1](https://wikidevi.com/wiki/Belkin_F9L1109_v1)

You must compile and install the 8821AU driver
[https://github.com/abperiasamy/rtl8812AU_8821AU_linux](https://github.com/abperiasamy/rtl8812AU_8821AU_linux)

Download the source by clicking the "download zip" button on the right side of the screen on the git hub site.
Following the instructions in the read-me

Assuming you downloaded the zip to your ~/Downloads folder. You must have dkms installed (most should by default)

```

cd Downloads/
unzip rtl8812AU_8821AU_linux-master.zip
cd rtl8812AU_8821AU_linux-master/
sudo cp -R . /usr/src/rtl8812AU_8821AU_linux-1.0
sudo dkms add -m rtl8812AU_8821AU_linux -v 1.0
sudo dkms build -m rtl8812AU_8821AU_linux -v 1.0
sudo dkms install -m rtl8812AU_8821AU_linux -v 1.0
sudo modprobe -a 8812au

```

And the lights come on! Have Fun with you're awesomely fast wireless connection.

---

