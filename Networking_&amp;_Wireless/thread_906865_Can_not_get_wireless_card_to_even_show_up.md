---
title: "Can not get wireless card to even show up"
date: 2008-08-31
forum: Networking &amp; Wireless
---

### Post by shinynew on 2008-08-31
Intel Mini PCI Wireless 5300 a/g/n WiFi is my card. I have yet to find a place that tells me how to do this.

---

### Post by pytheas22 on 2008-09-01
Please post the output of these commands so that we can tell you what you need to do:
```

lspci -nn
lshw -C Network
```

---

### Post by shinynew on 2008-09-01
lspci -nn

```
00:00.0 Host bridge [0600]: Intel Corporation Cantiga Memory Controller Hub [8086:2a40] (rev 07)
00:01.0 PCI bridge [0604]: Intel Corporation Cantiga PCI Express Graphics Port [8086:2a41] (rev 07)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)
00:1a.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 [8086:2944] (rev 03)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 [8086:2946] (rev 03)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 [8086:2948] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93)
00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M LPC Interface Controller [8086:2919] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation ICH9M/M-E SATA AHCI Controller [8086:2929] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03)
01:00.0 VGA compatible controller [0300]: nVidia Corporation Unknown device [10de:0649] (rev a1)
0e:00.0 Network controller [0280]: Intel Corporation Unknown device [8086:4235]
14:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 02)
1a:00.0 System peripheral [0880]: JMicron Technologies, Inc. Unknown device [197b:2382]
1a:00.2 SD Host controller [0805]: JMicron Technologies, Inc. Unknown device [197b:2381]
1a:00.3 System peripheral [0880]: JMicron Technologies, Inc. Unknown device [197b:2383]
1a:00.4 System peripheral [0880]: JMicron Technologies, Inc. Unknown device [197b:2384]

```

lshw -C Network

```
  *-network UNCLAIMED     
       description: Network controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0e:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:14:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:ec:57:06:15
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=206.174.228.247 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s

```

sorry doesn't look that helpful to me. I found the windows drivers for it so I am going to try and use ndiswrapper.

---

### Post by pytheas22 on 2008-09-01
I can't find much about the 5300 card and Linux.  I did however find [this thread]("http://forum.ubuntuusers.de/topic/intel-wifi-link-5300-es-funktioniert-nix/?highlight=rev#post-1552546") (I knew my five semesters of German in college would pay off someday :)) that says that you can get the card working using the iwl4965 driver if you update the firmware and recompile it.  Try doing this (this is what the poster in that thread says he or she did to get the card working, with as much as possible translated into bash commands):

First, download [this file]("http://linuxwireless.org/download/compat-wireless-2.6/compat-wireless-old.tar.bz2") and save it to your desktop.  Then run these commands:

```
sudo apt-get install build-essential
wget http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-5000-ucode-5.4.A.11.tar.gz
tar -xzvf iwlwifi*
sudo cp iwlwifi-5000-ucode-5.4.A.11/iwlwifi-5000-1.ucode /lib/firmware
bunzip2 compat-wireless-old
tar xf compat-wireless-old
cd compat-wireless*old*
make
sudo make install
sudo make unload
sudo make load
```

