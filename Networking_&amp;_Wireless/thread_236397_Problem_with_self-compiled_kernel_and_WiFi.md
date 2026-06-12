---
title: "Problem with self-compiled kernel and WiFi"
date: 2006-08-14
forum: Networking &amp; Wireless
---

### Post by gholen on 2006-08-14
Hi!

I have this somewhat odd (?) problem with my kernel.
I'm running a custom kernel, kenel 2.6.17.7, and the kernel works nice, but I've cannot use my USB-WiFi-dongle (D-Link DWL G-122), nor can I load the modules requierd to use this USB-Dongle (rt2570)](*,) 

This is a big problem, and I am not afraid of recompiling my kernel in any way, as long as I can get them to work.

Thank for any help in advance!

---

### Post by Darkhack on 2006-08-15
Were you able to use the card before recompiling your kernel?  Can you paste the output from "ifconfig" and "iwconfig".  Also are you using native drivers or ndiswrapper?  Some searches didn't turn up any native drivers on my end, but I don't know.

---

### Post by gholen on 2006-08-15
> **Darkhack said:**
> Were you able to use the card before recompiling your kernel?  Can you paste the output from "ifconfig" and "iwconfig".  Also are you using native drivers or ndiswrapper?  Some searches didn't turn up any native drivers on my end, but I don't know.

By tomorrow I can give you the posts that you asked for.
Sorry, but I cannot do it now, my girl would kill me!

---

### Post by gholen on 2006-08-15
Yes, I was able to use the D-Link before using this kernel (2.6.17.7).

lspci whitout D-link
```
gholen@Tina:~$ lspci
0000:00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
0000:00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
0000:00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
0000:00:1b.0 0403: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
0000:00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
0000:00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03)
0000:00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
0000:00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
0000:00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
0000:00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
0000:00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
0000:02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
0000:02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
gholen@Tina:~$ 

```

lspci with the D-Link:
```
gholen@Tina:~$ lspci
0000:00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
0000:00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
0000:00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
0000:00:1b.0 0403: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
0000:00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
0000:00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03)
0000:00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
0000:00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
0000:00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
0000:00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
0000:00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
0000:02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
0000:02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
gholen@Tina:~$ 

```

iwconfig
gholen@Tina:~$ iwconfig 

```
lo        no wireless extensions.

eth0      no wireless extensions.

Warning: Driver for device eth1 has been compiled with version 20
of Wireless Extension, while this program supports up to version 19.
Some things may be broken...

eth1      IEEE 802.11b/g  ESSID:"default"  Nickname:"default"
          Mode:Managed  Frequency=2.412 GHz  Access Point: 00:15:E9:04:7A:D0   
          Bit Rate=11 Mb/s   Tx-Power=18 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level=2/3  Noise level=184/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.
gholen@Tina:~$

```

As I can see (togh I'm quite tierd now) is that my card does not show.

In kernel 2.6.15-26 I was able to use the card, my current kernel is made using that config. I did remove some stuff from it, but I did not remove any stuff from WiFi... Will try again this weekend.
Thanks in advance!

---

