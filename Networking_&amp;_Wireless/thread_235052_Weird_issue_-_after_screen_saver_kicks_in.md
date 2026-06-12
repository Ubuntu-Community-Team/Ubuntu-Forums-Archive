---
title: "Weird issue - after screen saver kicks in"
date: 2006-08-12
forum: Networking &amp; Wireless
---

### Post by LinuxConvertJune2006 on 2006-08-12
my wireless stops working. I thought at first it was "power save" on the monitor so I disabled that, after after 20-30 minutes the wireless card stops working (no network connection).

Goto Networking, deactivate and reactivate and it works fine. This is annoying since m wife uses this PC also.

I've tried 2 seperate mobo's, CPU, memeory, video card and hard drive combo's. I also tried on i386 install and K& kernel, now getting same behavior on AMD64 box. All Dapper 6.06, with all patches/updates or without any.

Card TrendNet TEW-443PI , otherwise this card is absolutley fantastic, and cheap, Works right out of box,

Is there some kludge, or someway I could auto-deactivate/re-activate after awhile?

I was going to put together a script to ifdown ath0 then ifup ath0, but I get this when running these commands under sudo:

```

ifdown: interface ath0 not configured

```

And here is /etc/network/interfaces:
```

auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp
wireless-essid cantgetin
wireless-key s:cantgetin

auto wlan0
iface wlan0 inet dhcp

```


I edited SSID in case you were wondering. I'd prefer not to disable any WEP or security since that is neccesary stuff in my book. I'd rather a work around kludge instead of no security. Also, I try the same command on wlan0 and get the same not configured business. I then force it to read that confi file with the -i option, same result.

Any advice ? Known issues ? work arounds ?

---

### Post by LinuxConvertJune2006 on 2006-08-12
Here is my output of iwconfig :

```

lo        no wireless extensions.

eth0      no wireless extensions.

ath0      IEEE 802.11g  ESSID:"cantgetin"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:E0:98:FE:3D:B2
          Bit Rate:48 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=66/94  Signal level=-29 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

```

And lspci:

```

0000:00:00.0 Host bridge: nVidia Corporation nForce3 250Gb Host Bridge (rev a1)
0000:00:01.0 ISA bridge: nVidia Corporation nForce3 250Gb LPC Bridge (rev a2)
0000:00:01.1 SMBus: nVidia Corporation nForce 250Gb PCI System Management (rev a1)
0000:00:02.0 USB Controller: nVidia Corporation CK8S USB Controller (rev a1)
0000:00:02.1 USB Controller: nVidia Corporation CK8S USB Controller (rev a1)
0000:00:02.2 USB Controller: nVidia Corporation nForce3 EHCI USB 2.0 Controller (rev a2)
0000:00:05.0 Bridge: nVidia Corporation CK8S Ethernet Controller (rev a2)
0000:00:06.0 Multimedia audio controller: nVidia Corporation nForce3 250Gb AC'97 Audio Controller (rev a1)
0000:00:08.0 IDE interface: nVidia Corporation CK8S Parallel ATA Controller (v2.5) (rev a2)
0000:00:0a.0 IDE interface: nVidia Corporation CK8S Serial ATA Controller (v2.5) (rev a2)
0000:00:0b.0 PCI bridge: nVidia Corporation nForce3 250Gb AGP Host to PCI Bridge (rev a2)
0000:00:0e.0 PCI bridge: nVidia Corporation nForce3 250Gb PCI-to-PCI Bridge (rev a2)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AS [Radeon 9550]
0000:01:00.1 Display controller: ATI Technologies Inc RV350 ?? [Radeon 9550] (Secondary)
0000:02:07.0 FireWire (IEEE 1394): Texas Instruments TSB12LV26 IEEE-1394 Controller (Link)
0000:02:08.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)


```

---

### Post by LinuxConvertJune2006 on 2006-08-13
No one has any ideas or work arounds?

---

