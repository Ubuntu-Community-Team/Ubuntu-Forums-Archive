---
title: "broadcom bcm4311 802.11b/g wlan driver needed"
date: 2014-02-02
forum: Networking &amp; Wireless
---

### Post by Ralph_Lam on 2014-02-02
I installed Ubuntu onto an old Dell Inspiron 1501 and the wireless  driver is not part of the installation.  I can not get onto wireless/wifi  with this laptop using Ubuntu (although I can using SoldX on the same computer, go figure).

ONCE, and only once, when I booted up in Ubuntu, it asked me if I wanted it to go fetch the driver for

broadcom bcm4311 802.11b/g wlan (rev o1), my wireless "card".

I said yes, not thinking that it couldn't do this since I had no  internet connection. It gave up and I have never seen this offer again.

I was able to find an ethernet cable and jack into the router and am  able to get onto the internet that way, but again, it has not asked me  if I would lke it to fetch the driver.

Is there a way to go get this driver and have it installed once I am  booted in ubuntu and jacked into the internet with hard wire?

Also, I am wondering if, since SolydX is already using it, and since  both distros are based on DEbian, is there a way to "port" it over or  use by ubuntu?

Cheers

---

### Post by varunendra on 2014-02-02
While being connected to internet via cable, run this command in a terminal (opened by 'Ctrl-Alt-T') -
```
sudo apt-get install linux-firmware-nonfree
```

Then reboot and enjoy your wireless.

---

### Post by Ralph_Lam on 2014-02-02
I thought that I could get onto the internet using the cable, and I am sue I was, but now, I can only acess the inteet via cable using the ive DVD.

Can I still install it to the hardriv installation while running the live DVD?

---

### Post by varunendra on 2014-02-02
No problem.

Manually download the package from here : [http://packages.ubuntu.com/saucy/all/linux-firmware-nonfree/download](http://packages.ubuntu.com/saucy/all/linux-firmware-nonfree/download)

Copy it to your desktop, and double-click to install with Software Center.

**PS:**
Version doesn't really matter here, but if Software Center shows 'attitude' (figuratively ;)) in installing it, change saucy to raring or precise whatever you are using currently. Saucy is the latest (13.10).

---

### Post by Ralph_Lam on 2014-02-03
Can't install it after saving it to desktop of Ubuntu.

The software manager opens and the install button is grayed out.  Can't use it.

Here is the message that is in the software center box


An older version of "linux-firmware-nonfree" is available in your normal software channels.  Only install this file if you trust the origin.

This package provides non-free firmware sed by linux kernal drivers.

Most of the firmware in this package is for television tuner cards; However, non-free firmware or other classes of devcies are provided as well.

linux-irmware-nonfree 1.14ubuntu1
4.0 M to download, 9.0 MB wen instaled

---

### Post by varunendra on 2014-02-04
> **Ralph_Lam said:**
> An older version of "linux-firmware-nonfree" is available in your normal software channels.

Means the same problem as I suspected previously -
> **PS:**
Version doesn't really matter here, but if Software Center shows 'attitude' (figuratively ) in installing it, change **saucy** to **raring** or **precise** whatever you are using currently. Saucy is the latest (13.10) to raring or precise whatever you are using currently.
I meant to change that in the link that I gave.

But now that you already have one downloaded, let's not confuse it further and just get it done with, since the version is not and should not be an issue at all. Just install it with "dpkg -i" -

[INDENT]**1)** Copy the downloaded file (linux-firmware-nonfree......deb) on your desktop
**2)** Open a terminal (Ctrl-Alt-T) and run the following command -
```
sudo dpkg -i Desktop/linux-firmware-nonfree*deb
```[/INDENT]
Post back if you see any error messages in the terminal. If not, reboot and tell us if the wifi works.

---

### Post by Ralph_Lam on 2014-02-04
ralph@ralph-Inspiron-1501:~$ sudo dpkg -i Desktop/linux-firmware-nonfree*deb
[sudo] password for ralph: 
Sorry, try again.
[sudo] password for ralph: 
(Reading database ... 144684 files and directories currently installed.)
Preparing to replace linux-firmware-nonfree 1.14ubuntu1 (using .../linux-firmware-nonfree_1.14ubuntu1_all.deb) ...
Unpacking replacement linux-firmware-nonfree ...
Setting up linux-firmware-nonfree (1.14ubuntu1) ...
ralph@ralph-Inspiron-1501:~$

just sits there, does not seem to have done anything.  still not able to get on using wireless

---

### Post by Ralph_Lam on 2014-02-04
does it matter that the actual name of the file on the desktop is...

