---
title: "My Networker driver"
date: 2014-02-15
forum: Networking &amp; Wireless
---

### Post by Johnathon_Goddard on 2014-02-15
I just turn my old dell laptop from xp to Ubuntu 13.10 - My Driver is Broadcom BCM4318 [Air Force One 54g] 802.11 wireless LAN - I keep finding related posts on Broadcom b43 - I try to put the codex in from them and I find more than one problem - everytime I try to I load a codec in it , it states: 'DKMS: install completed - Segmentation fault' This as well as deleting my wired driver code.

I truly like help with this - I feel and I have worked with proir os like PC Linux and 11.04 Ubuntu - I have never been good with network drivers So please HELP!!

---

### Post by Bucky Ball on 2014-02-15
Have you plugged in an ethernet cable, gotten online, updated and checked 'Additional Drivers'? Catch 22 but always easier to get working if you can get online with a cable. 

That card should work out of the box. You shouldn't need to be installing anything manually. Please post the result of this command:

sudo lshw -C network

Thanks.

---

### Post by wildmanne39 on 2014-02-16
Hi, please do:
```
sudo apt-get purge --remove bcmwl-kernel-source
```
Then:
```
modprobe -v ssb
modprobe -v b44
```
now your wired connection should come back on.
Then do:
```
sudo apt-get install linux-firmware-nonfree
```
Then:
```
sudo modprobe -v b43
```
watch for errors while running all commands.
wireless should come alive.

Copy and paste all commands for accuracy one line at a time.

---

### Post by Johnathon_Goddard on 2014-02-16
> **Bucky Ball said:**
> Have you plugged in an ethernet cable, gotten online, updated and checked 'Additional Drivers'? Catch 22 but always easier to get working if you can get online with a cable. 

That card should work out of the box. You shouldn't need to be installing anything manually. Please post the result of this command:

sudo lshw -C network

Thanks.

[sudo] password for giovanni: 
  *-network:0             
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:14:22:aa:ac:cd
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.2.67 latency=64 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:18 memory:dfbfc000-dfbfdfff
  *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:17 memory:dfbfe000-dfbfffff

---

### Post by Johnathon_Goddard on 2014-02-16
> **Wild Man said:**
> Hi, please do:
```
sudo apt-get purge --remove bcmwl-kernel-source
```[/QOUTE]

This is the response given:
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

[QUOTE=Wild Man;12930446]
Then:
```
modprobe -v ssb
modprobe -v b44
```
now your wired connection should come back on.
Then do:
```
sudo apt-get install linux-firmware-nonfree
```[/QOUTE]

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

[QUOTE=Wild Man;12930446]
Then:
```
sudo modprobe -v b43
```
watch for errors while running all commands.
wireless should come alive.

Copy and paste all commands for accuracy one line at a time.

Thank you

---

### Post by wildmanne39 on 2014-02-16
Please run the command:
```
sudo dpkg --configure -a
```
now run the commands I posted and let us know the outcome.
Thanks

---

### Post by Johnathon_Goddard on 2014-02-16
> **Wild Man said:**
> Please run the command:
```
sudo dpkg --configure -a
```
now run the commands I posted and let us know the outcome.
Thanks

First off I must say thank you to both of you for great help - 

When I put this code in it stated : 

  	 	 	 	   giovanni@giovanni-ME051:~$ ```
sudo dpkg --configure -a  
 [sudo] password for giovanni:  
 Setting up bcmwl-kernel-source (6.30.223.141+bdcom-0ubuntu1) ...  
 Removing old bcmwl-6.30.223.141+bdcom DKMS files...  
 

 -------- Uninstall Beginning --------  
 Module:  bcmwl  
 Version: 6.30.223.141+bdcom  
 Kernel:  3.11.0-17-generic (i686)  
 -------------------------------------  
 

 Status: Before uninstall, this module version was ACTIVE on this kernel.  
 

 wl.ko:  
  - Uninstallation  
    - Deleting from: /lib/modules/3.11.0-17-generic/updates/dkms/  
  - Original module  
    - No original module was found for this module on this kernel.  
    - Use the dkms install command to reinstall any previous module version.  
 

 depmod............  
 

 DKMS: uninstall completed.  
 

 ------------------------------  
 Deleting module version: 6.30.223.141+bdcom  
 completely from the DKMS tree.  
 ------------------------------  
 Done.  
 Loading new bcmwl-6.30.223.141+bdcom DKMS files...  
 First Installation: checking all kernels...  
 Building only for 3.11.0-17-generic  
 Building for architecture i686  
 Building initial module for 3.11.0-17-generic  
 Done.  
 

 wl:  
 Running module version sanity check.  
  - Original module  
    - No original module exists within this kernel  
  - Installation  
    - Installing to /lib/modules/3.11.0-17-generic/updates/dkms/  
 

 depmod....  
 

 DKMS: install completed.  
 Segmentation fault
```

