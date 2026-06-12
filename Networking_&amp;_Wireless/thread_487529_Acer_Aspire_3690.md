---
title: "Acer Aspire 3690"
date: 2007-06-29
forum: Networking &amp; Wireless
---

### Post by mmoscosa on 2007-06-29
Hello, I just bough a new laptop and am habing some problems with the wifi card

check what lspci outputted:

```
mish@mish-laptop:~$ lspci 
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)

05:00.0 Ethernet controller: Atheros Communications, Inc. Unknown device 001c (rev 01)
06:01.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)

06:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
06:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
06:04.2 Generic system peripheral [0805]: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
06:04.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
06:04.4 FLASH memory: ENE Technology Inc Unknown device 0551 (rev 01)

```

but the ifconfig does not detect the wifi card:

```
 mish@mish-laptop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:16:D4:CB:CE:E6  
          inet addr:192.168.1.81  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:d4ff:fecb:cee6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:59015 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30686 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:86425861 (82.4 MiB)  TX bytes:2415768 (2.3 MiB)
          Interrupt:21 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:491 (491.0 b)  TX bytes:491 (491.0 b)

```

I just installed madwifi-tools but dont seem to understand hhow to work, do you have any idea?

Thank you

---

### Post by mmoscosa on 2007-06-29
i tried the following but nothing

```
mmoscosa@mish-laptop:~$ sudo wlanconfig ath0 create wlandev wlan0 wlanmode sta
Password:
wlanconfig: ioctl: No such device

```


any idea?

I.ve been reading and they say maybe this is because its a driver for winvista and ubuntu still has no support for it?

---

### Post by tturrisi on 2007-06-29
The card in the Acer 3690 is supported & works well.
I just setup one of those la[ptops for a friend's kid.
The card has an atheros chipset, thus requires that you install the madwifi driver which is in the restricted modules package.

---

### Post by mmoscosa on 2007-06-30
But ubuntu automaticly installs this?

---

### Post by AJB2K3 on 2007-07-06
Does this also apply to the 3693WLMI?

---

### Post by JesCed on 2007-08-21
Sorry to disagree with you, but I guess not all 3690s are alike. In my case, I am using an Aspire 3690-2767, and have not been able to get the wifi card to work. One interesting note is that, when booting from an Ubuntu Live CD, you can clearly read a system reply related to wifi, saying "Hardware revision not supported". Any ideas as to what I can do?

---

