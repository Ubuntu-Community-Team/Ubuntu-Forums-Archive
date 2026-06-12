---
title: "Laptop internet connection."
date: 2009-05-09
forum: New to Ubuntu
---

### Post by Duskao on 2009-05-09
Hello. I just installed Ubuntu on my wifes laptop (dual boot with XP). She has a Linksys Wireless-G 2.4 GHz 802.11g NIC and for some reason I cannot get ubuntu connected to the internet on the laptop. With XP it works fine. Can I get a bit of a walkthough of what to do to get connected? Let me know what information I need and where to find it. Thanks a bunch everyone.
Let me know if you need more info.

---

### Post by Wa1k3rTXRang3r on 2009-05-09
yea wireless gave me a bit of trouble when i first started out too but ive got it down now

1.go to System->Administration->Hardware Drivers
2.the driver for your wireless card should show up there
3.click on it then click the activate button
4.now restart your computer and it should work
5.then simply connect to your network

---

### Post by anewguy on 2009-05-09
If the above doesn't work, please do the following:

- open a terminal window (applications/accessories/terminal)

- type:

lspci <press enter>

lsusb <press enter>


Please copy/paste the output from above in a reply here so we can see what adapter the laptop is using, so we can locate a driver for it.


Dave :)

---

### Post by Peter09 on 2009-05-09
If the above does not work please post the output of the terminal commands
```
ifconfig
```

and

```
route
```

---

### Post by ugm6hr on 2009-05-09
The details as suggested would help.  Further details that might help:
[http://ubuntuforums.org/showpost.php?p=5024425&postcount=1](http://ubuntuforums.org/showpost.php?p=5024425&postcount=1)

---

### Post by Duskao on 2009-05-10
Thanks guys. I'm at work now, but I'll try that/those when I get home. Didn't even think about needing a driver for it LOL. DUH!!!! :P

---

### Post by Duskao on 2009-05-10
Ok, the driver idea did not work. Nothing showed up. But for the "lspci" and the "lsusb" here they are minus the names.

-laptop:~$ lspci
00:00.0 Host bridge: nVidia Corporation nForce3 Host Bridge (rev a4)
00:01.0 ISA bridge: nVidia Corporation nForce3 LPC Bridge (rev a6)
00:01.1 SMBus: nVidia Corporation nForce3 SMBus (rev a4)
00:02.0 USB Controller: nVidia Corporation nForce3 USB 1.1 (rev a5)
00:02.1 USB Controller: nVidia Corporation nForce3 USB 1.1 (rev a5)
00:02.2 USB Controller: nVidia Corporation nForce3 USB 2.0 (rev a2)
00:06.0 Multimedia audio controller: nVidia Corporation nForce3 Audio (rev a2)
00:06.1 Modem: nVidia Corporation nForce3 Audio (rev a2)
00:08.0 IDE interface: nVidia Corporation nForce3 IDE (rev a5)
00:0a.0 PCI bridge: nVidia Corporation nForce3 PCI Bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation nForce3 AGP Bridge (rev a4)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 420 Go 32M] (rev a3)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
02:04.0 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:04.1 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:04.2 System peripheral: Texas Instruments PCI1620 Firmware Loading Function (rev 01)
03:00.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
-laptop:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 

And here is the ifconfig

 ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0f:b0:08:f8:b5  
          inet addr:192.168.2.6  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:b0ff:fe08:f8b5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:1136 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1021 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1250481 (1.2 MB)  TX bytes:184998 (184.9 KB)
          Interrupt:18 Base address:0x7000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


And the route

 route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     *               255.255.255.0   U     1      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.2.1     0.0.0.0         UG    0      0        0 eth0



Was hooked to the net hardwired for this. Hope that doesn't change anything.

Alright guys. When I had it connected to the net by a hardwire I updated the system and then check the "hardware Drivers" again they popped up and I installed them and now everything is peachy. Thanks for all the help again guys. You guys are my heroes!!!

---

### Post by ugm6hr on 2009-05-10
It appears you have 2 wifi cards in that laptop, which is surprising.

03:00.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

What version of Ubuntu are you using?

Both those devices should work with the proprietary driver, which should be found in Hardware Drivers if you are connected with a cable.

Interestingly, ifconfig does not find either controller.  Perhaps lshw might help reveal what is happening:
```
lshw -class network
```

Can you disable one of the wifi controllers from BIOS, or unplug it?

---

### Post by Peter09 on 2009-05-10
try the following

```
sudo apt-get install b43-fwcutter
```

please note the following

[https://bugs.launchpad.net/ubuntu/+bug/373791](https://bugs.launchpad.net/ubuntu/+bug/373791)

---

### Post by Duskao on 2009-05-10
That is odd that I have two wireless NIC's in the laptop. Makes me wonder if there is a built in one, but I do have one put in through the exterior pci slot. But either way, it is working now. Very well actually, very well indeed. Oh yeah, and I'm using 9.04 on the laptop.

---