Now reboot.  Does *lshw -C Network* still think that the card is unclaimed?  If so, what does dmesg say about the iwl4965 and iwl5300 modules (I'm not sure if you're actually compiling a new module called iwl5300, or if you're recompiling iwl4965 to also support the 5300 card)...were they loaded alright?

---

### Post by shinynew on 2008-09-02
That worked perfectly.

I am usually pretty good with fixing stuff, for example I have been using linux in some form or another for 2 or 3 years, and I have only asked for help and received it about 4 times. Thank you very much, if there is anything small I can do to help you out I will do it.

EDIT: I just got this laptop and tried to install XP on it (pretty good for gaming) and that BSODed on me every single time I tried to install (during set up) on four different disks. this ubuntu install is working fine now.

---

### Post by pytheas22 on 2008-09-02
I'm glad it worked!  And you can thank the Germans, who appear to be the ones who figured this out first; I just translated.

Also, if you want to return the favor, take a look around these forums whenever you get some free time to see if you know the answer to someone else's problem.  Helping others use Linux gets around to you again eventually.

By the way, keep in mind that if you upgrade your kernel via Ubuntu updates, you will probably need to rebuild the iwl5300 module because I don't think that any of the kernels in the repository will include that driver.  Hopefully it will be in Intrepid.

---

### Post by cdukes on 2008-09-02
Hi,
I have the exact same problem, except that I followed the instructions and it's still not working.
It looks like the driver gets loaded, but it still shows as disabled under lshw. I've been reading for hours now and haven't been able to resolve the problem.
The card (Intel 5300AGN) is on a new laptop (PCmicroworks Edge, which is based on a Clevo M860TU).


Here's my output from each command:
lspci -nn:
```

00:00.0 Host bridge [0600]: Intel Corporation Cantiga Memory Controller Hub [8086:2a40] (rev 07)
00:01.0 PCI bridge [0604]: Intel Corporation Cantiga PCI Express Graphics Port [8086:2a41] (rev 07)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)
00:1a.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 [8086:2944] (rev 03)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 [8086:2948] (rev 03)
00:1c.5 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 [8086:294a] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93)
00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M LPC Interface Controller [8086:2919] (rev 03)
00:1f.2 IDE interface [0101]: Intel Corporation ICH9M/M-E 2 port SATA IDE Controller [8086:2928] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03)
00:1f.5 IDE interface [0101]: Intel Corporation ICH9M/M-E 2 port SATA IDE Controller [8086:292d] (rev 03)
01:00.0 VGA compatible controller [0300]: nVidia Corporation Unknown device [10de:060b] (rev a2)
06:00.0 Network controller [0280]: Intel Corporation Unknown device [8086:4235]
07:00.0 FireWire (IEEE 1394) [0c00]: JMicron Technologies, Inc. Unknown device [197b:2380]
07:00.1 System peripheral [0880]: JMicron Technologies, Inc. Unknown device [197b:2382]
07:00.2 SD Host controller [0805]: JMicron Technologies, Inc. Unknown device [197b:2381]
07:00.3 System peripheral [0880]: JMicron Technologies, Inc. Unknown device [197b:2383]
08:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 02)

```

lshw -C Network:
```

  *-network DISABLED      
       description: Wireless interface
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wmaster0
       version: 00
       serial: 00:16:ea:76:8c:8c
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl4965 latency=0 module=iwl4965 multicast=yes wireless=IEEE 802.11abgn
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 02
       serial: 00:90:f5:80:3d:d9
       size: 1GB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=192.168.28.141 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=1GB/s

```

---

### Post by pytheas22 on 2008-09-03
cdukes,

Does it work if you type:
```

sudo ifconfig wlan0 up
```

If not, try rebooting.  After the system finishes booting, please run these commands and post the output:
```

iwlist scan
ifconfig
iwconfig
sudo modprobe --verbose iwl4965
sudo modprobe --verbose iwl5300
sudo modprobe --verbose iwl5000
dmesg | grep -e iwl -e wlan
```

Also, if there's a physical switch or button on your computer to enable the wireless, make sure it's on (I know that seems like a 'duh' suggestion, but you'd be surprised how often it solves the problem...especially because with some drivers, the wireless light remains on regardless of whether the card is enabled or not.)

---

### Post by tmaus on 2008-09-03
brilliant work.
It clearly saved me days of hard work finding the right solution

---

### Post by HarbingTarble on 2008-09-03
I'm having the same problem, I am using, according to windows, a Intel Wifi link 5300, but it's listed as a Intel 4965 on the product spec sheet for my laptop.

It's a Sager NP9262 laptop, I have tried compact wireless and Ndiswrapper with no result from either one of them.

This is my first time using Ubuntu(Or any form of linux) so I'm still unsure of where exactly its encountering a problem.. The fact that I can only get online when connected to a line doesn't help matters either. I have to download it while in windows, open my windows partition and find it while using booted into Ubuntu.

Any help would be appreciated.

Edit: Forgot to mention, because of that I can't post a lspci log, since I don't know how to enter my Ubuntu partition while in windows.

---

### Post by pytheas22 on 2008-09-03
HarpingTable,

You can copy and paste output from the terminal to a text file (Applications>Accessories>Text Editor), and then save it to a USB stick or something, from which you can open it in Windows.  Alternatively, you can install drivers allowing you to [access your Linux partition from Windows]("http://www.fs-driver.org/index.html") (that link is for ext3 drivers; if you use a different file system, like reiserfs, you'll need reiserfs drivers for Windows).

Please run these commands and post the output here so that we can figure out what's going on with you:
```

lshw -C Network
lspci -nn
```

---

### Post by pdub on 2008-09-04
Thanks! Worked great on my new Dell E6500 and Ubuntu Hardy with 2.6.24 Kernel. I did have to use compat-wireless-2.6-old though.

---

### Post by phoenix116 on 2008-09-06
thank you worked fine with my 5300 card and

32 BIT HARDY

however, i am currently trying to re-do the same on

64 BIT HARDY

but its not working. Is there any special way to do this on 64 bit?
as you can see below it seems to be working but the wlan adapter is disabled. Can anyone help me with this?


lshw -C network
 ```
 *-network DISABLED      
       description: Wireless interface
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0e:00.0
       logical name: wmaster0
       version: 00
       serial: 00:16:ea:6e:4c:2a
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl4965 latency=0 module=iwl4965 multicast=yes wireless=IEEE 802.11abgn
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:14:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:ec:55:91:3d
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK ip=192.168.1.100 latency=0 module=r8169 multicast=yes

```

lspci -nn
```

00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port [8086:2a41] (rev 07)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)
00:1a.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 [8086:2944] (rev 03)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 [8086:2946] (rev 03)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 [8086:2948] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93)
00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M LPC Interface Controller [8086:2919] (rev 03)
00:1f.2 IDE interface [0101]: Intel Corporation ICH9M/M-E 2 port SATA IDE Controller [8086:2928] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03)
00:1f.5 IDE interface [0101]: Intel Corporation ICH9M/M-E 2 port SATA IDE Controller [8086:292d] (rev 03)
01:00.0 VGA compatible controller [0300]: nVidia Corporation Unknown device [10de:0649] (rev a1)
0e:00.0 Network controller [0280]: Intel Corporation Unknown device [8086:4235]
14:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 02)
1a:00.0 System peripheral [0880]: JMicron Technologies, Inc. Unknown device [197b:2382]
1a:00.2 SD Host controller [0805]: JMicron Technologies, Inc. Unknown device [197b:2381]
1a:00.3 System peripheral [0880]: JMicron Technologies, Inc. Unknown device [197b:2383]
1a:00.4 System peripheral [0880]: JMicron Technologies, Inc. Unknown device [197b:2384]

```

---

### Post by pytheas22 on 2008-09-06
phoenix116,

Usually you get the "disabled" message because the interface is not up for some reason.  Try typing:
```

sudo ifconfig wlan0 up
```

Does that solve the problem?  If not, please post the output of:
```

sudo ifconfig wlan0 down
sudo ifconfig wlan0 up
dmesg | grep -e iwl -e wlan
```

---

### Post by phoenix116 on 2008-09-06
hm doesnt solve it, but thank you for the fast reply

however,

sudo ifconfig wlan0 gives the output
```

phoenix@phoenix-laptop:~$ sudo ifconfig wlan0 up
[sudo] password for phoenix: 
SIOCSIFFLAGS: Connection timed out

```
no output for the down command

and this for dmesg | grep -e iwl -e wlan

```

phoenix@phoenix-laptop:~$ dmesg | grep -e iwl -e wlan
[   32.035055] iwl4965: Intel(R) Wireless WiFi Link 4965AGN driver for Linux, 1.3.27k
[   32.035058] iwl4965: Copyright(c) 2003-2008 Intel Corporation
[   32.036626] iwl4965: Detected Intel Wireless WiFi Link 5300AGN REV=0x24
[   32.072417] iwl4965: Tunable channels: 13 802.11bg, 24 802.11a channels
[   32.072791] phy0: Selected rate control algorithm 'iwl-4965-rs'
[   36.498412] iwl4965: START_ALIVE timeout after 4000ms.
[   40.727843] iwl4965: START_ALIVE timeout after 4000ms.
[   44.363186] iwl4965: START_ALIVE timeout after 4000ms.
[   47.673398] iwl4965: START_ALIVE timeout after 4000ms.
[   51.510986] iwl4965: START_ALIVE timeout after 4000ms.
[   52.073854] iwl4965: START_ALIVE timeout after 4000ms.
[   67.258857] iwl4965: START_ALIVE timeout after 4000ms.
[   77.273373] iwl4965: START_ALIVE timeout after 4000ms.
[  150.781934] iwl4965: START_ALIVE timeout after 4000ms.
[  262.989131] iwl4965: START_ALIVE timeout after 4000ms.
[  367.122502] iwl4965: START_ALIVE timeout after 4000ms.
[  438.929656] iwl4965: START_ALIVE timeout after 4000ms.
[  492.925392] iwl4965: START_ALIVE timeout after 4000ms.
[  555.529573] iwl4965: START_ALIVE timeout after 4000ms.
[  599.550862] iwl4965: START_ALIVE timeout after 4000ms.
[  635.399058] iwl4965: START_ALIVE timeout after 4000ms.
[  687.137264] iwl4965: START_ALIVE timeout after 4000ms.
[  728.404129] iwl4965: START_ALIVE timeout after 4000ms.
[  887.587039] iwl4965: START_ALIVE timeout after 4000ms.
[ 1069.272767] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26k
[ 1069.272771] iwl3945: Copyright(c) 2003-2008 Intel Corporation
[ 1069.293469] iwl4965: Intel(R) Wireless WiFi Link 4965AGN driver for Linux, 1.3.27k
[ 1069.293474] iwl4965: Copyright(c) 2003-2008 Intel Corporation
[ 1069.295705] iwl4965: Detected Intel Wireless WiFi Link 5300AGN REV=0x24
[ 1069.314741] iwl4965: Tunable channels: 13 802.11bg, 24 802.11a channels
[ 1069.315614] phy0: Selected rate control algorithm 'iwl-4965-rs'
[ 1069.454321] usbcore: registered new interface driver rndis_wlan
[ 1071.947909] iwl4965: START_ALIVE timeout after 4000ms.
[ 1072.353674] iwl4965: START_ALIVE timeout after 4000ms.
[ 1072.807814] iwl4965: START_ALIVE timeout after 4000ms.
[ 1073.176868] iwl4965: START_ALIVE timeout after 4000ms.
[ 1075.074967] iwl4965: START_ALIVE timeout after 4000ms.
[ 1075.998631] iwl4965: START_ALIVE timeout after 4000ms.
[ 1076.816967] iwl4965: START_ALIVE timeout after 4000ms.
[ 1084.552915] iwl4965: START_ALIVE timeout after 4000ms.
[ 1091.956769] iwl4965: START_ALIVE timeout after 4000ms.
[ 1092.807386] iwl4965: START_ALIVE timeout after 4000ms.
[ 1134.042243] iwl4965: START_ALIVE timeout after 4000ms.
[ 1158.959860] iwl4965: START_ALIVE timeout after 4000ms.
[ 1310.052094] iwl4965: START_ALIVE timeout after 4000ms.
[ 1478.676176] iwl4965: START_ALIVE timeout after 4000ms.
[ 1629.634131] iwl4965: START_ALIVE timeout after 4000ms.
[ 1642.118895] iwl4965: START_ALIVE timeout after 4000ms.
[ 1644.943191] iwl4965: START_ALIVE timeout after 4000ms.

```

---

### Post by pytheas22 on 2008-09-06
hmmm, I'm still not sure what's going on.  The only log entry that looks suspicious is all those lines about "iwl4965: START_ALIVE timeout after 4000ms."  I googled a bit but didn't find much about them, however, and they don't seem to necessarily indicate that anything bad is happening.

Try rebooting, then run:
```

sudo modprobe -r iwl4965
sudo modprobe iwl4965
sudo ifconfig wlan0 up
```

Does that do anything?  If not, could you please post the total output of:

```
dmesg
iwlist scan; iwlist scan
iwconfig
```

The dmesg part will be pretty long, but I'm not sure where else to look.

---

### Post by phoenix116 on 2008-09-06
i havent tried what you suggested yet, though I already rebooted twice.

I think I found a thread on this, Its just for the 5100 card but its the same procedure...

have a look at this: [http://ubuntuforums.org/showthread.php?t=879134](http://ubuntuforums.org/showthread.php?t=879134)

---

### Post by pytheas22 on 2008-09-06
I looked through that thread and found [this post]("http://ubuntuforums.org/showpost.php?p=5727196&postcount=56") detailing how to get the card working on 64-bit.  You may want to try that.  The user does report in a subsequent post that he or she still experienced problems with the driver after rebooting, but at least it's a start.

Things may work better on Intrepid alpha release, too, if you feel like giving that a shot (don't expect it to be stable enough for use on a production machine, though).

---

### Post by phoenix116 on 2008-09-07
yeah tried that but it did only last for one session :(
as the user said

the result of sudo modprobe -r iwl4965 is a total hangup(everything stops and a lock symbol on the notebook starts blinking)


i have tried the kernel update too, it didnt help.
(and i have messed up my video configuration, cant figure out how to fix this even if i boot kernel 2.6.24-21, the nvidia-restricted driver doesnt work!)

I have a nvidia geforce m 9600 GT, has anyone had this problem?

---

### Post by phoenix116 on 2008-09-16
sometimes the compat-loaded driver works, but only until reboot

so, i finally tried dmesg | grep -e iwl -e wlan

```

phoenix@phoenix-laptop:~/Desktop/compat-wireless-2.6-old$ sudo dmesg | grep -e iwl -e wlan
[  623.901325] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26k
[  623.901328] iwl3945: Copyright(c) 2003-2008 Intel Corporation
[  623.921880] iwl4965: Intel(R) Wireless WiFi Link 4965AGN driver for Linux, 1.3.27k
[  623.921883] iwl4965: Copyright(c) 2003-2008 Intel Corporation
[  623.923409] iwl4965: Detected Intel Wireless WiFi Link 5300AGN REV=0x24
[  623.954455] iwl4965: Tunable channels: 13 802.11bg, 24 802.11a channels
[  623.955607] phy0: Selected rate control algorithm 'iwl-4965-rs'
[  624.162870] usbcore: registered new interface driver rndis_wlan
[  628.097373] iwl4965: START_ALIVE timeout after 4000ms.
[  628.097994] iwl4965: Microcode HW error detected.  Restarting.
[  628.099997] iwl4965: Microcode HW error detected.  Restarting.
[  633.093330] iwl4965: Could not load the INST uCode section
[  633.093335] iwl4965: Unable to set up bootstrap uCode: -110
[  638.090284] iwl4965: Could not load the INST uCode section
[  638.090291] iwl4965: Unable to set up bootstrap uCode: -110
[  643.087223] iwl4965: Could not load the INST uCode section
[  643.087230] iwl4965: Unable to set up bootstrap uCode: -110
[  648.084194] iwl4965: Could not load the INST uCode section
[  648.084201] iwl4965: Unable to set up bootstrap uCode: -110
[  653.081154] iwl4965: Could not load the INST uCode section
[  653.081161] iwl4965: Unable to set up bootstrap uCode: -110
[  654.695939] iwl4965: Unable to initialize device after 5 attempts.
[  658.701729] iwl4965: START_ALIVE timeout after 4000ms.
[  662.716270] iwl4965: START_ALIVE timeout after 4000ms.
[  666.813755] iwl4965: START_ALIVE timeout after 4000ms.
[  670.815329] iwl4965: START_ALIVE timeout after 4000ms.
[  693.200714] iwl4965: START_ALIVE timeout after 4000ms.
[  697.970835] iwl4965: START_ALIVE timeout after 4000ms.

```

---

### Post by pytheas22 on 2008-09-16
phoenix116,

So to be clear: after some restarts, the driver works, but after others it doesn't?  Do you notice any pattern to it?  If the computer has been off for a long time before being restarted, does it tend to work then, or vice versa?

Is your dmesg output above from an instance where the card wasn't working at all since reboot, or where it was initially working but crashed later?

And if you run this:
```

sudo rmmod iwl4965
sudo modprobe iwl4965
```

does it fix things?  (Or crash the computer?)

Also is your nvidia driver still broken, and if so is this directly related to the presence iwl4965?  If so, why do you think that iwl4965 had to do with it?

---

### Post by publicv on 2008-09-16
> **pdub said:**
> Thanks! Worked great on my new Dell E6500 and Ubuntu Hardy with 2.6.24 Kernel. I did have to use compat-wireless-2.6-old though.


I have an E6400 and am trying to get it to work on 8.04/64 bit - i did as instructed (but with using compat-wireless-2.6-old like pdub), and i can get a list of all available networks but can not authenticate.

The same laptop manages to connect under windows.

```

lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82567LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:21:70:ac:9b:5b
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000e-ich9m driverversion=0.2.9.5 firmware=1.7-7 ip=192.168.1.5 latency=0 module=e1000e_ich9m multicast=yes
  *-network
       description: Wireless interface
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wmaster0
       version: 00
       serial: 00:16:ea:60:94:92
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn


```


```

lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 07)
00:02.1 Display controller [0380]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a43] (rev 07)
00:19.0 Ethernet controller [0200]: Intel Corporation 82567LM Gigabit Network Connection [8086:10f5] (rev 03)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)
00:1a.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 [8086:2944] (rev 03)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 [8086:2946] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93)
00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M-E LPC Interface Controller [8086:2917] (rev 03)
00:1f.2 RAID bus controller [0104]: Intel Corporation Mobile 82801 SATA RAID Controller [8086:282a] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03)
03:01.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 04)
03:01.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 21)
03:01.2 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev 11)
0c:00.0 Network controller [0280]: Intel Corporation Unknown device [8086:4235]

```

Any idea what I'm doing wrong?

EDIT: dmesg reports a lot of timeouts when i try to connect to my network:
```

[   72.526729] ACPI: PCI Interrupt 0000:0c:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   72.526822] PM: Writing back config space on device 0000:0c:00.0 at offset 1 (was 100102, writing 100106)
[   72.543534] Registered led device: iwl-phy0:radio
[   72.543574] Registered led device: iwl-phy0:assoc
[   72.543610] Registered led device: iwl-phy0:RX
[   72.543642] Registered led device: iwl-phy0:TX
[   72.582690] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   96.006197] wlan0: authenticate with AP 00:14:6c:51:68:78
[   96.060431] wlan0: authenticate with AP 00:14:6c:51:68:78
[   96.175916] wlan0: authenticate with AP 00:14:6c:51:68:78
[   96.320139] wlan0: authentication with AP 00:14:6c:51:68:78 timed out
[  101.156874] wlan0: authenticate with AP 00:14:6c:51:68:78
[  101.212700] wlan0: authenticate with AP 00:14:6c:51:68:78
[  101.333301] wlan0: authenticate with AP 00:14:6c:51:68:78
[  101.449101] wlan0: authentication with AP 00:14:6c:51:68:78 timed out
[  106.618693] wlan0: authenticate with AP 00:14:6c:51:68:78
[  106.619515] wlan0: authenticate with AP 00:14:6c:51:68:78
[  106.770393] wlan0: authenticate with AP 00:14:6c:51:68:78
[  106.926627] wlan0: authenticate with AP 00:14:6c:51:68:78
[  107.091499] wlan0: authentication with AP 00:14:6c:51:68:78 timed out
[  113.290363] wlan0: authenticate with AP 00:14:6c:51:68:78
[  113.353554] wlan0: authenticate with AP 00:14:6c:51:68:78
[  113.423176] wlan0: authenticate with AP 00:14:6c:51:68:78
[  113.487570] wlan0: authentication with AP 00:14:6c:51:68:78 timed out
[  119.823921] wlan0: authenticate with AP 00:14:6c:51:68:78
[  119.895244] wlan0: authenticate with AP 00:14:6c:51:68:78
[  119.978408] wlan0: authenticate with AP 00:14:6c:51:68:78
[  120.129148] wlan0: authentication with AP 00:14:6c:51:68:78 timed out
[  127.154078] ACPI: PCI interrupt for device 0000:0c:00.0 disabled


```

---

### Post by pytheas22 on 2008-09-16
> I have an E6400 and am trying to get it to work on 8.04/64 bit - i did as instructed (but with using compat-wireless-2.6-old like pdub), and i can get a list of all available networks but can not authenticate.

You may want to try connecting using [wicd]("http://wicd.sourceforge.net") instead of Network Manager.  Some people have better luck with wicd in situations like this.

If that doesn't help, try turning off security on your network to see if you can connect then.  Also, if your router is running in N mode, try changing to G or B.

Please let us know...

---

### Post by Outlaw Rudy on 2008-09-16
I've also got the 5300 and 64-bit ubuntu. I've followed the instructions in the thread and now can see wireless networks with the network manager, but I also cannot connect to them. wicd also does not connect. When I try with the network manager, neither of the balls turn green (whereas in my old laptop with ubuntu, the bottom one would always turn green).

If there's no good advice, I've been reading around and see that the 2.6.27 kernel has drivers which supposedly support the 5300, so maybe I'll finally learn how to compile kernels and get back to you sometime in the next couple of days.

---

### Post by publicv on 2008-09-17
> **pytheas22 said:**
> You may want to try connecting using [wicd]("http://wicd.sourceforge.net") instead of Network Manager.  Some people have better luck with wicd in situations like this.

If that doesn't help, try turning off security on your network to see if you can connect then.  Also, if your router is running in N mode, try changing to G or B.

Please let us know...

Same thing as Outlaw Rudy, wicd made no difference and neither did turning off security.  My router is running in G and B modes and I am trying to authenticate via WEP/64bit hex key.  I just keep getting the timeouts.

---

### Post by ffteixeira on 2008-09-17
Works very well with Intel Mini PCI Wireless 5300, thanks!

---

### Post by Outlaw Rudy on 2008-09-17
Success! While it's not the ideal solution, Intrepid Ibex Alpha 5 plays very nicely with my wireless card, and is probably easier than recompiling kernels (since I've never done that before). If you guys are desperate like I was, hopefully this will work for you too.

---

### Post by publicv on 2008-09-17
> **Outlaw Rudy said:**
> Success! While it's not the ideal solution, Intrepid Ibex Alpha 5 plays very nicely with my wireless card, and is probably easier than recompiling kernels (since I've never done that before). If you guys are desperate like I was, hopefully this will work for you too.

Same thing here.

---

### Post by rasmus91 on 2008-10-02
Hi guys, i've tried and tried, and im getting tired... -.-

I do appreciate all the help ;) But i just can't figure out how to do this, im just gonna show you a couple of things which i hope will help.

```
rasmus@rasmus-DellE6400:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Cantiga Memory Controller Hub [8086:2a40] (rev 07)
00:02.0 VGA compatible controller [0300]: Intel Corporation Cantiga Integrated Graphics Controller [8086:2a42] (rev 07)
00:02.1 Display controller [0380]: Intel Corporation Cantiga Integrated Graphics Controller [8086:2a43] (rev 07)
00:19.0 Ethernet controller [0200]: Intel Corporation 82567LM Gigabit Network Connection [8086:10f5] (rev 03)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)
00:1a.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 [8086:2944] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93)
00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M-E LPC Interface Controller [8086:2917] (rev 03)
00:1f.2 RAID bus controller [0104]: Intel Corporation Mobile 82801 SATA RAID Controller [8086:282a] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03)
03:01.0 CardBus bridge [0607]: Ricoh Co Ltd RL5c476 II [1180:0476] (rev ba)
03:01.1 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 04)
03:01.2 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 21)
03:01.3 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev 11)
0c:00.0 Network controller [0280]: Intel Corporation Unknown device [8086:4232]

```

And: 
```
rasmus@rasmus-DellE6400:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82567LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:21:70:a6:a4:ab
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000e-ich9m driverversion=0.2.9.5 firmware=1.7-7 ip=192.168.1.105 latency=0 module=e1000e_ich9m multicast=yes
  *-network UNCLAIMED
       description: Network controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0

```

I already tried to install, im not quite the genious at using the terminal, but i gues it okay, have a look at this, i followed a guide from this thread: ```
rasmus@rasmus-DellE6400:~$ sudo apt-get install build-essential
[sudo] password for rasmus: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
rasmus@rasmus-DellE6400:~$ wget http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-5000-ucode-5.4.A.11.tar.gz
--19:26:52--  http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-5000-ucode-5.4.A.11.tar.gz
           => `iwlwifi-5000-ucode-5.4.A.11.tar.gz.5'
Resolving intellinuxwireless.org... 204.253.143.234
Connecting to intellinuxwireless.org|204.253.143.234|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 180,429 (176K) [application/x-gzip]

100%[====================================>] 180,429      121.36K/s             

19:26:54 (121.07 KB/s) - `iwlwifi-5000-ucode-5.4.A.11.tar.gz.5' saved [180429/180429]

rasmus@rasmus-DellE6400:~$ tar -xzvf iwlwifi*
tar: iwlwifi-5000-ucode-5.4.A.11: Cannot read: Is a directory
tar: At beginning of tape, quitting now
tar: Error is not recoverable: exiting now

gzip: stdin: unexpected end of file
tar: Child returned status 2
tar: iwlwifi-5000-ucode-5.4.A.11.tar.gz: Not found in archive
tar: iwlwifi-5000-ucode-5.4.A.11.tar.gz.1: Not found in archive
tar: iwlwifi-5000-ucode-5.4.A.11.tar.gz.2: Not found in archive
tar: iwlwifi-5000-ucode-5.4.A.11.tar.gz.3: Not found in archive
tar: iwlwifi-5000-ucode-5.4.A.11.tar.gz.4: Not found in archive
tar: iwlwifi-5000-ucode-5.4.A.11.tar.gz.5: Not found in archive
tar: Error exit delayed from previous errors
rasmus@rasmus-DellE6400:~$ 

```

This is quite anoying. i noticed something though: iwlwifi-5000-ucode-5.4.A.11.tar.gz.5'... (i just mean there's also: tar: iwlwifi-5000-ucode-5.4.A.11.tar.gz.4)  and again just below... what the heck does this mean? yes i have tried to install several times... 

then, i tried to skip something and continue with this:
```
rasmus@rasmus-DellE6400:~$ bunzip2 compat-wireless-2.6.tar.bz2
bunzip2: Can't open input file compat-wireless-2.6.tar.bz2: No such file or directory.
rasmus@rasmus-DellE6400:~$ 


```

What am i doing wrong????

I've not had Ubuntu for that long, but please tell me what i should do. i'll follow your instuctions as well as i can, just tell me EXACTLY what to type please...


BTW: until i get this working im stuck on Vista/longhorn, which is a pain in my .... ](*,)
anyway, thank you guys you're the best

---

### Post by pytheas22 on 2008-10-02
rasmus91,

Sorry that you're having trouble--but actually you shouldn't blame yourself.  There were some problems with the instructions that I wrote out in step 4 that no one mentioned until now.  I think I may have forgotten to include an important command, and it also seems that trying to 'wget' source code from linuxwireless.org isn't working.  No one said anything before about having problems, but perhaps they just worked through them themselves, I don't know.

In any case, please follow these instructions, which should work:

1. download [this file]("http://linuxwireless.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2") and save it to your desktop on Ubuntu.

2. open a terminal and run these commands:

```
cd ~/Desktop
sudo apt-get install build-essential
wget http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-5000-ucode-5.4.A.11.tar.gz
tar -xzvf iwlwifi*
sudo cp iwlwifi-5000-ucode-5.4.A.11/iwlwifi-5000-1.ucode /lib/firmware
bunzip2 compat-wireless-2.6.tar.bz2
tar xf compat-wireless-2.6.tar
cd compat-wireless-2008*
gedit config.mk
```

3. At this point a file should pop open in your text editor.  Search the file for the line that reads *CONFIG_IWL4965_HT=y* (should be line 76).  Immediately below this line, insert a new line containing this:
```

CONFIG_IWL5000=y
```

Then save and close the file.

4. run these commands (in the same terminal that you used for the previous ones):
```

make
sudo make install
sudo make unload
sudo make load
```

At this point your wireless card should be recognized and working.  If not, try rebooting.  If it still doesn't work, please post the output of:
```

lshw -C Network
dmesg | grep -e iwl -e wlan
uname -m
```

Also note that this driver may not work well or at all on 64-bit kernels (32-bit should be fine), as far as I know.  I haven't checked in several weeks and there may well have been progress since then, but the last I heard, no 64-bit user had gotten this card working reliably.

---

### Post by rasmus91 on 2008-10-03
Ehmm.... I think i might just ran in to a little bit of a problem: ```
rasmus@rasmus-DellE6400:~/Desktop/compat-wireless-2008-10-03$ make
/home/rasmus/Desktop/compat-wireless-2008-10-03/config.mk:28: *** "ERROR: You should use compat-wireless-2.6-old for older kernels, this one is for kenrels >= 2.6.27".  Stop.

```

I've thought about this once before, but i have no idea on how to fix this...

What do i do now?

---

### Post by pytheas22 on 2008-10-03
Sorry, I didn't realize that.  Try using these instructions:

1. download [this file]("http://linuxwireless.org/download/compat-wireless-2.6/compat-wireless-old.tar.bz2") and save it to your desktop.  Also remove any directories or other files that are on your desktop from your previous attempts to install this.

2. run:
```

cd ~/Desktop
sudo apt-get install build-essential
wget http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-5000-ucode-5.4.A.11.tar.gz
tar -xzvf iwlwifi*
sudo cp iwlwifi-5000-ucode-5.4.A.11/iwlwifi-5000-1.ucode /lib/firmware
bunzip2 compat-wireless-old.tar.bz2 
tar xf compat-wireless-old.tar
cd compat-wireless-2.6-old
make
sudo make install
sudo make unload
sudo make load
```

You should not need to manually edit any configuration files this time.  Does the build work now?

Also, you may want to try simply switching to Intrepid alpha release.  It should include support for your wireless card out-of-the-box.

---

### Post by rasmus91 on 2008-10-03
Hmm... i don't really know... i can't figure out how to check up on it... I'll try rebooting now, If you wan't any information about the install, watch here: ```
00/rt73usb.o
  LD      /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/wireless/zd1211rw/built-in.o
  CC [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/wireless/zd1211rw/zd_chip.o
  CC [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/wireless/zd1211rw/zd_ieee80211.o
  CC [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/wireless/zd1211rw/zd_mac.o
  CC [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/wireless/zd1211rw/zd_rf_al2230.o
  CC [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/wireless/zd1211rw/zd_rf_rf2959.o
  CC [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/wireless/zd1211rw/zd_rf_al7230b.o
  CC [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/wireless/zd1211rw/zd_rf_uw2453.o
  CC [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/wireless/zd1211rw/zd_rf.o
  CC [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/wireless/zd1211rw/zd_usb.o
  LD [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/wireless/zd1211rw/zd1211rw.o
  LD      /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/ssb/built-in.o
  CC [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/ssb/main.o
  CC [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/ssb/scan.o
  CC [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/ssb/sprom.o
  CC [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/ssb/pci.o
  CC [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/ssb/pcihost_wrapper.o
  CC [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/ssb/pcmcia.o
  CC [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/ssb/driver_chipcommon.o
  CC [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/ssb/driver_pcicore.o
  CC [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/ssb/b43_pci_bridge.o
  LD [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/ssb/ssb.o
  LD      /home/rasmus/Desktop/compat-wireless-2.6-old/net/ieee80211/built-in.o
  CC [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/net/ieee80211/ieee80211_module.o
  CC [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/net/ieee80211/ieee80211_tx.o
  CC [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/net/ieee80211/ieee80211_rx.o
  CC [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/net/ieee80211/ieee80211_wx.o
  CC [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/net/ieee80211/ieee80211_geo.o
  LD [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/net/ieee80211/ieee80211.o
  CC [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/net/ieee80211/ieee80211_crypt.o
  CC [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/net/ieee80211/ieee80211_crypt_wep.o
  CC [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/net/ieee80211/ieee80211_crypt_ccmp.o
  CC [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/net/ieee80211/ieee80211_crypt_tkip.o
  LD      /home/rasmus/Desktop/compat-wireless-2.6-old/net/mac80211/built-in.o
  CC [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/net/mac80211/main.o
  CC [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/net/mac80211/wext.o
  CC [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/net/mac80211/sta_info.o
  CC [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/net/mac80211/wep.o
  CC [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/net/mac80211/wpa.o
  CC [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/net/mac80211/mlme.o
  CC [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/net/mac80211/iface.o
  CC [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/net/mac80211/rate.o
  CC [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/net/mac80211/michael.o
  CC [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/net/mac80211/tkip.o
  CC [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/net/mac80211/aes_ccm.o
  CC [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/net/mac80211/cfg.o
  CC [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/net/mac80211/rx.o
  CC [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/net/mac80211/tx.o
  CC [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/net/mac80211/key.o
  CC [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/net/mac80211/util.o
  CC [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/net/mac80211/event.o
  CC [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/net/mac80211/led.o
  CC [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/net/mac80211/debugfs.o
  CC [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/net/mac80211/debugfs_sta.o
  CC [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/net/mac80211/debugfs_netdev.o
  CC [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/net/mac80211/debugfs_key.o
  CC [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/net/mac80211/mesh.o
  CC [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/net/mac80211/mesh_pathtbl.o
  CC [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/net/mac80211/mesh_plink.o
  CC [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/net/mac80211/mesh_hwmp.o
  CC [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/net/mac80211/rc80211_pid_algo.o
  CC [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/net/mac80211/rc80211_pid_debugfs.o
  LD [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/net/mac80211/mac80211.o
  LD      /home/rasmus/Desktop/compat-wireless-2.6-old/net/wireless/built-in.o
  CC [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/net/wireless/core.o
  CC [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/net/wireless/sysfs.o
  CC [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/net/wireless/radiotap.o
  CC [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/net/wireless/util.o
  CC [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/net/wireless/reg.o
  CC [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/net/wireless/compat.o
  CC [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/net/wireless/nl80211.o
  LD [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/net/wireless/cfg80211.o
  LD      /home/rasmus/Desktop/compat-wireless-2.6-old/built-in.o
  Building modules, stage 2.
  MODPOST 44 modules
  CC      /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/misc/eeprom_93cx6.mod.o
  LD [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/misc/eeprom_93cx6.ko
  CC      /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/b44.mod.o
  LD [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/b44.ko
  CC      /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/usb/cdc_ether.mod.o
  LD [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/usb/cdc_ether.ko
  CC      /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/usb/rndis_host.mod.o
  LD [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/usb/rndis_host.ko
  CC      /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/usb/usbnet.mod.o
  LD [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/usb/usbnet.ko
  CC      /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/wireless/adm8211.mod.o
  LD [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/wireless/adm8211.ko
  CC      /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/wireless/at76_usb.mod.o
  LD [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/wireless/at76_usb.ko
  CC      /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/wireless/ath5k/ath5k.mod.o
  LD [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/wireless/ath5k/ath5k.ko
  CC      /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/wireless/ath9k/ath9k.mod.o
  LD [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/wireless/ath9k/ath9k.ko
  CC      /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/wireless/b43/b43.mod.o
  LD [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/wireless/b43/b43.ko
  CC      /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/wireless/b43legacy/b43legacy.mod.o
  LD [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/wireless/b43legacy/b43legacy.ko
  CC      /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/wireless/ipw2100.mod.o
  LD [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/wireless/ipw2100.ko
  CC      /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/wireless/ipw2200.mod.o
  LD [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/wireless/ipw2200.ko
  CC      /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwl3945.mod.o
  LD [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwl3945.ko
  CC      /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwlagn.mod.o
  LD [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwlagn.ko
  CC      /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwlcore.mod.o
  LD [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwlcore.ko
  CC      /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/wireless/libertas/libertas.mod.o
  LD [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/wireless/libertas/libertas.ko
  CC      /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/wireless/libertas/libertas_cs.mod.o
  LD [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/wireless/libertas/libertas_cs.ko
  CC      /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/wireless/libertas/libertas_sdio.mod.o
  LD [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/wireless/libertas/libertas_sdio.ko
  CC      /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/wireless/libertas/usb8xxx.mod.o
  LD [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/wireless/libertas/usb8xxx.ko
  CC      /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/wireless/mac80211_hwsim.mod.o
  LD [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/wireless/mac80211_hwsim.ko
  CC      /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/wireless/p54/p54common.mod.o
  LD [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/wireless/p54/p54common.ko
  CC      /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/wireless/p54/p54pci.mod.o
  LD [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/wireless/p54/p54pci.ko
  CC      /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/wireless/p54/p54usb.mod.o
  LD [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/wireless/p54/p54usb.ko
  CC      /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/wireless/rndis_wlan.mod.o
  LD [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/wireless/rndis_wlan.ko
  CC      /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2400pci.mod.o
  LD [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2400pci.ko
  CC      /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2500pci.mod.o
  LD [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2500pci.ko
  CC      /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2500usb.mod.o
  LD [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2500usb.ko
  CC      /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2x00lib.mod.o
  LD [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2x00lib.ko
  CC      /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2x00pci.mod.o
  LD [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2x00pci.ko
  CC      /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2x00usb.mod.o
  LD [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2x00usb.ko
  CC      /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt61pci.mod.o
  LD [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt61pci.ko
  CC      /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt73usb.mod.o
  LD [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt73usb.ko
  CC      /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/wireless/rtl8180.mod.o
  LD [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/wireless/rtl8180.ko
  CC      /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/wireless/rtl8187.mod.o
  LD [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/wireless/rtl8187.ko
  CC      /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/wireless/zd1211rw/zd1211rw.mod.o
  LD [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/wireless/zd1211rw/zd1211rw.ko
  CC      /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/ssb/ssb.mod.o
  LD [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/ssb/ssb.ko
  CC      /home/rasmus/Desktop/compat-wireless-2.6-old/net/ieee80211/ieee80211.mod.o
  LD [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/net/ieee80211/ieee80211.ko
  CC      /home/rasmus/Desktop/compat-wireless-2.6-old/net/ieee80211/ieee80211_crypt.mod.o
  LD [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/net/ieee80211/ieee80211_crypt.ko
  CC      /home/rasmus/Desktop/compat-wireless-2.6-old/net/ieee80211/ieee80211_crypt_ccmp.mod.o
  LD [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/net/ieee80211/ieee80211_crypt_ccmp.ko
  CC      /home/rasmus/Desktop/compat-wireless-2.6-old/net/ieee80211/ieee80211_crypt_tkip.mod.o
  LD [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/net/ieee80211/ieee80211_crypt_tkip.ko
  CC      /home/rasmus/Desktop/compat-wireless-2.6-old/net/ieee80211/ieee80211_crypt_wep.mod.o
  LD [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/net/ieee80211/ieee80211_crypt_wep.ko
  CC      /home/rasmus/Desktop/compat-wireless-2.6-old/net/mac80211/mac80211.mod.o
  LD [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/net/mac80211/mac80211.ko
  CC      /home/rasmus/Desktop/compat-wireless-2.6-old/net/wireless/cfg80211.mod.o
  LD [M]  /home/rasmus/Desktop/compat-wireless-2.6-old/net/wireless/cfg80211.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
rasmus@rasmus-DellE6400:~/Desktop/compat-wireless-2.6-old$ sudo make install

Your old wireless subsystem modules were left intact:

/lib/modules/2.6.24-19-generic/kernel/net/mac80211/mac80211.ko
/lib/modules/2.6.24-19-generic/kernel/net/wireless/cfg80211.ko
/lib/modules/2.6.24-19-generic/kernel/drivers/net/wireless/adm8211.ko
/lib/modules/2.6.24-19-generic/ubuntu/wireless/at76/at76_usb.ko
/lib/modules/2.6.24-19-generic/kernel/drivers/net/wireless/b43/b43.ko
/lib/modules/2.6.24-19-generic/kernel/drivers/net/wireless/b43legacy/b43legacy.ko
/lib/modules/2.6.24-19-generic/kernel/drivers/ssb/ssb.ko
/lib/modules/2.6.24-19-generic/ubuntu/wireless/iwlwifi/iwlwifi/compatible/iwl3945.ko
/lib/modules/2.6.24-19-generic/kernel/drivers/net/wireless/ipw2100.ko
/lib/modules/2.6.24-19-generic/kernel/drivers/net/wireless/ipw2200.ko
/lib/modules/2.6.24-19-generic/kernel/net/ieee80211/ieee80211.ko
/lib/modules/2.6.24-19-generic/kernel/net/ieee80211/ieee80211_crypt.ko
/lib/modules/2.6.24-19-generic/kernel/drivers/net/wireless/libertas/libertas_cs.ko
/lib/modules/2.6.24-19-generic/kernel/net/mac80211/mac80211.ko
/lib/modules/2.6.24-19-generic/kernel/drivers/net/wireless/p54pci.ko
/lib/modules/2.6.24-19-generic/kernel/drivers/net/wireless/p54usb.ko
/lib/modules/2.6.24-19-generic/kernel/drivers/net/wireless/rt2x00/rt2400pci.ko
/lib/modules/2.6.24-19-generic/kernel/drivers/net/wireless/rt2x00/rt2500pci.ko
/lib/modules/2.6.24-19-generic/kernel/drivers/net/wireless/rt2x00/rt2500usb.ko
/lib/modules/2.6.24-19-generic/kernel/drivers/net/wireless/rt2x00/rt61pci.ko
/lib/modules/2.6.24-19-generic/kernel/drivers/net/wireless/rt2x00/rt73usb.ko
/lib/modules/2.6.24-19-generic/kernel/drivers/net/usb/usbnet.ko
/lib/modules/2.6.24-19-generic/kernel/drivers/net/usb/cdc_ether.ko
/lib/modules/2.6.24-19-generic/kernel/drivers/net/usb/rndis_host.ko
/lib/modules/2.6.24-19-generic/kernel/drivers/net/wireless/rtl8187.ko
/lib/modules/2.6.24-19-generic/kernel/drivers/net/wireless/zd1211rw/zd1211rw.ko
/lib/modules/2.6.24-19-generic/kernel/net/ieee80211/softmac/ieee80211softmac.ko

make -C /lib/modules/2.6.24-19-generic/build M=/home/rasmus/Desktop/compat-wireless-2.6-old modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
/home/rasmus/Desktop/compat-wireless-2.6-old/config.mk:53: "WARNING: You are running a kernel >= 2.6.23, you should enable in it CONFIG_NETDEVICES_MULTIQUEUE for 802.11[ne] support"
  Building modules, stage 2.
  MODPOST 44 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make -C /lib/modules/2.6.24-19-generic/build M=/home/rasmus/Desktop/compat-wireless-2.6-old "INSTALL_MOD_DIR=updates"  \
		modules_install
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  INSTALL /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/misc/eeprom_93cx6.ko
  INSTALL /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/b44.ko
  INSTALL /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/usb/cdc_ether.ko
  INSTALL /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/usb/rndis_host.ko
  INSTALL /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/usb/usbnet.ko
  INSTALL /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/wireless/adm8211.ko
  INSTALL /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/wireless/at76_usb.ko
  INSTALL /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/wireless/ath5k/ath5k.ko
  INSTALL /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/wireless/ath9k/ath9k.ko
  INSTALL /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/wireless/b43/b43.ko
  INSTALL /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/wireless/b43legacy/b43legacy.ko
  INSTALL /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/wireless/ipw2100.ko
  INSTALL /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/wireless/ipw2200.ko
  INSTALL /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwl3945.ko
  INSTALL /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwlagn.ko
  INSTALL /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwlcore.ko
  INSTALL /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/wireless/libertas/libertas.ko
  INSTALL /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/wireless/libertas/libertas_cs.ko
  INSTALL /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/wireless/libertas/libertas_sdio.ko
  INSTALL /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/wireless/libertas/usb8xxx.ko
  INSTALL /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/wireless/mac80211_hwsim.ko
  INSTALL /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/wireless/p54/p54common.ko
  INSTALL /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/wireless/p54/p54pci.ko
  INSTALL /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/wireless/p54/p54usb.ko
  INSTALL /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/wireless/rndis_wlan.ko
  INSTALL /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2400pci.ko
  INSTALL /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2500pci.ko
  INSTALL /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2500usb.ko
  INSTALL /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2x00lib.ko
  INSTALL /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2x00pci.ko
  INSTALL /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2x00usb.ko
  INSTALL /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt61pci.ko
  INSTALL /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt73usb.ko
  INSTALL /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/wireless/rtl8180.ko
  INSTALL /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/wireless/rtl8187.ko
  INSTALL /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/net/wireless/zd1211rw/zd1211rw.ko
  INSTALL /home/rasmus/Desktop/compat-wireless-2.6-old/drivers/ssb/ssb.ko
  INSTALL /home/rasmus/Desktop/compat-wireless-2.6-old/net/ieee80211/ieee80211.ko
  INSTALL /home/rasmus/Desktop/compat-wireless-2.6-old/net/ieee80211/ieee80211_crypt.ko
  INSTALL /home/rasmus/Desktop/compat-wireless-2.6-old/net/ieee80211/ieee80211_crypt_ccmp.ko
  INSTALL /home/rasmus/Desktop/compat-wireless-2.6-old/net/ieee80211/ieee80211_crypt_tkip.ko
  INSTALL /home/rasmus/Desktop/compat-wireless-2.6-old/net/ieee80211/ieee80211_crypt_wep.ko
  INSTALL /home/rasmus/Desktop/compat-wireless-2.6-old/net/mac80211/mac80211.ko
  INSTALL /home/rasmus/Desktop/compat-wireless-2.6-old/net/wireless/cfg80211.ko
  DEPMOD  2.6.24-19-generic
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'

Note: madwifi detected, we're going to disable it. If you would like to enable it later you can run:
    sudo athenable madwifi

Running athenable ath5k...
Disabling ath_pci ...	[OK]	Module disabled:
/lib/modules/2.6.24-19-generic/madwifi/ath_pci.ko

Currently detected wireless subsystem modules:

/lib/modules/2.6.24-19-generic/updates/net/mac80211/mac80211.ko
/lib/modules/2.6.24-19-generic/updates/net/wireless/cfg80211.ko
/lib/modules/2.6.24-19-generic/updates/drivers/net/wireless/adm8211.ko
/lib/modules/2.6.24-19-generic/updates/drivers/net/wireless/at76_usb.ko
/lib/modules/2.6.24-19-generic/updates/drivers/net/wireless/ath5k/ath5k.ko
/lib/modules/2.6.24-19-generic/updates/drivers/net/wireless/ath9k/ath9k.ko
/lib/modules/2.6.24-19-generic/updates/drivers/net/wireless/b43/b43.ko
/lib/modules/2.6.24-19-generic/updates/drivers/net/wireless/b43legacy/b43legacy.ko
/lib/modules/2.6.24-19-generic/updates/drivers/ssb/ssb.ko
/lib/modules/2.6.24-19-generic/updates/drivers/net/wireless/iwlwifi/iwlcore.ko
/lib/modules/2.6.24-19-generic/updates/drivers/net/wireless/iwlwifi/iwl3945.ko
/lib/modules/2.6.24-19-generic/updates/drivers/net/wireless/iwlwifi/iwlagn.ko
/lib/modules/2.6.24-19-generic/updates/drivers/net/wireless/ipw2100.ko
/lib/modules/2.6.24-19-generic/updates/drivers/net/wireless/ipw2200.ko
/lib/modules/2.6.24-19-generic/updates/net/ieee80211/ieee80211.ko
/lib/modules/2.6.24-19-generic/updates/net/ieee80211/ieee80211_crypt.ko
/lib/modules/2.6.24-19-generic/updates/drivers/net/wireless/libertas/libertas_cs.ko
/lib/modules/2.6.24-19-generic/updates/drivers/net/wireless/rt2x00/rt2400pci.ko
/lib/modules/2.6.24-19-generic/updates/drivers/net/wireless/rt2x00/rt2500pci.ko
/lib/modules/2.6.24-19-generic/updates/drivers/net/wireless/rt2x00/rt2500usb.ko
/lib/modules/2.6.24-19-generic/updates/drivers/net/wireless/rt2x00/rt61pci.ko
/lib/modules/2.6.24-19-generic/updates/drivers/net/wireless/rt2x00/rt73usb.ko
/lib/modules/2.6.24-19-generic/updates/drivers/net/usb/usbnet.ko
/lib/modules/2.6.24-19-generic/updates/drivers/net/usb/cdc_ether.ko
/lib/modules/2.6.24-19-generic/updates/drivers/net/usb/rndis_host.ko
/lib/modules/2.6.24-19-generic/updates/drivers/net/wireless/rndis_wlan.ko
/lib/modules/2.6.24-19-generic/updates/drivers/net/wireless/rtl8180.ko
/lib/modules/2.6.24-19-generic/updates/drivers/net/wireless/rtl8187.ko
/lib/modules/2.6.24-19-generic/updates/drivers/net/wireless/zd1211rw/zd1211rw.ko

Now run:

make unload

And then load the wireless module you need. If unsure run:

make load

rasmus@rasmus-DellE6400:~/Desktop/compat-wireless-2.6-old$ sudo make unload
rasmus@rasmus-DellE6400:~/Desktop/compat-wireless-2.6-old$ sudo make load
Loading ipw2100...
Loading ipw2200...
Loading libertas_cs...
Loading usb8xxx...
Loading p54pci...
Loading p54usb...
Loading adm8211...
Loading zd1211rw...
Loading rtl8180...
Loading rtl8187...
Loading p54pci...
Loading p54usb...
Loading iwl3945...
Loading iwl4965...
WARNING: Error inserting iwlwifi_mac80211 (/lib/modules/2.6.24-19-generic/ubuntu/wireless/iwlwifi/mac80211/compatible/net/mac80211/iwlwifi_mac80211.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting iwl4965 (/lib/modules/2.6.24-19-generic/ubuntu/wireless/iwlwifi/iwlwifi/compatible/iwl4965.ko): Unknown symbol in module, or unknown parameter (see dmesg)
Loading rtl8180...
Loading rtl8187...
Loading rtl8180...
Loading rtl8187...
Loading rt2400pci...
Loading rt2500pci...
Loading rt61pci...
Loading rt2500usb...
Loading rt73usb...
Loading rndis_wlan...
Loading at76_usb...
Module ath_pci not detected -- this is fine
ath5k loaded successfully
Disabling bcm43xx ...	[OK]	Module disabled:
/lib/modules/2.6.24-19-generic/kernel/drivers/net/wireless/bcm43xx/bcm43xx.ko
b43 loaded successfully
b43legacy loaded successfully
rasmus@rasmus-DellE6400:~/Desktop/compat-wireless-2.6-old$ 

```

I'm just gonna write again if i can't make this work... any way thanks for all the help!

---

### Post by rasmus91 on 2008-10-03
Brilliant work dude... it recognizes my card now... how do i then manage my wireless connection? like choosing which to connect to, and typing codes for the wireless?

---

### Post by pytheas22 on 2008-10-03
It still seems to be complaining about some things ('WARNING: Error inserting iwlwifi_mac80211...') but if you say your card is now recognized, that's a good sign.

To connect, left-click on the Network Manager icon.  It should look like two computer screens and should be in the top-right corner of your screen, in the taskbar.  When you click on it you should see a list of networks and can choose which one to connect to.  Please let me know if it works.  If you can't see networks, what is the output of:
```

sudo iwlist scan
```

---

### Post by rasmus91 on 2008-10-03
Well well... It does show my network, but it seems that it can't connect to it, it tries for something like 2 minutes. i don't know if you can use that piece of code you gave me, but anyway here it is... 

```
rasmus@rasmus-DellE6400:~$ sudo iwlist scan
[sudo] password for rasmus: 
lo        Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1F:33:B7:A2:5E
                    ESSID:"NETGEAR"
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=87/100  Signal level:-46 dBm  Noise level=-127 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=0000000023604183
                    Extra: Last beacon: 48ms ago

eth0      Interface doesn't support scanning.

```

... this confuses me... -.-

But tell me what to do now, were closer than ever :D

---

### Post by pytheas22 on 2008-10-03
Please try running this command, which should connect you manually:

```
sudo iwconfig wlan0 mode managed channel 1 essid "NETGEAR"
sudo dhclient wlan0
```

If it works, you should be given an IP address.  If it fails the first time, try it once or twice more.  Any luck?  If not, please post the output of the following commands immediately after your attempts to connect:
```

dmesg | tail
lshw -C Network
```

---

### Post by rasmus91 on 2008-10-03
Im not sure about this at all, but this is what it says: ```
rasmus@rasmus-DellE6400:~$ sudo iwconfig wlan0 mode managed channel 1 essid "NETGEAR"
[sudo] password for rasmus: 
rasmus@rasmus-DellE6400:~$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:16:ea:6f:a9:76
Sending on   LPF/wlan0/00:16:ea:6f:a9:76
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

255.255.255.255 is that the IP you were talking about?

but I also tried the other commands:

```
rasmus@rasmus-DellE6400:~$ dmesg | tail
[   55.068906]   domain 1: span 03
[   55.068910]    groups: 03
[   55.068914]    domain 2: span 03
[   55.068918]     groups: 03
[   60.002392] UDF-fs: Partition marked readonly; forcing readonly mount
[   60.037491] UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume 'NWN2', timestamp 2006/10/11 11:38 (1078)
[  104.207360] wlan0: authenticate with AP 00:1f:33:b7:a2:5e
[  104.238651] wlan0: authenticate with AP 00:1f:33:b7:a2:5e
[  104.246642] wlan0: authenticate with AP 00:1f:33:b7:a2:5e
[  104.279725] wlan0: authentication with AP 00:1f:33:b7:a2:5e timed out
rasmus@rasmus-DellE6400:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82567LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:21:70:a6:a4:ab
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000e-ich9m driverversion=0.2.9.5 firmware=1.7-7 ip=192.168.1.4 latency=0 module=e1000e_ich9m multicast=yes
  *-network
       description: Wireless interface
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wmaster0
       version: 00
       serial: 00:16:ea:6f:a9:76
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn

```

Any suggestions? hope you get more out of this than i do...NWN2' could this possibly be the DVD in the tray? (NWN2 is usually short for neverwinter nights 2)   (anyway, thank for your efforts until now... :D)

---

### Post by pytheas22 on 2008-10-03
This is what I was afraid of...you can't get the card to authenticate with your router, but it doesn't give any good feedback as to what's wrong.

One thing to try is to reboot your router, then try to connect.  Almost certainly won't make a difference, but won't hurt.

Second thing is to go to a location where there's a different network that you can connect to, and see if it works there.  There could be some peculiarity about your "NETGEAR" network that's making it not work.

You could also try burning Intrepid beta (get ISO [here]("http://releases.ubuntu.com/releases/kubuntu/8.10/")) to see if that helps.  Your card should be up and working out-of-the-box in Intrepid.

---

### Post by pytheas22 on 2008-10-03
Update: I was trying to help out someone else in [another thread]("http://ubuntuforums.org/showthread.php?p=5903319&posted=1#post5903319") who was issues that appear to be the same as yours.  He or she discovered that there was a regression in the wireless source code since earlier this month (when things worked), which may be the cause of your problem.  Try recompiling the driver by running these steps:

```
wget http://www.orbit-lab.org/kernel/compat-wireless-2.6/2008/09/compat-wireless-old-2008-09-09.tar.bz2
bunzip2 compat-wireless-old-2008-09-09.tar.bz2 
tar xf compat-wireless-old-2008-09-09.tar 
cd compat-wireless-2.6-old
gedit config.mk
```

At this point a file should be open.  Search the file for the line that reads *CONFIG_IWL4965_HT=y* (should be line 76). Immediately below this line, insert a new line containing this:

```
CONFIG_IWL5000=y

```

Then save and close the file, and finish by running these commands:
```

make
sudo make install
sudo make unload
sudo make load
```

Then reboot and try connecting again.  Please let me know if you have any better luck.

---

### Post by rasmus91 on 2008-10-04
Hmm... this is what i get when installing:

```
.o
  CC [M]  /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/libertas/debugfs.o
  CC [M]  /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/libertas/persistcfg.o
  CC [M]  /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/libertas/ethtool.o
  CC [M]  /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/libertas/assoc.o
  CC [M]  /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/libertas/if_cs.o
  CC [M]  /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/libertas/if_sdio.o
  CC [M]  /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/libertas/if_usb.o
  LD [M]  /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/libertas/libertas.o
  LD [M]  /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/libertas/usb8xxx.o
  LD [M]  /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/libertas/libertas_cs.o
  LD [M]  /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/libertas/libertas_sdio.o
  LD      /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/p54/built-in.o
  CC [M]  /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/p54/p54common.o
  CC [M]  /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/p54/p54usb.o
  CC [M]  /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/p54/p54pci.o
  LD      /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/built-in.o
  CC [M]  /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2x00dev.o
  CC [M]  /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2x00mac.o
/home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2x00mac.c: In function ‘rt2x00mac_conf_tx’:
/home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2x00mac.c:557: warning: comparison is always true due to limited range of data type
  CC [M]  /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2x00config.o
  CC [M]  /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2x00queue.o
  CC [M]  /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2x00rfkill.o
/home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2x00rfkill.c:64: warning: ‘rt2x00rfkill_get_state’ defined but not used
  CC [M]  /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2x00firmware.o
  LD [M]  /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2x00lib.o
  CC [M]  /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2x00pci.o
  CC [M]  /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2x00usb.o
  CC [M]  /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2400pci.o
  CC [M]  /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2500pci.o
  CC [M]  /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt61pci.o
  CC [M]  /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2500usb.o
  CC [M]  /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt73usb.o
  LD      /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/zd1211rw/built-in.o
  CC [M]  /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/zd1211rw/zd_chip.o
  CC [M]  /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/zd1211rw/zd_ieee80211.o
  CC [M]  /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/zd1211rw/zd_mac.o
  CC [M]  /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/zd1211rw/zd_rf_al2230.o
  CC [M]  /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/zd1211rw/zd_rf_rf2959.o
  CC [M]  /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/zd1211rw/zd_rf_al7230b.o
  CC [M]  /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/zd1211rw/zd_rf_uw2453.o
  CC [M]  /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/zd1211rw/zd_rf.o
  CC [M]  /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/zd1211rw/zd_usb.o
  LD [M]  /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/zd1211rw/zd1211rw.o
  LD      /home/rasmus/compat-wireless-2.6-old/drivers/ssb/built-in.o
  CC [M]  /home/rasmus/compat-wireless-2.6-old/drivers/ssb/main.o
  CC [M]  /home/rasmus/compat-wireless-2.6-old/drivers/ssb/scan.o
  CC [M]  /home/rasmus/compat-wireless-2.6-old/drivers/ssb/sprom.o
  CC [M]  /home/rasmus/compat-wireless-2.6-old/drivers/ssb/pci.o
  CC [M]  /home/rasmus/compat-wireless-2.6-old/drivers/ssb/pcihost_wrapper.o
  CC [M]  /home/rasmus/compat-wireless-2.6-old/drivers/ssb/pcmcia.o
  CC [M]  /home/rasmus/compat-wireless-2.6-old/drivers/ssb/driver_chipcommon.o
  CC [M]  /home/rasmus/compat-wireless-2.6-old/drivers/ssb/driver_pcicore.o
  CC [M]  /home/rasmus/compat-wireless-2.6-old/drivers/ssb/b43_pci_bridge.o
  LD [M]  /home/rasmus/compat-wireless-2.6-old/drivers/ssb/ssb.o
  LD      /home/rasmus/compat-wireless-2.6-old/net/ieee80211/built-in.o
  CC [M]  /home/rasmus/compat-wireless-2.6-old/net/ieee80211/ieee80211_module.o
  CC [M]  /home/rasmus/compat-wireless-2.6-old/net/ieee80211/ieee80211_tx.o
  CC [M]  /home/rasmus/compat-wireless-2.6-old/net/ieee80211/ieee80211_rx.o
  CC [M]  /home/rasmus/compat-wireless-2.6-old/net/ieee80211/ieee80211_wx.o
  CC [M]  /home/rasmus/compat-wireless-2.6-old/net/ieee80211/ieee80211_geo.o
  LD [M]  /home/rasmus/compat-wireless-2.6-old/net/ieee80211/ieee80211.o
  CC [M]  /home/rasmus/compat-wireless-2.6-old/net/ieee80211/ieee80211_crypt.o
  CC [M]  /home/rasmus/compat-wireless-2.6-old/net/ieee80211/ieee80211_crypt_wep.o
  CC [M]  /home/rasmus/compat-wireless-2.6-old/net/ieee80211/ieee80211_crypt_ccmp.o
  CC [M]  /home/rasmus/compat-wireless-2.6-old/net/ieee80211/ieee80211_crypt_tkip.o
  LD      /home/rasmus/compat-wireless-2.6-old/net/mac80211/built-in.o
  CC [M]  /home/rasmus/compat-wireless-2.6-old/net/mac80211/main.o
  CC [M]  /home/rasmus/compat-wireless-2.6-old/net/mac80211/wext.o
  CC [M]  /home/rasmus/compat-wireless-2.6-old/net/mac80211/sta_info.o
  CC [M]  /home/rasmus/compat-wireless-2.6-old/net/mac80211/wep.o
  CC [M]  /home/rasmus/compat-wireless-2.6-old/net/mac80211/wpa.o
  CC [M]  /home/rasmus/compat-wireless-2.6-old/net/mac80211/mlme.o
  CC [M]  /home/rasmus/compat-wireless-2.6-old/net/mac80211/iface.o
  CC [M]  /home/rasmus/compat-wireless-2.6-old/net/mac80211/rate.o
  CC [M]  /home/rasmus/compat-wireless-2.6-old/net/mac80211/michael.o
  CC [M]  /home/rasmus/compat-wireless-2.6-old/net/mac80211/tkip.o
  CC [M]  /home/rasmus/compat-wireless-2.6-old/net/mac80211/aes_ccm.o
  CC [M]  /home/rasmus/compat-wireless-2.6-old/net/mac80211/cfg.o
  CC [M]  /home/rasmus/compat-wireless-2.6-old/net/mac80211/rx.o
  CC [M]  /home/rasmus/compat-wireless-2.6-old/net/mac80211/tx.o
  CC [M]  /home/rasmus/compat-wireless-2.6-old/net/mac80211/key.o
  CC [M]  /home/rasmus/compat-wireless-2.6-old/net/mac80211/util.o
  CC [M]  /home/rasmus/compat-wireless-2.6-old/net/mac80211/event.o
  CC [M]  /home/rasmus/compat-wireless-2.6-old/net/mac80211/led.o
  CC [M]  /home/rasmus/compat-wireless-2.6-old/net/mac80211/debugfs.o
  CC [M]  /home/rasmus/compat-wireless-2.6-old/net/mac80211/debugfs_sta.o
  CC [M]  /home/rasmus/compat-wireless-2.6-old/net/mac80211/debugfs_netdev.o
  CC [M]  /home/rasmus/compat-wireless-2.6-old/net/mac80211/debugfs_key.o
  CC [M]  /home/rasmus/compat-wireless-2.6-old/net/mac80211/mesh.o
  CC [M]  /home/rasmus/compat-wireless-2.6-old/net/mac80211/mesh_pathtbl.o
  CC [M]  /home/rasmus/compat-wireless-2.6-old/net/mac80211/mesh_plink.o
  CC [M]  /home/rasmus/compat-wireless-2.6-old/net/mac80211/mesh_hwmp.o
  CC [M]  /home/rasmus/compat-wireless-2.6-old/net/mac80211/rc80211_pid_algo.o
  CC [M]  /home/rasmus/compat-wireless-2.6-old/net/mac80211/rc80211_pid_debugfs.o
  LD [M]  /home/rasmus/compat-wireless-2.6-old/net/mac80211/mac80211.o
  LD      /home/rasmus/compat-wireless-2.6-old/net/wireless/built-in.o
  CC [M]  /home/rasmus/compat-wireless-2.6-old/net/wireless/core.o
  CC [M]  /home/rasmus/compat-wireless-2.6-old/net/wireless/sysfs.o
  CC [M]  /home/rasmus/compat-wireless-2.6-old/net/wireless/radiotap.o
  CC [M]  /home/rasmus/compat-wireless-2.6-old/net/wireless/util.o
  CC [M]  /home/rasmus/compat-wireless-2.6-old/net/wireless/reg.o
  CC [M]  /home/rasmus/compat-wireless-2.6-old/net/wireless/compat.o
  CC [M]  /home/rasmus/compat-wireless-2.6-old/net/wireless/nl80211.o
  LD [M]  /home/rasmus/compat-wireless-2.6-old/net/wireless/cfg80211.o
  LD      /home/rasmus/compat-wireless-2.6-old/built-in.o
  Building modules, stage 2.
  MODPOST 44 modules
  CC      /home/rasmus/compat-wireless-2.6-old/drivers/misc/eeprom_93cx6.mod.o
  LD [M]  /home/rasmus/compat-wireless-2.6-old/drivers/misc/eeprom_93cx6.ko
  CC      /home/rasmus/compat-wireless-2.6-old/drivers/net/b44.mod.o
  LD [M]  /home/rasmus/compat-wireless-2.6-old/drivers/net/b44.ko
  CC      /home/rasmus/compat-wireless-2.6-old/drivers/net/usb/cdc_ether.mod.o
  LD [M]  /home/rasmus/compat-wireless-2.6-old/drivers/net/usb/cdc_ether.ko
  CC      /home/rasmus/compat-wireless-2.6-old/drivers/net/usb/rndis_host.mod.o
  LD [M]  /home/rasmus/compat-wireless-2.6-old/drivers/net/usb/rndis_host.ko
  CC      /home/rasmus/compat-wireless-2.6-old/drivers/net/usb/usbnet.mod.o
  LD [M]  /home/rasmus/compat-wireless-2.6-old/drivers/net/usb/usbnet.ko
  CC      /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/adm8211.mod.o
  LD [M]  /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/adm8211.ko
  CC      /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/at76_usb.mod.o
  LD [M]  /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/at76_usb.ko
  CC      /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/ath5k/ath5k.mod.o
  LD [M]  /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/ath5k/ath5k.ko
  CC      /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/ath9k/ath9k.mod.o
  LD [M]  /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/ath9k/ath9k.ko
  CC      /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/b43/b43.mod.o
  LD [M]  /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/b43/b43.ko
  CC      /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/b43legacy/b43legacy.mod.o
  LD [M]  /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/b43legacy/b43legacy.ko
  CC      /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/ipw2100.mod.o
  LD [M]  /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/ipw2100.ko
  CC      /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/ipw2200.mod.o
  LD [M]  /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/ipw2200.ko
  CC      /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwl3945.mod.o
  LD [M]  /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwl3945.ko
  CC      /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwl4965.mod.o
  LD [M]  /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwl4965.ko
  CC      /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwlcore.mod.o
  LD [M]  /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwlcore.ko
  CC      /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/libertas/libertas.mod.o
  LD [M]  /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/libertas/libertas.ko
  CC      /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/libertas/libertas_cs.mod.o
  LD [M]  /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/libertas/libertas_cs.ko
  CC      /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/libertas/libertas_sdio.mod.o
  LD [M]  /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/libertas/libertas_sdio.ko
  CC      /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/libertas/usb8xxx.mod.o
  LD [M]  /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/libertas/usb8xxx.ko
  CC      /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/mac80211_hwsim.mod.o
  LD [M]  /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/mac80211_hwsim.ko
  CC      /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/p54/p54common.mod.o
  LD [M]  /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/p54/p54common.ko
  CC      /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/p54/p54pci.mod.o
  LD [M]  /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/p54/p54pci.ko
  CC      /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/p54/p54usb.mod.o
  LD [M]  /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/p54/p54usb.ko
  CC      /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/rndis_wlan.mod.o
  LD [M]  /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/rndis_wlan.ko
  CC      /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2400pci.mod.o
  LD [M]  /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2400pci.ko
  CC      /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2500pci.mod.o
  LD [M]  /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2500pci.ko
  CC      /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2500usb.mod.o
  LD [M]  /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2500usb.ko
  CC      /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2x00lib.mod.o
  LD [M]  /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2x00lib.ko
  CC      /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2x00pci.mod.o
  LD [M]  /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2x00pci.ko
  CC      /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2x00usb.mod.o
  LD [M]  /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2x00usb.ko
  CC      /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt61pci.mod.o
  LD [M]  /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt61pci.ko
  CC      /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt73usb.mod.o
  LD [M]  /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt73usb.ko
  CC      /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/rtl8180.mod.o
  LD [M]  /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/rtl8180.ko
  CC      /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/rtl8187.mod.o
  LD [M]  /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/rtl8187.ko
  CC      /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/zd1211rw/zd1211rw.mod.o
  LD [M]  /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/zd1211rw/zd1211rw.ko
  CC      /home/rasmus/compat-wireless-2.6-old/drivers/ssb/ssb.mod.o
  LD [M]  /home/rasmus/compat-wireless-2.6-old/drivers/ssb/ssb.ko
  CC      /home/rasmus/compat-wireless-2.6-old/net/ieee80211/ieee80211.mod.o
  LD [M]  /home/rasmus/compat-wireless-2.6-old/net/ieee80211/ieee80211.ko
  CC      /home/rasmus/compat-wireless-2.6-old/net/ieee80211/ieee80211_crypt.mod.o
  LD [M]  /home/rasmus/compat-wireless-2.6-old/net/ieee80211/ieee80211_crypt.ko
  CC      /home/rasmus/compat-wireless-2.6-old/net/ieee80211/ieee80211_crypt_ccmp.mod.o
  LD [M]  /home/rasmus/compat-wireless-2.6-old/net/ieee80211/ieee80211_crypt_ccmp.ko
  CC      /home/rasmus/compat-wireless-2.6-old/net/ieee80211/ieee80211_crypt_tkip.mod.o
  LD [M]  /home/rasmus/compat-wireless-2.6-old/net/ieee80211/ieee80211_crypt_tkip.ko
  CC      /home/rasmus/compat-wireless-2.6-old/net/ieee80211/ieee80211_crypt_wep.mod.o
  LD [M]  /home/rasmus/compat-wireless-2.6-old/net/ieee80211/ieee80211_crypt_wep.ko
  CC      /home/rasmus/compat-wireless-2.6-old/net/mac80211/mac80211.mod.o
  LD [M]  /home/rasmus/compat-wireless-2.6-old/net/mac80211/mac80211.ko
  CC      /home/rasmus/compat-wireless-2.6-old/net/wireless/cfg80211.mod.o
  LD [M]  /home/rasmus/compat-wireless-2.6-old/net/wireless/cfg80211.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
rasmus@rasmus-DellE6400:~/compat-wireless-2.6-old$ sudo make install
[sudo] password for rasmus: 
Module ath5k not detected -- this is fine
Enabling ath_pci ...	[OK]	Module enabled: 
/lib/modules/2.6.24-19-generic/madwifi/ath_pci.ko
Disabling b43 ...	[OK]	Module disabled:
/lib/modules/2.6.24-19-generic/kernel/drivers/net/wireless/b43/b43.ko
Disabling b43legacy ...	[OK]	Module disabled:
/lib/modules/2.6.24-19-generic/kernel/drivers/net/wireless/b43legacy/b43legacy.ko
Enabling bcm43xx ...	[OK]	Module enabled: 
/lib/modules/2.6.24-19-generic/kernel/drivers/net/wireless/bcm43xx/bcm43xx.ko

Your old wireless subsystem modules were left intact:

/lib/modules/2.6.24-19-generic/kernel/net/mac80211/mac80211.ko
/lib/modules/2.6.24-19-generic/kernel/net/wireless/cfg80211.ko
/lib/modules/2.6.24-19-generic/kernel/drivers/net/wireless/adm8211.ko
/lib/modules/2.6.24-19-generic/ubuntu/wireless/at76/at76_usb.ko
/lib/modules/2.6.24-19-generic/kernel/drivers/ssb/ssb.ko
/lib/modules/2.6.24-19-generic/ubuntu/wireless/iwlwifi/iwlwifi/compatible/iwl3945.ko
/lib/modules/2.6.24-19-generic/ubuntu/wireless/iwlwifi/iwlwifi/compatible/iwl4965.ko
/lib/modules/2.6.24-19-generic/kernel/drivers/net/wireless/ipw2100.ko
/lib/modules/2.6.24-19-generic/kernel/drivers/net/wireless/ipw2200.ko
/lib/modules/2.6.24-19-generic/kernel/net/ieee80211/ieee80211.ko
/lib/modules/2.6.24-19-generic/kernel/net/ieee80211/ieee80211_crypt.ko
/lib/modules/2.6.24-19-generic/kernel/drivers/net/wireless/libertas/libertas_cs.ko
/lib/modules/2.6.24-19-generic/kernel/net/mac80211/mac80211.ko
/lib/modules/2.6.24-19-generic/kernel/drivers/net/wireless/p54pci.ko
/lib/modules/2.6.24-19-generic/kernel/drivers/net/wireless/p54usb.ko
/lib/modules/2.6.24-19-generic/kernel/drivers/net/wireless/rt2x00/rt2400pci.ko
/lib/modules/2.6.24-19-generic/kernel/drivers/net/wireless/rt2x00/rt2500pci.ko
/lib/modules/2.6.24-19-generic/kernel/drivers/net/wireless/rt2x00/rt2500usb.ko
/lib/modules/2.6.24-19-generic/kernel/drivers/net/wireless/rt2x00/rt61pci.ko
/lib/modules/2.6.24-19-generic/kernel/drivers/net/wireless/rt2x00/rt73usb.ko
/lib/modules/2.6.24-19-generic/kernel/drivers/net/usb/usbnet.ko
/lib/modules/2.6.24-19-generic/kernel/drivers/net/usb/cdc_ether.ko
/lib/modules/2.6.24-19-generic/kernel/drivers/net/usb/rndis_host.ko
/lib/modules/2.6.24-19-generic/kernel/drivers/net/wireless/rtl8187.ko
/lib/modules/2.6.24-19-generic/kernel/drivers/net/wireless/zd1211rw/zd1211rw.ko
/lib/modules/2.6.24-19-generic/kernel/net/ieee80211/softmac/ieee80211softmac.ko

make -C /lib/modules/2.6.24-19-generic/build M=/home/rasmus/compat-wireless-2.6-old modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
/home/rasmus/compat-wireless-2.6-old/config.mk:54: "WARNING: You are running a kernel >= 2.6.23, you should enable in it CONFIG_NETDEVICES_MULTIQUEUE for 802.11[ne] support"
  Building modules, stage 2.
  MODPOST 44 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make -C /lib/modules/2.6.24-19-generic/build M=/home/rasmus/compat-wireless-2.6-old "INSTALL_MOD_DIR=updates"  \
		modules_install
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  INSTALL /home/rasmus/compat-wireless-2.6-old/drivers/misc/eeprom_93cx6.ko
  INSTALL /home/rasmus/compat-wireless-2.6-old/drivers/net/b44.ko
  INSTALL /home/rasmus/compat-wireless-2.6-old/drivers/net/usb/cdc_ether.ko
  INSTALL /home/rasmus/compat-wireless-2.6-old/drivers/net/usb/rndis_host.ko
  INSTALL /home/rasmus/compat-wireless-2.6-old/drivers/net/usb/usbnet.ko
  INSTALL /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/adm8211.ko
  INSTALL /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/at76_usb.ko
  INSTALL /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/ath5k/ath5k.ko
  INSTALL /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/ath9k/ath9k.ko
  INSTALL /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/b43/b43.ko
  INSTALL /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/b43legacy/b43legacy.ko
  INSTALL /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/ipw2100.ko
  INSTALL /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/ipw2200.ko
  INSTALL /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwl3945.ko
  INSTALL /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwl4965.ko
  INSTALL /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwlcore.ko
  INSTALL /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/libertas/libertas.ko
  INSTALL /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/libertas/libertas_cs.ko
  INSTALL /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/libertas/libertas_sdio.ko
  INSTALL /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/libertas/usb8xxx.ko
  INSTALL /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/mac80211_hwsim.ko
  INSTALL /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/p54/p54common.ko
  INSTALL /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/p54/p54pci.ko
  INSTALL /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/p54/p54usb.ko
  INSTALL /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/rndis_wlan.ko
  INSTALL /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2400pci.ko
  INSTALL /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2500pci.ko
  INSTALL /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2500usb.ko
  INSTALL /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2x00lib.ko
  INSTALL /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2x00pci.ko
  INSTALL /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2x00usb.ko
  INSTALL /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt61pci.ko
  INSTALL /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt73usb.ko
  INSTALL /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/rtl8180.ko
  INSTALL /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/rtl8187.ko
  INSTALL /home/rasmus/compat-wireless-2.6-old/drivers/net/wireless/zd1211rw/zd1211rw.ko
  INSTALL /home/rasmus/compat-wireless-2.6-old/drivers/ssb/ssb.ko
  INSTALL /home/rasmus/compat-wireless-2.6-old/net/ieee80211/ieee80211.ko
  INSTALL /home/rasmus/compat-wireless-2.6-old/net/ieee80211/ieee80211_crypt.ko
  INSTALL /home/rasmus/compat-wireless-2.6-old/net/ieee80211/ieee80211_crypt_ccmp.ko
  INSTALL /home/rasmus/compat-wireless-2.6-old/net/ieee80211/ieee80211_crypt_tkip.ko
  INSTALL /home/rasmus/compat-wireless-2.6-old/net/ieee80211/ieee80211_crypt_wep.ko
  INSTALL /home/rasmus/compat-wireless-2.6-old/net/mac80211/mac80211.ko
  INSTALL /home/rasmus/compat-wireless-2.6-old/net/wireless/cfg80211.ko
  DEPMOD  2.6.24-19-generic
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'

Note: madwifi detected, we're going to disable it. If you would like to enable it later you can run:
    sudo athenable madwifi

Running athenable ath5k...
Disabling ath_pci ...	[OK]	Module disabled:
/lib/modules/2.6.24-19-generic/madwifi/ath_pci.ko

Currently detected wireless subsystem modules:

/lib/modules/2.6.24-19-generic/updates/net/mac80211/mac80211.ko
/lib/modules/2.6.24-19-generic/updates/net/wireless/cfg80211.ko
/lib/modules/2.6.24-19-generic/updates/drivers/net/wireless/adm8211.ko
/lib/modules/2.6.24-19-generic/updates/drivers/net/wireless/at76_usb.ko
/lib/modules/2.6.24-19-generic/updates/drivers/net/wireless/ath5k/ath5k.ko
/lib/modules/2.6.24-19-generic/updates/drivers/net/wireless/ath9k/ath9k.ko
/lib/modules/2.6.24-19-generic/updates/drivers/net/wireless/b43/b43.ko
/lib/modules/2.6.24-19-generic/updates/drivers/net/wireless/b43legacy/b43legacy.ko
/lib/modules/2.6.24-19-generic/updates/drivers/ssb/ssb.ko
/lib/modules/2.6.24-19-generic/updates/drivers/net/wireless/iwlwifi/iwl3945.ko
/lib/modules/2.6.24-19-generic/updates/drivers/net/wireless/iwlwifi/iwl4965.ko
/lib/modules/2.6.24-19-generic/updates/drivers/net/wireless/ipw2100.ko
/lib/modules/2.6.24-19-generic/updates/drivers/net/wireless/ipw2200.ko
/lib/modules/2.6.24-19-generic/updates/net/ieee80211/ieee80211.ko
/lib/modules/2.6.24-19-generic/updates/net/ieee80211/ieee80211_crypt.ko
/lib/modules/2.6.24-19-generic/updates/drivers/net/wireless/libertas/libertas_cs.ko
/lib/modules/2.6.24-19-generic/updates/drivers/net/wireless/rt2x00/rt2400pci.ko
/lib/modules/2.6.24-19-generic/updates/drivers/net/wireless/rt2x00/rt2500pci.ko
/lib/modules/2.6.24-19-generic/updates/drivers/net/wireless/rt2x00/rt2500usb.ko
/lib/modules/2.6.24-19-generic/updates/drivers/net/wireless/rt2x00/rt61pci.ko
/lib/modules/2.6.24-19-generic/updates/drivers/net/wireless/rt2x00/rt73usb.ko
/lib/modules/2.6.24-19-generic/updates/drivers/net/usb/usbnet.ko
/lib/modules/2.6.24-19-generic/updates/drivers/net/usb/cdc_ether.ko
/lib/modules/2.6.24-19-generic/updates/drivers/net/usb/rndis_host.ko
/lib/modules/2.6.24-19-generic/updates/drivers/net/wireless/rndis_wlan.ko
/lib/modules/2.6.24-19-generic/updates/drivers/net/wireless/rtl8180.ko
/lib/modules/2.6.24-19-generic/updates/drivers/net/wireless/rtl8187.ko
/lib/modules/2.6.24-19-generic/updates/drivers/net/wireless/zd1211rw/zd1211rw.ko

Now run:

make unload

And then load the wireless module you need. If unsure run:

make load

rasmus@rasmus-DellE6400:~/compat-wireless-2.6-old$ sudo make unload
Unloading mac80211...
FATAL: Module mac80211 is in use.
Unloading cfg80211...
FATAL: Module cfg80211 is in use.
make: *** [unload] Error 1
rasmus@rasmus-DellE6400:~/compat-wireless-2.6-old$ sudo make load
Unloading mac80211...
FATAL: Module mac80211 is in use.
Unloading cfg80211...
FATAL: Module cfg80211 is in use.
make: *** [unload] Error 1
rasmus@rasmus-DellE6400:~/compat-wireless-2.6-old$ 

```

i'll try rebooting, and then connecting, tell me if I've done anything wrong...

---

### Post by rasmus91 on 2008-10-04
... NOT GOOD AT ALL!!!! now the wireless lamp ain't glowing any longer :S anyway, i think it has something to do with this: 

```
Now run:

make unload

And then load the wireless module you need. If unsure run:

make load

rasmus@rasmus-DellE6400:~/compat-wireless-2.6-old$ sudo make unload
Unloading mac80211...
FATAL: Module mac80211 is in use.
Unloading cfg80211...
FATAL: Module cfg80211 is in use.
make: *** [unload] Error 1
rasmus@rasmus-DellE6400:~/compat-wireless-2.6-old$ sudo make load
Unloading mac80211...
FATAL: Module mac80211 is in use.
Unloading cfg80211...
FATAL: Module cfg80211 is in use.
make: *** [unload] Error 1
rasmus@rasmus-DellE6400:~/compat-wireless-2.6-old$
```

Don't really now what it means, but i guess fatal ain't good for me... Is it Because i should have switched of the wireless while i maked install?

---

### Post by pytheas22 on 2008-10-04
I read from another user that the wireless light may not actually turn on using the drivers that you compiled, but the card will work...so don't assume that the light being off means that the wireless is not working.

You should first reboot your computer, then see if you can connect to networks.  If not, what is the output of:
```

lshw -C network
sudo iwlist scan
dmesg | grep -e iwl -e wlan
```

---

### Post by rasmus91 on 2008-10-05
... What i see when i click the network icon, under the category wireless networks: (blank)...

But here the output :O

```
rasmus@rasmus-DellE6400:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82567LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:21:70:a6:a4:ab
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000e-ich9m driverversion=0.2.9.5 firmware=1.7-7 ip=192.168.1.4 latency=0 module=e1000e_ich9m multicast=yes
  *-network DISABLED
       description: Wireless interface
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wmaster0
       version: 00
       serial: 00:16:ea:6f:a9:76
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl4965 latency=0 module=iwl4965 multicast=yes wireless=IEEE 802.11abgn
rasmus@rasmus-DellE6400:~$ 

```

AND:

```
rasmus@rasmus-DellE6400:~$ sudo iwlist scan
[sudo] password for rasmus: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

```

And:

```
rasmus@rasmus-DellE6400:~$ dmesg | grep -e iwl -e wlan
[   31.677125] iwl4965: Intel(R) Wireless WiFi Link 4965AGN driver for Linux, 1.3.27k
[   31.677128] iwl4965: Copyright(c) 2003-2008 Intel Corporation
[   31.678033] iwl4965: Detected Intel Wireless WiFi Link 5100AGN REV=0x54
[   31.714472] iwl4965: Tunable channels: 13 802.11bg, 24 802.11a channels
[   31.714899] phy0: Selected rate control algorithm 'iwl-4965-rs'
[   40.213663] iwl4965: START_ALIVE timeout after 4000ms.
[   44.461316] iwl4965: START_ALIVE timeout after 4000ms.
[   52.210466] iwl4965: START_ALIVE timeout after 4000ms.
[   64.965881] iwl4965: START_ALIVE timeout after 4000ms.
[   66.509843] iwl4965: START_ALIVE timeout after 4000ms.
[   82.091729] iwl4965: START_ALIVE timeout after 4000ms.
[   93.056158] iwl4965: START_ALIVE timeout after 4000ms.
[  101.282646] iwl4965: START_ALIVE timeout after 4000ms.
[  114.994729] iwl4965: START_ALIVE timeout after 4000ms.
[  129.174170] iwl4965: START_ALIVE timeout after 4000ms.
[  143.198201] iwl4965: START_ALIVE timeout after 4000ms.
[  157.130796] iwl4965: START_ALIVE timeout after 4000ms.
[  216.683000] iwl4965: START_ALIVE timeout after 4000ms.
rasmus@rasmus-DellE6400:~$ 

```

HUH? (seems to me its just disabled, but if i right click the network icon i can see it should be enabled...)

---

### Post by pytheas22 on 2008-10-05
If you type:
```

sudo rmmod iwl4965
sudo modprobe iwl4965
sudo ifconfig wmaster0 up
sudo ifconfig wlan0 up
sudo iwlist scan
```

does that produce a list of wireless networks around you?

---

### Post by rasmus91 on 2008-10-05
... :S

```
rasmus@rasmus-DellE6400:~$ sudo rmmod iwl4965
[sudo] password for rasmus: 
rasmus@rasmus-DellE6400:~$ sudo modprobe iwl4965
rasmus@rasmus-DellE6400:~$ sudo ifconfig wmaster0 up
SIOCSIFFLAGS: Operation not supported
rasmus@rasmus-DellE6400:~$ sudo ifconfig wlan0 up
SIOCSIFFLAGS: Connection timed out
rasmus@rasmus-DellE6400:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

rasmus@rasmus-DellE6400:~$ 

```

:confused:

---

### Post by pytheas22 on 2008-10-05
Are you using 64-bit Ubuntu?  Because I read [here]("http://www.fedoraforum.org/forum/showthread.php?t=196563") that there seems to be a problem with the iwl firmware that affects 64-bit users.  Unfortunately the only solution mentioned there is to use a more recent kernel, but that would be a lot of work...

Also, your card would probably "just work" if you were running Intrepid.  Have you given that a try?

---

### Post by rasmus91 on 2008-10-05
No, i have no clue on how to do that, wanna give me any instructions?

Also, theres no chance it'll damage my wireless card?

---

### Post by pytheas22 on 2008-10-05
> No, i have no clue on how to do that, wanna give me any instructions?

Do you mean for testing the card in Intrepid, or for installing a more up-to-date kernel (testing Intrepid would be very easy; installing a newer kernel would be more difficult and could potentially break some things, but it should work).

> 
Also, theres no chance it'll damage my wireless card?

By upgrading your kernel or using Intrepid?  No, there's no conceivable way for this to cause physical damage to your wireless card...the worst that could happen is that it won't work.

---

### Post by rasmus91 on 2008-10-05
I was talking about intrepid... lets try it out... one thing though: is it gonna be as fast and functional as the other thing would have been if it worked? (no matter what, tell me what i should do to install intrepid :) )

---

### Post by pytheas22 on 2008-10-05
Intrepid is just the next release of Ubuntu.  It's available now in beta form, which means that it has some bugs that still need to be worked out, and is not recommended for use on production machines.  But at this point it should be relatively stable, and a lot of people are using it.

If you need Ubuntu to be 100% reliable, you probably shouldn't install Intrepid to disk until the official stable release.  But if you have Windows to fall back on (which I think you do) or this is only a secondary computer, you can probably install Intrepid without much risk.  If you install it now, it will automatically be patched to the stable version via Ubuntu updates as the remaining issues with Intrepid are worked out.

You can download the Intrepid ISO from [here]("http://www.ubuntu.com/testing/intrepid/beta").  Burn it to CD, and boot to the CD to see if your wireless works.  From there, you can decide whether to install it to disk or not.

And as far as the wireless driver itself goes: yes, what we've been trying to do here--get you the latest Linux wireless stack--is identical to what Intrepid would do for you with regards to your wireless card.  It will have all of the latest versions of the wireless drivers installed by default, without any manual intervention (like we've been attempting here) required.

---

### Post by rasmus91 on 2008-10-06
HAHA.... i thought it was some sort of program... 

OF COURSE I'll TRY IT OUT... Just can't do it right now, cos im in school, but i'll be ready to do it as soon as i get home, btw, can i just overwrite my old ubuntu partition?

should i get 64 bit version?

Its a intel centrino 2 64 bit processor i have...

---

### Post by pytheas22 on 2008-10-06
Well, the first thing to do is just to try it out to see if your wireless card actually works in Intrepid.  If it does, you can install it to disk by overwriting your existing Ubuntu partition (if you want to save your personal settings, backup your /home folder first and copy it into the new installation).  The 64-bit version should work just as well as 32-bit.

Also, if you want, you can just upgrade your Hardy system to Intrepid by typing 'sudo update-manager -d' and following the instructions on the screen.

I hope things 'just work' in Intrepid!

---

### Post by rasmus91 on 2008-10-06
Did update, but the network manager crashes when i connect to wireless and then unplug, so i'm going to see about if it crashes when i start without cable and then connect... (but the driver works)

However, I'd like to know If my computer should run faster with the 64 bit version on it, or with the 86x??

And just another thing, why are there 2 choices when i boot which are similar to two others?
(found out that if i boot by the option longest down on the list of booting options, my computer won't run the Wifi driver... :( however if i use the top option, it will, and if i just don't connect a cable, it'll work out of the box... :) Ty for advicing me to do install intrepid, its very clear to me its a beta, but nice though.) 


Okay, by now i can say, that the network manager will not crash if i just don't start with the cable in the computer.

how do i change my boot options so that there wont be two similar recovery, and two similar normal booting options?

---

### Post by pytheas22 on 2008-10-06
I'm glad the wireless works in Intrepid--that was the hardest thing to figure out.

The boot options probably reflect different kernels--you have an option for booting into each kernel that you have installed on the system.  So if you have two kernels installed, you will have two similar entries in the boot menu.

You can edit the boot menu by opening up your menu.lst file in a text editor:
```

sudo kate /boot/grub/menu.lst
```

Scroll down, and you will see some sections that look like this:

```
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=b5725877-5158-4c5f-b858-e0f6eededc1e ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

```

Each section corresponds to a different line in your boot menu.  If you want to get rid of a line, erase that section (you should probably back up your /boot/grub/menu.lst file first just in case).

I suspect that the issue with Network Manager not working when the ethernet cable is plugged in will be worked out by the time Intrepid stable is released later this month.

Also, yes 64-bit is a little bit faster than 32-bit (like 6% faster on average or something, but with certain tasks the improvements are more significant).  But the difference is not earth-shattering, and there are some things that don't work as well on 64-bit (especially the Adobe flash plugin in Firefox); also some third-party applications (like Skype) are not compiled for 64-bit (you can still use the 32-bit versions, but you have to hack a lot to get them to work).

---

### Post by numberCruncher91144 on 2008-10-23
> **pytheas22 said:**
> Sorry, I didn't realize that.  Try using these instructions:

1. download [this file]("http://linuxwireless.org/download/compat-wireless-2.6/compat-wireless-old.tar.bz2") and save it to your desktop.  Also remove any directories or other files that are on your desktop from your previous attempts to install this.

2. run:
```

cd ~/Desktop
sudo apt-get install build-essential
wget http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-5000-ucode-5.4.A.11.tar.gz
tar -xzvf iwlwifi*
sudo cp iwlwifi-5000-ucode-5.4.A.11/iwlwifi-5000-1.ucode /lib/firmware
bunzip2 compat-wireless-old.tar.bz2 
tar xf compat-wireless-old.tar
cd compat-wireless-2.6-old
make
sudo make install
sudo make unload
sudo make load
```

You should not need to manually edit any configuration files this time.  Does the build work now?

Also, you may want to try simply switching to Intrepid alpha release.  It should include support for your wireless card out-of-the-box.


I had to download [this]("http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-old.tar.bz2") to my desktop instead of  [this file]("http://linuxwireless.org/download/compat-wireless-2.6/compat-wireless-old.tar.bz2") because the one you mentioned requires you to have git to build auto-conf something or other.  The file I used only requires the build-essential package.

Thanks again for the help!

---

### Post by b0On on 2008-10-27
maybe this isn't completely ontopic, sorry for that.

First of all, I'm a complete Linux-noob.
Second I run vista and ubuntu in dual boot.
After reading this thread i got my 5300-card detected. No problem with the detection, but when i try to connect to a wpa-protected network, network manager keeps asking for the password. I tried this both at work and at home, I know for sure I have the right password for both but still keeps asking for the password. I also tried with wicd, cause I read that should be a better network manager. Wicd stucks at authentication en then just closes.

---

### Post by pytheas22 on 2008-10-27
> maybe this isn't completely ontopic, sorry for that.

First of all, I'm a complete Linux-noob.
Second I run vista and ubuntu in dual boot.
After reading this thread i got my 5300-card detected. No problem with the detection, but when i try to connect to a wpa-protected network, network manager keeps asking for the password. I tried this both at work and at home, I know for sure I have the right password for both but still keeps asking for the password. I also tried with wicd, cause I read that should be a better network manager. Wicd stucks at authentication en then just closes.

The simplest thing for you to do would probably be to install Ubuntu Intrepid, which should support your card out-of-the-box (i.e. no manual driver installation necessary) and will hopefully allow you to connect there.  You can download the Intrepid beta ISO from [here]("http://www.ubuntu.com/testing/intrepid/beta"), or you can upgrade your existing system to Intrepid by typing:
```

sudo upgrade-manager -d
```

and clicking the upgrade button.  Intrepid is still beta now but will officially become stable in a few days.

If you don't want to switch to Intrepid, then the first thing for us to know is whether you can connect to a wireless network with security disabled.  Does that work?

---

### Post by b0On on 2008-10-28
Installed intrepid as you say, and now everything works just fine :)
At least I tried at work now, and there it works. 
Probably works just fine at home too..

---

### Post by Lamp on 2008-10-29
I am having trouble (pretty sure I caused about half of it)... I cannot get the driver (ath9 or the Compat wireless old (i am trying to use ath9)). I'll list what I think may be helpful... ifconfig devices... only the ethernet is functional
[FONT="System"]$ ifconfig |grep Link
eth0      Link encap:Ethernet  HWaddr 00:a0:d1:52:46:6b  
          inet6 addr: fe80::2a0:d1ff:fe52:466b/64 Scope:Link
ham0      Link encap:Ethernet  HWaddr 00:ff:b9:8f:e2:ff  
lo        Link encap:Local Loopback  
wlan0     Link encap:Ethernet  HWaddr 00:18:de:16:f0:4e  
wlan1     Link encap:Ethernet  HWaddr 00:1c:f0:bf:13:f2  
wmaster0  Link encap:UNSPEC  HWaddr 00-18-DE-16-F0-4E-00-00-00-00-00-00-00-00-00-00  
wmaster1  Link encap:UNSPEC  HWaddr 00-1C-F0-BF-13-F2-00-00-00-00-00-00-00-00-00-00  
[/FONT]

this is the "sudo iwlist scan"
[FONT="System"]lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:11:95:57:AC:E7
                    ESSID:"Lamp_Wireless"
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=93/100  Signal level:-36 dBm  Noise level=-127 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=000000f613589162
                    Extra: Last beacon: 1948ms ago
          Cell 02 - Address: 00:12:0E:6A:57:DB
                    ESSID:"Neighbors_wireless"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=43/100  Signal level:-83 dBm  Noise level=-127 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=00000450efd5df45
                    Extra: Last beacon: 1768ms ago
          Cell 03 - Address: 00:0F:B5:5F:D7:52
                    ESSID:"Other_neighbor"
                    Mode:Master
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=62/100  Signal level:-70 dBm  Noise level=-127 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=0000048550476c1b
                    Extra: Last beacon: 1620ms ago

wmaster1  Interface doesn't support scanning.

wlan1     Scan completed :
          Cell 01 - Address: 00:11:95:57:AC:E7
                    ESSID:"Lamp_Wireless"
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=79/100  Signal level:-44 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=000000f613783903
                    Extra: Last beacon: 632ms ago

ham0      Interface doesn't support scanning.

[/FONT]
 I put the ipw3945 into master mode, dont know how to undo that... cant get the dwl652 working at all (the dwl652 is represented by wlan0 and wlan1 I think) I had madwifi working in the past, but without N support, the ath9 should support N...

well, anything you might do to help would be really appreciated.

---

### Post by pytheas22 on 2008-10-29
Lamp: like others, you may have more success by installing Ubuntu 8.10.  The official stable release is tomorrow; check ubuntu.com.  That might be the simplest solution.

If you can't or don't want to install 8.10, I'm still happy to help; please post the output of:
```

lshw -C Network
uname -m
lspci -nn
lsusb
```

Also, you may want to try connecting using [wicd]("http://wicd.sourceforge.net") instead of Network Manager.  Installation instructions are on wicd's site.

Finally, to clear things up: do you have two wireless cards that you're trying to get working--one with an Intel 3945 chipset and the other one with some kind of Atheros chip?  And do you have any idea what the network interface named 'ham0' is?  I've never seen an interface named ham before...

---

### Post by spwn3d on 2008-11-06
Still lack of card detection.

*I have a W500 Thinkpad its got the 5300 AGN card, lspci -nn:

Communication controller [0780]: Intel Corporation Unknown device [8086:2a44] (rev 07)
Ethernet controller [0200]: Intel Coporation Unknown device [8086:10f5] (rev 03)
Network controller [0580]: Intel Corporation Unknown device [8086:4236]

I've completed each step, during the sudo make load each of the files are loaded except iwl4965 which i believe is what i need :(

...
Loading rtl8180...
Loading rtl8187...
Loading p54pci...
Loading p54usb...
Loading iwl3945...
Loading iwl4965...
FATAL: Module iwl4965 not found.
Loading rtl8180...
Loading rtl8187...
...
 
Everything else is successful, in the compat-wireless folder i have the following files so none should be missing:  iwl-4965.c, iwl-tx.c, iwl-4965-hw.h, iwl-dev.h, iwl-commands.h, iwl-eeprom.h.  all coming from \drivers\net\wireless.  Any ideas?

Thanks.

Oh also, the driver is supported by Intel it's supposed to be built into the kernel as I have Kernel 2.6.27.4 here is their note:

*After 2.6.26 the intree driver iwlagn also supports the new 5100BG, 5100ABG, 5100AGN, 5300AGN and 5350AGN series hardwares.

---

### Post by tamias on 2008-11-06
I found that my wireless card (and sound card) drivers had been removed during the upgrade to Intrepid. Installing the linux-generic package solved this for me.

---

### Post by spwn3d on 2008-11-06
> **tamias said:**
> I found that my wireless card (and sound card) drivers had been removed during the upgrade to Intrepid. Installing the linux-generic package solved this for me.

Interesting, any idea what's in the linux-generic package that made it work? I want to try and get the wifi card working on an additional computer - same problem, it has Ubuntu, Vista and Backtrack installed, I was trying to get Backtrack to run them.

---

### Post by pytheas22 on 2008-11-06
spwn3d: iwl4965 has been replaced by iwlagn in Intrepid.  Is your wireless card being claimed by iwlagn?  What is the output of:
```

lshw -C Network
sudo modprobe iwlagn
dmesg | grep -e iwl -e wlan
modinfo iwlagn
```

---

### Post by spwn3d on 2008-11-06
modinfo iwlagn
modinfo: could not find module iwlagn

dmesg | grep -e iwl -e wlan:

iwl3945:  Intel(r) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.25k
iwl3945:  Copyright(c)  2003-2008 Intel Corporation
usbcore:  registered new interface driver rndis_wlan
usbcore:  deregistering interface driver rndis_wlan
iwl3945:  Intel(r) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.25k
iwl3945:  Copyright(c)  2003-2008 Intel Corporation
usbcore:  registered new interface driver rndis_wlan
usbcore:  deregistering interface driver rndis_wlan
iwl3945:  Intel(r) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.25k
iwl3945:  Copyright(c)  2003-2008 Intel Corporation
usbcore:  registered new interface driver rndis_wlan
usbcore:  deregistering interface driver rndis_wlan
iwl3945:  Intel(r) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.25k
iwl3945:  Copyright(c)  2003-2008 Intel Corporation
usbcore:  registered new interface driver rndis_wlan
usbcore:  deregistering interface driver rndis_wlan
iwl3945:  Intel(r) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.25k
iwl3945:  Copyright(c)  2003-2008 Intel Corporation
usbcore:  registered new interface driver rndis_wlan

modinfo iwlagn:
modinfo: could not find module iwlagn     (but this distro isn't ubuntu it's backtrack I just was having the same problem in ubuntu before figured someone here might be able to help me fig. this one out.  I was about to give up since i've exhausted all my knowledge :(

---

### Post by pytheas22 on 2008-11-06
Yes, it appears that neither iwlagn nor iwl4965 exist on your system.  You need one of these drivers (preferably iwlagn) to get your wireless card to work.

I've never really used Backtrack, so I can't help you much there.  On a standard 2.6.27 Linux kernel, iwlagn should be included by default in the compat-wireless stack, I think, but I don't know what Backtrack does; they probably screw around with their wireless drivers a lot and deviate from the stock kernel.  After all, Backtrack is made more for specific tasks (including wireless sniffing and cracking, which in many cases requires hacked-up wireless drivers that aren't included in the default kernel) and is not really a general-purpose desktop distribution.

I am positive that on Ubuntu 8.10 (but not earlier), iwlagn is included by default.  If you use 8.10, your card should work out-of-the-box.

It should also be possible to install iwlagn manually by downloading the [compat-wireless source]("http://linuxwireless.org/download/compat-wireless-2.6/") and compiling it, although again, I'm not sure what things the Backtrack developers do in hacking up their kernels, so I can't guarantee that the standard compat-wireless will compile in Backtrack.  It definitely compiles on Ubuntu 8.04 (using compat-wireless-old) and 8.10 (using just compat-wireless-2.6), however.

So I would recommend that you give Ubuntu 8.10 a shot.  If things don't 'just work' there, you can compile compat-wireless from source.  If you need specific instructions on doing that, let me know.

---

### Post by spwn3d on 2008-11-06
First off, thanks for your insight.

Yes you are correct it does work natively in Ubuntu, I have a tri-boot of vista, backtrack and ubuntu right now.  Backtrack uses an older kernel, which i installed the compat-wireless-old drivers for but that didn't work out to well, instead I ended up updating to the latest linux kernel and manually installing but that one driver errors of course all the rest work, just as my post at the top says:

Communication controller [0780]: Intel Corporation Unknown device [8086:2a44] (rev 07)
Ethernet controller [0200]: Intel Coporation Unknown device [8086:10f5] (rev 03)
Network controller [0580]: Intel Corporation Unknown device [8086:4236]

I've completed each step, during the sudo make load each of the files are loaded except iwl4965 which i believe is what i need

...
Loading rtl8180...
Loading rtl8187...
Loading p54pci...
Loading p54usb...
Loading iwl3945...
Loading iwl4965...
FATAL: Module iwl4965 not found.
Loading rtl8180...
Loading rtl8187...
...
any idea why that one module would fail during the install.  Basically i've already done what you said might work, updating the kernel and manually installing, I thought everything was going to work but that one module failed.  any ideas on a fix for that?  i've also tried a couple patch files each time same outcome.

---

### Post by pytheas22 on 2008-11-07
It's strange that it's not building iwlagn or iwl4965 for you.  Unless the compat-wireless people changed something in their source code since the last time I compiled it (about a month ago), I thought that these modules get built by default.

Did you compile using the instructions from post #30?  Are you sure that you got the compat-wireless source from [http://linuxwireless.org/download/compat-wireless-2.6/](http://linuxwireless.org/download/compat-wireless-2.6/) and not somewhere else?

Also, what is your ultimate goal here in wanting to get this working under Backtrack when you already have it on Ubuntu?  If you're trying to do wireless sniffing/cracking stuff, it may be possible to do that on Ubuntu using the drivers that you already have.  There may be an easier way for you to achieve your objective without having to deal with Backtrack...

---

### Post by spwn3d on 2008-11-07
Yes, it was kinda a test to see if I could update the kernel with any adverse reactions to the other tools as well.  I like BT3, I could use ubuntu and just install each tool but at one point it seemed easier to get the wireless working.  I did compile multiple times from post 30 as well as linuxwireless.org, and i am sure they are the correct ones.  The files are all in there too, it seemed kinda baffling.  I just ended up spending so much time on it and getting so close that i didn't want to give up.  lol i dunnno :(

---

### Post by pytheas22 on 2008-11-07
Did you check the config.mk file in the compat-wireless source to make sure that it says to build iwlagn?  Also, is an iwlagn.ko (and/or iwl4965.ko) module being built in the source directory when you run 'make'?  Maybe it's just an issue of iwlagn.ko not being copied properly when you run 'make install'.

---

### Post by Aarookie on 2008-11-07
try this
Open a terminal and enter these commands:
(this is also assuming like me the target computer has no way of getting to the internet, if you have RJ45 plugged in or some alternate method of connecting to internet you can skip first step.

1. Insert your Ubuntu cd and open terminal
2.sudo apt-cdrom add
3.sudo apt-get install build-essential (Not sure this part is necessary but it sure was for proper tarballing when I was trying to install multiple tar.gz files.
4.sudo apt-get install ndisgtk

5.Open system>administration>Windows wireless drivers menu/program.
6.My computer sort of stuttered at this point but eventually a little window opened up and I was able to browse to my .inf file from winxp driver.
7.For some reason configure network didn't work at this point the unlock button was greyed out, also mouse pointer was skipping a few beats every so often but after a restart I am able to click on my 2 little computers in the gnome task bar and attempt to connect to my network same way I have done on my laptop here. At this point however I was unable to connect to wpa type network, switched router back to wep and hooked right up

---

### Post by BananaJoe on 2009-01-06
Does somebody knows if the WLAN 5300 Chip meanwhile is supported out of the box when i use a current distro (Like Ubuntu 8.10)?

Regards

---

### Post by pytheas22 on 2009-01-06
Yes, Intel 5300 chips should probably work out-of-the-box on Ubuntu 8.10 (but there are different versions of the 5300 card so without seeing your 'lspci -nn' output, it's impossible to verify that your particular version will definitely work).

In Ubuntu 8.04 and earlier you would have to install a driver yourself.

---

### Post by BananaJoe on 2009-01-06
Sound's good, thank you!

---

### Post by Agkelos on 2009-05-12
Sorry for "digging" this thread, but I have some sort of a problem.

I have a laptop with this wireless card, a Intel Corporation PRO/Wireless 5300 AGN, and it works fine out-of-the-box in Ubuntu 8.10. The problem is that sometimes the card doesn't "start". The wireless light in my laptop is off, and no wireless for me :(.
I didn't noticed any pattern for this happening, it looks like a random event.

Is there some kind of answer for this problem? It's kind of annoying.

---

### Post by pytheas22 on 2009-05-13
> Sorry for "digging" this thread, but I have some sort of a problem.

I have a laptop with this wireless card, a Intel Corporation PRO/Wireless 5300 AGN, and it works fine out-of-the-box in Ubuntu 8.10. The problem is that sometimes the card doesn't "start". The wireless light in my laptop is off, and no wireless for me .
I didn't noticed any pattern for this happening, it looks like a random event.

Is there some kind of answer for this problem? It's kind of annoying.

The first thing to check is that the wireless is not turned off via a physical switch.  If you have a button or software key-combination that you press to toggle the wireless on or off, check that.

It's also possible that the module is not being loaded automatically at boot, even though it should be.  Try running this command once:
```

echo iwlagn | sudo tee -a /etc/modules
```

which will tell the system to load the driver explicitly.

If this doesn't help, please post the output of these commands the next time you boot and the card isn't working:
```

lshw -C Network
dmesg | grep -e wlan -e iwl
sudo iwlist scan
```

---

### Post by schoelli on 2009-10-08
Hi
If got a Lenovo W500 with Intel Wifi 5300 included. I installed Ubuntu 9.04 and configurated with wpa_supplicant it like it is described on: [http://wiki.ubuntuusers.de/WLAN/wpa_supplicant ]("http://wiki.ubuntuusers.de/WLAN/wpa_supplicant")

**My wpa_supplicant.conf:**
ctrl_interface=/var/run/wpa_supplicant
eapol_version=1
ap_scan=1

network={
    ssid="XXXX"
    scan_ssid=1
    proto=RSN
    key_mgmt=WPA-PSK
    pairwise=CCMP TKIP
    group=TKIP
    psk=psk string translated by using wps_passphrase "SSID 63 ASCII Chars"
    }

After: **sudo wpa_supplicant -i wlan0 -D wext -c /etc/wpa_supplicant/wpa_supplicant.conf -dd **which seems to run forever without any errors.

I execute: **sudo wpa_supplicant -i wlan0 -D wext -c /etc/wpa_supplicant/wpa_supplicant.conf -B**

No errors.

So i dlike to get an ip using: **sudo dhclient wlan0**
There is already a pid file /var/run/dhclient.pid with pid 4340
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:21:6a:6e:0d:ae
Sending on   LPF/wlan0/00:21:6a:6e:0d:ae
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

[SIZE=4][SIZE=3]Someones got any idea what else i could try to get conected?[/SIZE][U][SIZE=3]

[/SIZE][/U][/SIZE][B][SIZE=4][U]More infos:

[/U][/SIZE]iwlist wlan0 scan[/B]
wlan0     Scan completed :
          Cell 01 - Address: 00:14:C1:19:EB:84
                    ESSID:"XXXX"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=77/100  Signal level:-57 dBm  Noise level=-127 dBm
                    Encryption key:on
                    IE: Unknown: 000A46697368383154726565
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD060010180200F4
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=0000000121a7e52d
                    Extra: Last beacon: 4296ms ago
My Router is an:         U.S. Robotics Wireless *MAX*g ADSL Gateway

**iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"XXXX"
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated
          Tx-Power=15 dBm
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

Do you need any more informations please let me know!
Thank you in advance for any advise!

I already tryed for hours many diffrent configurations!!:(

Regards,
Schoelli

---

### Post by pytheas22 on 2009-10-10
**schoelli**: instead of trying to connect manually from the command line, I'd recommend that you give wicd a try.  You can install wicd by typing:
```

sudo apt-get update
sudo apt-get install wicd
```

Then launch it from the Applications>Internet menu.  Are you able to connect then?

It should not really be necessary to use wpa_supplicant from the command line.

---

### Post by ndmiller on 2009-10-30
I am new to Linux and installed 9.10 on my Latitude 2100 that has an intel 5300 wireless card.  Here is the output of the two commands.  Any help you can offer would be appreciated.

lspci -nn

```
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GME Express Memory Controller Hub [8086:27ac] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GME Express Integrated Graphics Controller [8086:27ae] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 01)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 [8086:27d0] (rev 01)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 [8086:27d2] (rev 01)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 [8086:27d6] (rev 01)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 [8086:27c8] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 [8086:27c9] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 [8086:27ca] (rev 01)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 [8086:27cb] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller [8086:27cc] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e1)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 01)
00:1f.2 SATA controller [0106]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller [8086:27c5] (rev 01)
00:1f.3 SMBus [0c05]: Intel Corporation 82801G (ICH7 Family) SMBus Controller [8086:27da] (rev 01)
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5764M Gigabit Ethernet PCIe [14e4:1684] (rev 10)
0c:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 5300 AGN [Shiloh] Network Connection [8086:4235]
```lshw -C network

```
  *-network DISABLED      
       description: Wireless interface
       product: PRO/Wireless 5300 AGN [Shiloh] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wmaster0
       version: 00
       serial: 00:21:6a:4a:d3:1c
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:28 memory:f6dfe000-f6dfffff
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5764M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 10
       serial: 00:22:19:f8:37:63
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.99 firmware=5764m-v3.35 ip=192.168.1.80 latency=0 multicast=yes
       resources: irq:29 memory:f6cf0000-f6cfffff