linux-firmware-nonfree_1.14ubuntu1_all.deb


?

---

### Post by Ralph_Lam on 2014-02-04
hmmm  I think that you left out the dot in front of "deb"....

will re-try

---

### Post by Ralph_Lam on 2014-02-04
nope, same result

---

### Post by varunendra on 2014-02-04
> **Ralph_Lam said:**
> does it matter that the actual name of the file on the desktop is...

linux-firmware-nonfree_1.14ubuntu1_all.deb


?

> **Ralph_Lam said:**
> hmmm  I think that you left out the dot in front of "deb"....

will re-try

The asterisk (*) between "nonfree" and "deb" was a wildcard, it matches 'Everything' in-between, including the dot.

The firmware seems to have been installed fine. So the important part has been done. Let's see what is keeping your wireless from working now. Please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

### Post by Ralph_Lam on 2014-02-05
tried this

[http://www.youtube.com/watch?v=VP3dvzuukJA](http://www.youtube.com/watch?v=VP3dvzuukJA)

pretty cool, all I have to do is search for "additional drivers" and Ubuntu found the bcm 4311, just like that?  Problem - you need an internet connection to get it.  Since I have gotten several packages for this driver on my hard drive (after trying other methods) it would awesome if after Ubuntu finds that I need to driver for the bcm 4311, the next choice wold be "search your hard drive for package?", so....

still trying

---

### Post by chili555 on 2014-02-05
> **Ralph_Lam said:**
> tried this

[http://www.youtube.com/watch?v=VP3dvzuukJA](http://www.youtube.com/watch?v=VP3dvzuukJA)

pretty cool, all I have to do is search for "additional drivers" and Ubuntu found the bcm 4311, just like that?  Problem - you need an internet connection to get it.  Since I have gotten several packages for this driver on my hard drive (after trying other methods) it would awesome if after Ubuntu finds that I need to driver for the bcm 4311, the next choice wold be "search your hard drive for package?", so....

still tryingNooooooooooooo!! The real problem us that 'additional drivers' installs the proprietary Broadcom STA driver and it is* incorrect* for your 4311. STOP! Do not touch, use or even think about 'additional drivers.' 

This is a public service message. We now return you to your regularly scheduled guru, Varun.

EDIT: I think the file installed perfectly well:> Preparing to replace linux-firmware-nonfree 1.14ubuntu1 (using .../linux-firmware-nonfree_1.14ubuntu1_all.deb) ...
Unpacking replacement linux-firmware-nonfree ...
Setting up linux-firmware-nonfree (1.14ubuntu1) ...Please reboot, open a terminal and show us:```
sudo modprobe b43
lsmod | grep -e b43 -e wl
dmesg | grep b43
iwconfig
```Sorry to step on toes, Varun, but I couldn't help myself!!

---

### Post by varunendra on 2014-02-05
> **chili555 said:**
> Sorry to step on toes, Varun, but I couldn't help myself!!

No problem sir! When a BCM4311 issue goes beyond a page, it is hard to resist the itching. :P

@Ralph_Lam, please read this part of my previous post -
> The firmware seems to have been installed fine. So the important part has been done. Let's see what is keeping your wireless from working now. Please follow the "Wireless Script" link in my signature, **download and run the script as per instructions there, and post back the report it generates.**
The report I asked for should give us all the info we need to get it done.

---

### Post by Ralph_Lam on 2014-02-05
chili555 - here is wha came out

```
ralph@ralph-Inspiron-1501:~$ sudo modprobe b43
ralph@ralph-Inspiron-1501:~$ lsmod | grep -e b43 -e wl
b43                   364596  0 
mac80211              541819  1 b43
cfg80211              453853  2 b43,mac80211
bcma                   39810  1 b43
ssb                    51554  3 b43,b44,ssb_hcd
ralph@ralph-Inspiron-1501:~$ dmesg | grep b43
[  631.570433] b43-phy0: Broadcom 4311 WLAN found (core revision 10)
[  631.612073] b43-phy0: Found PHY: Analog 4, Type 2 (G), Revision 8
[  632.248055] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
ralph@ralph-Inspiron-1501:~$ iwconfig
wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
lo        no wireless extensions.

eth1      no wireless extensions.
```

---

### Post by Ralph_Lam on 2014-02-05
varunendra - here is the wireless info txt


```
*************** info trace ***************

***** uname -a *****

Linux ralph-Inspiron-1501 3.8.0-29-generic #42~precise1-Ubuntu SMP Wed Aug 14 15:31:16 UTC 2013 i686 athlon i386 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.3 LTS
Release:    12.04
Codename:    precise

***** lspci *****

05:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
    Subsystem: Dell Wireless 1390 WLAN Mini-Card [1028:0007]
    Kernel driver in use: b43-pci-bridge
--
08:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
    Subsystem: Dell Device [1028:01f5]
    Kernel driver in use: b44

***** lsusb *****

Bus 001 Device 003: ID 05dc:a20b Lexar Media, Inc. 
Bus 002 Device 002: ID 046d:c016 Logitech, Inc. Optical Wheel Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

***** PCMCIA Card Info *****


***** iwconfig *****

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

***** rfkill *****

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

***** lsmod *****

b43                   364596  0 
mac80211              541819  1 b43
cfg80211              453853  2 b43,mac80211
bcma                   39810  1 b43
ssb_hcd                12781  0 
ssb                    51554  3 b43,b44,ssb_hcd

***** nm-tool *****

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            b43
  State:             disconnected
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    belkin.ff6:      Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA2
    hloveeee:        Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 55 WPA2
    HOME-64E1:       Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 52 WPA WPA2


- Device: eth1  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            b44
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.2.4
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1

    DNS:             192.168.2.1



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

auto lo
iface lo inet loopback


***** iwlist *****

wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-14 dBm  
                    Encryption key:on
                    ESSID:"belkin.ff6"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001ddf047787
                    Extra: Last beacon: 56ms ago
                    IE: Unknown: 000A62656C6B696E2E666636
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A6C181BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B081500000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD090010180202100C0000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD9D0050F204104A00011010440001021041000100103B000103104700100000000000000001000308863BDD5FF61021001242656C6B696E20436F72706F726174696F6E1023000946394B31303031763410240007342E30302E30351042000E31323132313447423432333339391054000800060050F20400011011001B42656C6B696E20576972656C65737320526F757465722857464129100800020080


***** resolv.conf *****

nameserver 127.0.0.1
search Belkin

***** blacklist *****

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211
blacklist b44

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

filename:       /lib/modules/3.8.0-29-generic/kernel/drivers/net/wireless/b43/b43.ko
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
srcversion:     F6F97440A9DA6418F4C2856
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
vermagic:       3.8.0-29-generic SMP mod_unload modversions 686 
parm:           bad_frames_preempt:enable(1) / disable(0) Bad Frames Preemption (int)
parm:           fwpostfix:Postfix for the .fw files to load. (string)
parm:           hwpctl:Enable hardware-side power control (default off) (int)
parm:           nohwcrypt:Disable hardware encryption. (int)
parm:           hwtkip:Enable hardware tkip. (int)
parm:           qos:Enable QOS support (default on) (int)
parm:           btcoex:Enable Bluetooth coexistence (default on) (int)
parm:           verbose:Log message verbosity: 0=error, 1=warn, 2=info(default), 3=debug (int)
parm:           pio:Use PIO accesses by default: 0=DMA, 1=PIO (int)

filename:       /lib/modules/3.8.0-29-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     F7A1658A8CB1D58E3D347C1
alias:          pci:v000014E4d00004727sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004359sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004358sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004357sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004353sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004331sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000A8D8sv*sd*bc*sc*i*
alias:          pci:v000014E4d00000576sv*sd*bc*sc*i*
depends:        
intree:         Y
vermagic:       3.8.0-29-generic SMP mod_unload modversions 686 

filename:       /lib/modules/3.8.0-29-generic/kernel/drivers/usb/host/ssb-hcd.ko
license:        GPL
description:    Common USB driver for SSB Bus
author:         Hauke Mehrtens
srcversion:     E127A51EDC8F44D2C2A8F15
alias:          ssb:v4243id0819rev*
alias:          ssb:v4243id0817rev*
alias:          ssb:v4243id0808rev*
depends:        ssb
intree:         Y
vermagic:       3.8.0-29-generic SMP mod_unload modversions 686 

filename:       /lib/modules/3.8.0-29-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     14621F6EC014F731244437C
alias:          pci:v000014E4d00004350sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Csv*sd*bc*sc*i*
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
vermagic:       3.8.0-29-generic SMP mod_unload modversions 686 


***** udev rules *****

# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:14.4/0000:08:00.0/ssb2:0 (b44)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:14.4/0000:08:00.0/ssb3:0 (b44)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:06.0/0000:05:00.0/ssb0:0 (b43-pci-bridge)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

***** dmesg *****

[  243.060066] ssb: Found chip with id 0x4311, rev 0x01 and package 0x00
[  243.060078] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x11, vendor 0x4243)
[  243.060086] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x0A, vendor 0x4243)
[  243.060093] ssb: Core 2 found: USB 1.1 Host (cc 0x817, rev 0x03, vendor 0x4243)
[  243.060100] ssb: Core 3 found: PCI-E (cc 0x820, rev 0x01, vendor 0x4243)
[  243.133212] ssb: Sonics Silicon Backplane found on PCI device 0000:05:00.0
[  243.212161] ssb: Found chip with id 0x4401, rev 0x02 and package 0x00
[  243.212182] ssb: Core 0 found: Fast Ethernet (cc 0x806, rev 0x07, vendor 0x4243)
[  243.212195] ssb: Core 1 found: V90 (cc 0x807, rev 0x03, vendor 0x4243)
[  243.212208] ssb: Core 2 found: PCI (cc 0x804, rev 0x0A, vendor 0x4243)
[  243.252243] ssb: Sonics Silicon Backplane found on PCI device 0000:08:00.0
[  243.272919] b44 ssb1:0 eth0: Broadcom 44xx/47xx 10/100 PCI ethernet driver <MAC address removed>
[  243.418037] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[  243.429218] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[  246.816256] b44 ssb1:0 eth1: Link is up at 100 Mbps, full duplex
[  246.816271] b44 ssb1:0 eth1: Flow control is off for TX and off for RX
[  246.816397] IPv6: ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  354.781194] b44 ssb1:0 eth1: powering down PHY
[  354.856131] ssb: Found chip with id 0x4401, rev 0x02 and package 0x00
[  354.856143] ssb: Core 0 found: Fast Ethernet (cc 0x806, rev 0x07, vendor 0x4243)
[  354.856151] ssb: Core 1 found: V90 (cc 0x807, rev 0x03, vendor 0x4243)
[  354.856159] ssb: Core 2 found: PCI (cc 0x804, rev 0x0A, vendor 0x4243)
[  354.896193] ssb: Sonics Silicon Backplane found on PCI device 0000:08:00.0
[  354.916664] b44 ssb2:0 eth0: Broadcom 44xx/47xx 10/100 PCI ethernet driver <MAC address removed>
[  355.029109] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[  355.040195] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[  358.000245] b44 ssb2:0 eth1: Link is up at 100 Mbps, full duplex
[  358.000259] b44 ssb2:0 eth1: Flow control is off for TX and off for RX
[  358.000396] IPv6: ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  631.570433] b43-phy0: Broadcom 4311 WLAN found (core revision 10)
[  631.612073] b43-phy0: Found PHY: Analog 4, Type 2 (G), Revision 8
[  632.248055] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[  632.348462] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  632.348804] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

****************** done ******************
```

---

### Post by Ralph_Lam on 2014-02-05
Get this; I am posting all of this using Ubuntu, th hard drive version that I booted from, the version that neds the broadcom driver....

Here is how - I ran "additional drivers" (prior to the admonisment not to by chili555) and while it was wiggling back and forth, prior to telling me that I needed the broadcom driver, and being followed by it's attempt to download it, I slipped in the thumb drive from which I installed Ubuntu, and it flashed once, showed it was mounted, flashed again, and BINGO, I had a wired connection.  Then when "addidtional drivers" tried to download the driver, it killed the connection, gave up, hen the tumb drive flashed again, and I had wired connection again....

obviously I am using a driver off the thumb drive.  Why oh why doesn't the hard drive version just take it from the tumb drive?  Perplexing that it will use it but not take it...  odd.

---

### Post by Ralph_Lam on 2014-02-05
varunendra -I think I came accross some dialog betwen you and someone else in another thread pertaining to a similar problem.  Your solution (I think it was you) had something to do with undoing the "blacklist" of some things.  I don't know exactly what I am looking at in the text above, but I did pick out this

```
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211
blacklist b44
```

without knowing or sure, it looks bad to me.  It looks like the stuf that needs to work is blacklisted and so won't work.  Is my guessing anywhere close to part of the problem?

---

### Post by wildmanne39 on 2014-02-05
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by Ralph_Lam on 2014-02-05
define "code".  Is "code" is _any_ text that is in the terminal, even _output_?  Or is "code" _input_ that is entered by a human?

---

### Post by Ralph_Lam on 2014-02-05
OK - I am strongly considering re-installing Ubuntu onto the partition that I have it on.  I think that there is a possibility that a fresh start may save some time.

I just installed MINT onto another partition.  As many of you already know, MINT is a fork of Ubuntu.  It has many of the same raw features.  It too needed the driver for the broadcom wireless to be installed as an additional step after the initial installation.

After much time trying to get the broadcom wireless driver installed in Ubuntu, I have come across about 6 or 7 methods that have all failed (Probably because I have them all jumbled up and overlapping with a ton of meaningless, un-related crap).  I used a little intuition to glom together an amalgum from several methods I tri with Ubuntu and used the following to successfully get the wireles working in the MINT istallation.

1- Start by uninstalling firmware-linux-nonfree via Synaptic

in the terminal, enter

```
sudo apt-get remove firmware-linux-nonfree
```

(by the way, this did nothing, well, it tld me that it could not find the package to remove)

2- Download Ubuntu linux-firmware-nonfree_1.14_all.deb by another machine with internet connection or by connecting your machine via wired connection or using another USB wireless.

The download link is [http://www.ubuntuupdates.org/package/core/quantal/multiverse/base/linux-firmware-nonfree](http://www.ubuntuupdates.org/package/core/quantal/multiverse/base/linux-firmware-nonfree)

put the "linux-firmware-nonfree_1.14_all.deb" package on the desktop

in the terminal, enter

```
sudo dpkg -i Desktop/linux-firmware-nonfree*deb
```

re-boot

NOTE:  there was a method similar to this that I tried for Ubuntu and the package suggested in that scenario was

"linux-firmware-nonfree_1.14ubuntu1_all.deb", in the above steps the package that worked for MINT was called "linux-firmware-nonfree_1.14_all.deb"

Now, I am wondering if after a fresh installation of Ubuntu, using the above method might work with Ubuntu.

Either with "linux-firmware-nonfree_1.14ubuntu1_all.deb" or "linux-firmware-nonfree_1.14_all.deb"

???

Just grasping at straws here

---

### Post by Ralph_Lam on 2014-02-05
Just installed MINT onto another partition.  Like Ubuntu, it also needed extra steps to get the wireless working.
Used the following method to get wireless in MINT.

1- Start by uninstalling firmware-linux-nonfree via Synaptic

or

```
sudo apt-get remove firmware-linux-nonfree
```

(by the way, this had no effect except to give me the message that it could not find the package to remove it)

2- Download Ubuntu linux-firmware-nonfree_1.14_all.deb by another machine with internet connection or by connecting your machine via wired connection or using another USB wireless.

The download link is [ [URL]http://www.ubuntuupdates.org/package/core/quantal/multiverse/base/linux-firmware-nonfree]( [URL]http://www.ubuntuupdates.org/package/core/quantal/multiverse/base/linux-firmware-nonfree)
[/url]
put linux-firmware-nonfree_1.14_all.deb on desktop

in the terminal, enter

```
sudo dpkg -i Desktop/linux-firmware-nonfree*deb
```

re-boot

I am thinking that a fresh installation of Ubuntu on it's partition, then using the above method migh work for Ubuntu.

Thoughts?

---

### Post by varunendra on 2014-02-06
Wow! Now 3 pages for a 4311, amazing! :P

The solution to all your problems on all Linux based installations is -

[indent]**1)** Install (or simply copy-paste) the firmware files that are required by the native driver b43. This driver is part of the kernel hence already present, however, the firmware has to be installed separately.

**2)** NEVER install the proprietary sta driver (also called "wl", the package name being "bcmwl-kernel-source"). While it is supposed to work with your card, it mostly doesn't, and it also blacklists the driver "ssb" which is required by your wired connection.

**3)** IF you have by mistake, accidentally or out of desperation, installed this "sta" driver, purge it without a second thought and make sure all its configuration files have been deleted too, including the blacklist file you mentioned in post #18[/indent]

Now, to implement these, please do the following -
```
sudo apt-get purge bcmwl-kernel-source
```
This should purge the wrong driver along with all the customizations it did. But just to make sure, check -
```
grep 'blacklist b43' /etc/modprobe.d/*
```
It shouldn't return any output, means everything is okay. But if it does return any output, note the filename that contains this string (most probably, it will be "/etc/modprobe.d/blacklist-bcm43.conf" file). Remove this file manually in that case -
```
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
```

Now do -
```
sudo modprobe -v b44
```
This should get your wired connection working. Once you are connected to internet via cable, run the following command to install the firmware for your wireless -
```
sudo apt-get install linux-firmware-nonfree
```

Or if you don't have a wired connection available, or have no internet access for any other reasons, install the "linux-firmware-nonfree.." file manually like you did before. Please note that you can also open this file on your "Archive Manager" program (right-click > Open with..), where you can see the "b43" folder in it and manually extract > copy it to your "/lib/firmware" directory.

So you can see there are several possible methods, all leading to one simple solution - installing the firmware file, and NOT even by mistake installing the sta driver (easy to get rid of if you did).

Reboot and celebrate.

---

### Post by Ralph_Lam on 2014-02-06
varunendra -

I suspected I had a glob of goo in there. Your steps above seem VERY handy indeed.

I am optimistic that these steps will work. You were spot on in mentioning installing things in desperation; however, we can go ahead and throw in a healthy dose of utter ignorence to the mix (on my part).

So, WHY-OH-WHY, if you and others already know not to install the "wl" related files, are there instructions that lead us towards this, and even built-in steps which automatically do it?

We may never know. Be that that as it may, I am VERY happy that you have been so helpful here. I am eager to get close enogh to an ethernet cable to try this out.

AWESOME!

Oh, and one more thing.  

after follwing your purge steps

```

sudo apt-get purge bcmwl-kernel-source
grep 'blacklist b43' /etc/modprobe.d/*
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
sudo modprobe -v b44

```

Would I be able to put one of these pacakges...

"linux-firmware-nonfree_1.14ubuntu1_all.deb" or "linux-firmware-nonfree_1.14_all.deb"

on the desk-top, and then use the following command

```
sudo dpkg -i Desktop/linux-firmware-nonfree*deb
```

to efffect a proper installation of the drivers?  or should I stick with

```
sudo apt-get install linux-firmware-nonfree
```

with a wired connection?

---

### Post by varunendra on 2014-02-06
> **Ralph_Lam said:**
> So, WHY-OH-WHY, if you and others already know not to install the "wl" related files, are there instructions that lead us towards this, and even built-in steps which automatically do it?
Like I mentioned, it is *supposed* to work with your card, only that practically it doesn't (with this and some other specific cards that it is *supposed* to work with). Usually, it is a general (and reasonable) belief in people that the "Additional Drivers" program should install the correct driver for you. It indeed does when the proposed driver is suitable for the device.

I am not sure why the "Additional Drivers" program offers the wrong driver when it has become known that it doesn't work with some of these particular cards, while the native one with correct firmware does. There is some Licensing issue with Broadcom drivers, but to me it seems that the "Additional Drivers" program is just not smart enough to decide between whether to offer the sta driver, or just the firmware for the native one. But this is just a guess, I really don't have much clue on why it does so, maybe we should ask the program's developers. That program has a very important role in improving the overall user-experience with Ubuntu, and I agree that this problem with some Broadcom cards is very annoying.

> Would I be able to put one of these pacakges...

"linux-firmware-nonfree_1.14ubuntu1_all.deb" or "linux-firmware-nonfree_1.14_all.deb"

on the desk-top, and then use the following command

```
sudo dpkg -i Desktop/linux-firmware-nonfree*deb
```

to efffect a proper installation of the drivers?  or should I stick with

```
sudo apt-get install linux-firmware-nonfree
```

with a wired connection?
Whatever is easier for you. Both will get the job done and will have no difference once it is done. The proper way is the "sudo apt-get install.." method, the manual installation is a workaround, and manually extracting > copy-pasting the firmware directory is a hack. But after it is done, all lead to the same valid fix - placing the firmware files in a place where the driver "b43" expects it.

If you wish, I can attach the files in a zip file which you can simply download > extract > copy to your /lib/firmware directory. But basically it is same as extracting the files from the downloaded .deb files, the only difference being that the .zip file will automatically open with Archive Manager, while you'll have to use right-click > open with.... option to open the deb file on it. :)

---

### Post by Ralph_Lam on 2014-02-06
sssSSSSSsssswweeeEEEEEeeeet!!!

Your steps worked perfetly.  I am answering this thread using my wielss connection that is now working on Ubunutu..NICE!

I went ahead and just used the 
```

sudo apt-get install linux-firmware-nonfree
```

nice...

Thanks ever so much.  I hope that some day I can be as helpful to another "fledgling" user.

Thanks again.

P.S. How do I mark this thread as "SOLVED"?

---

### Post by varunendra on 2014-02-06
Sweet indeed, my confidence on B43 had started shaking..;)

