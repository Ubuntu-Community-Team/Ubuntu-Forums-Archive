---
title: "No WIFI detected using BT dual band dongle"
date: 2014-07-03
forum: Networking &amp; Wireless
---

### Post by simon43 on 2014-07-03
Hi all, completely new to Linux and Ubuntu.
Just switched form my windows machine to one with xubuntu, but I cant get any wireless.

I'm using my BT dual band wifi dongle with my bt home hub. I get the power light on the dongle but no wifi light.
Wireless info file data below

Any help much appreciated.

Cheers



```
########## wireless info START ##########


##### release #####


Distributor ID:    Ubuntu
Description:    Ubuntu 14.04 LTS
Release:    14.04
Codename:    trusty


##### kernel #####


Linux Xubuntu 3.13.0-30-generic #54-Ubuntu SMP Mon Jun 9 22:47:59 UTC 2014 i686 i686 i686 GNU/Linux


##### lspci #####


00:19.0 Ethernet controller [0200]: Intel Corporation 82566DM Gigabit Network Connection [8086:104a] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:2800]
    Kernel driver in use: e1000e


##### lsusb #####


Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0a5c:bd17 Broadcom Corp. BCM43236 802.11abgn Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 04b3:310b IBM Corp. Red Wheel Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


##### PCMCIA Card Info #####


##### rfkill #####


##### lsmod #####


brcmfmac              208286  0 
brcmutil               15066  1 brcmfmac
cfg80211              409394  1 brcmfmac


##### iw reg get #####


country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


##### interfaces #####


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


##### iwconfig #####


##### route #####


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 eth2
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth2


##### resolv.conf #####


nameserver 127.0.1.1
search home


##### nm-tool #####


NetworkManager Tool


State: connected (global)


- Device: eth2  [Auto Ethernet] ------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>


  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         192.168.1.86
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254


    DNS:             192.168.1.254


##### NetworkManager.state #####


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


##### NetworkManager.conf #####


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


no-auto-default=<MAC address removed>,


[ifupdown]
managed=false


##### iwlist #####


##### iwlist channel #####


##### modinfo #####


filename:       /lib/modules/3.13.0-30-generic/kernel/drivers/net/wireless/brcm80211/brcmfmac/brcmfmac.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11 wireless LAN fullmac driver.
author:         Broadcom Corporation
firmware:       brcm/brcmfmac4335-sdio.txt
firmware:       brcm/brcmfmac4335-sdio.bin
firmware:       brcm/brcmfmac4334-sdio.txt
firmware:       brcm/brcmfmac4334-sdio.bin
firmware:       brcm/brcmfmac4330-sdio.txt
firmware:       brcm/brcmfmac4330-sdio.bin
firmware:       brcm/brcmfmac4329-sdio.txt
firmware:       brcm/brcmfmac4329-sdio.bin
firmware:       brcm/brcmfmac43241b4-sdio.txt
firmware:       brcm/brcmfmac43241b4-sdio.bin
firmware:       brcm/brcmfmac43241b0-sdio.txt
firmware:       brcm/brcmfmac43241b0-sdio.bin
firmware:       brcm/brcmfmac43143-sdio.txt
firmware:       brcm/brcmfmac43143-sdio.bin
firmware:       brcm/brcmfmac43242a.bin
firmware:       brcm/brcmfmac43236b.bin
firmware:       brcm/brcmfmac43143.bin
srcversion:     8743BBB897E075DF249524B
alias:          usb:v0A5Cp0BDCd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0A5CpBD1Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0A5CpBD17d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0A5CpBD1Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          sdio:c*v02D0d4335*
alias:          sdio:c*v02D0d4334*
alias:          sdio:c*v02D0d4330*
alias:          sdio:c*v02D0d4329*
alias:          sdio:c*v02D0d4324*
alias:          sdio:c*v02D0dA887*
depends:        brcmutil,cfg80211
intree:         Y
vermagic:       3.13.0-30-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:20:8A:30:B4:73:36:D7:A1:A1:57:88:C8:B3:AC
sig_hashalgo:   sha512
parm:           debug:level of debug output (int)
parm:           fcmode:mode of firmware signalled flow control (int)


filename:       /lib/modules/3.13.0-30-generic/kernel/drivers/net/wireless/brcm80211/brcmutil/brcmutil.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver utilities.
author:         Broadcom Corporation
srcversion:     E81EE4CBB6A7A689150D93D
depends:        
intree:         Y
vermagic:       3.13.0-30-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:20:8A:30:B4:73:36:D7:A1:A1:57:88:C8:B3:AC
sig_hashalgo:   sha512


##### modules #####


lp


##### blacklist #####


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


[/etc/modprobe.d/fbdev-blacklist.conf]
blacklist arkfb
blacklist aty128fb
blacklist atyfb
blacklist radeonfb
blacklist cirrusfb
blacklist cyber2000fb
blacklist gx1fb
blacklist gxfb
blacklist kyrofb
blacklist matroxfb_base
blacklist mb862xxfb
blacklist neofb
blacklist nvidiafb
blacklist pm2fb
blacklist pm3fb
blacklist s3fb
blacklist savagefb
blacklist sisfb
blacklist tdfxfb
blacklist tridentfb
blacklist viafb
blacklist vt8623fb


##### udev rules #####


# PCI device 0x14e4:0x1600 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x8086:0x10de (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"


# PCI device 0x8086:0x104a (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth2"


##### dmesg #####


[   14.261309] brcmfmac: brcmf_usb_fw_download: unsupported chip 43236 rev 2
[   14.261368] brcmfmac: brcmf_usb_attach: failed!
[   14.261419] brcmfmac: brcmf_usb_probe: failed with errno -19


########## wireless info END ############
```