```The card is recognized but disabled.  I made sure it was on during the boot process, but don't know how to enable it.

Noah

---

### Post by pytheas22 on 2009-10-31
ndmiller: I suspect you have the radio for your card turned off.  In most cases you can toggle the radio on and off using either a physical switch on your computer, or a hotkey (like Fn+F2).  If you toggle this on a wait a few seconds, do networks appear, or does the "lshw -C Network" command no longer mention your card being "DISABLED"?

If that doesn't help, you should also check your BIOS; sometimes there are also options there for enabling or disabling the wireless card.

If none of the above helps, please post the output of:
```

sudo iwlist scan
dmesg | grep -e iwl -ie radio -e wlan

```

---

### Post by ndmiller on 2009-11-01
> **pytheas22 said:**
> ndmiller: I suspect you have the radio for your card turned off.  In most cases you can toggle the radio on and off using either a physical switch on your computer, or a hotkey (like Fn+F2).  If you toggle this on a wait a few seconds, do networks appear, or does the "lshw -C Network" command no longer mention your card being "DISABLED"?

If that doesn't help, you should also check your BIOS; sometimes there are also options there for enabling or disabling the wireless card.

If none of the above helps, please post the output of:
```

sudo iwlist scan
dmesg | grep -e iwl -ie radio -e wlan

