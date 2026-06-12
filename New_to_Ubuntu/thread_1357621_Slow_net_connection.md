---
title: "Slow net connection"
date: 2009-12-17
forum: New to Ubuntu
---

### Post by nancy143 on 2009-12-17
I'm back again I still have a problem with an unstable wireless internet connection it works fine when I start up but slows down after a few minutes I have been looking around and I found this  I am using a 32 bit version of Ubuntu and the dirver I have seems to be 64 bit this is what I have found

*-network
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:0e:00.0
       logical name: wmaster0
       version: 01
       serial: 00:1b:9e:87:2d:a1
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k ip=192.168.1.106 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:18 memory:f8200000-f820ffff

can anyone tell me if this is for 64 bit and if it is does anyone have simple directions for a beginner to follow to corect it

---

### Post by nancy143 on 2009-12-17
I'm back again I still have a problem with an unstable wireless internet connection it works fine when I start up but slows down after a few minutes I have been looking around and I found this  I am using a 32 bit version of Ubuntu and the dirver I have seems to be 64 bit this is what I have found

*-network
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:0e:00.0
       logical name: wmaster0
       version: 01
       serial: 00:1b:9e:87:2d:a1
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k ip=192.168.1.106 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:18 memory:f8200000-f820ffff

can anyone tell me if this is for 64 bit and if it is does anyone have simple directions for a beginner to follow to correct it

---

### Post by swoody on 2009-12-17
That 64bit note seems to be referring to your hardware, not the driver itself. When you run 'lshw' you should be able to see whether other devices are listed as 32 or 64 bit width as well.

Therefore, I don't think this is the cause of your slow connection. Can you provide us with a bit more info about your system (i.e. Ubuntu version, wireless encryption, etc.)? Also, have you tried this on another network to rule out any issues with your modem/router? Has any other device had the same issue on this network?

---

### Post by cariboo on 2009-12-17
If you are using a 32-bit version, a 64-bit driver won't install, so that is not your problem. Have you checked dmesg to see if anything sticks out. You can view dmesg two ways. Go to System-->Administration-->Log File Viewer, or open a terminal and type:

```
dmesg | grep wlan0
```

---

### Post by nancy143 on 2009-12-17
I did what you said and I got this
[   16.809482] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   43.689563] wlan0: authenticate with AP 00:21:29:9f:7c:aa
[   43.888041] wlan0: authenticate with AP 00:21:29:9f:7c:aa
[   43.921334] wlan0: authenticated
[   43.921337] wlan0: associate with AP 00:21:29:9f:7c:aa
[   43.936659] wlan0: RX AssocResp from 00:21:29:9f:7c:aa (capab=0x411 status=0 aid=1)
[   43.936662] wlan0: associated
[   43.937279] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   54.144028] wlan0: no IPv6 routers present
frank@frank-laptop:~$

---

### Post by Sef on 2009-12-17
Double post, so merged threads.

---

### Post by nancy143 on 2009-12-17
I am using Ubuntu 9.10 I have a dual boot when I boot to Windows everthing works fine I not sure what you mean by the encryption Like I said when I boot to Ubuntu it works fine but it get slower and slower as time passes

---