I tried to get the drivers that you put up so the cord would work and it stated that it wouldnt work - So I had to reboot with the disc in the distro 

Thank you once again

---

### Post by wildmanne39 on 2014-02-16
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by wildmanne39 on 2014-02-16
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named (wireless-info.txt, or wireless-info.txt.tar.gz) in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the wireless-info.tar.gz file as a zip file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

---

### Post by Johnathon_Goddard on 2014-02-16
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
--2014-02-16 19:22:40--  http://dl.dropbox.com/u/57264241/wireless_script
Resolving dl.dropbox.com (dl.dropbox.com)... 107.21.231.54
Connecting to dl.dropbox.com (dl.dropbox.com)|107.21.231.54|:80... connected.
HTTP request sent, awaiting response... 302 FOUND
Location: http://dl.dropboxusercontent.com/u/57264241/wireless_script [following]
--2014-02-16 19:22:40--  http://dl.dropboxusercontent.com/u/57264241/wireless_script
Resolving dl.dropboxusercontent.com (dl.dropboxusercontent.com)... 23.21.252.164
Connecting to dl.dropboxusercontent.com (dl.dropboxusercontent.com)|23.21.252.164|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 4161 (4.1K) [text/plain]
Saving to: &#8216;wireless_script&#8217;

100%[======================================>] 4,161       --.-K/s   in 0s      

Last-modified header missing -- time-stamps turned off.
2014-02-16 19:22:40 (91.6 MB/s) - &#8216;wireless_script&#8217; saved [4161/4161]

 
```

It saved the file

---

### Post by wildmanne39 on 2014-02-16
Please post this file wireless-info.txt, or wireless-info.txt.tar.gz it should be in your home folder.
Thanks

---

### Post by Johnathon_Goddard on 2014-02-16
```
 
*************** info trace ***************

***** uname -a *****

Linux giovanni-ME051 3.11.0-17-generic #31-Ubuntu SMP Mon Feb 3 21:53:31 UTC 2014 i686 i686 i686 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 13.10
Release:    13.10
Codename:    saucy

***** lspci *****

02:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
    Subsystem: Dell Device [1028:01c9]
    Kernel driver in use: b44
02:03.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
    Subsystem: Dell Wireless 1370 WLAN Mini-PCI Card [1028:0005]
    Kernel driver in use: b43-pci-bridge

***** lsusb *****

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

***** PCMCIA Card Info *****


***** iwconfig *****


***** rfkill *****


***** iw reg get *****

country 00:
    (2402 - 2472 @ 40), (6, 20)
    (2457 - 2482 @ 40), (6, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (6, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 80), (6, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 80), (6, 20), PASSIVE-SCAN, NO-IBSS
    (57240 - 63720 @ 2160), (N/A, 0)

***** lsmod *****

ssb                    51596  1 b44

***** nm-tool *****

NetworkManager Tool

State: connected (global)

- Device: eth0  [Ethernet connection 1] ----------------------------------------
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
    Address:         192.168.2.67
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
plugins=ifupdown,keyfile,ofono
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
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma
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

filename:       /lib/modules/3.11.0-17-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     78379A0109AF2689B4F6028
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
vermagic:       3.11.0-17-generic SMP mod_unload modversions 686 


***** udev rules *****

# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1e.0/0000:02:00.0/ssb1:0 (b44)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

***** dmesg *****

[    1.760127] ssb: Found chip with id 0x4318, rev 0x02 and package 0x02
[    1.760141] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x0D, vendor 0x4243)
[    1.760149] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x09, vendor 0x4243)
[    1.760157] ssb: Core 2 found: PCI (cc 0x804, rev 0x0C, vendor 0x4243)
[    1.760165] ssb: Core 3 found: PCMCIA (cc 0x80D, rev 0x07, vendor 0x4243)
[    1.830633] ssb: Sonics Silicon Backplane found on PCI device 0000:02:03.0
[    1.880053] ssb: Found chip with id 0x4401, rev 0x02 and package 0x00
[    1.880062] ssb: Core 0 found: Fast Ethernet (cc 0x806, rev 0x07, vendor 0x4243)
[    1.880069] ssb: Core 1 found: V90 (cc 0x807, rev 0x03, vendor 0x4243)
[    1.880076] ssb: Core 2 found: PCI (cc 0x804, rev 0x0A, vendor 0x4243)
[    1.920217] ssb: Sonics Silicon Backplane found on PCI device 0000:02:00.0
[    1.940696] b44 ssb1:0 eth0: Broadcom 44xx/47xx 10/100 PCI ethernet driver <MAC address removed>
[   61.816198] b44 ssb1:0 eth0: Link is up at 100 Mbps, full duplex
[   61.816208] b44 ssb1:0 eth0: Flow control is off for TX and off for RX