```

I spent so much time reading why the 5300 card didn't work and how to get it running in Ubuntu, I never even thought the laptop wireless was off.  in BIOS the wireless was on and I normally use a MacBook Pro with no option to turn wireless on and off via a switch.  Fn-F6 was the ticket, turned on the 5300 and everything works fine.

Thank you for your help,

Noah

---

### Post by hakop on 2010-01-03
> **pytheas22 said:**
> Sorry, I didn't realize that.  Try using these instructions:

1. download [this file]("http://linuxwireless.org/download/compat-wireless-2.6/compat-wireless-old.tar.bz2") and save it to your desktop.  Also remove any directories or other files that are on your desktop from your previous attempts to install this.

2. run:
```

cd ~/Desktop
sudo apt-get install build-essential
wget http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-5000-ucode-5.4.A.11.tar.gz
tar -xzvf iwlwifi*
sudo cp iwlwifi-5000-ucode-5.4.A.11/iwlwifi-5000-1.ucode /lib/firmware
bunzip2 compat-wireless-old.tar.bz2 
tar xf compat-wireless-old.tar
cd compat-wireless-2.6-old
make
sudo make install
sudo make unload
sudo make load
```You should not need to manually edit any configuration files this time.  Does the build work now?

Also, you may want to try simply switching to Intrepid alpha release.  It should include support for your wireless card out-of-the-box.

Hi Everyone, first of all, i'm nex on ubuntu and i'm sorry for my english because i'm still learning.
I've tried everything said there, everything worked until i did the "make" instruction, here is what's written: 
/home/hakop/Bureau/compat-wireless-2.6-old/config.mk:37: *** "ERROR: You should use another tree/tarball for newer kernels, this one is for kenrels <= 2.6.26". Arrêt.

I don't know how to know what kernel i have and how to download the right version of compat-wireless-2.6-old or something
please help me, i'm trying to activate wi-fi for a month!!!

---

### Post by hakop on 2010-01-03
```
root@hakop-laptop:/home/hakop# dmesg | grep -e iwl -ie radio -e wlan
[   13.949723] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[   13.949726] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[   13.949810] iwlagn 0000:0e:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   13.949839] iwlagn 0000:0e:00.0: setting latency timer to 64
[   13.949893] iwlagn 0000:0e:00.0: Detected Intel Wireless WiFi Link 5300AGN REV=0x24
[   13.987463] iwlagn 0000:0e:00.0: Unsupported (too old) EEPROM VER=0x114 < 0x11a CALIB=0x0 < 0x4
[   13.987479] iwlagn 0000:0e:00.0: PCI INT A disabled
[   14.004990] iwlagn: probe of 0000:0e:00.0 failed with error -22
root@hakop-laptop:/home/hakop# 

