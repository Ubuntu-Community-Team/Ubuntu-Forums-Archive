---
title: "No Wireless card"
date: 2018-11-19
forum: Networking &amp; Wireless
---

### Post by rarecaramels on 2018-11-19
Seems that my "new" Hp Compaq 6000 pro MT don`t have Network card. Is that true, or is that I`m a fool? (I wish will be the second option:D) hahaha

anyways... I attached the "wireles-info.txt.tar.gz" and this is the result of

```
inxi -Fx
```

```
System:    Host: Rocinante Kernel: 4.15.0-20-lowlatency i686           bits: 32 gcc: 7.3.0
           Desktop: Xfce 4.12.3 (Gtk 2.24.31) Distro: Ubuntu 18.04 LTS
Machine:   Device: desktop System: Hewlett-Packard product: HP Compaq 6000 Pro MT PC serial: N/A
           Mobo: Hewlett-Packard model: 3048h serial: N/A
           BIOS: Hewlett-Packard v: 786G2 v01.09 date: 08/25/2009
CPU:       Dual core Pentium E5500 (-MCP-) 
           arch: Penryn rev.10 cache: 2048 KB
           flags: (lm nx pae sse sse2 sse3 ssse3 vmx) bmips: 11172
           clock speeds: max: 2800 MHz 1: 1197 MHz 2: 1197 MHz
Graphics:  Card: Intel 4 Series Integrated Graphics Controller
           bus-ID: 00:02.0
           Display Server: x11 (X.Org 1.19.6 )
           drivers: modesetting (unloaded: fbdev,vesa)
           Resolution: 1024x768@60.00hz
           OpenGL: renderer: Mesa DRI Intel Q45/Q43 x86/MMX/SSE2
           version: 2.1 Mesa 18.0.0-rc5 Direct Render: Yes
Audio:     Card Intel 82801JD/DO (ICH10 Family) HD Audio Controller
           driver: snd_hda_intel bus-ID: 00:1b.0
           Sound: Advanced Linux Sound Architecture v: k4.15.0-20-lowlatency
Network:   Card: Intel 82567LM-3 Gigabit Network Connection
           driver: e1000e v: 3.2.6-k port: 1100 bus-ID: 00:19.0
           IF: enp0s25 state: down mac: 00:23:24:0d:bd:35
Drives:    HDD Total Size: 169.8GB (7.7% used)
           ID-1: /dev/sda model: WDC_WD1600JS size: 160.0GB
           ID-2: USB /dev/sdg model: WALKMAN size: 2.0GB
           ID-3: USB /dev/sdh model: USB_DISK_2.0 size: 7.8GB
Partition: ID-1: / size: 145G used: 9.1G (7%) fs: ext4 dev: /dev/dm-0
           ID-2: swap-1 size: 1.02GB used: 0.00GB (0%)
           fs: swap dev: /dev/dm-1
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 36.0C mobo: N/A
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 197 Uptime: 23 min Memory: 252.7/3935.1MB
           Init: systemd runlevel: 5 Gcc sys: N/A
           Client: Shell (bash 4.4.191) inxi: 2.3.56 



```


Hope this will help because I don`t see the Wifi Connecction option in the Network Manager, don`t have ethernet cable (or physical access to the modem; because the modem is in the first floor and I live in the second floor)  and badly want to use wifi. Thanks

---

