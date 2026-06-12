---
title: "How to make wireless work"
date: 2007-01-20
forum: Networking &amp; Wireless
---

### Post by jasonz on 2007-01-20
How do i detect and connect to a wireless network in linux. I apologize for my stupidity, but i am really interested in linux and this forum was highly recommended.

Thanks for any help.

---

### Post by happy-and-lost on 2007-01-20
What network card are you using?

---

### Post by jasonz on 2007-01-20
integrated wireless card

---

### Post by happy-and-lost on 2007-01-20
Please paste

```

lspci
```

and

```
iwconfig
```

Into your terminal and post what it gives you.

---

### Post by jasonz on 2007-01-20
> lspci
0000:00:00.0 Host bridge: Intel Corporation Mobile Memory Controller Hub (rev 03)
0000:00:02.0 VGA compatible controller: Intel Corporation Mobile Integrated Graphics Controller (rev 03)
0000:00:02.1 Display controller: Intel Corporation Mobile Integrated Graphics Controller (rev 03)
0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
0000:00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
0000:00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
0000:00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
0000:00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
0000:00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
0000:00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
0000:00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
0000:00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
0000:00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
0000:00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controllers cc=IDE (rev 02)
0000:00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
0000:05:00.0 Network controller: Intel Corporation: Unknown device 4222 (rev 02)0000:07:06.0 CardBus bridge: Texas Instruments: Unknown device 8039
0000:07:06.1 FireWire (IEEE 1394): Texas Instruments: Unknown device 803a
0000:07:06.2 Mass storage controller: Texas Instruments: Unknown device 803b
0000:07:06.3 0805: Texas Instruments: Unknown device 803c
0000:07:08.0 Ethernet controller: Intel Corporation: Unknown device 1092 (rev 02)
> iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any
          Mode:Managed  Frequency=nan kHz  Access Point: Not-Associated
          Bit Rate:0 kb/s   Tx-Power:16 dBm
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:45363   Missed beacon:0

sit0      no wireless extensions.

---