```

i think my network device is detected but i can't use it

---

### Post by pytheas22 on 2010-01-03
hakop: if you're using Ubuntu 8.10 (Intrepid) or later, you need to download the compat-wireless-2.6.tar.bz file from [http://linuxwireless.org/download/compat-wireless-2.6/](http://linuxwireless.org/download/compat-wireless-2.6/).  On Ubuntu 8.04 (Hardy) and earlier, you would download the compat-wireless-2.6-**old**.tar.bz file.

With the correct file, "make" should be able to run without problems.

However, in order to know whether installing compat-wireless will help you, it would be helpful to see the output of these commands on your computer:
```

dmesg | grep wlan
uname -rm
cat /etc/issue
lshw -C Network
lsusb
lspci -nn
```

If you give me that information, I will be able provide instructions that will hopefully make your wireless card work.

---

### Post by pytheas22 on 2010-01-03
>  Re: Can not get wireless card to even show up
Code:

root@hakop-laptop:/home/hakop# dmesg | grep -e iwl -ie radio -e wlan
[   13.949723] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[   13.949726] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[   13.949810] iwlagn 0000:0e:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   13.949839] iwlagn 0000:0e:00.0: setting latency timer to 64
[   13.949893] iwlagn 0000:0e:00.0: Detected Intel Wireless WiFi Link 5300AGN REV=0x24
[   13.987463] iwlagn 0000:0e:00.0: Unsupported (too old) EEPROM VER=0x114 < 0x11a CALIB=0x0 < 0x4
[   13.987479] iwlagn 0000:0e:00.0: PCI INT A disabled
[   14.004990] iwlagn: probe of 0000:0e:00.0 failed with error -22
root@hakop-laptop:/home/hakop#

i think my network device is detected but i can't use it

Yes, that's strange; it appears that your wireless device is too old for the iwlagn driver to support.  But if you let me know the output of the commands in my previous post, I should be able to help you find another way to make the wireless card work (probably ndiswrapper).

---

### Post by hakop on 2010-01-04
here are the results of the 4 first commands

```
root@hakop-laptop:/home/hakop/Bureau/compat-wireless-2009-12-11# dmesg | grep wlan
root@hakop-laptop:/home/hakop/Bureau/compat-wireless-2009-12-11# uname -rm
2.6.31-16-generic i686
root@hakop-laptop:/home/hakop/Bureau/compat-wireless-2009-12-11# cat /etc/issue
Ubuntu 9.10 \n \l

root@hakop-laptop:/home/hakop/Bureau/compat-wireless-2009-12-11# lshw -C Network
  *-network UNCLAIMED     
       description: Network controller
       product: PRO/Wireless 5300 AGN [Shiloh] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0e:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:f2200000-f2201fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:14:00.0
       logical name: eth0
       version: 02
       serial: 00:26:22:60:aa:1a
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.4 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:29 ioport:3000(size=256) memory:f2010000-f2010fff(prefetchable) memory:f2000000-f200ffff(prefetchable) memory:f2020000-f202ffff(prefetchable)


```

lsusb :

```
root@hakop-laptop:~# lsusb 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 003: ID 064e:a115 Suyin Corp. 
Bus 002 Device 002: ID 1c7a:0801 LighTuning Technology Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0a5c:2151 Broadcom Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

lspci -nn :

```
root@hakop-laptop:~# lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port [8086:2a41] (rev 07)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)
00:1a.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 [8086:2944] (rev 03)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 [8086:2946] (rev 03)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 [8086:2948] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93)
00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M LPC Interface Controller [8086:2919] (rev 03)
00:1f.2 IDE interface [0101]: Intel Corporation ICH9M/M-E 2 port SATA IDE Controller [8086:2928] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03)
00:1f.5 IDE interface [0101]: Intel Corporation ICH9M/M-E 2 port SATA IDE Controller [8086:292d] (rev 03)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc M96 [Mobility Radeon HD 4650] [1002:9480]
01:00.1 Audio device [0403]: ATI Technologies Inc R700 Audio Device [Radeon HD 4000 Series] [1002:aa38]
02:00.0 System peripheral [0880]: JMicron Technology Corp. SD/MMC Host Controller [197b:2382]
02:00.2 SD Host controller [0805]: JMicron Technology Corp. Standard SD Host Controller [197b:2381]
02:00.3 System peripheral [0880]: JMicron Technology Corp. MS Host Controller [197b:2383]
0e:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 5300 AGN [Shiloh] Network Connection [8086:4235]
14:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 02)

```

i'm really thankfull for your help pytheas22 :)

---

### Post by pytheas22 on 2010-01-04
I think I might have some bad news for you.  I've done some research on this wireless card and it seems it may be bad hardware and there will be no way to make it work without modifying the wireless card physically (which I don't know how to do).  See for example this [bug report]("http://bugzilla.intellinuxwireless.org/show_bug.cgi?id=1997") and [this post]("http://ohioloco.ubuntuforums.org/showpost.php?p=7897732&postcount=90")--both deal with the same situation as yours, where dmesg reports "Unsupported (too old) EEPROM."

Where did you get the wireless card?  Did you purchase it on ebay or from a more legitimate retailer?  Does it work in Windows?

If it works in Windows, there may be hope for us making it work.  But otherwise you may need to purchase a new wireless card.  Let me know.

---

### Post by hakop on 2010-01-04
thank you very much for your answer, and i hope that the problem is not my wireless card, because it works very good in windows. i also hope that something can be done because this is the only rason why i don't use only ubuntu :(
i forgot to say that i have purchased my computer with the intel 5300 agn wireless card on this site : [http://www.notebookguru.de/en/Notebooks/Guru-ICE-config.html](http://www.notebookguru.de/en/Notebooks/Guru-ICE-config.html)

please reassure me, if my wireless card works perfectly in windows, that means the problem is not my wireless card but something in my kernel or something. am i right to think that???

---

### Post by pytheas22 on 2010-01-04
If the card works in Windows, that is reassuring.  It might be possible to make it work in Linux using ndiswrapper rather than the iwlagn driver (as you already tried).

If you could please provide a link to the driver that you have used to make the wireless device work in Windows, I will provide instructions for setting up ndiswrapper (ndiswrapper requires the Windows driver).  Hopefully that will work.

---

### Post by hakop on 2010-01-05
> **pytheas22 said:**
> If the card works in Windows, that is reassuring.  It might be possible to make it work in Linux using ndiswrapper rather than the iwlagn driver (as you already tried).

If you could please provide a link to the driver that you have used to make the wireless device work in Windows, I will provide instructions for setting up ndiswrapper (ndiswrapper requires the Windows driver).  Hopefully that will work.

i have received my drivers with my computer one month ago, so they're on a cd.
but i think that the driver on this link: [http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=18211&ProdId=3062&lang=eng](http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=18211&ProdId=3062&lang=eng)
would make my wireless device work.
but i'll try it now and tell you about it (i'm using the 32 bits version of windows 7)
this one works very well too and for the 64 bits driver that's this link :  [http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&ProdId=3062&DwnldID=18212&lang=eng](http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&ProdId=3062&DwnldID=18212&lang=eng)

---

### Post by pytheas22 on 2010-01-05
Thank you for finding those drivers.  To install them with ndiswrapper, please download the 32-bit driver link and save it to your desktop (please download the .zip file, not the .exe one).  Then run these commands:
```

cd ~/Desktop
sudo apt-get update
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9
unzip ICS_Ds32.zip
sudo ndiswrapper -i Disk/Drivers/s32/NETw5s32.INF 
sudo ndiswrapper -i Disk/Drivers/s32/NETw5v32.INF 
echo ndiswrapper | sudo tee -a /etc/modules
```

Then reboot.  After rebooting, please run these commands to activate ndiswrapper.  Please post the output of all the commands so I can be sure they worked (some commands could have no output):
```

sudo rmmod iwlagn
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
ndiswrapper -l
dmesg | grep -e wlan -e ndis
sudo iwlist scan
```

---

### Post by hakop on 2010-01-05
hi pytheas22, i've followed all your instructions and here is the output of the commands i made:

```
root@hakop-laptop:/home/hakop# rmmod iwlagn
root@hakop-laptop:/home/hakop# rmmod ndiswrapper
root@hakop-laptop:/home/hakop# modprobe ndiswrapper
root@hakop-laptop:/home/hakop# ndiswrapper -l
netw5s32 : driver installed
    device (8086:4235) present (alternate driver: iwlagn)
netw5v32 : driver installed
root@hakop-laptop:/home/hakop# dmesg | grep -e wlan -e ndis
[   13.256950] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   14.012773] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'_aulldvrm'
[   14.012818] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'KeRegisterBugCheckReasonCallback'
[   14.012824] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'KeDeregisterBugCheckReasonCallback'
[   14.012857] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[   14.012869] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[   14.012875] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMResetComplete'
[   14.012881] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[   14.012887] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[   14.012893] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[   14.012909] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterInterruptEx'
[   14.012915] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[   14.012921] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterInterruptEx'
[   14.012932] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateTimerObject'
[   14.012937] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisCancelTimerObject'
[   14.012943] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisSetTimerObject'
[   14.012949] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeTimerObject'
[   14.012955] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetBusData'
[   14.012960] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMGetBusData'
[   14.012966] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[   14.012972] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisGetSystemUpTimeEx'
[   14.012978] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisCopyFromNetBufferToNetBuffer'
[   14.012984] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[   14.012990] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMAllocateNetBufferSGList'
[   14.012996] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMFreeNetBufferSGList'
[   14.013019] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterScatterGatherDma'
[   14.013033] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterScatterGatherDma'
[   14.013039] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[   14.013046] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMNetPnPEvent'
[   14.013052] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMFreePort'
[   14.013059] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMAllocatePort'
[   14.013065] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSynchronizeWithInterruptEx'
[   14.013079] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[   14.013100] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[   14.013107] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[   14.013114] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
[   14.013121] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[   14.013128] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[   14.013135] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[   14.013142] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[   14.013145] ndiswrapper (load_sys_files:206): couldn't prepare driver 'netw5s32'
[   14.017688] ndiswrapper (load_wrap_driver:108): couldn't load driver netw5s32; check system log for messages from 'loadndisdriver'
[   14.021092] usbcore: registered new interface driver ndiswrapper
[  110.763080] usbcore: deregistering interface driver ndiswrapper
[  110.763216] ndiswrapper (ntoskernel_exit:2677): object f3d56a20(2) was not freed, freeing it now
[  130.544042] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[  130.576838] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'_aulldvrm'
[  130.576912] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'KeRegisterBugCheckReasonCallback'
[  130.576921] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'KeDeregisterBugCheckReasonCallback'
[  130.576977] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[  130.576997] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[  130.577027] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMResetComplete'
[  130.577037] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[  130.577046] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[  130.577056] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[  130.577083] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterInterruptEx'
[  130.577094] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[  130.577105] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterInterruptEx'
[  130.577125] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateTimerObject'
[  130.577136] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisCancelTimerObject'
[  130.577147] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisSetTimerObject'
[  130.577157] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeTimerObject'
[  130.577168] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetBusData'
[  130.577179] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMGetBusData'
[  130.577190] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[  130.577201] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisGetSystemUpTimeEx'
[  130.577212] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisCopyFromNetBufferToNetBuffer'
[  130.577223] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[  130.577235] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMAllocateNetBufferSGList'
[  130.577246] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMFreeNetBufferSGList'
[  130.577257] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterScatterGatherDma'
[  130.577269] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterScatterGatherDma'
[  130.577280] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[  130.577291] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMNetPnPEvent'
[  130.577302] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMFreePort'
[  130.577313] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMAllocatePort'
[  130.577324] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSynchronizeWithInterruptEx'
[  130.577345] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[  130.577378] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[  130.577390] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[  130.577401] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
[  130.577412] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[  130.577423] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[  130.577434] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[  130.577445] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[  130.577450] ndiswrapper (load_sys_files:206): couldn't prepare driver 'netw5s32'
[  130.578519] ndiswrapper (load_wrap_driver:108): couldn't load driver netw5s32; check system log for messages from 'loadndisdriver'
[  130.588598] usbcore: registered new interface driver ndiswrapper
root@hakop-laptop:/home/hakop# iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

```

maybe should i install the 64 bits driver? what do you think about it?
Thank you for your help :)

---

### Post by pytheas22 on 2010-01-05
It looks like ndiswrapper won't work with the Windows 7 driver.  The Windows XP one may be better.  To install that, please download the driver file from [here]("http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=18404&ProdId=3062&lang=eng") and save it to your desktop (again, please download the .zip version of the file instead of the .exe).  Then type:
```

sudo ndiswrapper -r netw5v32
sudo ndiswrapper -r netw5s32
cd ~/Desktop
unzip ICS_Dx32.zip
sudo ndiswrapper -i Disk/Drivers/x32/NETw5x32.INF
```

Then reboot, and again, please run the following commands and post all output:
```

sudo rmmod iwlagn
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
ndiswrapper -l
dmesg | grep -e wlan -e ndis
sudo iwlist scan
```

Hopefully this will work.  If not, we may be out of luck :(

---

### Post by hakop on 2010-01-06
> **pytheas22 said:**
> It looks like ndiswrapper won't work with the Windows 7 driver.  The Windows XP one may be better.  To install that, please download the driver file from [here]("http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=18404&ProdId=3062&lang=eng") and save it to your desktop (again, please download the .zip version of the file instead of the .exe).  Then type:
```

sudo ndiswrapper -r netw5v32
sudo ndiswrapper -r netw5s32
cd ~/Desktop
unzip ICS_Dx32.zip
sudo ndiswrapper -i Disk/Drivers/x32/NETw5x32.INF
```Then reboot, and again, please run the following commands and post all output:
```

sudo rmmod iwlagn
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
ndiswrapper -l
dmesg | grep -e wlan -e ndis
sudo iwlist scan
```Hopefully this will work.  If not, we may be out of luck :(


thank you for all your help and advices, but i think you're right, we're out of luck. i've tried with the XP driver, but unfortunately it didn't work neither (the output was the same as the windows 7 driver except for the files names) i don't know if there is something else I can do. I'll try to install the 64 bits driver (my version of ubuntu is 64 bits), it will maybe work with some luck.

but again, thank you very much :) and happy new year.

---

### Post by pytheas22 on 2010-01-06
Yes, if you received the same error messages using ndiswrapper and the Windows XP driver, I don't know what else to do.  Unfortunately the Intel Linux driver developers say they cannot support this type of hardware because it is a "pre-production" device (see [this email]("http://article.gmane.org/gmane.linux.kernel.commits.head/198188") for example).

The 64-bit Windows driver and ndiswrapper should not work on 32-bit Ubuntu; they would only work if you installed 64-bit Ubuntu.  But I guess it wouldn't hurt to try.

Sorry again we couldn't figure this out but thanks for your patience through the process.

---

### Post by anilj on 2010-01-06
hi im new to linux and changed my OS from windows to ubuntu 9.10 netbook remix. i cant connect to the net wirelessly so i uninstalled network manager and installed wicd network manager (which doesnt pick up the router either). now im not even sure if i have a driver for the wireless card which is a RaLink RT2860. can someone help me please as i am totally lost on what to do next.

---

### Post by pytheas22 on 2010-01-06
anilj: please open a terminal from the Applications>Internet menu, run the following commands and post the output here:
```

dmesg | grep -e wlan
lshw -C Network
lspci -nn
lsusb
sudo iwlist scan
```

With that information, I can hopefully help you figure out how to make your wireless connection work.

---

### Post by H3LlIoN on 2010-01-07
I tried this:

> **pytheas22 said:**
> 
First, download [this file]("http://linuxwireless.org/download/compat-wireless-2.6/compat-wireless-old.tar.bz2") and save it to your desktop.  Then run these commands:

```
sudo apt-get install build-essential
wget http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-5000-ucode-5.4.A.11.tar.gz
tar -xzvf iwlwifi*
sudo cp iwlwifi-5000-ucode-5.4.A.11/iwlwifi-5000-1.ucode /lib/firmware
bunzip2 compat-wireless-old
tar xf compat-wireless-old
cd compat-wireless*old*
make
sudo make install
sudo make unload
sudo make load
```

and it made it as far as sudo cp iwlwifi..... and then it wouldn't do anything further, and now network manager appears to be gone, as I can no longer connect via lan, which I could do before.  HELP!!! 

(I'm a noob. kthanks)

---

### Post by anilj on 2010-01-07
dmesg | grep -e wlan: nothing happens

lshw -C Network:

anil@anil-laptop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: Atheros AR8121/AR8113/AR8114 PCI-E Ethernet Controller
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: b0
       serial: 00:22:15:55:f6:00
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI firmware=L1e ip=92.236.189.171 latency=0 multicast=yes
       resources: irq:28 memory:fbfc0000-fbffffff ioport:ec80(size=128)
  *-network DISABLED
       description: Wireless interface
       product: RT2860
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: ra0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2860 latency=0 multicast=yes wireless=RT2860 Wireless
       resources: irq:19 memory:f7ff0000-f7ffffff

lspci -nn:
anil@anil-laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GME Express Memory Controller Hub [8086:27ac] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GME Express Integrated Graphics Controller [8086:27ae] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 [8086:27d2] (rev 02)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 [8086:27d4] (rev 02)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 [8086:27d6] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
00:1f.2 IDE interface [0101]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller [8086:27c4] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801G (ICH7 Family) SMBus Controller [8086:27da] (rev 02)
01:00.0 Network controller [0280]: RaLink RT2860 [1814:0781]
03:00.0 Ethernet controller [0200]: Attansic Technology Corp. Atheros AR8121/AR8113/AR8114 PCI-E Ethernet Controller [1969:1026] (rev b0)

lsusb:
anil@anil-laptop:~$ lsusb
Bus 001 Device 002: ID 04f2:b071 Chicony Electronics Co., Ltd 2.0M UVC WebCam / CNF7129
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

sudo iwlist scan:
anil@anil-laptop:~$ sudo iwlist scan
[sudo] password for anil: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

ra0       Interface doesn't support scanning : Network is down

(thanks for help in advance)

---

### Post by pytheas22 on 2010-01-07
anilj: your wireless interface is detected but is listed as "DISABLED".  Usually this happens because the wireless card is turned off.  On most computers there's either a physical switch or a hotkey (like Fn+F2) that you can use for toggling the wireless on and off.  There may also be an option in BIOS.  Please make sure the wireless is turned on, then try scanning again.

If this doesn't solve the problem, you may also need to open up the Preferences window in wicd and make sure your wireless interface is set to "ra0".  Then try scanning again.

If this still fails, please make sure the wireless radio is on, then please run these commands and let me know the output:

```
dmesg | grep -e rt28 -e ra -ie radio
sudo ifconfig ra0 up
sudo iwlist scan
```

H3LlIoN: chances are that those commands are not going to help you anyway.  That was an old post and unless you're using Ubuntu 8.04 or earlier, the issue that those commands solved is no longer relevant in more more modern versions of Ubuntu.  But if you post the output of these commands, I'll try to help you:
```

dmesg | grep wlan
lspci -nn
lsusb
lshw -C Network
sudo iwlist scan
uname -rm
cat /etc/issue
```

---

### Post by anilj on 2010-01-07
i set the wireless interface to ra0 and can now find wireless network. but wen i try to connect to mine it does not connect even though i hav entered the correct wep key, IP, netmask and gateway. it keeps saying: connection failed, could not contact wireless access point.

---

### Post by pytheas22 on 2010-01-07
anilj: please post the output of these commands (the first command may have no output), and let me know the name of the network you're trying to connect to:
```

sudo ifconfig ra0 up
sudo iwlist scan
```

---

### Post by anilj on 2010-01-08
from  [FONT=monospace][/FONT]sudo ifconfig ra0 up there was no output

sudo iwlist scan:
anil@anil-laptop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

ra0       Scan completed :
          Cell 01 - Address: 00:18:4D:0B:C1:FA
                    ESSID:"SKY92581"
                    Mode:Managed
                    Channel:1
                    Quality:34/100  Signal level:-76 dBm  Noise level:-97 dBm
                    Encryption key:on
                    Bit Rates:18 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: 00:17:3F:E0:62:01
                    ESSID:"Jassi's"
                    Mode:Managed
                    Channel:11
                    Quality:100/100  Signal level:-31 dBm  Noise level:-97 dBm
                    Encryption key:on
                    Bit Rates:36 Mb/s
          Cell 03 - Address: 00:B0:0C:00:36:B0
                    ESSID:"TENDA"
                    Mode:Managed
                    Channel:6
                    Quality:81/100  Signal level:-58 dBm  Noise level:-97 dBm
                    Encryption key:off
                    Bit Rates:11 Mb/s
          Cell 04 - Address: 00:1F:33:B6:31:10
                    ESSID:"Suntino"
                    Mode:Managed
                    Channel:7
                    Quality:15/100  Signal level:-84 dBm  Noise level:-97 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: 00:24:01:A7:3D:EA
                    ESSID:"abui and fety"
                    Mode:Managed
                    Channel:11
                    Quality:20/100  Signal level:-82 dBm  Noise level:-97 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK



i am trying to connect to Jassi's

---

### Post by pytheas22 on 2010-01-09
Thanks for the output and sorry for not getting back to you sooner.  Please try running these commands and see if they get you connected.  These should get you connected manually; if they work, then we will at least know that your wireless driver is not the problem here.  Please have wicd and any other connection managers closed before you run these:
```

sudo ifconfig ra0 down
sudo iwconfig ra0 mode managed channel 11 essid "Jassi's" key '''your-wep-key'''
sudo ifconfig ra0 up
sudo dhclient ra0
```

(Enter your WEP key where indicated, without any spaces or colons between the characters, and without quotes surrounding the key.)

If this works, the final command should give output telling you you've been assigned an IP address, and you should then be able to browse web pages, etc.  If it fails, the last command will say something like "No persistent leases in database--sleeping" and drop back to the command line.

This assumes that you use dynamic IP addresses assigned via dhcp.  If that's not the case, let me know (I know you mentioned earlier trying to set a static IP address in wicd, but I assume you don't need to do that normally).

If this fails as well, we may need to look into using ndiswrapper to get you connected instead of the native Linux driver.

Also, one thing that could possibly be causing issues here is that your network has an apostrophe in its name.  That shouldn't matter, but it might be confusing some piece of software.  If possible, you might want to try changing the network name to something simpler just to see if that allows you to connect (either using wicd or the command line).

---

### Post by anilj on 2010-01-09
from the 2nd command with the essid etc came:

Error for wireless request "Set Mode" (8B06) : 
   SET failed on device ra0 ; Network is down.

After the final command came "No persistent leases in database--sleeping"

---

### Post by pytheas22 on 2010-01-09
**anilj**: that's a strange error.  I'm thinking the version of the driver that you currently have installed is just not going to work, and that you should upgrade to a more recent version.  You can do that by first going to [http://linuxwireless.org/download/compat-wireless-2.6](http://linuxwireless.org/download/compat-wireless-2.6) and downloading the file named "compat-wireless-2.6.tar.bz2." Then run these commands, which will compile and install the latest Linux wireless code for you:
```

sudo apt-get update
sudo apt-get install build-essential
cd ~/Desktop
tar -xjvf compat-wireless-2.6.tar.bz2
cd compat-wireless*
make
sudo make install
```

Then reboot and hopefully the wireless will work.  If it still doesn't, please let me know the output of:
```

dmesg | grep -e rt -e wlan -e ra
lshw -C Network
modinfo rt2860sta
```

I'm sorry this process is turning out to be more difficult than you probably hoped, but thanks for your patience.

---

### Post by anilj on 2010-01-10
it did not work with the first set of commands after the reboot.
so i entered the 2nd set of commands, here is what they gave:

dmesg | grep -e rt -e wlan -e ra:
anil@anil-laptop:~$ dmesg | grep -e rt -e wlan -e ra
[    0.000000] KERNEL supported cpus:
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] MTRR fixed ranges enabled:
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000] Zone PFN ranges:
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 3f800000 (gap: 3f800000:bf600000)
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] virtual kernel memory layout:
[    0.000000] Fast TSC calibration using PIT
[    0.002375] Calibrating delay loop (skipped), value calculated using timer frequency.. 3200.43 BogoMIPS (lpj=6400872)
[    0.002413] Security Framework initialized
[    0.002795] mce: CPU supports 5 MCE banks
[    0.004000] Calibrating delay using timer specific routine.. 3199.91 BogoMIPS (lpj=6399820)
[    0.004000] mce: CPU supports 5 MCE banks
[    0.172332] Booting paravirtualized kernel on bare hardware
[    0.172604] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.172945] PCI: Using configuration type 1 for base access
[    0.190393] ACPI: (supports S0 S1 S3 S4 S5)
[    0.190549] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.201951] PCI: updated MCFG configuration 0: base e0000000 segment 0 buses 0 - 63
[    0.211845] ACPI: EC: driver started in poll mode
[    0.212660] pci 0000:00:02.0: reg 14 io port: [0xdc80-0xdc87]
[    0.212946] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.213058] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.213172] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.213286] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.213399] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.213488] pci 0000:00:1d.0: reg 20 io port: [0xd480-0xd49f]
[    0.213568] pci 0000:00:1d.1: reg 20 io port: [0xd800-0xd81f]
[    0.213647] pci 0000:00:1d.2: reg 20 io port: [0xd880-0xd89f]
[    0.213726] pci 0000:00:1d.3: reg 20 io port: [0xdc00-0xdc1f]
[    0.213884] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.214207] pci 0000:00:1f.2: reg 10 io port: [0x00-0x07]
[    0.214220] pci 0000:00:1f.2: reg 14 io port: [0x00-0x03]
[    0.214232] pci 0000:00:1f.2: reg 18 io port: [0x00-0x07]
[    0.214244] pci 0000:00:1f.2: reg 1c io port: [0x00-0x03]
[    0.214256] pci 0000:00:1f.2: reg 20 io port: [0xffa0-0xffaf]
[    0.214300] pci 0000:00:1f.2: PME# supported from D3hot
[    0.214386] pci 0000:00:1f.3: reg 20 io port: [0x400-0x41f]
[    0.214604] pci 0000:03:00.0: reg 18 io port: [0xec80-0xecff]
[    0.214699] pci 0000:03:00.0: PME# supported from D3hot D3cold
[    0.214802] pci 0000:00:1c.1: bridge io port: [0xe000-0xefff]
[    0.215084] pci 0000:01:00.0: PME# supported from D0 D3hot
[    0.215262] pci 0000:00:1e.0: transparent bridge
[    0.252084] NetLabel:  unlabeled traffic allowed by default
[    0.252176] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.273154] system 00:01: iomem range 0xfed13000-0xfed19fff has been reserved
[    0.273176] system 00:08: ioport range 0x25c-0x25f has been reserved
[    0.273184] system 00:08: ioport range 0x380-0x383 has been reserved
[    0.273191] system 00:08: ioport range 0x400-0x41f has been reserved
[    0.273198] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[    0.273205] system 00:08: ioport range 0x800-0x87f has been reserved
[    0.273212] system 00:08: ioport range 0x480-0x4bf has been reserved
[    0.273220] system 00:08: iomem range 0x8c000000-0x8c01ffff has been reserved
[    0.273247] system 00:08: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.273255] system 00:08: iomem range 0xfed20000-0xfed3ffff has been reserved
[    0.273262] system 00:08: iomem range 0xfed50000-0xfed8ffff has been reserved
[    0.273270] system 00:08: iomem range 0xffb00000-0xffbfffff has been reserved
[    0.273278] system 00:08: iomem range 0xfff00000-0xffffffff could not be reserved
[    0.273293] system 00:0a: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.273301] system 00:0a: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.273313] system 00:0b: iomem range 0xe0000000-0xe3ffffff has been reserved
[    0.273326] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
[    0.273333] system 00:0c: iomem range 0xc0000-0xcffff could not be reserved
[    0.273341] system 00:0c: iomem range 0xe0000-0xfffff could not be reserved
[    0.273348] system 00:0c: iomem range 0x100000-0x3f7fffff could not be reserved
[    0.311705] Trying to unpack rootfs image as initramfs...
[    0.706292] pcieport-driver 0000:00:1c.0: irq 24 for MSI/MSI-X
[    0.706309] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    0.706549] pcieport-driver 0000:00:1c.1: irq 25 for MSI/MSI-X
[    0.706565] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    0.706793] pcieport-driver 0000:00:1c.2: irq 26 for MSI/MSI-X
[    0.706808] pcieport-driver 0000:00:1c.2: setting latency timer to 64
[    0.707047] pcieport-driver 0000:00:1c.3: irq 27 for MSI/MSI-X
[    0.707062] pcieport-driver 0000:00:1c.3: setting latency timer to 64
[    0.724294] ACPI: Processor [CPU0] (supports 8 throttling states)
[    0.726724] ACPI: Processor [CPU1] (supports 8 throttling states)
[    1.106803] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    1.110738] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    1.121074] ehci_hcd 0000:00:1d.7: debug port 1
[    1.121088] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    1.136030] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.136221] usb usb1: configuration #1 chosen from 1 choice
[    1.136312] hub 1-0:1.0: 8 ports detected
[    1.136909] usb usb2: configuration #1 chosen from 1 choice
[    1.136988] hub 2-0:1.0: 2 ports detected
[    1.137393] usb usb3: configuration #1 chosen from 1 choice
[    1.137468] hub 3-0:1.0: 2 ports detected
[    1.137860] usb usb4: configuration #1 chosen from 1 choice
[    1.137936] hub 4-0:1.0: 2 ports detected
[    1.138345] usb usb5: configuration #1 chosen from 1 choice
[    1.138422] hub 5-0:1.0: 2 ports detected
[    1.173900] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.173915] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.174339] rtc_cmos 00:03: RTC can wake from S4
[    1.174411] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.174457] rtc0: alarms up to one month, 114 bytes nvram, hpet irqs
[    1.181450] Using IPI No-Shortcut mode
[    1.181994] rtc_cmos 00:03: setting system clock to 2010-01-10 14:48:19 UTC (1263134899)
[    1.204076] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    1.313359] sd 1:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[    1.315868] sd 1:0:1:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[    1.609412] Linux agpgart interface v0.103
[    1.621072] agpgart-intel 0000:00:00.0: Intel 945GME Chipset
[    1.621408] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
[    1.624590] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    1.670138] usb 1-8: configuration #1 chosen from 1 choice
[    2.167541] [drm] fb0: inteldrmfb frame buffer device
[    2.963023] Console: switching to colour frame buffer device 128x37
[    3.497709] PM: Starting manual resume from disk
[    3.497719] PM: Resume from partition 8:5
[    3.511215] kjournald2 starting: pid 385, dev sda1:8, commit interval 5 seconds
[    3.790363] type=1505 audit(1263134902.106:2): operation="profile_load" pid=408 name=/sbin/dhclient3
[    3.790943] type=1505 audit(1263134902.106:3): operation="profile_load" pid=408 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    3.791270] type=1505 audit(1263134902.106:4): operation="profile_load" pid=408 name=/usr/lib/connman/scripts/dhclient-script
[    3.837880] type=1505 audit(1263134902.154:5): operation="profile_load" pid=409 name=/usr/bin/evince
[    3.847303] type=1505 audit(1263134902.162:6): operation="profile_load" pid=409 name=/usr/bin/evince-previewer
[    3.853088] type=1505 audit(1263134902.170:7): operation="profile_load" pid=409 name=/usr/bin/evince-thumbnailer
[    3.866947] type=1505 audit(1263134902.182:8): operation="profile_load" pid=411 name=/usr/lib/cups/backend/cups-pdf
[    3.867676] type=1505 audit(1263134902.182:9): operation="profile_load" pid=411 name=/usr/sbin/cupsd
[    9.260438] udev: starting version 147
[    9.379566] eeepc_laptop: TYPE (2000000) not reported by BIOS, enabling anyway
[    9.399239] eeepc_laptop: PANELPOWER (4000000) not reported by BIOS, enabling anyway
[    9.399255] eeepc_laptop: Get control methods supported: 0x6101713
[    9.399391] input: Asus EeePC extra buttons as /devices/virtual/input/input7
[    9.654179] rt2860sta: module is from the staging directory, the quality is unknown, you have been warned.
[    9.751224] rt2860 0000:01:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    9.751908] rt2860 0000:01:00.0: setting latency timer to 64
[   10.636094] __ratelimit: 3 callbacks suppressed
[   10.636104] type=1505 audit(1263134908.950:11): operation="profile_replace" pid=860 name=/sbin/dhclient3
[   10.636938] type=1505 audit(1263134908.954:12): operation="profile_replace" pid=860 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   10.637562] type=1505 audit(1263134908.954:13): operation="profile_replace" pid=860 name=/usr/lib/connman/scripts/dhclient-script
[   10.653057] type=1505 audit(1263134908.970:14): operation="profile_replace" pid=861 name=/usr/bin/evince
[   10.695299] type=1505 audit(1263134909.010:15): operation="profile_replace" pid=861 name=/usr/bin/evince-previewer
[   10.703730] type=1505 audit(1263134909.018:16): operation="profile_replace" pid=861 name=/usr/bin/evince-thumbnailer
[   10.722898] type=1505 audit(1263134909.038:17): operation="profile_replace" pid=879 name=/usr/lib/cups/backend/cups-pdf
[   10.723969] type=1505 audit(1263134909.038:18): operation="profile_replace" pid=879 name=/usr/sbin/cupsd
[   10.730638] type=1505 audit(1263134909.046:19): operation="profile_replace" pid=880 name=/usr/sbin/tcpdump
[   13.072856] ppdev: user-space parallel port driver
[   14.226431] RTMPSetPhyMode: channel is out of range, use first channel=1 
[   16.384553] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 630
[   23.041527] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 630
[   24.957041] ra0: no IPv6 routers present
[   25.121237] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 630
[   29.040156] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 713
[   30.376220] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=11)
[   40.196129] ra0: no IPv6 routers present
[   45.368465] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 594
[   45.368853] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=11)
[   53.637860] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 673
[   54.437776] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=11)
[   59.521901] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 554
[   59.522368] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=11)
[   67.681985] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 828
[   68.036156] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=11)
[   73.120887] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 828
[   73.121440] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=11)
[   85.056547] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 673
[   89.726707] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=6)
[   99.749178] ra0: no IPv6 routers present