> **Ralph_Lam said:**
> P.S. How do I mark this thread as "SOLVED"?

See this link : [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by Ralph_Lam on 2014-02-07
did it.  Marked as SOLVED!! :)

---

### Post by Onesimus_Venzant_ on 2014-10-24
I tried for the last 3 days to get my wireless to work.  I remove files, I purged files, I update, I install, I download directly and my wireless still didn't work.  I thought all the excercises I went through was unnecessary. I may have read about 100 post on this bcm4311. I just have to share that the very first thing that needs to be checked is whether or not your wireless driver has been blacklisted.

The only thing that I had to do was remove the files containing the blacklist information. I am sure everything else that was suggested worked as well, but nothing worked until that happened.  

So follow the information for installing the bcm4311 in the previous post but it is important that "blacklist" be DESTROYED!!  :0( 

Thanks for allowing me to share, "Keep coming back, It works!"

---

### Post by neil21 on 2014-12-05
I gotta weigh in on this one cuz I'm in the same situation, no wireless or wired connection and still a bit stuck.

I downloaded the linux-firmware-nonfree on another computer and copied it via flashdrive. Installed successfully and restarted but still nothing.
I've been following this whole thread which I'm glad to hear got someone fixed up.

Right now I'm at the end of your thread trying the sudo modprobe -v b44 which the terminal is just sitting there running the process infinitely.

---

### Post by chili555 on 2014-12-05
> **neil21 said:**
> I gotta weigh in on this one cuz I'm in the same situation, no wireless or wired connection and still a bit stuck.

I downloaded the linux-firmware-nonfree on another computer and copied it via flashdrive. Installed successfully and restarted but still nothing.
I've been following this whole thread which I'm glad to hear got someone fixed up.

Right now I'm at the end of your thread trying the sudo modprobe -v b44 which the terminal is just sitting there running the process infinitely.Let's begin at the beginning. What are your devices?```
lspci -nn | grep -e 0200 -e 0280
```And what drivers are loaded now?```
lsmod | grep -e b43 -e wl
```By the way, linux-firmware-nonfree is now obsolete.

---

### Post by neil21 on 2014-12-05
> **chili555 said:**
> Let's begin at the beginning. What are your devices?```
lspci -nn | grep -e 0200 -e 0280
```And what drivers are loaded now?```
lsmod | grep -e b43 -e wl
```By the way, linux-firmware-nonfree is now obsolete.


devices are:

02:00.0 Ethernet controller [0200]: Broadcom BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
0c:00.0 Network controller [0280]: Broadcom BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)


drivers loaded:

wl                          3999690  1
lib80211                  14040     1 wl
cfg80211                 409394   1 wl

---

### Post by chili555 on 2014-12-05
> **neil21 said:**
> devices are:

02:00.0 Ethernet controller [0200]: Broadcom BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
0c:00.0 Network controller [0280]: Broadcom BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)


drivers loaded:

wl                          3999690  1
lib80211                  14040     1 wl
cfg80211                 409394   1 wlPlease do:```
sudo apt-get purge bcmwl-kernel-source
```Reboot. Your ethernet should be working. Then do:```
sudo apt-get install firmware-b43-installer
sudo modprobe -r b43
sudo modprobe b43
```Now both should be working!

---

### Post by neil21 on 2014-12-06
> **chili555 said:**
> Please do:```
sudo apt-get purge bcmwl-kernel-source
```Reboot. Your ethernet should be working. Then do:```
sudo apt-get install firmware-b43-installer
sudo modprobe -r b43
sudo modprobe b43
```Now both should be working!



Well I'm up and running on the ethernet connection so thanks for that

The rest of it runs through without errors but still no wireless, when I enter 'sudo apt-get install firmware-b43-installer' I get the following:

Reading package lists...Done
Building dependency tree
Reading state information.... Done
The following package was automatically installed and is no longer required:
    dkms
Use 'apt-get autoremove' to remove it.
0 upgraded, 0 newly installed, 0 to remove and 235 not upgraded.


The last two commands run through without and output or error. I can probably live with just the ethernet but it's got me curious. I've never had wireless on this system since I wiped Windows off it and installed Linux. 

Once wireless is working does it just allow me to select the network and away I go or is there more setup?

---

### Post by chili555 on 2014-12-06
> 0 upgraded, 0 newly installed, 0 to remove and 235 not upgraded.An updated system is always more secure and works better than an out-dated system. I suggest you let Update Manager run all the updates and you'll probably be asked to reboot. When you reboot, detach the ethernet and see if the wireless doesn't start.> Once wireless is working does it just allow me to select the network and away I go Exactly! No other configuration is needed. You will see available networks by clicking the Network Manager icon at the top right. [http://www.eui.eu/Images-2011/ServicesAdmin/ComputingService/eduroam/eduroamUbuntu(1).png](http://www.eui.eu/Images-2011/ServicesAdmin/ComputingService/eduroam/eduroamUbuntu(1).png) Click on the one you want, supply the password and you're all set.

---

### Post by neil21 on 2014-12-06
> **chili555 said:**
> An updated system is always more secure and works better than an out-dated system. I suggest you let Update Manager run all the updates and you'll probably be asked to reboot. When you reboot, detach the ethernet and see if the wireless doesn't start.Exactly! No other configuration is needed. You will see available networks by clicking the Network Manager icon at the top right. [http://www.eui.eu/Images-2011/ServicesAdmin/ComputingService/eduroam/eduroamUbuntu(1).png](http://www.eui.eu/Images-2011/ServicesAdmin/ComputingService/eduroam/eduroamUbuntu(1).png) Click on the one you want, supply the password and you're all set.



Ok all the updates are done, I had to select the option to install previously authorized updates. So that's all good

Wireless still not up but I did notice one thing while starting the system during some of the startup text output that flashes by. The general message is:

firmware files not found:


b43/ucodes.fw
b43-open/ucodes.fw 

I had to restart a few times to copy this down because it shows it for a little over 1 second during boot, seen this before?

---

### Post by chili555 on 2014-12-06
> seen this before?In my short tenure on Planet Earth? Many hundreds of times. 

The firmware you tried to install didn't get installed correctly. Please try again:```
sudo apt-get install --reinstall firmware-b43-installer
sudo modprobe -r b43
sudo modprobe b43
```Detach the ethernet, reboot and enjoy your wireless!

---

### Post by neil21 on 2014-12-06
> **chili555 said:**
> In my short tenure on Planet Earth? Many hundreds of times. 

The firmware you tried to install didn't get installed correctly. Please try again:```
sudo apt-get install --reinstall firmware-b43-installer
sudo modprobe -r b43
sudo modprobe b43
```Detach the ethernet, reboot and enjoy your wireless!



Interesting.... I think this was a problem a while ago too. When I type the last command 'sudo modprobe b43' I get a system freeze while the process is still running. 

Just waiting to see if it completes but mouse is frozen as well

---

### Post by chili555 on 2014-12-06
I suggest you try Ctrl+Alt+F1 bringing you to a command prompt. Log in and then do:```
sudo reboot
```Then see if the wireless is working.

I assume the firmware was installed without error or drama.

---

### Post by neil21 on 2014-12-06
> **chili555 said:**
> I suggest you try Ctrl+Alt+F1 bringing you to a command prompt. Log in and then do:```
sudo reboot
```Then see if the wireless is working.

I assume the firmware was installed without error or drama.



Success!! Kudos!! You are a God among men!

---

### Post by chili555 on 2014-12-06
Awesome! Glad it's working.

---

### Post by 3bsalcedo on 2015-06-24
> **varunendra said:**
> Wow! Now 3 pages for a 4311, amazing! :P

The solution to all your problems on all Linux based installations is -

[indent]**1)** Install (or simply copy-paste) the firmware files that are required by the native driver b43. This driver is part of the kernel hence already present, however, the firmware has to be installed separately.

**2)** NEVER install the proprietary sta driver (also called "wl", the package name being "bcmwl-kernel-source"). While it is supposed to work with your card, it mostly doesn't, and it also blacklists the driver "ssb" which is required by your wired connection.

**3)** IF you have by mistake, accidentally or out of desperation, installed this "sta" driver, purge it without a second thought and make sure all its configuration files have been deleted too, including the blacklist file you mentioned in post #18[/indent]

Now, to implement these, please do the following -
```
sudo apt-get purge bcmwl-kernel-source
```
This should purge the wrong driver along with all the customizations it did. But just to make sure, check -
```
grep 'blacklist b43' /etc/modprobe.d/*
```
It shouldn't return any output, means everything is okay. But if it does return any output, note the filename that contains this string (most probably, it will be "/etc/modprobe.d/blacklist-bcm43.conf" file). Remove this file manually in that case -
```
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
```

Now do -
```
sudo modprobe -v b44
```
This should get your wired connection working. Once you are connected to internet via cable, run the following command to install the firmware for your wireless -
```
sudo apt-get install linux-firmware-nonfree
```

Or if you don't have a wired connection available, or have no internet access for any other reasons, install the "linux-firmware-nonfree.." file manually like you did before. Please note that you can also open this file on your "Archive Manager" program (right-click > Open with..), where you can see the "b43" folder in it and manually extract > copy it to your "/lib/firmware" directory.

So you can see there are several possible methods, all leading to one simple solution - installing the firmware file, and NOT even by mistake installing the sta driver (easy to get rid of if you did).

Reboot and celebrate.

After trying for days and many driver installs later I found the thread with what I needed. After purging (I installed the 'sta' driver out of frustration) and following the rest of the instructions in the post quoted, I rebooted and celebrated.

Thanks varunendra!

---

### Post by chili555 on 2015-06-24
Please note that *linux-firmware-nonfree* is now deprecated; it no longer installs any firmware. The preferred package is now *firmware-b43-installer.*

---