****************** done ******************

 
```

---

### Post by wildmanne39 on 2014-02-16
We need to remove some modules from the blacklist.

Please do:
```
gksu gedit /etc/modprobe.d/blacklist.conf
```
put a # in front of:
```
blacklist b43
blacklist ssb
blacklist bcma
blacklist b44
```
save and close gedit.
Reboot

---

### Post by Johnathon_Goddard on 2014-02-16
OK thank you - Did that and rebooted -

---

### Post by wildmanne39 on 2014-02-16
Does it connect now? if not run and post the file again so we can see if the changes stayed and what effect it had.
Thanks

---

### Post by Johnathon_Goddard on 2014-02-17
it didnt work and I have no idea what to try now ???? HELP!!

---

### Post by Iowan on 2014-02-17
> **Johnathon_Goddard said:**
> it didnt work and I have no idea what to try now ???? HELP!!
Maybe this? ;)
> **Wild Man said:**
> ... if not run and post the file again so we can see if the changes stayed and what effect it had.

---

### Post by Johnathon_Goddard on 2014-02-17
Sorry - 

```
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

filename:       /lib/modules/3.11.0-17-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     78379A0109AF2689B4F6028
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
vermagic:       3.11.0-17-generic SMP mod_unload modversions 686 


***** udev rules *****

# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1e.0/0000:02:00.0/ssb1:0 (b44)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

***** dmesg *****

[    1.868728] ssb: Found chip with id 0x4318, rev 0x02 and package 0x02
[    1.868739] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x0D, vendor 0x4243)
[    1.868746] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x09, vendor 0x4243)
[    1.868754] ssb: Core 2 found: PCI (cc 0x804, rev 0x0C, vendor 0x4243)
[    1.868762] ssb: Core 3 found: PCMCIA (cc 0x80D, rev 0x07, vendor 0x4243)
[    1.914891] ssb: Sonics Silicon Backplane found on PCI device 0000:02:03.0
[    1.975237] ssb: Found chip with id 0x4401, rev 0x02 and package 0x00
[    1.975251] ssb: Core 0 found: Fast Ethernet (cc 0x806, rev 0x07, vendor 0x4243)
[    1.975258] ssb: Core 1 found: V90 (cc 0x807, rev 0x03, vendor 0x4243)
[    1.975266] ssb: Core 2 found: PCI (cc 0x804, rev 0x0A, vendor 0x4243)
[    2.012107] ssb: Sonics Silicon Backplane found on PCI device 0000:02:00.0
[    2.032570] b44 ssb1:0 eth0: Broadcom 44xx/47xx 10/100 PCI ethernet driver <MAC address removed>
[   67.816203] b44 ssb1:0 eth0: Link is up at 100 Mbps, full duplex
[   67.816212] b44 ssb1:0 eth0: Flow control is off for TX and off for RX
[  664.544245] b44 ssb1:0 eth0: powering down PHY
[  674.000386] b44 ssb1:0 eth0: Link is up at 100 Mbps, full duplex
[  674.000395] b44 ssb1:0 eth0: Flow control is off for TX and off for RX

****************** done ****************** 
```

---

### Post by wildmanne39 on 2014-02-17
That is only a small portion of the file can you try to post all the file again.
Thanks

---

### Post by Johnathon_Goddard on 2014-02-18
Sorry-

```
 