lshw -C Network:
anil@anil-laptop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: Atheros AR8121/AR8113/AR8114 PCI-E Ethernet Controller
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: b0
       serial: 00:22:15:55:f6:00
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI firmware=L1e latency=0 multicast=yes
       resources: irq:28 memory:fbfc0000-fbffffff ioport:ec80(size=128)
  *-network
       description: Wireless interface
       product: RT2860
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: ra0
       version: 00
       serial: 00:15:af:e5:44:98
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2860 latency=0 multicast=yes wireless=RT2860 Wireless
       resources: irq:19 memory:f7ff0000-f7ffffff


modinfo rt2860sta:
anil@anil-laptop:~$ modinfo rt2860sta
filename:       /lib/modules/2.6.31-17-generic/kernel/drivers/staging/rt2860/rt2860sta.ko
version:        1.8.1.1
license:        GPL
srcversion:     2DB10B2D13BA8040F82A25A
alias:          pci:v00001A3Bd00001059sv*sd*bc*sc*i*
alias:          pci:v00001814d00000781sv*sd*bc*sc*i*
alias:          pci:v00001814d00000701sv*sd*bc*sc*i*
alias:          pci:v00001814d00000681sv*sd*bc*sc*i*
alias:          pci:v00001814d00000601sv*sd*bc*sc*i*
depends:        
staging:        Y
vermagic:       2.6.31-17-generic SMP mod_unload modversions 586 
parm:           mac:rt28xx: wireless mac addr (charp)

---

### Post by pytheas22 on 2010-01-10
It looks like the new driver was built and installed successfully, so that's at least good news.  I'm wondering if NetworkManager may work better for you at this point than wicd--I read a thread yesterday while researching your issue that said that NM works with the updated driver.  To reinstall NM, type:
```

sudo apt-get install network-manager-gnome
```

Then left-click on the NetworkManager applet and you should see a list of networks.  Does this connect you?

If NM still fails, I'd be interested in seeing the output of these commands after you attempt to connect:
```

ifconfig
sudo iwlist scan
dmesg | grep -e ra0 -e rt28
```

---

### Post by anilj on 2010-01-10
Network Manager worked like a charm, i'd like to thank you for being patient with me and my problem and finally helping me solve the issue. This forum is much better than the linuxquestions because it has people like yourself who actually help people. thank you once again.

---

### Post by pytheas22 on 2010-01-11
Very glad to hear it's sorted out.  One final word of advice: if you upgrade your kernel via Ubuntu Updates, you will probably need to recompile the driver using the commands from post #107.  You may want to keep a copy of the source code on hand for this.

Hopefully by the time Ubuntu 10.04 is released in April, your wireless card will be working out-of-the-box and you will no longer have to deal with all this.

---

### Post by bhargav@in.com on 2010-02-20
I am running Ubuntu 9.10 on my Dell XPS 16 with core i7 with Intel 5300 wifi card .
On starting ubuntu , wifi works normally but when i physically turn it off and then on , it doesnt work any further .

rfkill list shows the output 
```

bhargav@bhargav-laptop:~$ rfkill list
0: dell-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
1: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: yes
6: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
7: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

```lspci -nn
```

bhargav@bhargav-laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Core Processor DMI [8086:d132] (rev 11)
00:03.0 PCI bridge [0604]: Intel Corporation Core Processor PCI Express Root Port 1 [8086:d138] (rev 11)
00:08.0 System peripheral [0880]: Intel Corporation Core Processor System Management Registers [8086:d155] (rev 11)
00:08.1 System peripheral [0880]: Intel Corporation Core Processor Semaphore and Scratchpad Registers [8086:d156] (rev 11)
00:08.2 System peripheral [0880]: Intel Corporation Core Processor System Control and Status Registers [8086:d157] (rev 11)
00:08.3 System peripheral [0880]: Intel Corporation Core Processor Miscellaneous Registers [8086:d158] (rev 11)
00:10.0 System peripheral [0880]: Intel Corporation Core Processor QPI Link [8086:d150] (rev 11)
00:10.1 System peripheral [0880]: Intel Corporation Core Processor QPI Routing and Protocol Registers [8086:d151] (rev 11)
00:1a.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b3c] (rev 05)
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 05)
00:1c.0 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 [8086:3b42] (rev 05)
00:1c.1 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 [8086:3b44] (rev 05)
00:1c.2 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 [8086:3b46] (rev 05)
00:1c.3 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 [8086:3b48] (rev 05)
00:1c.4 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 [8086:3b4a] (rev 05)
00:1c.5 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 [8086:3b4c] (rev 05)
00:1d.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b34] (rev 05)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev a5)
00:1f.0 ISA bridge [0601]: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller [8086:3b03] (rev 05)
00:1f.2 SATA controller [0106]: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller [8086:3b2f] (rev 05)
00:1f.3 SMBus [0c05]: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller [8086:3b30] (rev 05)
02:00.0 VGA compatible controller [0300]: ATI Technologies Inc Device [1002:9488]
02:00.1 Audio device [0403]: ATI Technologies Inc R700 Audio Device [Radeon HD 4000 Series] [1002:aa38]
05:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 5300 AGN [Shiloh] Network Connection [8086:4235]
0b:00.0 SD Host controller [0805]: Ricoh Co Ltd Device [1180:e822] (rev 01)
0b:00.1 System peripheral [0880]: Ricoh Co Ltd Device [1180:e230] (rev 01)
0b:00.2 System peripheral [0880]: Ricoh Co Ltd Device [1180:e852] (rev 01)
0b:00.3 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd Device [1180:e832] (rev 01)
0d:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe [14e4:1698] (rev 10)
ff:00.0 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture Generic Non-Core Registers [8086:2c52] (rev 04)
ff:00.1 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture System Address Decoder [8086:2c81] (rev 04)
ff:02.0 Host bridge [0600]: Intel Corporation Core Processor QPI Link 0 [8086:2c90] (rev 04)
ff:02.1 Host bridge [0600]: Intel Corporation Core Processor QPI Physical 0 [8086:2c91] (rev 04)
ff:03.0 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller [8086:2c98] (rev 04)
ff:03.1 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Target Address Decoder [8086:2c99] (rev 04)
ff:03.4 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Test Registers [8086:2c9c] (rev 04)
ff:04.0 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Control Registers [8086:2ca0] (rev 04)
ff:04.1 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Address Registers [8086:2ca1] (rev 04)
ff:04.2 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Rank Registers [8086:2ca2] (rev 04)
ff:04.3 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Thermal Control Registers [8086:2ca3] (rev 04)
ff:05.0 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Control Registers [8086:2ca8] (rev 04)
ff:05.1 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Address Registers [8086:2ca9] (rev 04)
ff:05.2 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Rank Registers [8086:2caa] (rev 04)
ff:05.3 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Thermal Control Registers [8086:2cab] (rev 04)

```lshw -C Network
```

  *-network DISABLED      
       description: Wireless interface
       product: PRO/Wireless 5300 AGN [Shiloh] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wmaster0
       version: 00
       serial: 00:21:6a:11:78:84
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:37 memory:f0b00000-f0b01fff
  *-network
       description: Ethernet interface
       product: NetLink BCM5784M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0d:00.0
       logical name: eth0
       version: 10
       serial: 00:26:b9:17:8c:1a
       size: 1GB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.99 duplex=full firmware=sb v2.19 ip=10.20.254.73 latency=0 link=yes multicast=yes port=twisted pair speed=1GB/s
       resources: irq:40 memory:f1000000-f100ffff

```

---

### Post by chili555 on 2010-02-20
Please open a terminal and do:```
sudo rmmod -f dell-laptop
rfkill list
```Is the behavior improved? If so, we can make this permanent.

---

### Post by bhargav@in.com on 2010-02-20
Wifi worked now . But it does not work after restart . I need to enter the commands again to start wifi .

```

bhargav@bhargav-laptop:~$ rfkill list
0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: yes
2: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
4: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

``````

bhargav@bhargav-laptop:~$ sudo rmmod -f dell-laptop
[sudo] password for bhargav: 
bhargav@bhargav-laptop:~$ rfkill list
2: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
4: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

```rfkill unblock all

```

bhargav@bhargav-laptop:~$ rfkill list
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
6: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

```

So , Do I have to run the commands everytime i run  ubuntu ??

---

### Post by pytheas22 on 2010-02-21
Don't know if chili is going to respond and I apologize if I'm interjecting, but the easy solution to the issue would be to write a boot script to run the commands automatically.  To do that, type:

```
sudo gedit /etc/init.d/rfkill.sh
```

A file will open up.  Make the first line of the file look like this:

```
#!/bin/bash
```

Then below that line, add all of the commands that you need to run to make the wifi work again (one command per line).  I think these were just "sudo rmmod -f dell-laptop" and "rfkill unblock all" but I'm not sure.

When you're done, save and close the file.  Then run these commands so it gets added to the boot sequence:
```

cd /etc/init.d
sudo chmod +x rfkill.sh
sudo update-rc.d rfkill.sh defaults
```

Let me know if this does the trick.

---

### Post by khoi0107 on 2010-10-17
Hi guys, Im a new user of ubuntu. I installed Ubuntu 8.04 LTS from an old CD. So now my laptop has both Window 7 64bit and Ubuntu on it. On window i can use both Ethernet and Wireless perfectly, but in Ubuntu I can't connect to internet either ways. F
My devices are:
wireless: Intel(R) Wifi Link 5100 AGN
ethernet: Marvell Yukon 88E8057 PCI-E gigabit ethernet controller
But for now i just need wireless to work. 
Please help me step by step, im very new to this OS. Since I dont have Ethernet too I cant use commands like apt-get or something. I have to use another laptop to follow your instructions (either that or reboot to window 7)
This is my result for 
lspci -nn:
```

00:00.0 Host bridge [0600]: Intel Corporation Cantiga Memory Controller Hub [8086:2a40] (rev 07)
00:01.0 PCI bridge [0604]: Intel Corporation Cantiga PCI Express Graphics Port [8086:2a41] (rev 07)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)
00:1a.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 [8086:2944] (rev 03)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 [8086:2946] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93)
00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M LPC Interface Controller [8086:2919] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation ICH9M/M-E SATA AHCI Controller [8086:2929] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03)
01:00.0 VGA compatible controller [0300]: nVidia Corporation Unknown device [10de:0a2a] (rev a2)
01:00.1 Audio device [0403]: nVidia Corporation Unknown device [10de:0be2] (rev a1)
02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. Unknown device [11ab:4380] (rev 10)
03:00.0 Network controller [0280]: Intel Corporation Unknown device [8086:4232]
04:00.0 SD Host controller [0805]: Ricoh Co Ltd Unknown device [1180:e822]
04:00.1 System peripheral [0880]: Ricoh Co Ltd Unknown device [1180:e230]
04:00.3 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd Unknown device [1180:e832]
04:00.4 SD Host controller [0805]: Ricoh Co Ltd Unknown device [1180:e822]

```
lshw -C Network:
```

  *-network UNCLAIMED     
       description: Ethernet controller
       product: Marvell Technology Group Ltd.
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 10
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
  *-network UNCLAIMED
       description: Network controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0



```
Sorry for my English, im not a native speaker

---

### Post by pytheas22 on 2010-10-17
**khoi0107**: the easiest solution for you would be to install a more recent version of Ubuntu.  Ubuntu 8.04 is now 2.5 years old and lacks support for newer hardware.  If you're able to upgrade to Ubuntu 10.04 or 10.10, your Intel 5100 wireless card will be supported out-of-the-box: no need to install drivers at all.  You can download a more recent version of Ubuntu (for free, of course) from [http://ubuntu.com](http://ubuntu.com).

If you're unable to upgrade, I can still help you to get the wireless card to work on Ubuntu 8.04, though it will be a little complicated to do since you don't have an ethernet connection.  Let me know if you need to go this route, however, and I'll provide step-by-step instructions on what to do.

Your English is very good, by the way :)

---

### Post by khoi0107 on 2010-10-18
I thought of installing new version of Ubuntu too but for some reasons i can't. I downloaded 10.10 ISO and made a CD, after the boot i get a purple screen thingy and then it just goes all to black screen and stays still, same for booting from USB. 

I will try to download another ISO file, if I still cant do it maybe I need a step by step instruction.
Btw, what u recommend for the version i should download? I'm running window 7 64bit, so do I have to use ubuntu 64bit too? coz somebody told me drivers 64bit dont work on 32bit. 

Sorry for any dump question coz my major is EE, trying to learn linux for embedded system.

PS: thank you so much pytheas, u're the best staff in all the forums i have ever joined.

---

### Post by pytheas22 on 2010-10-18
**khoi0107**: hmmm, it sounds like Ubuntu 10.10 doesn't like your computer for some reason.  What is the model and manufacturer of your computer, and what kind of graphics card do you have?  We may be able to find a way to work around the black screen issue if we know what hardware you have.  You could then install Ubuntu 10.10 and everything would be great :)

Alternatively, if you'd rather just use your Ubuntu 8.04 system, here are instructions for getting the wireless working there:

First, on a different computer, download the file [http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2](http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2) and transfer it to your Ubuntu system.  Save it on the desktop there.

