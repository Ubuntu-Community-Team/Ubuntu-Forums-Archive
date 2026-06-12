---
title: "network administration tool missing tab?"
date: 2010-08-25
forum: New to Ubuntu
---

### Post by anonomo on 2010-08-25
Hi absolutely new to linux just installed Ubuntu Studio 10.04 x64

unlike described in help files
"Network Administration Tool main window contains four tabbed sections
Connections - General - DNS - Hosts"

the connections tab is missing!!?

unlike described in Ubuntu Pocket GUide -
"Ubuntu’s NetworkManager apple that can be found at the top right of the desktop"
there is only blutooth symbol no network manager button

Also directly plugging in LAN cable doesn't auto connect to internet, as it does from windows.

Any clues?

Could having modified GRUB 'spash quiet' and replaced with 'nomodeset'
in order that my NVIDIA graphics display worked have caused a problem?
(thanks to this forum for solving that issue:D)

Using Intel 6000 series wireless driver - it looks like the driver for linux is pre-installed in the firmware library so guess thats not the problem.

[Vaio CW series i5 4GBram dual booting with windows 7 x64]

---

### Post by Peter09 on 2010-08-25
Can you post the out put of the two terminal commands
 
```
ifconfig
```
and
```
lshw -C network
```
 
also - after an install you should do an update to download any drivers that are required, have you done that?

---

### Post by anonomo on 2010-08-25
hi :KSpeter09!

interesting questions 

Q. ifconfig
A.
```
Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:80 errors:0 dropped:0 overruns:0 frame:0
          TX packets:80 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6080 (6.0 KB)  TX bytes:6080 (6.0 KB)
```


~$ lshw -C network

returns

```
WARNING: you should run this program as super-user.
  *-network DISABLED      
       description: Wireless interface
       product: WiFi Link 6000 Series
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 35
       serial: 00:23:14:46:70:cc
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:36 memory:e7a00000-e7a01fff
  *-network DISABLED
       description: Ethernet interface
       product: Marvell Technology Group Ltd.
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 10
       serial: 54:42:49:03:af:cc
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.25 firmware=N/A latency=0 multicast=yes
       resources: irq:34 memory:e5220000-e5223fff ioport:a000(size=256) memory:e5200000-e521ffff(prefetchable)

```

i'll leave it to you crew to understand this, THANKS WITH BIG LETTERS! 
i can just guess 'network DISABLED' is some kind of an issue ;)?

---

### Post by anonomo on 2010-08-25
also response to dineshs

iwconfig

returns

```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
pan0      no wireless extensions.
```

> also - after an install you should do an update to download any drivers that are required, have you done that? 	

- thats a bit of a catch 22 situation;) sorry no

---

### Post by dineshs on 2010-08-25
I do not know about ubuntu studio.I think it is better to  install Network manager.Restart ,right click NM icon and enable wired/wireless.You may also check BIOS setup
[http://ubuntuforums.org/showthread.php?t=1479788](http://ubuntuforums.org/showthread.php?t=1479788)

---

### Post by anonomo on 2010-08-25
wow thanks for the wisdoms

to go back to root with network, get install network manager
yes it works with:popcorn:! talking to you through Ubustudio now)

---