*************** info trace ***************

***** uname -a *****

Linux giovanni-ME051 3.11.0-17-generic #31-Ubuntu SMP Mon Feb 3 21:53:31 UTC 2014 i686 i686 i686 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 13.10
Release:    13.10
Codename:    saucy

***** lspci *****

02:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
    Subsystem: Dell Device [1028:01c9]
    Kernel driver in use: b44
02:03.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
    Subsystem: Dell Wireless 1370 WLAN Mini-PCI Card [1028:0005]
    Kernel driver in use: b43-pci-bridge

***** lsusb *****

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

***** PCMCIA Card Info *****


***** iwconfig *****


***** rfkill *****


***** iw reg get *****

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

***** lsmod *****

ssb                    51596  1 b44

***** nm-tool *****

NetworkManager Tool

State: connected (global)

- Device: eth0  [Ethernet connection 1] ----------------------------------------
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
    Address:         192.168.2.67
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
plugins=ifupdown,keyfile,ofono
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
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma
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

filename:       /lib/modules/3.11.0-17-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     78379A0109AF2689B4F6028
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
vermagic:       3.11.0-17-generic SMP mod_unload modversions 686 


***** udev rules *****

# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1e.0/0000:02:00.0/ssb1:0 (b44)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

***** dmesg *****

[    1.868728] ssb: Found chip with id 0x4318, rev 0x02 and package 0x02
[    1.868739] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x0D, vendor 0x4243)
[    1.868746] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x09, vendor 0x4243)
[    1.868754] ssb: Core 2 found: PCI (cc 0x804, rev 0x0C, vendor 0x4243)
[    1.868762] ssb: Core 3 found: PCMCIA (cc 0x80D, rev 0x07, vendor 0x4243)
[    1.914891] ssb: Sonics Silicon Backplane found on PCI device 0000:02:03.0
[    1.975237] ssb: Found chip with id 0x4401, rev 0x02 and package 0x00
[    1.975251] ssb: Core 0 found: Fast Ethernet (cc 0x806, rev 0x07, vendor 0x4243)
[    1.975258] ssb: Core 1 found: V90 (cc 0x807, rev 0x03, vendor 0x4243)
[    1.975266] ssb: Core 2 found: PCI (cc 0x804, rev 0x0A, vendor 0x4243)
[    2.012107] ssb: Sonics Silicon Backplane found on PCI device 0000:02:00.0
[    2.032570] b44 ssb1:0 eth0: Broadcom 44xx/47xx 10/100 PCI ethernet driver <MAC address removed>
[   67.816203] b44 ssb1:0 eth0: Link is up at 100 Mbps, full duplex
[   67.816212] b44 ssb1:0 eth0: Flow control is off for TX and off for RX
[  664.544245] b44 ssb1:0 eth0: powering down PHY
[  674.000386] b44 ssb1:0 eth0: Link is up at 100 Mbps, full duplex
[  674.000395] b44 ssb1:0 eth0: Flow control is off for TX and off for RX

****************** done ******************

 
```

---

### Post by wildmanne39 on 2014-02-18
Please do:
```
sudo gedit /etc/modprobe.d/blacklist-bcm43.conf
```
Then completely remove:
```
blacklist b43
blacklist ssb
blacklist bcma
blacklist b44
```
save, close gedit and reboot.
Thanks

---

### Post by Johnathon_Goddard on 2014-02-19
I put in the first code and now where do I put the second

---

### Post by wildmanne39 on 2014-02-19
Copy and paste all commands for accuracy.

After the first command it will ask for your password, type your user password, it will not show it in the terminal, after you are done typing it just hit enter and the file should open in gedit then you should see the blacklist files, delete them save and close gedit then reboot.
Thanks

---

### Post by varunendra on 2014-02-19
> **Johnathon_Goddard said:**
> I put in the first code and now where do I put the second
If by "second" you meant this code -
> **Wild Man said:**
> 
```
blacklist b43
blacklist ssb
blacklist bcma
blacklist b44
```

..it is not something that you have to 'Put' or run somewhere. It is the text that you have to remove from the file that will open with the first command.

---

### Post by Johnathon_Goddard on 2014-02-19
```
*************** info trace *************** 

***** uname -a ***** 

