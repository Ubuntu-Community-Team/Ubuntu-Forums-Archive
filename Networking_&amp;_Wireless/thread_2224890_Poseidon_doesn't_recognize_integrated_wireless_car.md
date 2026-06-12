---
title: "Poseidon doesn't recognize integrated wireless card"
date: 2014-05-18
forum: Networking &amp; Wireless
---

### Post by Ruben_Gonzalo_Sori on 2014-05-18
I've installed Poseidon 4.0 on my chinese netbook (atom processor - RAM  1GB- SSD 16GB) and on the network icon says "not  network devices"

Here is what it shows after lspci and lsusb:

```
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)


Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 148f:2070 Ralink Technology, Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0bda:5801 Realtek Semiconductor Corp. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

I think is: "Bus 003 Device 002: ID 148f:2070 Ralink Technology, Corp." but don't know how to get the drivers or what...?
Please help me.


This is what it shows when I type ifconfig and iwconfig:
[ifconfig]
lo        Link encap:Bucle local  
              Direc. inet:127.0.0.1  Másc:255.0.0.0
              Dirección inet6: ::1/128 Alcance:Anfitrión
              ACTIVO BUCLE FUNCIONANDO  MTU:16436  Métrica:1
              Paquetes RX:54 errores:0 perdidos:0 overruns:0 frame:0
              Paquetes TX:54 errores:0 perdidos:0 overruns:0 carrier:0
              colisiones:0 long.colaTX:0 
              Bytes RX:16105 (16.1 KB)  TX bytes:16105 (16.1 KB)

[iwconfig]
lo        no wireless extensions.

vboxnet0  no wireless extensions.
```

---

### Post by varunendra on 2014-05-20
Welcome to the forums Ruben!

The Ralink card you have is natively supported by rt2800usb driver which comes with the kernel. Isn't it loaded? Please check -
```
lsmod | grep rt2
```

I've no idea how different Poseidon is from Ubuntu, so not sure if the network manager is same or much different. If it is the same, the "nm-tool" command should also show the driver in use if is available.

Is it an inbuilt card? If yes, have you cross-checked if it is enabled in BIOS (if there is an option to enable/disable it from there), and is turned 'On' if there is a physical switch or key combo to toggle it on/off?

**PS:**
Please use 'Code' tags to post command outputs. It preserves the formatting and makes it easier to read.

---

### Post by Ruben_Gonzalo_Sori on 2014-05-25
Well. First of all I'm sorry for not be online 4 days ago.
I was looking for a solution and I found a solution to my problem on this post:
[http://ubuntuforums.org/showthread.php?t=1285828](http://ubuntuforums.org/showthread.php?t=1285828)
including all the updates posted. After all the lines I realized that the card didn't work.
Started to search again and I found this other page:
[http://linuxforums.org.uk/index.php?topic=852.0](http://linuxforums.org.uk/index.php?topic=852.0)
that says to edit the **/os/linux/config.mk** file. I did it.
for my final steps I used the info of this page:
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)
and also looked all the thread:
[http://ubuntuforums.org/showthread.php?t=1670201](http://ubuntuforums.org/showthread.php?t=1670201)
(that was a wonderful thread)... followed some of they steps (changed 3370 code ... used 3070)
and then the wireless card worked!

---

