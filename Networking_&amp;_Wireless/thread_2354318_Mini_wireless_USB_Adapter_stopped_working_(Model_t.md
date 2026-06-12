---
title: "Mini wireless USB Adapter stopped working (Model tl-wn823n TP-Link): Black screen"
date: 2017-03-01
forum: Networking &amp; Wireless
---

### Post by federicodemaria on 2017-03-01
Hi all, 
I'm using a desktop computer with Ubuntu 16.04 (Intel® Core™ i5-4460 CPU @ 3.20GHz × 4). 

For wifi connection, I used an USB adapter. After six months it stopped working. In fact, if I keep it plugged in, it prevents the computer to start. 
The system does not load, and get stucked with a black screen. If I switch off the computer, and remove the USB adapter, then it loads correctly. 

Somebody told me to update the driver, but don't know how to do it. I downloaded the driver package called TL-WN823NEU_V2_160315_Linux. 
I extracted it, but then I was not able to install it. 

I would be glad if you could help me. Now I'm writing from the same computer, connected to internet via a LAN cable. 

I've seen suggestions to change network manager, or install a USB switch mode. However, given previous bad experiences, I decided to ask before doing something I don't really understand. 

Thank you very much 

Best, 
f

Different solutions that I checked but could not help me. 
(SOLVED) Wireless USB adaptor install, ndiswrapper, wicd
(SOLVED) USB Wifi card TL-WN823N in Ubuntu 14.04.2 no working
TP-Link TL-WN823N Mini (Sin Hilos-N, USB, 300Mbps)
Install usb wifi tl-wn823n on Debian

---

### Post by mikewhatever on 2017-03-01
"Update the driver" is what a Windows user would do, but you don't seem to have a driver related problem, and you use Ubuntu.
So, after the system loads, plug it in, open a terminal window run the following, and post the outputs:
```

dmesg | tail -n20

lsusb

```

---

### Post by federicodemaria on 2017-03-01
Hi, 
thanks a lot for your support, I really appreciate it. 

Now, once I plug in the USB Adapter the screen gets stucked. I'm not sure if everything gets stucked, or just the mouse. 
Because of this, I was not succesfull in the task you gave me. I anyway post the result, after a reboot, without plugging the USB adapter. 



```
 
$ dmesg | tail -n20
[   27.833229] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[   29.687078] r8169 0000:02:00.0 enp2s0: link up
[   29.687086] IPv6: ADDRCONF(NETDEV_CHANGE): enp2s0: link becomes ready
[   91.115754] usb 3-1: new high-speed USB device number 5 using xhci_hcd
[   91.244381] usb 3-1: New USB device found, idVendor=059f, idProduct=1005
[   91.244384] usb 3-1: New USB device strings: Mfr=10, Product=11, SerialNumber=5
[   91.244385] usb 3-1: Product: little disk
[   91.244386] usb 3-1: Manufacturer: LaCie
[   91.244387] usb 3-1: SerialNumber: 152D203380B6
[   91.245131] usb-storage 3-1:1.0: USB Mass Storage device detected
[   91.245569] scsi host6: usb-storage 3-1:1.0
[   94.562707] scsi 6:0:0:0: Direct-Access     Hitachi  HTS543232L9A300       PQ: 0 ANSI: 2 CCS
[   94.563114] sd 6:0:0:0: Attached scsi generic sg3 type 0
[   94.633011] sd 6:0:0:0: [sdc] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[   94.633262] sd 6:0:0:0: [sdc] Write Protect is off
[   94.633264] sd 6:0:0:0: [sdc] Mode Sense: 00 38 00 00
[   94.633433] sd 6:0:0:0: [sdc] Asking for cache data failed
[   94.633435] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[   94.655121]  sdc: sdc1 sdc2
[   94.656114] sd 6:0:0:0: [sdc] Attached SCSI disk

```

```

lsusb
Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 002: ID 2109:3431 VIA Labs, Inc. Hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 046d:c31c Logitech, Inc. Keyboard K120
Bus 003 Device 002: ID 14cd:125c Super Top SD card reader
Bus 003 Device 004: ID 046d:c077 Logitech, Inc. M105 Optical Mouse
Bus 003 Device 005: ID 059f:1005 LaCie, Ltd 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by mikewhatever on 2017-03-02
Well, I can only guess that something is wrong with that adapter. One way to check is to try it on another machine. If it misbehaves, then it would be safe to assume it is broken.

---

### Post by federicodemaria on 2017-03-03
Ok, thank you. I'll do so. 

Since I probably have to buy a new one, in case you have any suggestions, please let me know.

---

### Post by ander10 on 2017-03-05
I have the same problem using ubuntu 16.04 and the tl-wn823n TP-Link. A few days ago stopped working. If I turn on the computer with the tp-link plugged in, at the login screen the computer stops working (mouse and keyboard do not respond) and I have to turn off the computer.

---