Second, insert your Ubuntu installation CD into the drive.  Then go to System>Administration>Software Sources (sorry--I don't know what these are called in languages other than English), and under the "Ubuntu Software" tab, enable the use of your CD as a repository.  Then close the window.  When you're asked about updating the sources list, say no (or you can say yes if you want; it doesn't actually matter).

Third, on Ubuntu, open a terminal and type these commands:
```

sudo apt-get update
sudo apt-get install build-essential
cd ~/Desktop
tar -xjvf compat-wireless-2.6.tar.bz2
cd compat-wireless*
scripts/driver-select intel
make
sudo make install
echo iwlagn | sudo tee -a /etc/modules
```

After this, reboot, and if all has gone as planned, your wireless card should now work.  If it's still not, please post the output of all of the commands above, as well as:
```

dmesg | grep -e iwl -e wlan
lshw -C Network
sudo iwlists can
modinfo iwlagn
```

Let me know how it goes, if you choose this route.  And thanks for the compliment on being a good forum moderator!  I actually joined the staff only about a month ago.

---

### Post by khoi0107 on 2010-10-19
I've tried 10.04 LTS but it doesnt work too. This time i got installation menu,  when i chose install ubuntu on a hardware, it showed up booting texts and went black again, nothing running at all 
I chekced out installation box and some ppl having same problems as me, but I dont get any good helping there, some same topics are abandoned. 

My laptop is SONY VAIO VPCCW19FX, Intel Dual Core T4300, Nvidia GeForce GT 230M, widescreen monitor

I know this is out of the topic but I really want to install new version of Ubuntu, if this wont help either Ima try follow ur instructions, get wireless and update. Thanks !!!

Btw, do i have to uninstall 8.04 before installing 10.10?

---

### Post by pytheas22 on 2010-10-19
According to some googling, the black screen issue seems to be a known problem that affects certain VAIO laptops with your type of graphics card.  We should be able to fix it using the information in [this thread]("http://ubuntuforums.org/showpost.php?p=9025582&postcount=6").

But first, you'll need to have Ubuntu 10.04 or 10.10 installed.  To do that, your best bet is to download the alternative installer CD, which will allow you to run the installer in text-only mode and avoid any issues with a black screen.

Once you have the system installed, boot to it.  When you get to a black screen, press control-alt-F2, which should hopefully bring you to a command prompt.  There, log in with your username and password.  Then type:

```
sudo nano /etc/X11/xorg.conf
```

A blank file should open.  Put these lines in it:
```

Section "Device"
Identifier "Configured Video Device"
Driver "vesa"
EndSection
```

Save the file by pressing control-O (the letter O, not the number zero), then reboot your computer.  It should work graphically this time, albeit with low resolution.  Once you've gotten this far, let me know and we can work on fixing the graphics so they work in full resolution (that should be easy, since with this more recent version of Ubuntu, your wireless should work out-of-the-box).

---

### Post by khoi0107 on 2010-10-19
Will try, thank you do much for your time

---

### Post by khoi0107 on 2010-10-20
I installed 10.10 via alternate CD as u said. I booted ubuntu, it went black screen and I heard a drum beat sound (It should be the login screen i guess). Tried to press ctrl+alt+f2 many times but nothing happened, it's still black for me :(.

does it work if I use another LCD monitor, plugin VGA port to display it?

---

### Post by pytheas22 on 2010-10-20
Sorry that didn't work quite as expected.  It's good that you hear the drumbeat sound--that means Ubuntu is loading without a problem--but apparently there's an issue preventing it from displaying on the screen correctly.

It might work with an external monitor.  That's worth a try if you have one easily accessible.

If not, or if an external monitor doesn't help, you can make the change you need by booting your computer to a live Ubuntu CD or USB (you can use any version of Ubuntu that you are able to boot to).  Once in the live environment, open a file browser with root privileges by typing in a terminal:

```
sudo nautilus
```

A window will open.  In the window, navigate to the Ubuntu partition of your internal hard drive by clicking its name in the left-hand section of the window (if it's not obvious which entry in the left-hand menu is the correct one for your Ubuntu partition, you may have to experiment to find it; unfortunately it's impossible for me to know exactly what it will be called).  Note that you should **not** navigate to the location "/" of the live file system.  Instead, you will be looking for the root directory of the Linux partition of your computer's hard drive, which will be something like /media/9a278276-edfb-4c26-afba-1f73637ddf4c (again, I can't know the exact path without having access to your computer).

Once you're in the root directory of your internal hard drive, you should see a folder called "etc."  Inside "etc" should be another folder called "X11."  Open X11, then right-click and select Create Document>Empty File.  Name the file "xorg.conf" (without the quotation marks).  Double-click the file to open it in an editor, then enter the lines:
```

Section "Device"
Identifier "Configured Video Device"
Driver "vesa"
EndSection
```

Save and close the file, then reboot your computer.  It should now load with the failsafe graphics driver, and hopefully display a screen.

Sorry this is proving to be more complicated than I'd anticipated, but thanks so much for your patience.

---

### Post by khoi0107 on 2010-10-21
should've tried before asking u.I dont have to use live CD, It works with another LCD monitor. I got wireless and everything.
So i tried to edit the file like u to get its on my primary screen too.
I used  
sudo nano /etc/X11/xorg.conf[FONT=monospace]

and put the content in like u said. But when i pressed ctrl+o and enter it gave me this
[error writing /etc/x11/xorg.conf: no such file or directory]

I looked up in Filesystem/etc too but there isnt any "x11" folder 
[/FONT]

---

### Post by khoi0107 on 2010-10-21
aw, sry i screwed up again. I used "additional drivers", hope I could find something to do with my graphic card and I did. It said I need Nvidia accelerator driver, i activated it and restart

Now I get a "single-color "no-effect" (sry for my English, i mean it's much simplier)pink screen with ubuntu loading (4 dots thingy), some text loading and everything goes pink screen and stay still, same like black screen but now even external monitor cant work as well :(

If u can help me a way to set up the laptop screen by using the external monitor i will gladly install 10.10 again to have it work on the external monitor again.

Thank you very much 

PS: i think the problem is the widescreen. I have had a lot of problems dealing with applications&games can't run in 16-9 mode.

---

### Post by pytheas22 on 2010-10-21
Good to hear that the external monitor works.  FYI, you got the "[error writing /etc/x11/xorg.conf: no such file or directory]" message because the path has to be /etc/X11/xorg.conf, with an uppercase X, not x.  In Linux case matters, so X is totally different from x.

But we don't need to worry about editing the xorg.conf file anymore, since you can get the screen to display on the external monitor.  That should be sufficient for installing an updated graphics driver that should solve the whole problem.

To do that, reinstall Ubuntu 10.10 and attach your external monitor.  Then follow these steps (which are based mostly on what I'm reading [here]("http://ubuntuforums.org/showthread.php?p=9995502")):

1. first, we'll disable "kernel mode setting," which can cause graphics problems, by editing your grub configuration.  Open a terminal and type:
```

sudo nano /etc/grub/default

```
A file will open.  Look for the line that reads:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```

Modify that line so it says:
```

GRUB_CMDLINE_LINUX_DEFAULT="**nomodeset**"
```

Finally, type:
```

sudo update-grub
```

to make this change permanent.

2. reboot the computer so that you're running without kernel mode setting.

3. now we need to install the proprietary nvidia Linux driver.  The thread that I've referenced says that the latest version of the nvidia driver doesn't work, but an older one does.  This would explain why the driver that you installed on your own previously didn't solve the problem.

We can download an older version of the driver from nvidia's site and install it manually (for this step, I've referred a little to [this thread]("http://ubuntuforums.org/showthread.php?t=990978")).  First, download the source either from [here]("http://www.nvidia.com/object/linux-display-ia32-256.53-driver.html") (if you're using 32-bit Ubuntu) or [here]("http://www.nvidia.com/object/linux-display-amd64-256.53-driver.html") (for 64-bit).  Save the downloaded file to your desktop.

Next, open a terminal and type this command (to install a compiler and other tools that you will need to build the nvidia driver):
```

sudo apt-get install build-essential
```

Next, press control-alt-F2, which should take you to a fullscreen terminal.  There, log in and run these commands:
```

sudo /etc/init.d/gdm stop
cd ~/Desktop
sudo bash NVIDIA*run
```

Follow the instructions on the screen for compiling the nvidia driver.  Once it's all done, reboot by typing "sudo reboot".

After the reboot, with any luck, your display will be working.  Please let me know.

---

### Post by khoi0107 on 2010-10-21
i reinstalled it 
The sudo nano I gave me this
[IMG]http://img143.imageshack.us/img143/6374/screenshotvc.png[/IMG]
I don't see aything in the file to edit, its like a im making a new file here. There's only grub.d in etc, and grub is in boot i think. I did try sudo nano /boot/grub/default but the result was the same :( 
btw, sry abt the x and X thingy, Im such a noob :P

---

### Post by pytheas22 on 2010-10-21
So sorry--it was a mistake on my part!  The file to edit is /etc/default/grub/, not /etc/grub/default.  So:
```

sudo nano /etc/default/grub
```

will open it up for you.  Sorry for not catching that.  Good thinking trying to find it in /etc/grub.d but unfortunately that's not quite it!
> 
btw, sry abt the x and X thingy, Im such a noob

Don't worry, we've all done that before :)

---

### Post by khoi0107 on 2010-10-21
awesome, i got the screen after the "nomodeset" and reboot. I installed NVIDIA, but the final problem is now my ubuntu (rebooted after install Nvidia) always starts up with a tty1 console. As I googled i used ctrl+atl+f7 to return to graphical screen but it stuck at checking sensor or battery. Seems like this guy had the same problem [http://ubuntuforums.org/showthread.php?t=1495722](http://ubuntuforums.org/showthread.php?t=1495722) 

Do i have to... like "start" the /etc/init.d/gdm after I stopped it? :KS

Thank you so much for time :D

---

### Post by pytheas22 on 2010-10-22
Sorry not to reply sooner...

hmmm, that is a bit strange, but at least you're a lot closer now.  If you type:
```

sudo /etc/init.d/gdm start
```

are you then able to get a graphical screen (you may need to press control-alt-F7 to get to it)?  If that doesn't work, what happens if you type:
```

startx
```

"startx" should also start a graphical session for you, although in a slightly different way than using the /etc/init.d/gdm script.

If you get errors when running either of these commands, it would be great to know what they are.

---

### Post by khoi0107 on 2010-10-22
It doesnt seem like it
when I typed 

sudo /etc/init.d/gdm start 

it gave me like this: 
[B]"rather than invoke init script through /etc/init.d, try to use service (8 ) utility eg service gdm start
since the script you're trying to invoke has ben converted to an upstart job, u can also use start(8 ) eg start gdm"[/B]

Its like a description and my command didnt do anything at all. I remember there were these same lines when i typed  "sudo /etc/init.d/gdm stop"

And the "startx" loaded some NVIDIA checked (error) and gave me "Fatal server error: no screen found" and Im still in the console[ http://yfrog.com/6rimg2569hgj]("http://yfrog.com/6rimg2569hgj")

Did i messed up? what happened if I didnt stop the gdm and installed NVIDIA last time? 
Seem like I have to reinstall :(
Sorry !!!

---

### Post by pytheas22 on 2010-10-23
> And the "startx" loaded some NVIDIA checked (error) and gave me "Fatal server error: no screen found" and Im still in the console [http://yfrog.com/6rimg2569hgj](http://yfrog.com/6rimg2569hgj)


From the image you posted, it looks like a permissions issue.  There are a few things you can try to fix that without having to reinstall.  Does it work if you type:
```

sudo startx
```

If not, make sure your user is a member of the group "video" by running:
```

sudo adduser $(whoami) video
```

and that the devices /dev/nvidia0 and /dev/nvidiactl have appropriate permissions:
```

sudo chown root:video /dev/nvidia0
sudo chown root:video /dev/nvidiactl
sudo chmod 774 /dev/nvidia0
sudo chmod 774 /dev/nvidiactl
```
> 
Did i messed up? what happened if I didnt stop the gdm and installed NVIDIA last time?

You have to stop gdm before installing the nvidia driver.  Otherwise the installer will refuse to work.  I don't know why they do it this way (it doesn't seem to me to be actually necessary), but it's how it's always been.

---

### Post by khoi0107 on 2010-10-23
i mean I did type sudo /etc/init.d/gdm stop but for what I got I think my command didnt work.

Anw, will try those now. Thanks

---

### Post by khoi0107 on 2010-10-23
I've tried all those commands, it doesnt work, still that screen
Im giving up hope here. Can we start again from the "nomodeset" part? Is it the right driver that works? 
I doubt that I did stop the gdm back then. should've try
service gdm stop
stop gdm
Just like those lines said
Thank you so much for your times :(

As I read in here
[http://ubuntuforums.org/showthread.php?t=99078](http://ubuntuforums.org/showthread.php?t=99078)
Do I have to set the "nomodeset" ? And if I do, can I keep it that way wi/o install NVIDIA? coz I got the screen up after "nomodeset"

---

### Post by pytheas22 on 2010-10-23
> I got the screen up after "nomodeset"

Ah, sorry, I didn't realize that.  If you got a screen working as desired simply by enabling the "nomodeset" option, then certainly, you can leave it at that and not install the driver from Nvidia's site.  I was under the impression, from reading those other threads, that you needed the driver from Nvidia in order to get the laptop screen to work, but I don't have that type of computer so I don't know.

Without the driver from Nvidia's site, you might not be able to use 3D acceleration and things like that, meaning no 3D games or desktop effects, but I'm not positive.  Otherwise, everything will work as normal.

You could probably uninstall the Nvidia driver, but that would be difficult and it might be easiest just to reinstall Ubuntu again, then apply the "nomodeset" change.
> 
I doubt that I did stop the gdm back then. should've try
service gdm stop
stop gdm

You can type "sudo /etc/init.d/gdm stop", "sudo service gdm stop" *or* "sudo stop gdm"--all three commands do the same thing (which I think is dumb--there should be only way to do it to avoid confusing users--but I'm not the one in charge).

If you didn't type any of those commands to stop gdm, however, the Nvidia driver should have refused to install, because you can't install it when gdm (which is the "Gnome display daemon," the service responsible for the graphical console) is running.  So I'm not sure what happened there...

Anyway, hopefully you can get what you need simply with the "nomodeset" change.

---

### Post by khoi0107 on 2010-10-24
I've been running around in many forums but u're the only one who spends time with my my problems. Can u check this out ? 
[http://art.ubuntuforums.org/showthread.php?p=8591463](http://art.ubuntuforums.org/showthread.php?p=8591463)
>  problem is to do with ubuntu not reading the EDID correctly so the  monitor is not recognised and therefore is not used... He seems to know what he is doing. I dont know what EDID is but i downloaded SoftMCCS like he said, dont know what to do next
This guy solved his problem by custom EDID too
[http://ubuntuforums.org/showthread.php?t=1487383&page=1](http://ubuntuforums.org/showthread.php?t=1487383&page=1)
I have read a lot but u know, my English isnt good enough and their instructions aren't step by step, there're so many new definitions like "X" server, gdm, GUI, ...  so I confused. 
I contacted those guys but seems like those thread are very old and they aren't active anymore 

Here is my new thread summarized what i got so far so everybody can help, but I expect yours the most
[http://ubuntuforums.org/showthread.php?t=1604327&highlight=khoi0107](http://ubuntuforums.org/showthread.php?t=1604327&highlight=khoi0107)
Thanks again :(

---

### Post by khoi0107 on 2010-10-24
I tried to follow those step but i have to install nvdia first to have xorg.conf file to edit,but like i said, i only get the tty1 console, i dont know how to edit xorg, the only command i know is gedit which doesnt work w/o graphical screen

---

### Post by pytheas22 on 2010-10-24
I read those threads relating to the EDID thing.  From what I understand, this is what you need to do:

1. use the program softMCCS to extract the EDID for your computer.  I am not sure exactly how to do this, but hopefully you can figure it out.  Apparently softMCCS should generate a file with the extension .bin; this is what you need for the next step.

2. copy the .bin file that softMCCs gave you to your /etc/X11 folder on Ubuntu.  If the file is saved on your desktop in Ubuntu and is named sonyedid.bin, you could copy it to the correct location with the command:
```

sudo cp ~/Desktop/sonedid.bin /etc/X11
```

3. install the Nvidia driver from Nvidia's site, as you did before (you need to stop gdm first to install the driver, of course)

4. edit your /etc/X11/xorg.conf file in Ubuntu so that the "Device" section looks like this:
```

Section "Device"
   Identifier         "Device0"
   Driver              "nvidia"
   VendorName    "NVIDIA Corporation"
   Option            "ConnectedMonitor"   "DFP-0"
   Option            "CustomEDID"          "DFP-0:/etc/X11/sonyedid.bin"
EndSection
```

If you need to edit a file from the command line, you can use the program "nano" instead of gedit.  For example:
```

sudo nano /etc/X11/xorg.conf
```

would open the xorg.conf file in an editor.

If you open your xorg.conf file and it's empty, that's alright.  Just add in the "Device" section from above and save the file.  If the file is not empty, modify the "Device" section so it looks like the example above.  If the file is not empty but no "Device" section exists, add in that section.

I am not sure if you need to make the "nomodeset" change as well, but those threads don't appear to mention it, so it doesn't seem necessary.

I see also in the new thread you started that someone suggests trying Ubuntu 10.04.  That may indeed work better, since it has been out longer and there has been more time for fixing bugs.  You might even be able to use the Nvidia driver available in the Ubuntu Software Center (just search for "nvidia driver"), which you can install much more easily, rather than having to stop gdm and install the driver downloaded from Nvidia's site.

---

### Post by khoi0107 on 2010-10-24
Omg it works! 10.04 +195.36.15 nvidia + EDID work . Thank you sooo much pyth. U have no idea how much this means to me.thanks !

---

### Post by khoi0107 on 2010-10-24
LOL after the 10.04 auto update I still have the Driver working good but the boot loader loaded 8 OS for me
```
risket@risket-laptop:~$ sudo update-grubGenerating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-25-generic
Found initrd image: /boot/initrd.img-2.6.32-25-generic
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sda1
Found Windows 7 (loader) on /dev/sda2
done
```Usually there're only 6, I have no idea why i get another kernel version here. 10.04 is 2.6.32-25 right? How can i get rid of other 2? 
```
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
```These 2 don't boot up anything !!!

---

### Post by joeheim on 2010-10-25
Hi there, 

I followed your advice step by step, unfortunately it does not work.
As long as I am working with the options 

Section "Device"
Identifier "Configured Video Device"
Driver "vesa"
EndSection

I can work at least with this low resolution. But after try to install the Nvidia driver I end up with a command prompt asking me to login.

My system is a Vaio VPCZ128GG with a NVIDIA Geforce GT330M
I am using Nvidias 	260.19.12 driver (actually not, because it is not working).

Perhaps any further suggestions?

Thanks



> **pytheas22 said:**
> I read those threads relating to the EDID thing.  From what I understand, this is what you need to do:

1. use the program softMCCS to extract the EDID for your computer.  I am not sure exactly how to do this, but hopefully you can figure it out.  Apparently softMCCS should generate a file with the extension .bin; this is what you need for the next step.

2. copy the .bin file that softMCCs gave you to your /etc/X11 folder on Ubuntu.  If the file is saved on your desktop in Ubuntu and is named sonyedid.bin, you could copy it to the correct location with the command:
```

sudo cp ~/Desktop/sonedid.bin /etc/X11
```

3. install the Nvidia driver from Nvidia's site, as you did before (you need to stop gdm first to install the driver, of course)

4. edit your /etc/X11/xorg.conf file in Ubuntu so that the "Device" section looks like this:
```

Section "Device"
   Identifier         "Device0"
   Driver              "nvidia"
   VendorName    "NVIDIA Corporation"
   Option            "ConnectedMonitor"   "DFP-0"
   Option            "CustomEDID"          "DFP-0:/etc/X11/sonyedid.bin"
EndSection
```

If you need to edit a file from the command line, you can use the program "nano" instead of gedit.  For example:
```

sudo nano /etc/X11/xorg.conf
```

would open the xorg.conf file in an editor.

If you open your xorg.conf file and it's empty, that's alright.  Just add in the "Device" section from above and save the file.  If the file is not empty, modify the "Device" section so it looks like the example above.  If the file is not empty but no "Device" section exists, add in that section.

I am not sure if you need to make the "nomodeset" change as well, but those threads don't appear to mention it, so it doesn't seem necessary.

I see also in the new thread you started that someone suggests trying Ubuntu 10.04.  That may indeed work better, since it has been out longer and there has been more time for fixing bugs.  You might even be able to use the Nvidia driver available in the Ubuntu Software Center (just search for "nvidia driver"), which you can install much more easily, rather than having to stop gdm and install the driver downloaded from Nvidia's site.

---

### Post by pytheas22 on 2010-10-25
**khoi0107**: glad to hear it finally works.  Thanks for your patience through the whole thing.  I guess this is a good example of why it's usually safer to stick with slightly older Ubuntu releases (10.04 vs. 10.10) to avoid nasty bugs.

I'm not sure why grub has menu entries that don't boot.  You should be able to get rid of them by editing /boot/grub/grub.cfg and removing them from that file--look for the sections in the file that start with the word "menuentry."

Note that the grub.cfg file warns you not to edit it directly.  I think you're supposed to make the changes in some other way, but I don't know how.  I've always just edited grub.cfg directly and it works.  But if changing it makes your computer fail to boot, don't blame me :)

Edit: also, it would be great if you could please update the other thread you started explaining what the solution was, or just link back to the post in this thread that solved the problem for you.  This way hopefully other people in a similar situation can find the solution more easily.

[B]
joeheim[/B]: are you on Ubuntu 10.10 or Ubuntu 10.04?  It seems like this only works with Ubuntu 10.04 for the moment (see this [bug report]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/660596?comments=all") for details), using the 195.36.15 version of the Nvidia driver.  That seems like it is the only option for the time being (other than using the vesa driver, which doesn't support high resolution or 3D acceleration).

---

### Post by joeheim on 2010-10-25
Hi,

unfortunately 10.10, I never got 10.04 installed on my SSD Raid 0.

Cheers

---

### Post by pytheas22 on 2010-10-25
> Hi,

unfortunately 10.10, I never got 10.04 installed on my SSD Raid 0.

Cheers

hmmm, I searched a bit more but can't find any solutions that seem to work for 10.10.  Installing version 195.36.24 of the driver, which you have to download from nvidia's site, appears possibly to work, but in the experience of khoi0107 above, it seemed not to.

You could try installing the xserver-xorg-video-nv package, which would provide a driver that should at least give you fullscreen resolution, but still no hardware acceleration.  You'd need to make sure that in the "Device" section of your /etc/X11/xorg.conf file, the "Driver" is set to "nv" instead of "nvidia"

Or you could always try falling back to Ubuntu 10.04.  What kind of issues did you run into trying to set up RAID?  Did you use the alternate CD to install (you should have; I'm pretty sure RAID configuration isn't supported by the live CD installer).

---

### Post by claven123 on 2010-10-25
Do you think having two monitors connected when you install the nvidia drivers will make a difference?  How do I find out what the recommended drivers are that ubuntu 10.10 prefers we install.  This would be in the additional drivers utility....

Thanks,

---

### Post by pytheas22 on 2010-10-25
> Do you think having two monitors connected when you install the nvidia drivers will make a difference?

Having two monitors connected shouldn't have anything to do with the bug that's preventing the Nvidia drivers from working properly.  I wouldn't worry about this.

>  How do I find out what the recommended drivers are that ubuntu 10.10 prefers we install. This would be in the additional drivers utility....

I'm not positive what you mean, but if you're asking which drivers Ubuntu installs when you run the "Hardware Drivers" program, it installs packages for the latest Nvidia proprietary drivers.  On Ubuntu 10.10, that currently means version 260.19.12 of the Nvidia driver, which apparently does not work on Ubuntu 10.10.  An earlier version of the driver, version 195.36.24, *may* work based on what I've read elsewhere, but I am not positive (I don't own any Nvidia hardware myself so I can't test any of this).  To install version 195.36.24, however, you would have to use the manual installer available from Nvidia's website, rather than the package provided by Ubuntu.

FYI, here's a quick outline of the Nvidia driver situation in Ubuntu: by default, Ubuntu ships with a driver called "[nouveau]("http://nouveau.freedesktop.org/wiki/")," which is an open-source driver for Nvidia cards.  Currently, nouveau doesn't support 3D acceleration or other advanced features, but for most devices it will at least provide fullscreen resolution.

If you want 3D acceleration, you have to download the Nvidia closed-source driver from Nvidia's site (this driver might also be referred to as the "Nvidia glx driver" or the "Nvidia proprietary driver").  Ubuntu doesn't ship with the closed-source driver by default due to philosophical objections (Ubuntu aims to be fully open-source), among other concerns.

There's another driver called "nv" that, like nouveau, is open-source but supports only 2D graphics.  Until about a year ago, Ubuntu used the nv driver for Nvidia devices instead of noveau.  Currently nv is no longer used by default, but it's still a third option that might be useful if neither nouveau nor the proprietary Nvidia driver works.

---

### Post by claven123 on 2010-10-25
Yes, I guess I was referring to the two drivers suggested by ubuntu's hardware program.  I tired both of them, and manual installs of the current driver.  I've tried all sorts of fixes but nothing has worked.  I get an error that the can't install nvidia.ko.

Not really, sure what to do next.  The graphics I have are ok, but it's only one screen.  I feel I have the issue with vga vs dvi.  I'm sure I have one of each for monitors.  I will have to double check on that.  

Any ideas.

I think later, I am going to try to do some of the suggestions in this thread.

Thanks,

---

### Post by pytheas22 on 2010-10-26
> Yes, I guess I was referring to the two drivers suggested by ubuntu's hardware program. I tired both of them, and manual installs of the current driver. I've tried all sorts of fixes but nothing has worked. I get an error that the can't install nvidia.ko.

Not really, sure what to do next. The graphics I have are ok, but it's only one screen. I feel I have the issue with vga vs dvi. I'm sure I have one of each for monitors. I will have to double check on that.

Any ideas.

I think later, I am going to try to do some of the suggestions in this thread.

Yes, you probably need the proprietary Nvidia driver to use dual screens.  nouveau likely doesn't support that.

What is the exact error message you get about being unable to install nvidia.ko?  Are you disabling gdm (by typing "sudo /etc/init.d/gdm stop") before running the installer from the Nvidia website?  (Warning: typing that command will kill your graphical session, so don't do it if you have unsaved work, etc.)

---

### Post by claven123 on 2010-10-26
[http://ubuntuforums.org/showthread.php?t=990978](http://ubuntuforums.org/showthread.php?t=990978)
I followed the directions on post #1 of this thread and many of the other directions.


[http://ubuntuforums.org/showthread.php?t=1565176](http://ubuntuforums.org/showthread.php?t=1565176)
I followed the directions in post #5 

I have not messed with the xconfig files or anything to do with x yet.  I feel that nv or nouveau is in the boot loader or something, since I have blacklisted it and uninstalled it and I keep getting the error that is is conflicting etc...

I'm at work right now so I can't get at the specific error or report.  I do know there is a problem with nvidia.ko and I will get that error message soon.


Oh, ironically.  With the first fresh install I had so so graphics and after a restart or something both monitors showed up and I was able to adjust refresh rates and resolution etc....  then later I ran the suggested updates that pops up all the time.  Then after the updates I only have one screen.  I'm debating on doing a fresh install and not doing the updates....

Thanks

---

### Post by pytheas22 on 2010-10-26
> I have not messed with the xconfig files or anything to do with x yet. I feel that nv or nouveau is in the boot loader or something, since I have blacklisted it and uninstalled it and I keep getting the error that is is conflicting etc...

Sometimes you have to update your "init ramdisk" in order to prevent modules from loading.  You can find out more about what this means via Google if you want; I only have a vague understanding, but the command you need to run is:
```

sudo update-initramfs
```

Then try rebooting and whichever modules you have in the blacklist should not load, unless you explicitly load them with the "modprobe" command.
> 
Oh, ironically. With the first fresh install I had so so graphics and after a restart or something both monitors showed up and I was able to adjust refresh rates and resolution etc.... then later I ran the suggested updates that pops up all the time. Then after the updates I only have one screen. I'm debating on doing a fresh install and not doing the updates....

Did both monitors start working after you installed the Nvidia driver using the package from the website, or after?  If it was before, then it's likely that installing the Nvidia driver is what caused the problems.  If it was after, then it's likely that you originally had everything working with the proprietary Nvidia driver, but then an update to a different package broke things (the update manager would not have updated the Nvidia driver if you installed it from source, since the update manager can only take care of packages installed through the Software Center, or ones that are present in a fresh installation of Ubuntu).  In the latter case, if you knew which package caused the problem (probably one related to X11, but it's hard to know for sure without more information), you could reinstall Ubuntu, then mark that package to be held at its current, working version, so that it would not be upgraded anymore.

---

### Post by d3v1150m471c on 2010-10-26
> **pytheas22 said:**
> mark that package to be held at its current, working version, so that it would not be upgraded anymore.

i never noticed that... how does one go about this?

---

### Post by claven123 on 2010-10-26
Here is my var/log/nvidia-installer.log 

To clarify...  I had two monitors and was able to alter the refresh rates... I attempted to get install the new monitors etc... and many many other things.  Then always returned to the same state.  The only time I lost the two monitors was when I installed the suggested updates.

I was looking at the monitors to figure out which was vga and dvi and I restarted and now I have both monitors and I'm able to adjust refresh rates etc... but no nvidia drivers.

I have two outputs one is vga and the other is DVI.  BOTH monitors are connected by VGA connectors, so one is converted by the cable.

Interesting....



nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Sun Oct 24 14:15:58 2010
installer version: 260.19.12

PATH:
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin

option status:
  license pre-accepted               : false
  update                             : false
  force update                       : false
  expert                             : false
  uninstall                          : false
  driver info                        : false
  precompiled interfaces             : true
  no ncurses color                   : false
  query latest version               : false
  no questions                       : false
  silent                             : false
  no recursion                       : false
  no backup                          : false
  kernel module only                 : false
  sanity                             : false
  add this kernel                    : false
  no runlevel check                  : false
  no network                         : false
  no ABI note                        : false
  no RPMs                            : false
  no kernel module                   : false
  force SELinux                      : default
  no X server check                  : false
  no cc version check                : false
  run distro scripts                 : true
  no nouveau check                   : false
  run nvidia-xconfig                 : false
  sigwinch work around               : true
  force tls                          : (not specified)
  X install prefix                   : (not specified)
  X library install path             : (not specified)
  X module install path              : (not specified)
  OpenGL install prefix              : (not specified)
  OpenGL install libdir              : (not specified)
  utility install prefix             : (not specified)
  utility install libdir             : (not specified)
  installer prefix                   : (not specified)
  doc install prefix                 : (not specified)
  kernel name                        : (not specified)
  kernel include path                : (not specified)
  kernel source path                 : (not specified)
  kernel output path                 : (not specified)
  kernel install path                : (not specified)
  precompiled kernel interfaces path : (not specified)
  precompiled kernel interfaces url  : (not specified)
  proc mount point                   : /proc
  ui                                 : (not specified)
  tmpdir                             : /tmp
  ftp mirror                         : [ftp://download.nvidia.com](ftp://download.nvidia.com)
  RPM file list                      : (not specified)
  selinux chcon type                 : (not specified)

Using: nvidia-installer ncurses user interface
-> License accepted.
-> Installing NVIDIA driver version 260.19.12.
-> Running distribution scripts
   executing: '/usr/lib/nvidia/pre-install'...
-> done.
-> The distribution-provided pre-install script failed!  Continue installation 
   anyway? (Answer: Yes)
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
-> Kernel source path: '/lib/modules/2.6.35-22-generic/build'
-> Kernel output path: '/lib/modules/2.6.35-22-generic/build'
-> Performing rivafb check.
-> Performing nvidiafb check.
-> Performing Xen check.
-> Cleaning kernel module build directory.
   executing: 'cd ./kernel; make clean'...
-> Building kernel module:
   executing: 'cd ./kernel; make module SYSSRC=/lib/modules/2.6.35-22-generic/b
   uild SYSOUT=/lib/modules/2.6.35-22-generic/build'...
   NVIDIA: calling KBUILD...
   test -e include/generated/autoconf.h -a -e include/config/auto.conf || (        \
       echo;                                \
       echo "  ERROR: Kernel configuration is invalid.";        \
       echo "         include/generated/autoconf.h or include/config/auto.conf are
   missing.";\
       echo "         Run 'make oldconfig && make prepare' on kernel src to fix it
   .";    \
       echo;                                \
       /bin/false)
   mkdir -p /tmp/selfgz1981/NVIDIA-Linux-x86-260.19.12/kernel/.tmp_versions ; r
   m -f /tmp/selfgz1981/NVIDIA-Linux-x86-260.19.12/kernel/.tmp_versions/*
   make -f scripts/Makefile.build obj=/tmp/selfgz1981/NVIDIA-Linux-x86-260.19.1
   2/kernel
     cc -Wp,-MD,/tmp/selfgz1981/NVIDIA-Linux-x86-260.19.12/kernel/.nv.o.d  -nos
   tdinc -isystem /usr/lib/gcc/i686-linux-gnu/4.4.5/include  -I/usr/src/linux-h
   eaders-2.6.35-22-generic/arch/x86/include -Iinclude  -include include/genera
   ted/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototy
   pes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-functio
   n-declaration -Wno-format-security -fno
   -delete-null-pointer-checks -O2 -m32 -msoft-float -mregparm=3 -freg-struct-r
   eturn -mpreferred-stack-boundary=2 -march=i686 -mtune=generic -maccumulate-o
   utgoing-args -Wa,-mtune=generic32 -ffreestanding -fstack-protector -DCONFIG_
   AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -pipe -Wn
   o-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -
   mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sib
   ling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-o
   verflow -fconserve-stack -I/tmp/selfgz1981/NVIDIA-Linux-x86-260.19.12/kernel
   -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DN
   VRM -DNV_VERSION_STRING=\"260.19.12\" -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE -D
   "KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv)"  -D"KBUILD_MODNAME=KBU
   ILD_STR(nvidia)"  -c -o /tmp/selfgz1981/NVIDIA-Linux-x86-260.19.12/kernel/.t
   mp_nv.o /tmp/selfgz1981/NVIDIA-Linux-x86-260.19.12/kernel/nv.c
   In file included from include/linux/kernel.h:17,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz1981/NVIDIA-Linux-x86-260.19.12/kernel/nv-l
   inux.h:27,
                    from /tmp/selfgz1981/NVIDIA-Linux-x86-260.19.12/kernel/nv.c
   :13:
   include/linux/bitops.h: In function ‘hweight_long’:
   include/linux/bitops.h:49: warning: signed and unsigned type in conditional 
   expression
   In file included from /usr/src/linux-headers-2.6.35-22-generic/arch/x86/incl
   ude/asm/uaccess.h:571,
                    from include/linux/poll.h:14,
                    from /tmp/selfgz1981/NVIDIA-Linux-x86-260.19.12/kernel/nv-l
   inux.h:84,
                    from /tmp/selfgz1981/NVIDIA-Linux-x86-260.19.12/kernel/nv.c
   :13:
   /usr/src/linux-headers-2.6.35-22-generic/arch/x86/include/asm/uaccess_32.h: 
   In function ‘copy_from_user’:
   /usr/src/linux-headers-2.6.35-22-generic/arch/x86/include/asm/uaccess_32.h:2
   09: warning: comparison between signed and unsigned integer expressions
     set -e ; perl /usr/src/linux-headers-2.6.35-22-generic/scripts/recordmcoun
   t.pl "i386" "little" "32" "objdump" "objcopy" "cc" "ld" "nm" "" "" "1" "/tmp
   /selfgz1981/NVIDIA-Linux-x86-260.19.12/kernel/nv.o";
     cc -Wp,-MD,/tmp/selfgz1981/NVIDIA-Linux-x86-260.19.12/kernel/.nv_gvi.o.d  
   -nostdinc -isystem /usr/lib/gcc/i686-linux-gnu/4.4.5/include  -I/usr/src/lin
   ux-headers-2.6.35-22-generic/arch/x86/include -Iinclude  -include include/ge
   nerated/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-pro
   totypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-fun
   ction-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -
   m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=
   2 -march=i686 -mtune=generic -maccumulate-outgoing-args -Wa,-mtune=generic32
   -ffreestanding -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FR
   AME=1 -DCONFIG_AS_CFI_SECTIONS=1 -pipe -Wno-sign-compare -fno-asynchronous-u
   nwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024
   -fno-omit-frame-pointer
    -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-
   sign -fno-strict-overflow -fconserve-stack -I/tmp/selfgz1981/NVIDIA-Linux-x8
   6-260.19.12/kernel -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KE
   RNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"260.19.12\" -UDEBUG -U_DEBUG -D
   NDEBUG  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_gvi)"
    -D"KBUILD_MODNAME=KBUILD_STR(nvidia)"  -c -o /tmp/selfgz1981/NVIDIA-Linux-x
   86-260.19.12/kernel/.tmp_nv_gvi.o /tmp/selfgz1981/NVIDIA-Linux-x86-260.19.12
   /kernel/nv_gvi.c
   In file included from include/linux/kernel.h:17,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz1981/NVIDIA-Linux-x86-260.19.12/kernel/nv-l
   inux.h:27,
                    from /tmp/selfgz1981/NVIDIA-Linux-x86-260.19.12/kernel/nv_g
   vi.c:15:
   include/linux/bitops.h: In function ‘hweight_long’:
   include/linux/bitops.h:49: warning: signed and unsigned type in conditional 
   expression
   In file included from /usr/src/linux-headers-2.6.35-22-generic/arch/x86/incl
   ude/asm/uaccess.h:571,
                    from include/linux/poll.h:14,
                    from /tmp/selfgz1981/NVIDIA-Linux-x86-260.19.12/kernel/nv-l
   inux.h:84,
                    from /tmp/selfgz1981/NVIDIA-Linux-x86-260.19.12/kernel/nv_g
   vi.c:15:
   /usr/src/linux-headers-2.6.35-22-generic/arch/x86/include/asm/uaccess_32.h: 
   In function ‘copy_from_user’:
   /usr/src/linux-headers-2.6.35-22-generic/arch/x86/include/asm/uaccess_32.h:2
   09: warning: comparison between signed and unsigned integer expressions
     set -e ; perl /usr/src/linux-headers-2.6.35-22-generic/scripts/recordmcoun
   t.pl "i386" "little" "32" "objdump" "objcopy" "cc" "ld" "nm" "" "" "1" "/tmp
   /selfgz1981/NVIDIA-Linux-x86-260.19.12/kernel/nv_gvi.o";
     cc -Wp,-MD,/tmp/selfgz1981/NVIDIA-Linux-x86-260.19.12/kernel/.nv-vm.o.d  -
   nostdinc -isystem /usr/lib/gcc/i686-linux-gnu/4.4.5/include  -I/usr/src/linu
   x-headers-2.6.35-22-generic/arch/x86/include -Iinclude  -include include/gen
   erated/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prot
   otypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-func
   tion-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m
   32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2
   -march=i686 -mtune=generic -maccumulate-outgoing-args -Wa,-mtune=generic32 -
   ffreestanding -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRA
   ME=1 -DCONFIG_AS_CFI_SECTIONS=1 -pipe -Wno-sign-compare -fno-asynchronous-un
   wind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 
   -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-
   statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -I/tmp/sel
   fgz1981/NVIDIA-Linux-x86-260.19.12/kernel -Wall -MD -Wsign-compare -Wno-cast
   -qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"260.19.1
   2\" -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASEN
   AME=KBUILD_STR(nv_vm)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidi
   a)"  -c -o /tmp/selfgz1981/NVIDIA-Linux-x86-260.19.12/kernel/.tmp_nv-vm.o /t
   mp/selfgz1981/NVIDIA-Linux-x86-260.19.12/kernel/nv-vm.c
   In file included from include/linux/kernel.h:17,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz1981/NVIDIA-Linux-x86-260.19.12/kernel/nv-l
   inux.h:27,
                    from /tmp/selfgz1981/NVIDIA-Linux-x86-260.19.12/kernel/nv-v
   m.c:14:
   include/linux/bitops.h: In function ‘hweight_long’:
   include/linux/bitops.h:49: warning: signed and unsigned type in conditional 
   expression
   In file included from /usr/src/linux-headers-2.6.35-22-generic/arch/x86/incl
   ude/asm/uaccess.h:571,
                    from include/linux/poll.h:14,
                    from /tmp/selfgz1981/NVIDIA-Linux-x86-260.19.12/kernel/nv-l
   inux.h:84,
                    from /tmp/selfgz1981/NVIDIA-Linux-x86-260.19.12/kernel/nv-v
   m.c:14:
   /usr/src/linux-headers-2.6.35-22-generic/arch/x86/include/asm/uaccess_32.h: 
   In function ‘copy_from_user’:
   /usr/src/linux-headers-2.6.35-22-generic/arch/x86/include/asm/uaccess_32.h:2
   09: warning: comparison between signed and unsigned integer expressions
     set -e ; perl /usr/src/linux-headers-2.6.35-22-generic/scripts/recordmcoun
   t.pl "i386" "little" "32" "objdump" "objcopy" "cc" "ld" "nm" "" "" "1" "/tmp
   /selfgz1981/NVIDIA-Linux-x86-260.19.12/kernel/nv-vm.o";
     cc -Wp,-MD,/tmp/selfgz1981/NVIDIA-Linux-x86-260.19.12/kernel/.os-agp.o.d  
   -nostdinc -isystem /usr/lib/gcc/i686-linux-gnu/4.4.5/include  -I/usr/src/lin
   ux-headers-2.6.35-22-generic/arch/x86/include -Iinclude  -include include/ge
   nerated/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-pro
   totypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-fun
   ction-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -
   m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=
   2 -march=i686 -mtune=generic -maccumulate-outgoing-args -Wa,-mtune=generic32
   -ffreestanding -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_
   CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -pipe -Wno-sign-compare -fno-a
   synchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-lar
   ger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdecl
   aration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-st
   ack -I/tmp/selfgz1981/NVIDIA-Linux-x86-260.19.12/kernel -Wall -MD -Wsign-com
   pare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STR
   ING=\"260.19.12\" -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE -D"KBUILD_STR(s)=#s" -
   D"KBUILD_BASENAME=KBUILD_STR(os_agp)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)"
    -c -o /tmp/selfgz1981/NVIDIA-Linux-x86-260.19.12/kernel/.tmp_os-agp.o /tmp/
   selfgz1981/NVIDIA-Linux-x86-260.19.12/kernel/os-agp.c
   In file included from include/linux/kernel.h:17,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz1981/NVIDIA-Linux-x86-260.19.12/kernel/nv-l
   inux.h:27,
                    from /tmp/selfgz1981/NVIDIA-Linux-x86-260.19.12/kernel/os-a
   gp.c:24:
   include/linux/bitops.h: In function ‘hweight_long’:
   include/linux/bitops.h:49: warning: signed and unsigned type in conditional 
   expression
   In file included from /usr/src/linux-headers-2.6.35-22-generic/arch/x86/incl
   ude/asm/uaccess.h:571,
                    from include/linux/poll.h:14,
                    from /tmp/selfgz1981/NVIDIA-Linux-x86-260.19.12/kernel/nv-l
   inux.h:84,
                    from /tmp/selfgz1981/NVIDIA-Linux-x86-260.19.12/kernel/os-a
   gp.c:24:
   /usr/src/linux-headers-2.6.35-22-generic/arch/x86/include/asm/uaccess_32.h: 
   In function ‘copy_from_user’:
   /usr/src/linux-headers-2.6.35-22-generic/arch/x86/include/asm/uaccess_32.h:2
   09: warning: comparison between signed and unsigned integer expressions
     set -e ; perl /usr/src/linux-headers-2.6.35-22-generic/scripts/recordmcoun
   t.pl "i386" "little" "32" "objdump" "objcopy" "cc" "ld" "nm" "" "" "1" "/tmp
   /selfgz1981/NVIDIA-Linux-x86-260.19.12/kernel/os-agp.o";
     cc -Wp,-MD,/tmp/selfgz1981/NVIDIA-Linux-x86-260.19.12/kernel/.os-interface
   .o.d  -nostdinc -isystem /usr/lib/gcc/i686-linux-gnu/4.4.5/include  -I/usr/s
   rc/linux-headers-2.6.35-22-generic/arch/x86/include -Iinclude  -include incl
   ude/generated/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstri
   ct-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implic
   it-function-declaration -Wno-format-security -fno-delete-null-pointer-checks
   -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boun
   dary=2 -march=i686 -mtune=generic -maccumulate-outgoing-args -Wa,-mtune=gene
   ric32 -ffreestanding -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIG
   NAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -pipe -Wno-sign-compare -fno-asynchro
   nous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-tha
   n=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration
   -after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -I/
   tmp/selfgz1981/NVIDIA-Linux-x86-260.19.12/kernel -Wall -MD -Wsign-compare -W
   no-cast-qual -Wno-err
   or -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"260.19.12\" -UDEBUG -U
   _DEBUG -DNDEBUG  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR
   (os_interface)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)"  -c -o /tmp/selfgz198
   1/NVIDIA-Linux-x86-260.19.12/kernel/.tmp_os-interface.o /tmp/selfgz1981/NVID
   IA-Linux-x86-260.19.12/kernel/os-interface.c
   In file included from include/linux/kernel.h:17,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz1981/NVIDIA-Linux-x86-260.19.12/kernel/nv-l
   inux.h:27,
                    from /tmp/selfgz1981/NVIDIA-Linux-x86-260.19.12/kernel/os-i
   nterface.c:26:
   include/linux/bitops.h: In function ‘hweight_long’:
   include/linux/bitops.h:49: warning: signed and unsigned type in conditional 
   expression
   In file included from /usr/src/linux-headers-2.6.35-22-generic/arch/x86/incl
   ude/asm/uaccess.h:571,
                    from include/linux/poll.h:14,
                    from /tmp/selfgz1981/NVIDIA-Linux-x86-260.19.12/kernel/nv-l
   inux.h:84,
                    from /tmp/selfgz1981/NVIDIA-Linux-x86-260.19.12/kernel/os-i
   nterface.c:26:
   /usr/src/linux-headers-2.6.35-22-generic/arch/x86/include/asm/uaccess_32.h: 
   In function ‘copy_from_user’:
   /usr/src/linux-headers-2.6.35-22-generic/arch/x86/include/asm/uaccess_32.h:2
   09: warning: comparison between signed and unsigned integer expressions
     set -e ; perl /usr/src/linux-headers-2.6.35-22-generic/scripts/recordmcoun
   t.pl "i386" "little" "32" "objdump" "objcopy" "cc" "ld" "nm" "" "" "1" "/tmp
   /selfgz1981/NVIDIA-Linux-x86-260.19.12/kernel/os-interface.o";
     cc -Wp,-MD,/tmp/selfgz1981/NVIDIA-Linux-x86-260.19.12/kernel/.os-registry.
   o.d  -nostdinc -isystem /usr/lib/gcc/i686-linux-gnu/4.4.5/include  -I/usr/sr
   c/linux-headers-2.6.35-22-generic/arch/x86/include -Iinclude  -include inclu
   de/generated/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstric
   t-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implici
   t-function-declaration -Wno-format-security -fno-delet
   e-null-pointer-checks -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return 
   -mpreferred-stack-boundary=2 -march=i686 -mtune=generic -maccumulate-outgoin
   g-args -Wa,-mtune=generic32 -ffreestanding -fstack-protector -DCONFIG_AS_CFI
   =1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -pipe -Wno-sign
   -compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3d
   now -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-c
   alls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflo
   w -fconserve-stack -I/tmp/selfgz1981/NVIDIA-Linux-x86-260.19.12/kernel -Wall
   -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -D
   NV_VERSION_STRING=\"260.19.12\" -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE -D"KBUIL
   D_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(os_registry)"  -D"KBUILD_MODNAME=
   KBUILD_STR(nvidia)"  -c -o /tmp/selfgz1981/NVIDIA-Linux-x86-260.19.12/kernel
   /.tmp_os-registry.o /tmp/selfgz1981/NVIDIA-Linux-x86-260.19.12/kernel/os-reg
   istry.c
   In file included from include/linux/kernel.h:17,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz1981/NVIDIA-Linux-x86-260.19.12/kernel/nv-l
   inux.h:27,
                    from /tmp/selfgz1981/NVIDIA-Linux-x86-260.19.12/kernel/os-r
   egistry.c:15:
   include/linux/bitops.h: In function ‘hweight_long’:
   include/linux/bitops.h:49: warning: signed and unsigned type in conditional 
   expression
   In file included from /usr/src/linux-headers-2.6.35-22-generic/arch/x86/incl
   ude/asm/uaccess.h:571,
                    from include/linux/poll.h:14,
                    from /tmp/selfgz1981/NVIDIA-Linux-x86-260.19.12/kernel/nv-l
   inux.h:84,
                    from /tmp/selfgz1981/NVIDIA-Linux-x86-260.19.12/kernel/os-r
   egistry.c:15:
   /usr/src/linux-headers-2.6.35-22-generic/arch/x86/include/asm/uaccess_32.h: 
   In function ‘copy_from_user’:
   /usr/src/linux-headers-2.6.35-22-generic/arch/x86/include/asm/uaccess_32.h:2
   09: warning: comparison between signed and unsigned integer expressions
     set -e ; perl /usr/src/linux-headers-2.6.35-22-generic/scripts/recordmcoun
   t.pl "i386" "little" "32" "objdump" "objcopy" "cc" "ld" "nm" "" "" "1" "/tmp
   /selfgz1981/NVIDIA-Linux-x86-260.19.12/kernel/os-registry.o";
     cc -Wp,-MD,/tmp/selfgz1981/NVIDIA-Linux-x86-260.19.12/kernel/.nv-i2c.o.d  
   -nostdinc -isystem /usr/lib/gcc/i686-linux-gnu/4.4.5/include  -I/usr/src/lin
   ux-headers-2.6.35-22-generic/arch/x86/include -Iinclude  -include include/ge
   nerated/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-pro
   totypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-fun
   ction-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -
   m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=
   2 -march=i686 -mtune=generic -maccumulate-outgoing-args -Wa,-mtune=generic32
   -ffreestanding -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FR
   AME=1 -DCONFIG_AS_CFI_SECTIONS=1 -pipe -Wno-sign-compare -fno-asynchronous-u
   nwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow 
   -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls
   -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fc
   onserve-stack -I/tmp/selfgz1981/NVIDIA-Linux-x86-260.19.12/kernel -Wall -MD 
   -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_V
   ERSION_STRING=\"260.19.12\" -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE -D"KBUILD_ST
   R(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_i2c)"  -D"KBUILD_MODNAME=KBUILD_ST
   R(nvidia)"  -c -o /tmp/selfgz1981/NVIDIA-Linux-x86-260.19.12/kernel/.tmp_nv-
   i2c.o /tmp/selfgz1981/NVIDIA-Linux-x86-260.19.12/kernel/nv-i2c.c
   In file included from include/linux/kernel.h:17,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz1981/NVIDIA-Linux-x86-260.19.12/kernel/nv-l
   inux.h:27,
                    from /tmp/selfgz1981/NVIDIA-Linux-x86-260.19.12/kernel/nv-i
   2c.c:8:
   include/linux/bitops.h: In function ‘hweight_long’:
   include/linux/bitops.h:49: warning: signed and unsigned type in conditional 
   expression
   In file included from /usr/src/linux-headers-2.6.35-22-generic/arch/x86/incl
   ude/asm/uaccess.h:571,
                    from include/linux/poll.h:14,
                    from /tmp/selfgz1981/NVIDIA-Linux-x86-260.19.12/kernel/nv-l
   inux.h:84,
                    from /tmp/selfgz1981/NVIDIA-Linux-x86-260.19.12/kernel/nv-i
   2c.c:8:
   /usr/src/linux-headers-2.6.35-22-generic/arch/x86/include/asm/uaccess_32.h: 
   In function ‘copy_from_user’:
   /usr/src/linux-headers-2.6.35-22-generic/arch/x86/include/asm/uaccess_32.h:2
   09: warning: comparison between signed and unsigned integer expressions
     set -e ; perl /usr/src/linux-headers-2.6.35-22-generic/scripts/recordmcoun
   t.pl "i386" "little" "32" "objdump" "objcopy" "cc" "ld" "nm" "" "" "1" "/tmp
   /selfgz1981/NVIDIA-Linux-x86-260.19.12/kernel/nv-i2c.o";
     cc -Wp,-MD,/tmp/selfgz1981/NVIDIA-Linux-x86-260.19.12/kernel/.nvacpi.o.d  
   -nostdinc -isystem /usr/lib/gcc/i686-linux-gnu/4.4.5/include  -I/usr/src/lin
   ux-headers-2.6.35-22-generic/arch/x86/include -Iinclude  -include include/ge
   nerated/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-pro
   totypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-fun
   ction-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -
   m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=
   2 -march=i686 -mtune=generic -maccumulate-outgoing-args -Wa,-mtune=generic32
   -ffreestanding -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FR
   AME=1 -DCONFIG_AS_CFI_SECTIONS=1 -pipe -Wno-sign-compare -fno-asynchronous-u
   nwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024
   -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-
   statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -I/tmp/sel
   fgz1981/NVIDIA-Linux-x86-260.19.12/kernel -Wall -MD -Wsign-compare -Wno-cast
   -qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"260.19.1
   2\" -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASEN
   AME=KBUILD_
   STR(nvacpi)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)"  -c -o /tmp/selfgz1981/N
   VIDIA-Linux-x86-260.19.12/kernel/.tmp_nvacpi.o /tmp/selfgz1981/NVIDIA-Linux-
   x86-260.19.12/kernel/nvacpi.c
   In file included from include/linux/kernel.h:17,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz1981/NVIDIA-Linux-x86-260.19.12/kernel/nv-l
   inux.h:27,
                    from /tmp/selfgz1981/NVIDIA-Linux-x86-260.19.12/kernel/nvac
   pi.c:15:
   include/linux/bitops.h: In function ‘hweight_long’:
   include/linux/bitops.h:49: warning: signed and unsigned type in conditional 
   expression
   In file included from /usr/src/linux-headers-2.6.35-22-generic/arch/x86/incl
   ude/asm/uaccess.h:571,
                    from include/linux/poll.h:14,
                    from /tmp/selfgz1981/NVIDIA-Linux-x86-260.19.12/kernel/nv-l
   inux.h:84,
                    from /tmp/selfgz1981/NVIDIA-Linux-x86-260.19.12/kernel/nvac
   pi.c:15:
   /usr/src/linux-headers-2.6.35-22-generic/arch/x86/include/asm/uaccess_32.h: 
   In function ‘copy_from_user’:
   /usr/src/linux-headers-2.6.35-22-generic/arch/x86/include/asm/uaccess_32.h:2
   09: warning: comparison between signed and unsigned integer expressions
     set -e ; perl /usr/src/linux-headers-2.6.35-22-generic/scripts/recordmcoun
   t.pl "i386" "little" "32" "objdump" "objcopy" "cc" "ld" "nm" "" "" "1" "/tmp
   /selfgz1981/NVIDIA-Linux-x86-260.19.12/kernel/nvacpi.o";
     ld -m elf_i386   -r -o /tmp/selfgz1981/NVIDIA-Linux-x86-260.19.12/kernel/n
   vidia.o /tmp/selfgz1981/NVIDIA-Linux-x86-260.19.12/kernel/nv-kernel.o /tmp/s
   elfgz1981/NVIDIA-Linux-x86-260.19.12/kernel/nv.o /tmp/selfgz1981/NVIDIA-Linu
   x-x86-260.19.12/kernel/nv_gvi.o /tmp/selfgz1981/NVIDIA-Linux-x86-260.19.12/k
   ernel/nv-vm.o /tmp/selfgz1981/NVIDIA-Linux-x86-260.19.12/kernel/os-agp.o /tm
   p/selfgz1981/NVIDIA-Linux-x86-260.19.12/kernel/os-interface.o /tmp/selfgz198
   1/NVIDIA-Linux-x86-260.19.12/kernel/os-registry.o /tmp/selfgz1981/NVIDIA-Lin
   ux-x86-260.19.12/kernel/nv-i2c.o /tmp/selfgz1981/NVIDIA-Linux-x86-260.19.12/
   kernel/nvac
   pi.o 
   (cat /dev/null;   echo kernel//tmp/selfgz1981/NVIDIA-Linux-x86-260.19.12/ker
   nel/nvidia.ko;) > /tmp/selfgz1981/NVIDIA-Linux-x86-260.19.12/kernel/modules.
   order
   make -f /usr/src/linux-headers-2.6.35-22-generic/scripts/Makefile.modpost
     scripts/mod/modpost -m -a -i /usr/src/linux-headers-2.6.35-22-generic/Modu
   le.symvers -I /tmp/selfgz1981/NVIDIA-Linux-x86-260.19.12/kernel/Module.symve
   rs  -o /tmp/selfgz1981/NVIDIA-Linux-x86-260.19.12/kernel/Module.symvers -S -
   w  -s
   WARNING: could not find /tmp/selfgz1981/NVIDIA-Linux-x86-260.19.12/kernel/.n
   v-kernel.o.cmd for /tmp/selfgz1981/NVIDIA-Linux-x86-260.19.12/kernel/nv-kern
   el.o
     cc -Wp,-MD,/tmp/selfgz1981/NVIDIA-Linux-x86-260.19.12/kernel/.nvidia.mod.o
   .d  -nostdinc -isystem /usr/lib/gcc/i686-linux-gnu/4.4.5/include  -I/usr/src
   /linux-headers-2.6.35-22-generic/arch/x86/include -Iinclude  -include includ
   e/generated/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict
   -prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit
   -function-decla
   ration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m32 -msoft-
   float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i6
   86 -mtune=generic -maccumulate-outgoing-args -Wa,-mtune=generic32 -ffreestan
   ding -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCO
   NFIG_AS_CFI_SECTIONS=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tabl
   es -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit
   -frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement
   -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -I/tmp/selfgz1981/NV
   IDIA-Linux-x86-260.19.12/kernel -Wall -MD -Wsign-compare -Wno-cast-qual -Wno
   -error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"260.19.12\" -UDEBU
   G -U_DEBUG -DNDEBUG  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nvid
   ia.mod)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)"  -DMODULE -c -o /tmp/selfgz1
   981/NVIDIA-Linux-x86-260.19.12/kernel/nvidia.mod.o /tmp/selfgz1981/NVIDIA-Li
   nux-x86-260.19.12/kernel/nvidia.mod
   .c
   In file included from include/linux/kernel.h:17,
                    from /usr/src/linux-headers-2.6.35-22-generic/arch/x86/incl
   ude/asm/percpu.h:44,
                    from /usr/src/linux-headers-2.6.35-22-generic/arch/x86/incl
   ude/asm/current.h:5,
                    from /usr/src/linux-headers-2.6.35-22-generic/arch/x86/incl
   ude/asm/processor.h:15,
                    from include/linux/prefetch.h:14,
                    from include/linux/list.h:6,
                    from include/linux/module.h:9,
                    from /tmp/selfgz1981/NVIDIA-Linux-x86-260.19.12/kernel/nvid
   ia.mod.c:1:
   include/linux/bitops.h: In function ‘hweight_long’:
   include/linux/bitops.h:49: warning: signed and unsigned type in conditional 
   expression
     ld -r -m elf_i386 -T /usr/src/linux-headers-2.6.35-22-generic/scripts/modu
   le-common.lds --build-id -o /tmp/selfgz1981/NVIDIA-Linux-x86-260.19.12/kerne
   l/nvidia.ko /tmp/selfgz1981/NVIDIA-Linux-x86-260.19.12/kernel/nvidia.o /tmp/
   selfgz1981/NVIDIA-Linux-x86-260.19.12/kernel/nvidia.mod.o
   NVIDIA: left KBUILD.
-> done.
-> Kernel module compilation complete.
ERROR: Unable to load the kernel module 'nvidia.ko'.  This happens most
       frequently when this kernel module was built against the wrong or
       improperly configured kernel sources, with a version of gcc that differs
       from the one used to build the target kernel, or if a driver such as
       rivafb, nvidiafb, or nouveau is present and prevents the NVIDIA kernel
       module from obtaining ownership of the NVIDIA graphics device(s), or
       NVIDIA GPU installed in this system is not supported by this NVIDIA
       Linux graphics driver release.
       
       Please see the log entries 'Kernel module load error' and 'Kernel
       messages' at the end of the file '/var/log/nvidia-installer.log' for
       more information.
-> Kernel module load error: insmod: error inserting './kernel/nvidia.ko': -1
   Cannot allocate memory
-> Kernel messages:
   [   15.292046] hda_codec: ALC888: SKU not ready 0x411111f0
   [   15.300032] hda_codec: ALC888: BIOS auto-probing.
   [   15.743679] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
   [   16.044706] cx18-0 843: loaded v4l-cx23418-dig.fw firmware (16382 bytes)
   [   16.064985] cx18-0 843: verified load of v4l-cx23418-dig.fw firmware
   (16382 bytes)
   [   16.115723] ppdev: user-space parallel port driver
   [   16.304570] Linux agpgart interface v0.103
   [   16.327148] [drm] Initialized drm 1.1.0 20060810
   [   16.360871] ACPI: PCI Interrupt Link [APC5] enabled at IRQ 16
   [   16.360879]   alloc irq_desc for 16 on node -1
   [   16.360881]   alloc kstat_irqs on node -1
   [   16.360893] nouveau 0000:02:00.0: PCI INT A -> Link[APC5] -> GSI 16
   (level, low) -> IRQ 16
   [   16.360899] nouveau 0000:02:00.0: setting latency timer to 64
   [   16.365128] [drm] nouveau 0000:02:00.0: Detected an NV50 generation card
   (0x086400a2)
   [   16.369157] [drm] nouveau 0000:02:00.0: Failed to PRAMIN BAR
   [   16.370269] nouveau 0000:02:00.0: PCI INT A disabled
   [   16.370281] nouveau: probe of 0000:02:00.0 failed with error -12
   [   16.386356] usb 1-4: usbfs: interface 1 claimed by usblp while 'usb' sets
   config #1
   [   16.905149] mtrr: base(0xf9000000) is not aligned on a size(0xe00000)
   boundary
   [   18.746661] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
   [   25.281020] eth0: no IPv6 routers present
   [   76.504023] Clocksource tsc unstable (delta = -77409520 ns)
   [  255.703632] mtrr: no MTRR for f9000000,e00000 found
   [  313.955982] alloc_vmap_area: 10 callbacks suppressed
   [  313.955986] vmap allocation for size 9334784 failed: use vmalloc=<size>
   to increase size.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com).

---

### Post by claven123 on 2010-10-27
Quote:
Originally Posted by **claven123** [[IMG]http://www.nvnews.net/vbulletin/images/buttons/viewpost.gif[/IMG]]("http://www.nvnews.net/vbulletin/showthread.php?p=2337540#post2337540") 
*vmap allocation for size 9334784 failed: use vmalloc=<size> to increase size.*

This is a 32-bit memory limitation issue. Your options are to use 64-bit if your system supports it or increase vmalloc. The README explains this problem and how to fix it: [[COLOR=#0000dd]http://us.download.nvidia.com/XFree8...kva_exhaustion[/COLOR]]("http://us.download.nvidia.com/XFree8...kva_exhaustion")
 
 
Does this sound like a good idea?  I have to edit the grub to increase the size of my vmalloc....

---

### Post by pytheas22 on 2010-10-27
**claven123**: thanks for the output.  It looks like the nvidia.ko module built without issue, so the vmalloc error mentioned in your dmesg output is probably the issue (though it's hard to say with certainty because the nvidia module is not too verbose about why it can't load).  I would definitely try changing the vmalloc allocation using the instructions you found--to which the link is corrupted, by the way, but if I recall correctly, you just need to change one of the boot parameters, which should be easy to do by editing /etc/default/grub.  If you need help let me know.

**d3v1150m471c**: yes, it's a little-known feature that can come in handy sometimes.  Basically:
```

sudo aptitude hold name_of_package
```

is the syntax, although there are other approaches outlined [here]("http://www.debianadmin.com/how-to-prevent-a-package-from-being-updated-in-debian.html").  I think there's also a way to do it graphically using Synaptic Package Manager but I'm not sure.

---

### Post by claven123 on 2010-10-27
[http://us.download.nvidia.com/XFree86/Linux-x86/169.12/README/chapter-09.html](http://us.download.nvidia.com/XFree86/Linux-x86/169.12/README/chapter-09.html)
 
Chpt 9, then this heading:  Kernel virtual address space exhaustion on the X86 platform 
 
Thanks, will do this tonight.
 
Question....  I update the grub and I can't boot the machine.... then what.  I guess I need to get to the tty, and then edit the grub2 back to the original setting...
 
 
 
I wonder why this is an issue and why it's not corrected on the kernel or nvidia developers....
 
Is this the fix for all the others who are having the same issues with ubuntu 10.10 and nvidia drivers....

---

### Post by d3v1150m471c on 2010-10-28
pytheas, that's an excellent tool. thanks for that.

---

### Post by pytheas22 on 2010-10-28
> [http://us.download.nvidia.com/XFree8...hapter-09.html](http://us.download.nvidia.com/XFree8...hapter-09.html)

Chpt 9, then this heading: Kernel virtual address space exhaustion on the X86 platform

Thanks, will do this tonight.

Question.... I update the grub and I can't boot the machine.... then what. I guess I need to get to the tty, and then edit the grub2 back to the original setting...


Unfortunately, if screwing with grub renders your system unbootable, you won't even be able to get into a fullscreen terminal because you won't be able to boot at all.  So to be safe from grub errors, you should back up your /boot/grub and /etc/grub.d directories before playing with grub.  If something goes wrong, you'll be able to boot to a live CD and restore your grub configuration from the back up.

> I wonder why this is an issue and why it's not corrected on the kernel or nvidia developers....

The kernel people would say they can't be responsible because Nvidia's driver is closed-source, so even if they wanted to fix the problem, they can't without access to the code.

Nvidia probably would reply that it can't support every possible Linux configuration, because there are too many of them and they are not regulated by anyone, so you shouldn't use the latest kernel if it causes problems with whichever driver Nvidia makes available.

Then some kernel developer would reiterate that if only Nvidia would open up its code, there would be no more war or poverty or buggy software.

This is why the open-source world is so fun :)

> Is this the fix for all the others who are having the same issues with ubuntu 10.10 and nvidia drivers....

I'm not sure, honestly.  Since I don't have Nvidia I haven't followed this issue too closely.  But it certainly looks from your dmesg output like the vmalloc bit is your problem.  I'm not sure if that's also at the root of other people's problems.

---

