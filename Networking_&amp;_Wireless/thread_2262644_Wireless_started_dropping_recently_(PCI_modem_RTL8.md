---
title: "Wireless started dropping recently (PCI modem RTL8188CE)"
date: 2015-01-26
forum: Networking &amp; Wireless
---

### Post by brendonwp on 2015-01-26
I fixed this problem in 12.04 by compiling the driver from the Realtek website.  When I moved to 14.04 last year there was no need as wireless worked fine out of the box to my surprise.  

In the last week or so the wireless has again started dropping after 5 minutes or so.  I have to disable the Realtek adapter to get my USB modem working.  I know that there is an informal update to the Realtek adapter: [http://askubuntu.com/questions/367587/unable-to-compile-realtek-rtl8188ce-driver-on-ubuntu-13-10](http://askubuntu.com/questions/367587/unable-to-compile-realtek-rtl8188ce-driver-on-ubuntu-13-10) This can break with any kernel update.

The output of the [wireless utility]("http://ubuntuforums.org/showthread.php?t=370108") is attached [ATTACH]259512[/ATTACH]

I have not run dist-upgrade to avoid breaking my system.  Would appreciate a work-around that only upgrades network-related components.

EDIT: Have run dist-upgrade now, and the system reported there was nothing that needed upgrading.

---

### Post by brendonwp on 2015-01-26
Here is the first part of wireless-info.txt:


```
cat wireless-info.txt | more

########## wireless info START ##########


Report from: 26 Jan 2015 15:31 SAST +0200


Booted last: 26 Jan 2015 14:59 SAST +0200


Script from: 20 Sep 2014 23:04 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty


##### kernel ############################


Linux 3.13.0-44-generic #73-Ubuntu SMP Tue Dec 16 00:22:43 UTC 2014 x86_64 x86_6
4 x86_64 GNU/Linux


Parameters: ro


##### desktop ###########################


Ubuntu


##### lspci #############################


00:19.0 Ethernet controller [0200]: Intel Corporation 82566DC Gigabit Network Co
nnection [8086:104b] (rev 02)
    Subsystem: Intel Corporation Device [8086:d701]
    Kernel driver in use: e1000e


03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802
.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
    Subsystem: ASUSTeK Computer Inc. Device [1043:84b5]
    Kernel driver in use: rtl8192ce


##### lsusb #############################


Bus 002 Device 005: ID 03f0:2b17 Hewlett-Packard LaserJet 1020
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 003: ID 046d:c31c Logitech, Inc. Keyboard K120 for Business
Bus 006 Device 002: ID 045e:0084 Microsoft Corp. Basic Optical Mouse
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


rtl8192ce              53550  0 
rtl_pci                26690  1 rtl8192ce
rt2800usb              27034  0 
rt2x00usb              20742  1 rt2800usb
rtlwifi                63475  2 rtl_pci,rtl8192ce
rt2800lib              89076  1 rt2800usb
rt2x00lib              55307  3 rt2x00usb,rt2800lib,rt2800usb
rtl8192c_common        53172  1 rtl8192ce
crc_ccitt              12707  1 rt2800lib
mac80211              630669  6 rtl_pci,rtlwifi,rt2x00lib,rt2x00usb,rt2800lib,rt
l8192ce
cfg80211              484040  3 mac80211,rtlwifi,rt2x00lib


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
          Interrupt:20 Memory:e3300000-e3320000 


wlan1     Link encap:Ethernet  HWaddr <MAC 'wlan1' [IF]>  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::f66d:4ff:fea1:4325/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7878 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10104 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5502494 (5.5 MB)  TX bytes:2095914 (2.0 MB)


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


wlan1     IEEE 802.11bgn  ESSID:"Cherwood X"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'Cherwood X' [AC
1]>   
          Bit Rate=150 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=48/70  Signal level=-62 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:3   Missed beacon:0


##### route #############################



```

---

### Post by brendonwp on 2015-01-27
Had a system error message  when I booted up today where the detailed report indicated that network-manager has crashed. Found the log file in /var/crash but cannot make head or tail of it. It is 2.1MB, but if someone here is interested I could post up to the core dump or else grep for a relevant term?

My system is a clean 14.04 install that is only a few months old.  The first screen of the log file follows:

```
sudo cat '/var/crash/_usr_sbin_NetworkManager.0.crash' | more
ProblemType: Crash
Architecture: amd64
Date: Mon Jan 26 20:52:03 2015
DistroRelease: Ubuntu 14.04
ExecutablePath: /usr/sbin/NetworkManager
ExecutableTimestamp: 1397057028
ProcCmdline: NetworkManager
ProcCwd: /
ProcEnviron:
 LANGUAGE=en_ZA:en
 TERM=linux
 PATH=(custom, no user)
 LANG=en_ZA.UTF-8
ProcMaps:
 00400000-0050c000 r-xp 00000000 08:17 391683                             /usr/sbin/NetworkManager
 0070c000-0070f000 r--p 0010c000 08:17 391683                             /usr/sbin/NetworkManager
 0070f000-00712000 rw-p 0010f000 08:17 391683                             /usr/sbin/NetworkManager
 00712000-00713000 rw-p 00000000 00:00 0 
 01c07000-01c28000 rw-p 00000000 00:00 0                                  [heap]
 01c28000-01cb2000 rw-p 00000000 00:00 0                                  [heap]
 7f8c5c000000-7f8c5c022000 rw-p 00000000 00:00 0 
 7f8c5c022000-7f8c60000000 ---p 00000000 00:00 0 
 7f8c60000000-7f8c60022000 rw-p 00000000 00:00 0 
 7f8c60022000-7f8c64000000 ---p 00000000 00:00 0 
 7f8c677ff000-7f8c67800000 ---p 00000000 00:00 0 
 7f8c67800000-7f8c68000000 rw-p 00000000 00:00 0                          [stack:895]
 7f8c68000000-7f8c68021000 rw-p 00000000 00:00 0 
 7f8c68021000-7f8c6c000000 ---p 00000000 00:00 0 
 7f8c6c663000-7f8c6c668000 r-xp 00000000 08:17 531209                     /usr/lib/x86_64-linux-gnu/NetworkManager/libnm-settings-plugin-ofono.so
 7f8c6c668000-7f8c6c868000 ---p 00005000 08:17 531209                     /usr/lib/x86_64-linux-gnu/NetworkManager/libnm-settings-plugin-ofono.so
 7f8c6c868000-7f8c6c869000 r--p 00005000 08:17 531209                     /usr/lib/x86_64-linux-gnu/NetworkManager/libnm-settings-plugin-ofono.so
 7f8c6c869000-7f8c6c86a000 rw-p 00006000 08:17 531209                     /usr/lib/x86_64-linux-gnu/NetworkManager/libnm-settings-plugin-ofono.so
 7f8c6c86a000-7f8c6c876000 r-xp 00000000 08:17 531208                     /usr/lib/x86_64-linux-gnu/NetworkManager/libnm-settings-plugin-ifupdown.so
 7f8c6c876000-7f8c6ca75000 ---p 0000c000 08:17 531208                     /usr/lib/x86_64-linux-gnu/NetworkManager/libnm-settings-plugin-ifupdown.so
 7f8c6ca75000-7f8c6ca76000 r--p 0000b000 08:17 531208                     /usr/lib/x86_64-linux-gnu/NetworkManager/libnm-settings-plugin-ifupdown.so
 

```

---

### Post by brendonwp on 2015-03-15
I compiled the updated Realtek driver linked in my first post.  That didn't help at the time.

The partition that /var was on filled up completely with the log file recently (over 3GB of files!).  After searching around a bit I decided that maybe my hardware was failing, so I ordered a new power supply (the existing one was over 5 years old and not adequate for my recent graphics card upgrade).

Having installed the new one, a Corsair CX430, my system is purring like a kitten and all the problems (including with my wireless card) have disappeared!

---

