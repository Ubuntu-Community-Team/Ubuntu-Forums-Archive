---
title: "yes i am having a problem w/ broadcom wireless! please help."
date: 2008-09-15
forum: Networking &amp; Wireless
---

### Post by khayden39005 on 2008-09-15
i followed the "having trouble w/ broadcom on hardy" instructions ([http://ubuntuforums.org/showthread.php?t=880218](http://ubuntuforums.org/showthread.php?t=880218)) and i got my wireless light to turn on. i can see the driver listed in system> administration> hardware drivers (listed as wl), but no internet. ive tried the " sudo iwlist ath0 scan" command and i get a message saying interface does not support scanning. the tutorial asked for three pieces of info if it did or didnt work. obviously in my case it didnt. anyway here is the requested info and i really appreciate everyones hard work.
[U]
uname -a:[/U]

Linux ubuntu 2.6.24-21-rt #1 SMP PREEMPT RT Mon Aug 25 18:23:02 UTC 2008 x86_64 GNU/Linux

_lspci -nn:_

00:00.0 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02f0] (rev a2)
00:00.1 RAM memory [0500]: nVidia Corporation C51 Memory Controller 0 [10de:02fa] (rev a2)
00:00.2 RAM memory [0500]: nVidia Corporation C51 Memory Controller 1 [10de:02fe] (rev a2)
00:00.3 RAM memory [0500]: nVidia Corporation C51 Memory Controller 5 [10de:02f8] (rev a2)
00:00.4 RAM memory [0500]: nVidia Corporation C51 Memory Controller 4 [10de:02f9] (rev a2)
00:00.5 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02ff] (rev a2)
00:00.6 RAM memory [0500]: nVidia Corporation C51 Memory Controller 3 [10de:027f] (rev a2)
00:00.7 RAM memory [0500]: nVidia Corporation C51 Memory Controller 2 [10de:027e] (rev a2)
00:02.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fc] (rev a1)
00:03.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fd] (rev a1)
00:05.0 VGA compatible controller [0300]: nVidia Corporation C51 [Geforce 6150 Go] [10de:0244] (rev a2)
00:09.0 RAM memory [0500]: nVidia Corporation MCP51 Host Bridge [10de:0270] (rev a2)
00:0a.0 ISA bridge [0601]: nVidia Corporation MCP51 LPC Bridge [10de:0260] (rev a3)
00:0a.1 SMBus [0c05]: nVidia Corporation MCP51 SMBus [10de:0264] (rev a3)
00:0a.3 Co-processor [0b40]: nVidia Corporation MCP51 PMU [10de:0271] (rev a3)
00:0b.0 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026d] (rev a3)
00:0b.1 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026e] (rev a3)
00:0d.0 IDE interface [0101]: nVidia Corporation MCP51 IDE [10de:0265] (rev f1)
00:0e.0 IDE interface [0101]: nVidia Corporation MCP51 Serial ATA Controller [10de:0266] (rev f1)
00:0f.0 IDE interface [0101]: nVidia Corporation MCP51 Serial ATA Controller [10de:0267] (rev f1)
00:10.0 PCI bridge [0604]: nVidia Corporation MCP51 PCI Bridge [10de:026f] (rev a2)
00:10.1 Audio device [0403]: nVidia Corporation MCP51 High Definition Audio [10de:026c] (rev a2)
00:14.0 Bridge [0680]: nVidia Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
03:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 02)
07:05.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832]
07:05.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 19)
07:05.2 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev 0a)
07:05.3 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 05)
07:05.4 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev ff)
[U]
dpkg -l | grep linux-restricted:
[/U]
ii  linux-restricted-modules-2.6.24-19-rt 2.6.24.13-19.45                                      Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-21-rt 2.6.24.14-21.48                                      Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-common       2.6.24.14-21.48                                      Non-free Linux 2.6.24 modules helper script
ii  linux-restricted-modules-rt           2.6.24.21.23                                         Restricted Linux modules for rt kernels

---

### Post by Wobblybob on 2008-09-15
I'm no expert, but you don't mention if you have tried to create a connection, do you have a connection icon in the top RH panel and have to tried to configure a connection using it?

---

