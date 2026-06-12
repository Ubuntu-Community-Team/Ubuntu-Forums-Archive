---
title: "No wireless networks detected in 10.04 with rtl8191SEVA2"
date: 2010-05-05
forum: New to Ubuntu
---

### Post by blckz28 on 2010-05-05
First off PLEASE be nice, I'm coming from Windows and I know very little about Linux but I'm just so board with windows and wanted something new to try.

Anyway I have a Toshiba Satellite T135D-S1325 laptop.  I installed Ubuntu 10.04 using the Windows installer.  Everything seems to be working except it will not find wireless networks.  The wlan is seen by Ubuntu.  Iwconfig shows:
wlan0     802.11bgn  Nickname:"rtl8191SEVA2"
          Mode:Managed  Frequency=2.457 GHz  Access Point: Not-Associated   
          Bit Rate:300 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=10/100  Signal level=0 dBm  Noise level=-100 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

I've tried both WPA and unsecured routers but neither would show in the network manager.  I've tried switching to Wicd with the same results. I've tried the Linux drivers suggested in this post [http://ubuntuforums.org/showthread.php?t=1267961&highlight=RTL8191SE-VA2&page=2#13](http://ubuntuforums.org/showthread.php?t=1267961&highlight=RTL8191SE-VA2&page=2#13).  

Before I had Ubuntu 10.04 installed I was on Ubuntu 9 and tried using ndiswrapper and the windows 7 drivers.  Using that setup it said the hardware was found but if I used iwconfig it said no interface found.  It was right after that that 10.04 was release so I just started fresh and re-installed Ubuntu.

Does anybody have any ideas?  Should I try ndiswrapper again?

Thanks

---

### Post by Peter09 on 2010-05-06
Can you post the output of the terminal command
 
```
lshw -C network
```

---

### Post by blckz28 on 2010-05-06
Here you go Peter:

WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: Atheros AR8132 / L1c Gigabit Ethernet Adapter
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: c0
       serial: 00:26:9e:9d:89:d0
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=atl1c driverversion=1.0.0.1-NAPI firmware=N/A ip=192.168.0.83 latency=0 multicast=yes
       resources: irq:27 memory:ce000000-ce03ffff ioport:1000(size=128)
  *-network
       description: Wireless interface
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: wlan0
       version: 10
       serial: 00:26:b6:75:b7:f5
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl819xSE driverversion=0014.0115.2010 firmware=62 latency=0 multicast=yes wireless=802.11bgn
       resources: irq:18 ioport:d000(size=256) memory:f0500000-f0503fff

Thanks for the help

---

### Post by Peter09 on 2010-05-06
this thread
[http://ubuntuforums.org/showthread.php?t=1267961&page=9](http://ubuntuforums.org/showthread.php?t=1267961&page=9)
seems to be discussing the same problems, most probably worth joining it.

---

### Post by blckz28 on 2010-05-06
Sweet, thanks Peter!

---

### Post by blckz28 on 2010-05-06
Great news, I just ran all the updates this morning and now I can see AND connect to all my wireless networks!

---

