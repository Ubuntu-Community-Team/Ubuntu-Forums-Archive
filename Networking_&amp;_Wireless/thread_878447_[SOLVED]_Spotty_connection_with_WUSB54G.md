---
title: "[SOLVED] Spotty connection with WUSB54G"
date: 2008-08-02
forum: Networking &amp; Wireless
---

### Post by xchecker on 2008-08-02
On a new box running Edubuntu 8.04 I have a Linksys WUSB54G v4 adapter connecting wirelessly to a WRT54G v4 Router.  At first it worked practically out of the box as the installed rt2500usb driver seemed to work fine with this hardware.  But after a day or two we lost connection to the network, then it reappeared by itself but ran very slowly.  Today it comes and goes, sometimes at good speed sometimes it can't find a server.  My browser is Firefox 3.0.1.

Here's some info from the terminal:

```

crichmond@brichmond-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"linksys"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:14:BF:16:FC:66   
          Bit Rate=1 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=72/100  Signal level=-44 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

crichmond@brichmond-desktop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:12:17:72:e9:26
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.101 multicast=yes wireless=IEEE 802.11g
crichmond@brichmond-desktop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

```

Suggestions?

---

### Post by xchecker on 2008-08-05
Anyone, please?

---

### Post by liquoredolce on 2008-08-06
I'm having the same problem so I'm bumping this to the top :)

---

### Post by beameup on 2008-08-06
Not going to be much help, but AFAIK this adapter wasn't supported at all by any Linux distro in the past. I just used one when i was reinstalling XP / Ubuntu on my daughters PC and was surprised when Ubuntu 8.04 picked it up without any effort, I never used it extensively, just for a few days but never had any issues with it. I presume y'all have unplugged and replugged it already, let it refind it?

---

### Post by xchecker on 2008-08-11
Various threads and personal trial and error have led me to conclude the default rt2500usb driver in Ubuntu is not reliable with this adapter, so I installed ndiswrapper and the driver from Linksys.

So far it seems to be working fine now.  Anyone using this adapter I recommend going this route even if the default driver seems to work OK at first.

---

