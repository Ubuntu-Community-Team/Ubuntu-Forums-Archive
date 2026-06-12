---
title: "Broadcom BCM4311 / Lenovo 8922 3000 C200"
date: 2013-11-09
forum: Networking &amp; Wireless
---

### Post by Tom_ZeCat on 2013-11-09
I've installed Ubuntu 12.10 onto an old Lenovo laptop, an 8922 3000 C200.  I originally installed Kubuntu 13.10 (my preferred distro) and then Lubuntu 13.10.  I've been having a BEAST of a time getting the wireless networking card to work.  In fact, the only reason for the switch to Ubuntu 12.10 is the wireless install directions exist for that distro, but not for the distros I previously tried.  I can always convert this thing to Kubuntu later.  

A trip to the command line reveals this info about the wireless card:  

BCM4311 <--------------- Chip ID
14e4:4311 <---------- PCI-ID

Based on that info, I've found this instruction page:  

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx")

And based on that, I've run these commands in the terminal:  

> sudo apt-get update
sudo apt-get --reinstall install bcmwl-kernel-source

sudo modprobe -r b43 ssb wl brcmfmac brcmsmac bcma
sudo modprobe wl

sudo apt-get install firmware-b43-installer

sudo modprobe -r b43 bcma
sudo modprobe -r brcmsmac bcma
sudo modprobe -r wl

sudo modprobe b43


After all this I've pulled up all the listings of BCM4311 drivers in the Synaptik Package Manager and it looks like this: (image, and then post continues below it)
[IMG]http://imageshack.us/a/img571/4478/0xfk.png[/IMG] 