### Post by Ayuthia on 2008-09-15
[QUOTE=khayden39005;5795702]i followed the "having trouble w/ broadcom on hardy" instructions ([http://ubuntuforums.org/showthread.php?t=880218](http://ubuntuforums.org/showthread.php?t=880218)) and i got my wireless light to turn on. i can see the driver listed in system> administration> hardware drivers (listed as wl), but no internet. ive tried the " sudo iwlist ath0 scan" command and i get a message saying interface does not support scanning. the tutorial asked for three pieces of info if it did or didnt work. obviously in my case it didnt. anyway here is the requested info and i really appreciate everyones hard work.
[U]
uname -a:[/U]

Linux ubuntu 2.6.24-21-rt #1 SMP PREEMPT RT Mon Aug 25 18:23:02 UTC 2008 x86_64 GNU/Linux

_lspci -nn:_
03:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 02)

Can you post the results of:
```
lshw -C network
```

Usually the wl driver uses eth1, but lshw -C network will tell you what the logical name (eth1, wlan0, etc.) is.

---

### Post by khayden39005 on 2008-09-17
this is the output for sudo lshw -C network....

*-network
description: Wireless interface
product: BCM4311 802.11b/g WLAN
vendor: Broadcom Corporation

---

### Post by Ayuthia on 2008-09-17
> **khayden39005 said:**
> this is the output for sudo lshw -C network....

*-network
description: Wireless interface
product: BCM4311 802.11b/g WLAN
vendor: Broadcom Corporation
That's odd.  Usually more information is given.  Can you check the following:
```
ls /sys/class/net
```
This should return a list of network names.  Hopefully we can figure out what the logical name is from there and then we can see what driver it is trying to use.  You can also try this step also:
```
sudo modprobe -r b43 ssb ndiswrapper wl bcm43xx
sudo modprobe wl
sudo ifconfig eth1 up
sudo iwlist scan
```
This will remove any conflicting modules and then load the wl module.  It will then try to bring up your wireless and scan for any wireless sites.

---

### Post by khayden39005 on 2008-09-18
im back. i made a mistake in my previous post. you were right there should have been more info for "lshw -C network". in fact, there was, i somehow didnt get it all posted. i have it now. i also have the other info you mentioned (ls /sys/class/net, and sudo modprobe -r b43 ssb ndiswrapper wl bcm43xx, sudo modprobe wl, sudo ifconfig eth1 up, and sudo iwlist scan). 
[B][U]
the output of "sudo lshw -C" is[/U][/B]:

WARNING: you should run this program as a super-user.
 *-network
    description:Wireless interface
    product: BCM4311 802.11b/g WLAN
    vendor: Broadcom Corporation
    physical id:0
    bus info: pci@0000:03:00.0
    logical name: eth1
    version: 02
    serial: 00:1a:73:7f:58:1d
    width: 64 bits
    clock: 33mhz
    capabilities: bus_master cap_list ethernet physical wireless
    configuration: broadcast=yes driver=wl latency=0 module=wl multicast=yes wireless=IEEE 802.11

[B][U]
the output for ls /sys/class/net is[/U][/B]:
eth0 eth1 lo

**_the output for "sudo modprobe -r b43 ssb ndiswrapper wl bcm43xx" is_**:
FATAL: module is in use.

[B][U]the command "sudo modprobe wl" doesnt do anything.
the command "sudo iconfig eth1 up" doesnt do anything.
[/U][/B]
**_the output for "iwlist scan" is_**:

lo Interface doesnt support scanning.
eth0 Interface doesnt support scanning.
eth1 Scan completed: 
    Cell 01 - Address:00:0C:41:F2:F5:A7
            ESSID:"linksys"
            Mode:Managed
            Frequency=2.437 GHz (Channel 6)           
            Quality:5/5 Signal level:-51 dBm Noise level:-92 dBm
            Encrtption key: off
            Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 M/bs; 6 Mb/s 
                   12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                   48 Mb/s; 54 Mb/s

---

### Post by adult swim on 2008-09-18
it appears as your wireless card is working, it picks up that there is the unsecured wireless network 'linksys' within range.  run from terminal ```
sudo modprobe -r ssb
```  then ```
sudo modprobe -r wl
``` and finally ```
sudo modprobe wl
```
give it a few seconds and then left click once on the network icon in your taskbar and select linksys.  hopefully that will work!

---

### Post by khayden39005 on 2008-09-18
arghh!! so close. adult swim, i did what you said and i got this error message when clicking on the network icon in the taskbar:
"please contact your system administrator to resolve the following problem: could not find information on interface 'eth1:avahi' in /proc/net/dev"

---

### Post by Ayuthia on 2008-09-18
> **khayden39005 said:**
> im back. i made a mistake in my previous post. you were right there should have been more info for "lshw -C network". in fact, there was, i somehow didnt get it all posted. i have it now. i also have the other info you mentioned (ls /sys/class/net, and sudo modprobe -r b43 ssb ndiswrapper wl bcm43xx, sudo modprobe wl, sudo ifconfig eth1 up, and sudo iwlist scan). 
[B][U]
the output of "sudo lshw -C" is[/U][/B]:

WARNING: you should run this program as a super-user.
 *-network
    description:Wireless interface
    product: BCM4311 802.11b/g WLAN
    vendor: Broadcom Corporation
    physical id:0
    bus info: pci@0000:03:00.0
    logical name: eth1
    version: 02
    serial: 00:1a:73:7f:58:1d
    width: 64 bits
    clock: 33mhz
    capabilities: bus_master cap_list ethernet physical wireless
    configuration: broadcast=yes driver=wl latency=0 module=wl multicast=yes wireless=IEEE 802.11

[B][U]
the output for ls /sys/class/net is[/U][/B]:
eth0 eth1 lo

**_the output for "sudo modprobe -r b43 ssb ndiswrapper wl bcm43xx" is_**:
FATAL: module is in use.

[B][U]the command "sudo modprobe wl" doesnt do anything.
the command "sudo iconfig eth1 up" doesnt do anything.
[/U][/B]
**_the output for "iwlist scan" is_**:

lo Interface doesnt support scanning.
eth0 Interface doesnt support scanning.
eth1 Scan completed: 
    Cell 01 - Address:00:0C:41:F2:F5:A7
            ESSID:"linksys"
            Mode:Managed
            Frequency=2.437 GHz (Channel 6)           
            Quality:5/5 Signal level:-51 dBm Noise level:-92 dBm
            Encrtption key: off
            Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 M/bs; 6 Mb/s 
                   12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                   48 Mb/s; 54 Mb/s

Can you post the results of:
```
lsmod | grep -i -e bcm43xx -e b43 -e b44 -e ndiswrapper -e wl
```

Were you trying ndiswrapper before?  If so, please try the following:
```
sudo modprobe -r b43 b44 ssb ndiswrapper bcm43xx wl
sudo modprobe wl
sudo ifconfig eth1 up
sudo iwlist scan
```
If you were using ndiswrapper, there was a script that was used for the b44 module.  I looked at your lspci info and it does not look like you really needed it so the command above removes it for this session.

---

### Post by khayden39005 on 2008-09-19
the result of "lsmod | grep -i -e bcm43xx -e b43 -e b44 -e ndiswrapper -e wl" is:

b44           33552  0
ssb          38020   1 b44
mii           7552  1 b44
wl          1082192 0
ieee80211_crypt   8320 2 wl,ieee80211_crypt_tkip

i ran all the code you mentioned. the output for "sudo iwlist scan"
is still:

lo Interface doesnt support scanning.
eth0 Interface doesnt support scanning.
eth1 Scan completed:
Cell 01 - Address:00:0C:41:F2:F5:A7
ESSID:"linksys"
Mode:Managed
Frequency=2.437 GHz (Channel 6)
Quality:5/5 Signal level:-51 dBm Noise level:-92 dBm
Encrtption key: off
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 M/bs; 6 Mb/s
12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
48 Mb/s; 54 Mb/s

think im close to giving up and doing a fresh install. does ubuntu have a system restore?

---

### Post by Ayuthia on 2008-09-19
> **khayden39005 said:**
> the result of "lsmod | grep -i -e bcm43xx -e b43 -e b44 -e ndiswrapper -e wl" is:

b44           33552  0
ssb          38020   1 b44
mii           7552  1 b44
wl          1082192 0
ieee80211_crypt   8320 2 wl,ieee80211_crypt_tkip

i ran all the code you mentioned. the output for "sudo iwlist scan"
is still:

lo Interface doesnt support scanning.
eth0 Interface doesnt support scanning.
eth1 Scan completed:
Cell 01 - Address:00:0C:41:F2:F5:A7
ESSID:"linksys"
Mode:Managed
Frequency=2.437 GHz (Channel 6)
Quality:5/5 Signal level:-51 dBm Noise level:-92 dBm
Encrtption key: off
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 M/bs; 6 Mb/s
12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
48 Mb/s; 54 Mb/s

think im close to giving up and doing a fresh install. does ubuntu have a system restore?

You can try the following if you are getting the messages above:
```
sudo ifconfig eth1 down
sudo iwconfig eth1 mode Managed essid linksys
sudo ifconfig eth1 up
sudo dhclient eth1
```
You probably only need to do the iwconfig and dhclient steps, but when I compiled the wl driver on my own, it kept defaulting to ad-hoc mode instead of managed.

As far as I know, I have not seen any system restore for Ubuntu unless you are doing routine backups.

---