Linux giovanni-ME051 3.11.0-17-generic #31-Ubuntu SMP Mon Feb 3 21:53:31 UTC 2014 i686 i686 i686 GNU/Linux 

***** lsb_release ***** 

Distributor ID:    Ubuntu 
Description:    Ubuntu 13.10 
Release:    13.10 
Codename:    saucy 

***** lspci ***** 

02:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02) 
    Subsystem: Dell Device [1028:01c9] 
    Kernel driver in use: b44 
02:03.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02) 
    Subsystem: Dell Wireless 1370 WLAN Mini-PCI Card [1028:0005] 
    Kernel driver in use: b43-pci-bridge 

***** lsusb ***** 

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 

***** PCMCIA Card Info ***** 


***** iwconfig ***** 


***** rfkill ***** 


***** iw reg get ***** 

country 00: 
    (2402 - 2472 @ 40), (3, 20) 
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS 
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS 
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS 
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS 

***** lsmod ***** 

ssb                    51596  1 b44 

***** nm-tool ***** 

NetworkManager Tool 

State: connected (global) 

- Device: eth0  [Ethernet connection 1] ---------------------------------------- 
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
    Address:         192.168.2.67 
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
plugins=ifupdown,keyfile,ofono 
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
blacklist brcmfmac 
blacklist brcmsmac 
blacklist bcma 
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

filename:       /lib/modules/3.11.0-17-generic/kernel/drivers/ssb/ssb.ko 
license:        GPL 
description:    Sonics Silicon Backplane driver 
srcversion:     78379A0109AF2689B4F6028 
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
vermagic:       3.11.0-17-generic SMP mod_unload modversions 686 


***** udev rules ***** 

# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1e.0/0000:02:00.0/ssb1:0 (b44) 
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0" 

***** dmesg ***** 

[    1.868728] ssb: Found chip with id 0x4318, rev 0x02 and package 0x02 
[    1.868739] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x0D, vendor 0x4243) 
[    1.868746] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x09, vendor 0x4243) 
[    1.868754] ssb: Core 2 found: PCI (cc 0x804, rev 0x0C, vendor 0x4243) 
[    1.868762] ssb: Core 3 found: PCMCIA (cc 0x80D, rev 0x07, vendor 0x4243) 
[    1.914891] ssb: Sonics Silicon Backplane found on PCI device 0000:02:03.0 
[    1.975237] ssb: Found chip with id 0x4401, rev 0x02 and package 0x00 
[    1.975251] ssb: Core 0 found: Fast Ethernet (cc 0x806, rev 0x07, vendor 0x4243) 
[    1.975258] ssb: Core 1 found: V90 (cc 0x807, rev 0x03, vendor 0x4243) 
[    1.975266] ssb: Core 2 found: PCI (cc 0x804, rev 0x0A, vendor 0x4243) 
[    2.012107] ssb: Sonics Silicon Backplane found on PCI device 0000:02:00.0 
[    2.032570] b44 ssb1:0 eth0: Broadcom 44xx/47xx 10/100 PCI ethernet driver <MAC address removed> 
[   67.816203] b44 ssb1:0 eth0: Link is up at 100 Mbps, full duplex 
[   67.816212] b44 ssb1:0 eth0: Flow control is off for TX and off for RX 
[  664.544245] b44 ssb1:0 eth0: powering down PHY 
[  674.000386] b44 ssb1:0 eth0: Link is up at 100 Mbps, full duplex 
[  674.000395] b44 ssb1:0 eth0: Flow control is off for TX and off for RX 

****************** done ******************
```

---

### Post by wildmanne39 on 2014-02-19
What happened when you entered this command:
```
sudo gedit /etc/modprobe.d/blacklist-bcm43.conf
```
in the terminal?

The blacklist files are still there.

Please add code tags to your previous post.
Thanks

---

### Post by Johnathon_Goddard on 2014-02-20
```
  (gedit:2300): The owner of /home/giovanni/.config/ibus/bus is not root!


IBUS-WARNING **: Calling Inhibit failed: GDBus.Error.org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files 
```

---

### Post by wildmanne39 on 2014-02-20
Did the gedit file open with the drivers that are blacklisted? you really should be letting us know when something fails, we need to communicate. It looks like you have other issues, are some of your applications running slow? do you have high cpu usage?

Here is a bug report.
[https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/1217757](https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/1217757)

---

