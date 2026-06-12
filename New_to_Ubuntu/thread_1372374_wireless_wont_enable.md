---
title: "wireless wont enable"
date: 2010-01-04
forum: New to Ubuntu
---

### Post by libihero on 2010-01-04
my wireless has stopped working, and it says "wireless disabled"
the switch for wireless on my computer is turned on, so i dont know if my computer hardware is broke or if ubuntu cant recognize it any more :S

---

### Post by J V on 2010-01-04
right click the network manager (little icon in notifications area aka tray) and enable it...

---

### Post by libihero on 2010-01-04
i have already tried that, the "enable wireless" is grayed out

---

### Post by Greenwidth on 2010-01-04
Is there a driver to enable in:
System > Admin > Hardware drivers ?

if not post the output of:
lspci
to see what card you have.

---

### Post by USB_NL on 2010-01-04
maby this will help

run in terminal
```
ifconfig
```

```
ifconfig --help
```

---

### Post by Charlietje on 2010-01-04
you can also try 

```
iwconfig
```

to see what interface is the wireless card

---

### Post by libihero on 2010-01-04
here is the lspci:
```
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:02.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Graphics Port 0)
00:04.0 PCI bridge: ATI Technologies Inc Device 7914
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
01:05.2 Audio device: ATI Technologies Inc Radeon X1200 Series Audio Controller
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
```

here is the output of ifconfig:
```
 eth0      Link encap:Ethernet  HWaddr 00:e0:b8:f9:70:9c  
          inet addr:141.217.222.26  Bcast:141.217.223.255  Mask:255.255.252.0
          inet6 addr: fe80::2e0:b8ff:fef9:709c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1614 errors:0 dropped:0 overruns:0 frame:0
          TX packets:567 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:494142 (494.1 KB)  TX bytes:76215 (76.2 KB)
          Interrupt:29 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:40 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2400 (2.4 KB)  TX bytes:2400 (2.4 KB)
```

iwconfig gives:
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  Mode:Managed  Access Point: Not-Associated   
          Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off 
```

i was looking through google, and i think it MIGHT be because of the new kernal i downloaded since my previous kernal had a bug that didnt let me use my webcam.  how can i tell if thats the case?

---

### Post by lotharmat on 2010-01-04
When Ubunbtu boots; select the previous kernel from the grub screen

iirc you press escape to get to the menu list

Actually; looking at the output from lspci I am not seeing a wireless card

Could you post the output of

```
lsusb
```

---

### Post by USB_NL on 2010-01-04
> i was looking through google, and i think it MIGHT be because of the new kernal i downloaded since my previous kernal had a bug that didnt let me use my webcam.  how can i tell if thats the case?

if you want to test webcam install Cheese

---

### Post by libihero on 2010-01-04
here's the output of lsusb:
```
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 04f2:b027 Chicony Electronics Co., Ltd Gateway USB 2.0 Webcam
Bus 001 Device 003: ID 0bda:8189 Realtek Semiconductor Corp. RTL8187B Wireless 802.11g 54Mbps Network Adapter
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

what if i deleted my old kernal :S
cheese didnt work on it, it was a bug i filed for and they stated it was fixed with the newer kernal that i just downloaded

---

### Post by lotharmat on 2010-01-04
Ahhhh- The realtek 8187B

I haven't managed to get this working with WPA2 - With WEP it worked out of the box.

Hopefully someone will be along presently who can offer some advice that is better than mine!

---

### Post by libihero on 2010-01-04
i'm jus gonna reinstall, i've just reinstalled recently and played with (or messed up :P) a lot of stuff.  i'll just reinstall and learn to not fix what is not broken haha

---

### Post by libihero on 2010-01-04
yeppp installing the older kernal fixed it
i guess i'll just have to wait till i can use my webcam again :( o well priorities haha

---

### Post by USB_NL on 2010-01-04
> **libihero said:**
> yeppp installing the older kernal fixed it
i guess i'll just have to wait till i can use my webcam again :( o well priorities haha

mark this a solved and try the webcam issue in new thread

---

### Post by libihero on 2010-01-04
i already had the webcam issue in a new thread, and i filed a bug report and the bug was confirmed, but fixed in linux-
image-2.6.32-02063202-generic_2.6.32-02063202_i386.deb
i installed that image and it messed up my wireless

---