That's identical to how it looked when I tried this in Lubuntu.  On my other Lenovo, the one I've used Kubuntu 13.x on for several months now, the wireless icon shows up in the system tray.  All I have to do is click on it and it shows all available networks, the two wireless ones we have here, as well as those of the neighbors.  On this Lenovo 8922 I haven't been able to get any of the distros to do that.  It's been the same in each case, including Kubuntu 12.10 now.  When I click on the networking icon, all I can see is the information for the wired network, the ethernet.  (I've been using it plugged in via an ethernet cable.)    I've been able to list adding a wireless network manually, like this: 

[IMG]http://imageshack.us/photo/my-images/36/pc7n.png[/IMG]
Edit: I can't seem to get the image to hot link.  It's here: [http://imageshack.us/photo/my-images/36/pc7n.png]("http://imageshack.us/photo/my-images/36/pc7n.png")

But when I enter all the info, it doesn't even let me save it.  I don't think the card's driver is actually working.  And, btw, there is a switch on the front of the laptop for turning on the wireless card.  I've made sure to do that, but it doesn't do any good.  The little icon on the laptop indicates that the wireless card is turned on when the switch is flipped to the left.  I've tried it both left and right, but it doesn't work either way.  

I'm at my wits end.  I've done what it says to do in that link.  I'm about ready to proceed to Plan B and just order off for a USB-based networking card that has good ratings for Linux.  

However, before I resort to that, is there anything I've overlooked?  

I'll stick to Ubuntu 12.10 for now.  I can always run the upgrade command.  Then I can install whatever modules turn Ubuntu into Kubuntu, which has an interface I much prefer.

---

### Post by varunendra on 2013-11-11
Most of us here in the wireless village believe the native b43 driver is the best for this card you have. The sta driver blacklists it and itself is not as good. So, please try -
```
sudo apt-get purge bcmwl-kernel-source
```

Then reboot and see if your wifi is up and working any better. If not, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

---

### Post by Hadaka on 2013-11-11
Hi, 14e4:4311 seems to run best on the linux-firmware-nonfree package..
please do.
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree
sudo modprobe b43
```
BOOT
thanks.

---

### Post by Tom_ZeCat on 2013-11-13
Thanks to both of you for your replies.  I first tried what varunendra suggested.  Still no luck after the reboot.  Next, I did all the commands suggested by Hadaka.  After those and a reboot, I was still unable to connect wirelessly.  However, I did notice one difference.  When I click on that networking icon (the one that looks like an up and a down arrow), it now shows an "enable wireless" option, though it's greyed out.  

So I went to the link suggested by varunendra and ran that program.  Here are the results from the wireless-info.txt file: 

```

*************** info trace ***************

***** uname -a *****

Linux roger-laptop 3.5.0-43-generic #66-Ubuntu SMP Wed Oct 23 17:33:43 UTC 2013 i686 i686 i686 GNU/Linux

***** lsb_release *****

Distributor ID:	Ubuntu
Description:	Ubuntu 12.10
Release:	12.10
Codename:	quantal

***** lspci *****

03:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
	Subsystem: Broadcom Corporation Device [14e4:0465]
	Kernel driver in use: b43-pci-bridge
--
05:01.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
	Subsystem: Lenovo Device [17aa:2074]
	Kernel driver in use: 8139too

***** lsusb *****

Bus 001 Device 003: ID 0781:5577 SanDisk Corp. 
Bus 003 Device 002: ID 045e:071f Microsoft Corp. Mouse/Keyboard 2.4GHz Transceiver V2.0
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

***** PCMCIA Card Info *****

PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255

***** iwconfig *****

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

***** rfkill *****

0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes

***** lsmod *****

b43                   347496  0 
mac80211              461261  1 b43
cfg80211              175574  2 b43,mac80211
ssb_hcd                12750  0 
bcma                   34484  1 b43
ssb                    50294  2 b43,ssb_hcd

***** nm-tool *****

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            b43
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            8139too
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.35
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1
    DNS:             205.171.2.25

  IPv6 Settings:
    Address:         fd00::3484:c1f8:35ab:d992
    Prefix:          64
    Gateway:         ::

    Address:         fd00::20f:b0ff:fece:3bcb
    Prefix:          64
    Gateway:         ::

    Address:         fe80::20f:b0ff:fece:3bcb
    Prefix:          64
    Gateway:         ::




***** NetworkManager.state *****
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

***** NetworkManager.conf *****

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false

***** interfaces *****

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

***** iwlist *****


***** resolv.conf *****

nameserver 127.0.1.1
search Home

***** blacklist *****

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

***** modinfo *****

filename:       /lib/modules/3.5.0-43-generic/kernel/drivers/net/wireless/b43/b43.ko
firmware:       b43/ucode9.fw
firmware:       b43/ucode5.fw
firmware:       b43/ucode16_mimo.fw
firmware:       b43/ucode15.fw
firmware:       b43/ucode14.fw
firmware:       b43/ucode13.fw
firmware:       b43/ucode11.fw
license:        GPL
author:         Rafa&#322; Mi&#322;ecki
author:         Gábor Stefanik
author:         Michael Buesch
author:         Stefano Brivio
author:         Martin Langer
description:    Broadcom B43 wireless driver
srcversion:     5C5408969167493023BD033
alias:          bcma:m04BFid0812rev1Dcl*
alias:          bcma:m04BFid0812rev11cl*
alias:          ssb:v4243id0812rev10*
alias:          ssb:v4243id0812rev0F*
alias:          ssb:v4243id0812rev0D*
alias:          ssb:v4243id0812rev0C*
alias:          ssb:v4243id0812rev0B*
alias:          ssb:v4243id0812rev0A*
alias:          ssb:v4243id0812rev09*
alias:          ssb:v4243id0812rev07*
alias:          ssb:v4243id0812rev06*
alias:          ssb:v4243id0812rev05*
depends:        ssb,mac80211,bcma,cfg80211
intree:         Y
vermagic:       3.5.0-43-generic SMP mod_unload modversions 686 
parm:           bad_frames_preempt:enable(1) / disable(0) Bad Frames Preemption (int)
parm:           fwpostfix:Postfix for the .fw files to load. (string)
parm:           hwpctl:Enable hardware-side power control (default off) (int)
parm:           nohwcrypt:Disable hardware encryption. (int)
parm:           hwtkip:Enable hardware tkip. (int)
parm:           qos:Enable QOS support (default on) (int)
parm:           btcoex:Enable Bluetooth coexistence (default on) (int)
parm:           verbose:Log message verbosity: 0=error, 1=warn, 2=info(default), 3=debug (int)
parm:           pio:Use PIO accesses by default: 0=DMA, 1=PIO (int)

filename:       /lib/modules/3.5.0-43-generic/kernel/drivers/usb/host/ssb-hcd.ko
license:        GPL
description:    Common USB driver for SSB Bus
author:         Hauke Mehrtens
srcversion:     197001ECB808ACBCA18D7DC
alias:          ssb:v4243id0819rev*
alias:          ssb:v4243id0817rev*
alias:          ssb:v4243id0808rev*
depends:        ssb
intree:         Y
vermagic:       3.5.0-43-generic SMP mod_unload modversions 686 

filename:       /lib/modules/3.5.0-43-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     2C92CCB735C6654CB7E788B
alias:          pci:v000014E4d00004727sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004357sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004353sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004331sv*sd*bc*sc*i*
alias:          pci:v000014E4d00000576sv*sd*bc*sc*i*
depends:        
intree:         Y
vermagic:       3.5.0-43-generic SMP mod_unload modversions 686 

filename:       /lib/modules/3.5.0-43-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     CEE38CB0F94873CD9858D32
alias:          pci:v000014E4d0000432Bsv*sd*bc*sc*i*
alias:          pci:v000014E4d00004329sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004328sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004325sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004324sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000A8D6sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004322sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004321sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004320sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004319sv*sd*bc*sc*i*
alias:          pci:v000014A4d00004318sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004318sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004315sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004312sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004311sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004307sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004306sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004301sv*sd*bc*sc*i*
depends:        
intree:         Y
vermagic:       3.5.0-43-generic SMP mod_unload modversions 686 


***** udev rules *****

# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1e.0/0000:05:01.0 (8139too)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/ssb0:0 (b43-pci-bridge)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

***** dmesg *****

[   19.604222] ssb: Found chip with id 0x4311, rev 0x01 and package 0x00
[   19.604241] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x11, vendor 0x4243)
[   19.604255] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x0A, vendor 0x4243)
[   19.604265] ssb: Core 2 found: USB 1.1 Host (cc 0x817, rev 0x03, vendor 0x4243)
[   19.604274] ssb: Core 3 found: PCI-E (cc 0x820, rev 0x01, vendor 0x4243)
[   19.702161] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
[   21.704852] b43-phy0: Broadcom 4311 WLAN found (core revision 10)
[   22.191481] Registered led device: b43-phy0::tx
[   22.191507] Registered led device: b43-phy0::rx
[   22.191535] Registered led device: b43-phy0::radio
[   22.392066] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[   22.481048] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   22.482534] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   22.488401] b43-phy0: Radio hardware status changed to DISABLED

****************** done ******************

```

I very much appreciate the help thus far and am grateful for any suggestions to follow.

Edit: I have good news.  I've successfully connected!  I noticed that the icon indicating that the wireless card is on was not glowing even though the switch was in the right position.  I shut it off and turned it back on again and it glowed for a short time and went out.  I switched it back and forth a few times and it then finally glowed consistently.  I was then able to click on the networking icon and find our network and put our password in.  Many thanks to you for your help!

---

### Post by Tom_ZeCat on 2013-11-13
Another update: Converting Ubuntu 12.10 to Kubuntu 13.10 turned out to be more of a beast than I had anticipated.  I therefore wiped this laptop by installing Kubuntu 13.10 from the install DVD.  I applied the commands for turning on the wireless card previously done in the terminal and they worked.  Wireless is now working on this laptop in Kubuntu 13.10.  the solution offered was not unique to Ubuntu 12.10.  

Thank you once again for your help.  I had been pulling my hair out for quite a while on this one.

---

