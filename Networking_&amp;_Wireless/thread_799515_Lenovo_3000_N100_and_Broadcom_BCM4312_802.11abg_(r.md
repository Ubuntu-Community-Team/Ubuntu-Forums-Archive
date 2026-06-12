---
title: "Lenovo 3000 N100 and Broadcom BCM4312 802.11a/b/g (rev 01)"
date: 2008-05-19
forum: Networking &amp; Wireless
---

### Post by Zlatan on 2008-05-19
Tried everything- nothing helps. Maybe I'm missing something? 
[http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)
did not help either. 
Please advise, if You are familiar with wireless.

---

### Post by Ayuthia on 2008-05-19
> **Zlatan said:**
> Tried everything- nothing helps. Maybe I'm missing something? 
[http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)
did not help either. 
Please advise, if You are familiar with wireless.

From the Terminal, can you post the results of the following:
```
lshw -C network
lsmod|grep -i -e b43 -e b43 legacy -e ssb -e b44 -e ndiswrapper
```

---

### Post by Zlatan on 2008-05-20
> **Ayuthia said:**
> From the Terminal, can you post the results of the following:
```
lshw -C network
lsmod|grep -i -e b43 -e b43 legacy -e ssb -e b44 -e ndiswrapper
```

thanks for the answer.
here's the output:
============
*-network               
       description: Wireless interface
       product: BCM4312 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 00:16:cf:79:1e:ca
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,03/23/2006, 4.40.1 latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11a
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:05:01.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:cc:01:b4
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=10.10.10.10 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
============
grep: legacy: No such file or directory
============
what do we do now?

---

### Post by Ayuthia on 2008-05-20
> **Zlatan said:**
> 
============
grep: legacy: No such file or directory
============
what do we do now?

I put a space between b43 and legacy by accident in the grep.  It should have been:
```
lsmod|grep -i -e b43 -e b43legacy -e ssb -e b44 -e ndiswrapper
```
From your post, it looks like ndiswrapper has loaded.  What does these items show:
```
ifconfig
iwconfig
sudo iwlist scan
```

---

### Post by Zlatan on 2008-05-20
> **Ayuthia said:**
> I put a space between b43 and legacy by accident in the grep.  It should have been:
```
lsmod|grep -i -e b43 -e b43legacy -e ssb -e b44 -e ndiswrapper
```

===
```
:~$ lsmod|grep -i -e b43 -e b43legacy -e ssb -e b44 -e ndiswrapper
b44                    28432  0 
ssb                    32260  1 b44
ndiswrapper           192920  0 
mii                     6400  3 b44,8139cp,8139too
usbcore               146028  5 ndiswrapper,usbhid,ehci_hcd,uhci_hcd

```
===

From your post, it looks like ndiswrapper has loaded.  What does these items show:
```
ifconfig
iwconfig
sudo iwlist scan
```


**ifconfig**
===
```
:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0f:b0:cc:01:b4  
          inet addr:192.168.1.65  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:b0ff:fecc:1b4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1214 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1189 errors:0 dropped:0 overruns:0 carrier:0
          collisions:17 txqueuelen:1000 
          RX bytes:802843 (784.0 KB)  TX bytes:159775 (156.0 KB)
          Interrupt:21 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1582 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1582 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:79100 (77.2 KB)  TX bytes:79100 (77.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:16:cf:79:1e:ca  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Memory:b0200000-b0204000 

```
===

**iwconfig**
===
```
:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11a  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
===

**sudo iwlist scan**
===
```
:~$ sudo iwlist scan
[sudo] password for laurynas: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results

```
===

does it help you?

---

### Post by Ayuthia on 2008-05-20
Ok.  From your lshw -C network information, it says that you have a Realtek ethernet card for your wired connection and it is using 8139too driver.  This means that b44 and ssb are not needed.  This means that the Hardy fix that was applied is not needed.

To start things out, let's clear out the modules and reload them:
```
sudo modprobe -r b44 ssb ndiswrapper
sudo depmod -ae
sudo modprobe ndiswrapper
sudo iwlist scan
```If we are still getting no scan results, please post the results of dmesg|grep ndiswrapper (from the Terminal).

---

### Post by Zlatan on 2008-05-20
> **Ayuthia said:**
> Ok.  From your lshw -C network information, it says that you have a Realtek ethernet card for your wired connection and it is using 8139too driver.  This means that b44 and ssb are not needed.  This means that the Hardy fix that was applied is not needed.

To start things out, let's clear out the modules and reload them:
```
sudo modprobe -r b44 ssb ndiswrapper
sudo depmod -ae
sudo modprobe ndiswrapper
sudo iwlist scan
```If we are still getting no scan results, please post the results of dmesg|grep ndiswrapper (from the Terminal).

===========
:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results
===========
:~$ dmesg|grep ndiswrapper
[   39.233350] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   39.324271] usbcore: registered new interface driver ndiswrapper
[   44.437813] usbcore: deregistering interface driver ndiswrapper
[   44.466367] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   44.614131] ndiswrapper: driver bcmwl5 (Broadcom,03/23/2006, 4.40.19.0) loaded
[   44.623060] ndiswrapper: using IRQ 16
[   44.832358] usbcore: registered new interface driver ndiswrapper
[ 2761.390672] ndiswrapper: device wlan0 removed
[ 2761.390845] usbcore: deregistering interface driver ndiswrapper
[ 2761.512591] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[ 2761.664915] ndiswrapper: driver bcmwl5 (Broadcom,03/23/2006, 4.40.19.0) loaded
[ 2761.673819] ndiswrapper: using IRQ 16
[ 2761.882691] usbcore: registered new interface driver ndiswrapper
===========

is it going any better?;)

---

### Post by Zlatan on 2008-05-20
By the way, System > Administration > Hardware Drivers is empty now, earlier it used to have a position for wireless, that did not work either. I suppose that thing is "blacklisted" now?

---

### Post by Ayuthia on 2008-05-20
> **Zlatan said:**
> By the way, System > Administration > Hardware Drivers is empty now, earlier it used to have a position for wireless, that did not work either. I suppose that thing is "blacklisted" now?

You can say that.  When you use ndiswrapper, the option disappears.

Can you now post this:
```
ls -l /etc/ndiswrapper/bcmwl5
lspci -nnm
```
I want to see if the links are in the right place.  We look close.  It looks like the driver might be the issue.

---

### Post by Zlatan on 2008-05-20
> **Ayuthia said:**
> You can say that.  When you use ndiswrapper, the option disappears.

Can you now post this:
```
ls -l /etc/ndiswrapper/bcmwl5
lspci -nnm
```
I want to see if the links are in the right place.  We look close.  It looks like the driver might be the issue.

===========

**ls -l /etc/ndiswrapper/bcmwl5**
```
total 1172
-rw-r--r-- 1 root root    922 2008-05-17 17:44 14E4:4311:1363:103C.5.conf
-rw-r--r-- 1 root root    922 2008-05-17 17:44 14E4:4311:1364:103C.5.conf
-rw-r--r-- 1 root root    922 2008-05-17 17:44 14E4:4311:1365:103C.5.conf
lrwxrwxrwx 1 root root     26 2008-05-17 17:44 14E4:4311.5.conf -> 14E4:4311:1363:103C.5.conf
-rw-r--r-- 1 root root    978 2008-05-17 17:44 14E4:4312:135F:103C.5.conf
-rw-r--r-- 1 root root    978 2008-05-17 17:44 14E4:4312:1360:103C.5.conf
-rw-r--r-- 1 root root    978 2008-05-17 17:44 14E4:4312:1361:103C.5.conf
-rw-r--r-- 1 root root    978 2008-05-17 17:44 14E4:4312:1362:103C.5.conf
lrwxrwxrwx 1 root root     26 2008-05-17 17:44 14E4:4312.5.conf -> 14E4:4312:135F:103C.5.conf
-rw-r--r-- 1 root root    918 2008-05-17 17:44 14E4:4318:1355:103C.5.conf
-rw-r--r-- 1 root root    918 2008-05-17 17:44 14E4:4318:1356:103C.5.conf
-rw-r--r-- 1 root root    918 2008-05-17 17:44 14E4:4318:1357:103C.5.conf
lrwxrwxrwx 1 root root     26 2008-05-17 17:44 14E4:4318.5.conf -> 14E4:4318:1355:103C.5.conf
-rw-r--r-- 1 root root    974 2008-05-17 17:44 14E4:4319:1358:103C.5.conf
-rw-r--r-- 1 root root    974 2008-05-17 17:44 14E4:4319:1359:103C.5.conf
-rw-r--r-- 1 root root    974 2008-05-17 17:44 14E4:4319:135A:103C.5.conf
lrwxrwxrwx 1 root root     26 2008-05-17 17:44 14E4:4319.5.conf -> 14E4:4319:1358:103C.5.conf
-rw-r--r-- 1 root root    918 2008-05-17 17:44 14E4:4320:00E7:0E11.5.conf
-rw-r--r-- 1 root root    941 2008-05-17 17:44 14E4:4320:12F4:103C.5.conf
-rw-r--r-- 1 root root    918 2008-05-17 17:44 14E4:4320:12F8:103C.5.conf
-rw-r--r-- 1 root root    918 2008-05-17 17:44 14E4:4320:12FA:103C.5.conf
-rw-r--r-- 1 root root    918 2008-05-17 17:44 14E4:4320:12FB:103C.5.conf
lrwxrwxrwx 1 root root     26 2008-05-17 17:44 14E4:4320.5.conf -> 14E4:4320:00E7:0E11.5.conf
-rw-r--r-- 1 root root    974 2008-05-17 17:44 14E4:4324:12F9:103C.5.conf
-rw-r--r-- 1 root root    974 2008-05-17 17:44 14E4:4324:12FC:103C.5.conf
lrwxrwxrwx 1 root root     26 2008-05-17 17:44 14E4:4324.5.conf -> 14E4:4324:12F9:103C.5.conf
-rw-r--r-- 1 root root 675862 2008-05-17 17:44 bcmwl5.inf
-rw-r--r-- 1 root root 429184 2008-05-17 17:44 bcmwl5.sys

```

**lspci -nnm**
```
00:00.0 "Host bridge [0600]" "Intel Corporation [8086]" "Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [27a0]" -r03 "Lenovo [17aa]" "Unknown device [2061]"
00:02.0 "VGA compatible controller [0300]" "Intel Corporation [8086]" "Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [27a2]" -r03 "Lenovo [17aa]" "Unknown device [2062]"
00:02.1 "Display controller [0380]" "Intel Corporation [8086]" "Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [27a6]" -r03 "Lenovo [17aa]" "Unknown device [2062]"
00:1b.0 "Audio device [0403]" "Intel Corporation [8086]" "82801G (ICH7 Family) High Definition Audio Controller [27d8]" -r02 "Lenovo [17aa]" "Unknown device [2066]"
00:1c.0 "PCI bridge [0604]" "Intel Corporation [8086]" "82801G (ICH7 Family) PCI Express Port 1 [27d0]" -r02 "" ""
00:1c.1 "PCI bridge [0604]" "Intel Corporation [8086]" "82801G (ICH7 Family) PCI Express Port 2 [27d2]" -r02 "" ""
00:1d.0 "USB Controller [0c03]" "Intel Corporation [8086]" "82801G (ICH7 Family) USB UHCI Controller #1 [27c8]" -r02 "Lenovo [17aa]" "Unknown device [206b]"
00:1d.1 "USB Controller [0c03]" "Intel Corporation [8086]" "82801G (ICH7 Family) USB UHCI Controller #2 [27c9]" -r02 "Lenovo [17aa]" "Unknown device [206c]"
00:1d.2 "USB Controller [0c03]" "Intel Corporation [8086]" "82801G (ICH7 Family) USB UHCI Controller #3 [27ca]" -r02 "Lenovo [17aa]" "Unknown device [206d]"
00:1d.3 "USB Controller [0c03]" "Intel Corporation [8086]" "82801G (ICH7 Family) USB UHCI Controller #4 [27cb]" -r02 "Lenovo [17aa]" "Unknown device [206e]"
00:1d.7 "USB Controller [0c03]" "Intel Corporation [8086]" "82801G (ICH7 Family) USB2 EHCI Controller [27cc]" -r02 -p20 "Lenovo [17aa]" "Unknown device [206f]"
00:1e.0 "PCI bridge [0604]" "Intel Corporation [8086]" "82801 Mobile PCI Bridge [2448]" -re2 -p01 "" ""
00:1f.0 "ISA bridge [0601]" "Intel Corporation [8086]" "82801GBM (ICH7-M) LPC Interface Bridge [27b9]" -r02 "Lenovo [17aa]" "Unknown device [2071]"
00:1f.2 "IDE interface [0101]" "Intel Corporation [8086]" "82801GBM/GHM (ICH7 Family) SATA IDE Controller [27c4]" -r02 -p80 "Lenovo [17aa]" "Unknown device [2072]"
00:1f.3 "SMBus [0c05]" "Intel Corporation [8086]" "82801G (ICH7 Family) SMBus Controller [27da]" -r02 "Lenovo [17aa]" "Unknown device [2073]"
03:00.0 "Network controller [0280]" "Broadcom Corporation [14e4]" "BCM4312 802.11a/b/g [4312]" -r01 "Broadcom Corporation [14e4]" "Unknown device [0466]"
05:01.0 "Ethernet controller [0200]" "Realtek Semiconductor Co., Ltd. [10ec]" "RTL-8139/8139C/8139C+ [8139]" -r10 "Lenovo [17aa]" "Unknown device [2074]"
05:04.0 "CardBus bridge [0607]" "ENE Technology Inc [1524]" "CB1410 Cardbus Controller [1410]" -r01 "Lenovo [17aa]" "Unknown device [2075]"
05:06.0 "FireWire (IEEE 1394) [0c00]" "Ricoh Co Ltd [1180]" "R5C832 IEEE 1394 Controller [0832]" -p10 "Lenovo [17aa]" "Unknown device [2076]"
05:06.1 "SD Host controller [0805]" "Ricoh Co Ltd [1180]" "R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [0822]" -r19 "Lenovo [17aa]" "Unknown device [2077]"
05:06.2 "System peripheral [0880]" "Ricoh Co Ltd [1180]" "R5C843 MMC Host Controller [0843]" -r0a "Lenovo [17aa]" "Unknown device [2079]"
05:06.3 "System peripheral [0880]" "Ricoh Co Ltd [1180]" "R5C592 Memory Stick Bus Host Adapter [0592]" -r05 "Lenovo [17aa]" "Unknown device [207a]"
05:06.4 "System peripheral [0880]" "Ricoh Co Ltd [1180]" "xD-Picture Card Controller [0852]" -rff -pff "" ""

```

I am sorry, will get back tomorrow, it is 23:30 here:) Thank you, I really appreciate your help;)

---

### Post by Ayuthia on 2008-05-20
> **Zlatan said:**
> 
I am sorry, will get back tomorrow, it is 23:30 here:) Thank you, I really appreciate your help;)
You might want to try another driver.  If you have a high-speed connection, you can try this link:
[http://www-307.ibm.com/pc/support/site.wss/license.do?filename=mobiles/63wb03ww.exe](http://www-307.ibm.com/pc/support/site.wss/license.do?filename=mobiles/63wb03ww.exe)

It is the XP driver from the Lenovo site.  The file is about 78Mb in size.

---

### Post by Zlatan on 2008-05-21
> **Ayuthia said:**
> You might want to try another driver.  If you have a high-speed connection, you can try this link:
[http://www-307.ibm.com/pc/support/site.wss/license.do?filename=mobiles/63wb03ww.exe](http://www-307.ibm.com/pc/support/site.wss/license.do?filename=mobiles/63wb03ww.exe)

It is the XP driver from the Lenovo site.  The file is about 78Mb in size.

How should I use it? It would be better with some clear step-by-step for me, or maybe there's some how-to already?

---

### Post by Ayuthia on 2008-05-21
> **Zlatan said:**
> How should I use it? It would be better with some clear step-by-step for me, or maybe there's some how-to already?
If you have an internet connection in Ubuntu:
```
cd
sudo aptitude install cabextract
wget -c http://www-307.ibm.com/pc/support/site.wss/license.do?filename=mobiles/63wb03ww.exe
```
Wait until the download is complete.
```
cabextract 63wb03ww.exe
```
This step will extract the files out of the .exe.  It should create a new folder.  I am going to guess that it is called 63wb03ww.  You will want to check and see if it is there:
```
ls -ltr
```This will list out the files with the newest files showing up last.  The last file should be a directory (the first character of the line will start with d).  If it does not, please stop and post your ls -ltr results.  So if it is called 63wb03ww:
```
cd 63wb03ww
sudo ndiswrapper -e bcmwl5
sudo ndiswrapper -i bcmwl5.inf
```
If there are no errors, continue.  If there are any messages that come up after running this command, please stop and post the message that you receive.  If all is ok:
```
sudo ndiswrapper -ma
sudo modprobe -r ndiswrapper
sudo depmod -ae
sudo modprobe ndiswrapper
```

---

### Post by Zlatan on 2008-05-22
```
cd 63wb03ww
sudo ndiswrapper -e bcmwl5
sudo ndiswrapper -i bcmwl5.inf
```
If there are no errors, continue.  If there are any messages that come up after running this command, please stop and post the message that you receive.  If all is ok:
```
sudo ndiswrapper -ma
sudo modprobe -r ndiswrapper
sudo depmod -ae
sudo modprobe ndiswrapper
```[/QUOTE]

epic example of help in ubuntu comunity!;)

there were some errors:

**sudo ndiswrapper -e bcmwl5**
```
sudo: unable to resolve host laurynas-laptop
```

**sudo ndiswrapper -i bcmwl5.inf**
```
sudo: unable to resolve host laurynas-laptop
```

waiting for your command, chief;)

---

### Post by Ayuthia on 2008-05-22
> **Zlatan said:**
> ```
cd 63wb03ww
sudo ndiswrapper -e bcmwl5
sudo ndiswrapper -i bcmwl5.inf
```
If there are no errors, continue.  If there are any messages that come up after running this command, please stop and post the message that you receive.  If all is ok:
```
sudo ndiswrapper -ma
sudo modprobe -r ndiswrapper
sudo depmod -ae
sudo modprobe ndiswrapper
```

epic example of help in ubuntu comunity!;)

there were some errors:

**sudo ndiswrapper -e bcmwl5**
```
sudo: unable to resolve host laurynas-laptop
```

**sudo ndiswrapper -i bcmwl5.inf**
```
sudo: unable to resolve host laurynas-laptop
```

waiting for your command, chief;)[/QUOTE]

Some people are running into a bug with sudo.  Please try out the workaround in post #4 of this link:
[http://ubuntuforums.org/showthread.php?t=723361](http://ubuntuforums.org/showthread.php?t=723361)

---

### Post by Zlatan on 2008-05-23
> **Ayuthia said:**
> epic example of help in ubuntu comunity!;)

there were some errors:

**sudo ndiswrapper -e bcmwl5**
```
sudo: unable to resolve host laurynas-laptop
```

**sudo ndiswrapper -i bcmwl5.inf**
```
sudo: unable to resolve host laurynas-laptop
```

waiting for your command, chief;)

Some people are running into a bug with sudo.  Please try out the workaround in post #4 of this link:
[http://ubuntuforums.org/showthread.php?t=723361](http://ubuntuforums.org/showthread.php?t=723361)[/QUOTE]


it wooooooooOOOOOOOOORKSSSSsssss!!!!!! i can see 5 unlocked wireless networks right now:D
i'm so grateful to you!:) have a nicest weekend!

---

### Post by Zlatan on 2008-06-04
BTW, will all this work with Kubuntu Hardy Heron KDE4?

---

### Post by Ayuthia on 2008-06-04
> **Zlatan said:**
> BTW, will all this work with Kubuntu Hardy Heron KDE4?
It should.  I am currently using KDE4 right now without any problems.

---

### Post by Zlatan on 2008-06-05
> **Ayuthia said:**
> It should.  I am currently using KDE4 right now without any problems.

YES. very good news:) have a good day, mate!

---

### Post by primitivling on 2011-11-01
> **Ayuthia said:**
> From the Terminal, can you post the results of the following:
```
lshw -C network
lsmod|grep -i -e b43 -e b43 legacy -e ssb -e b44 -e ndiswrapper
```
Hey, I have the same problem. I remember that it occured first after I installed Ubuntu 11.04 and that I fixed it somehow back then. Recently I kicked off everything and installed 11.10 and the wireless stopped working again. I am pretty bad with Ubuntu/ the terminal but managed to type in these two commands you asked for:

                   lshw -C network
    *-network UNCLAIMED     
         description: Network controller
         product: BCM4311 802.11b/g WLAN
         vendor: Broadcom Corporation
         physical id: 0
         bus info: pci@0000:03:00.0
         version: 01
         width: 32 bits
         clock: 33MHz
         capabilities: pm msi pciexpress bus_master cap_list
         configuration: latency=0
         resources: memory:d0000000-d0003fff
    *-network
         description: Ethernet interface
         product: RTL-8139/8139C/8139C+
         vendor: Realtek Semiconductor Co., Ltd.
         physical id: 1
         bus info: pci@0000:05:01.0
         logical name: eth0
         version: 10
         serial: 00:1b:38:08:80:0b
         size: 10Mbit/s
         capacity: 100Mbit/s
         width: 32 bits
         clock: 33MHz
         capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
         configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s
         resources: irq:21 ioport:2000(size=256) memory:d0100000-d01000ff


lsmod|grep -i -e b43 -e b43legacy -e ssb -e b44 -e ndiswrapper   did not return anything but went straight to the next line..


I'd be very grateful if you had some suggestions how to fix my wireless.

---

### Post by wildmanne39 on 2011-11-01
Hi, you should start your own thread this one is very old, I am going to ask a staff member to close it.
Thank you

---

### Post by coffeecat on 2011-11-01
> **wildmanne39 said:**
> Hi, you should start your own thread this one is very old,

Agreed. :)

@primitivling, the discussion in this thread would refer to now-obsolete versions of Ubuntu. Please start your own thread and provide the information you have posted here.

Good luck with that.

Thread closed.

---