---

### Post by stephen54 on 2014-08-23
Hi, created an account just to post this ):P. I was having the same problem as simon43 using xubuntu 14.04, however I have managed to get mine working using ndiswrapper. 

To install ndiswrapper I used the commands:

> 
sudo apt-get update
sudo apt-get install ndisgtk
 

Then I used the drivers from here:[http://catalog.update.microsoft.com/v7/site/ScopedViewRedirect.aspx?updateid=b78e6df7-da7c-4152-957a-22643f3d4123](http://catalog.update.microsoft.com/v7/site/ScopedViewRedirect.aspx?updateid=b78e6df7-da7c-4152-957a-22643f3d4123) extracted from the cab file. I found these drivers using this wiki:[https://wikidevi.com/wiki/BT_Dual-Band_Wi-Fi_Dongle_600_%28075715%29](https://wikidevi.com/wiki/BT_Dual-Band_Wi-Fi_Dongle_600_%28075715%29).

I ran ndisgtk using the command:

> 
gksu ndisgtk 


Finally pointing to the bcmwlhigh5.inf file where I had previously unpacked the .cab archive and things just worked for me.

I am aware that using ndisgtk is not the ideal method for getting a usb wireless card to function however it worked for me so I thought I would share, hope this helps!

P.S I did have a little trouble after rebooting using this method where the wireless card was always showing as not ready to fix this I just unplugged it and put it back in again and it worked fine, also it only seems to operate in the 2.4GHz band but at least it is no longer useless to me! :lolflag:

P.P.S This forum thread helped a ton to come to this solution: [http://ubuntuforums.org/showthread.php?t=1805830](http://ubuntuforums.org/showthread.php?t=1805830), I was working under the assumption that the AE2500 was similar to the BT 600 dual band dongle (probably a bad idea but I was at a dead end looking for related posts about this BT dongle).

---

### Post by corin-u on 2014-09-18
So essentially, having bought a dual-band USB dongle - there is no way to get 5GHz out of it and I might as well take it back?
I installed the drivers as above and have it working but the wireless light doesn't flash and the driver/card is only running in 802.11g.
Does **anyone **have a solution to get the card running at 802.11n?
If not, it's going back to the shop.

Thanks

---

### Post by Michael_McKenney on 2014-09-18
I think those are Intel Wireless based.  Check their web site for drivers. They do support Linux.

---

### Post by dave131 on 2014-09-19
The wireless is the Broadcom noted in the output from the network script.  I'm currently doing a google search with ubuntu 14 bcm43236 USB to see if I can find something for you.

---

### Post by dave131 on 2014-09-19
Ok, as best I can tell, you have the correct driver (the mac driver) according to what I could find on the net.  The net also says you need the loadable firmware files as well and I do see some being referenced:```
firmware:       brcm/brcmfmac43236b.bin
```
Perhaps the error in the log file says the most:
```
[   14.261309] brcmfmac: brcmf_usb_fw_download: unsupported chip 43236 rev 2
[   14.261368] brcmfmac: brcmf_usb_attach: failed!
[   14.261419] brcmfmac: brcmf_usb_probe: failed with errno -19
```

I am beyond my knowledge to really be of much help, but usually if I post something someone with more knowledge comes along quite quickly so hopefully they will be able to help upi.

---

### Post by dave131 on 2014-09-21
Hummm, I'm going bump this up in hopes someone can help the OP.  I noticed today that under nm-tool there is no wireless interface listed.  I'm not familiar with nm-tool, so I just ran "nm-tool" from a terminal on my PC and it shows my wireless.  So, *IF* I'm reading the information from the wireless script correctly, the physical device is known to Ubuntu as shown in the lsusb output.  According to what I can tell (I don't know much about this!) the driver module (the full mac driver?) is loaded is loaded as shown in the modinfo.  It looks like it also knows the firmware.  The log file shows that it didn't "pick up" the adapter, *IF* I'm reading it right.

So, as you can tell, I don't much about this and was hoping someone more knowledgeable could help the OP, if they are still with us.

---

### Post by dave131 on 2014-09-23
I'm sorry - I seem to have jinxed your chances of getting answer by posting in your thread.  Hopefully someone will be big enough to help you.  Again, I'm sorry.

---

### Post by slickymaster on 2014-09-23
Hi simon43, welcome to the forums. I'm moving your thread to the **Networking & Wireless** sub-forum, which is the proper place for it and hopefully you'll have better chances there.

Also, I've edited your post, adding code tags. Output code posted as plain text loses its formatting and parts of it sometimes turn into smileys making it difficult to read and understand. The [use of code tags]("http://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168") makes the post clean, compact and more appealing, thus getting more attention from readers.

---

### Post by JeQhdMD on 2014-09-24
This adapter ($12.99) on Amazon works great on ubuntu and other linux distros:   [http://www.amazon.com/Panda-Ultra-Wireless-Adapter-150Mbps/dp/B00762YNMG/ref=sr_1_1?s=pc&ie=UTF8&qid=1411532462&sr=1-1&keywords=panda+ultra+wireless+n+usb+adapter](http://www.amazon.com/Panda-Ultra-Wireless-Adapter-150Mbps/dp/B00762YNMG/ref=sr_1_1?s=pc&ie=UTF8&qid=1411532462&sr=1-1&keywords=panda+ultra+wireless+n+usb+adapter)

It is plug and play . . . no drivers to install.   Solid connections and no drops.

---

### Post by dave131 on 2014-09-24
I've used Tenda W322U V2.0 - also USB, also works out of the box, also $12.99 (at least at our local Micro Center).  So as you can see from the last post and this one, there are plenty of other options available out there, but I don't know how many are dual-band.  You could check the Ubuntu supported hardware list to see if there is another device you might try, *if* you want to try another adapter.

---

### Post by dave131 on 2014-09-25
I found a site with linux wireless drivers, and this is what they said there for your chip - BCM43236 rev 2 :
```

**Unsupported Chips**

 [TABLE="class: devtable"]
[TR]
[TD]**Chip** [/TD]
[TD]**Rev** [/TD]
[TD]**Marketing name** [/TD]
[TD]**USB ID** [/TD]
[/TR]
[TR]
[TD]0x4322 [/TD]
[TD]1 [/TD]
[TD]? [/TD]
[TD]0846:9011[/TD]
[/TR]
[TR]
[TD]0x4322 [/TD]
[TD]1 [/TD]
[TD]BCM43231 [/TD]
[TD]0846:9020[/TD]
[/TR]
[TR]
[TD]43236 [/TD]
[TD] 2 [/TD]
[TD]BCM43236 [/TD]
[TD]0a5c:bd17[/TD]
[/TR]
[/TABLE]

BCM43231 and BCM43236 (rev <= 2) have another architecture and can't be easily supported by **brcmfmac**.  
They have less memory on the chip and can't run full MAC firmware, so  they require implementing some extra code
 in the Linux driver. On the  other hand they are not standard soft MAC devices, so they can't be  supported by [B]
brcmsmac[/B] or **b43**.
```

I don't know how old that information is, but it might provide a clue that your wireless adapter isn't supported.  Others have mentioned what they use, and I mentioned the one that I have used on all of my PCs and it definetly connects with wireless "N".

Best of luck!

---

