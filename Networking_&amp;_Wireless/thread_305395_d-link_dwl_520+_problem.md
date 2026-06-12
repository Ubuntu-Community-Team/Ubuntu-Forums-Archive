---
title: "d-link dwl 520+ problem"
date: 2006-11-23
forum: Networking &amp; Wireless
---

### Post by sir_skiner on 2006-11-23
Hi.
I need a simple recipe for making my sister's d-link dwl 520+. my sister is totally newb, and I have no acces to her machine, so I need a way to make it as simple as possible. please give me some ideas, and keep in mind I have no wifi knowledge. 
the sysystem is edgy.

---

### Post by FrodoB on 2006-11-23
If you have access to the card you need to boot the system and run from a live CD and then publish the output of:

lspci

There is a chance that this card will just work with a regular install of Edgy, in fact it may just work on the live CD. Many of these cards have the TI ACX111 chipset which is supported in Edgy. The only thing to note is that an install from the Alternate CD does not work after a reboot until the linux-restricted-modules have been installed for your particular kernel.

The output of lspci will tell us if we are on the right track here.

---

### Post by sir_skiner on 2006-11-23
well, I can't do it myself, however I let you know as soon i'll know it from my sister.

---

### Post by sir_skiner on 2006-11-24
ok, so here you are:

```
**lspci**
00:00.0 Host bridge: nVidia Corporation nForce3 250Gb Host Bridge (rev a1)
00:01.0 ISA bridge: nVidia Corporation nForce3 250Gb LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation nForce 250Gb PCI System Management (rev a1)
00:02.0 USB Controller: nVidia Corporation CK8S USB Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation CK8S USB Controller (rev a1)
00:02.2 USB Controller: nVidia Corporation nForce3 EHCI USB 2.0 Controller (rev a2)
00:06.0 Multimedia audio controller: nVidia Corporation nForce3 250Gb AC'97 Audio Controller (rev a1)
00:08.0 IDE interface: nVidia Corporation CK8S Parallel ATA Controller (v2.5) (rev a2)
00:0a.0 IDE interface: nVidia Corporation CK8S Serial ATA Controller (v2.5) (rev a2)
00:0b.0 PCI bridge: nVidia Corporation nForce3 250Gb AGP Host to PCI Bridge (rev a2)
00:0e.0 PCI bridge: nVidia Corporation nForce3 250Gb PCI-to-PCI Bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
**02:08.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface**
```

```
**ifconfig**
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1384 (1.3 KiB)  TX bytes:1384 (1.3 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:13:46:B1:B0:BF  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:201 
```
```

```

```
 iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11b+/g+  ESSID:"STAB1B0BF"  Nickname:"acx v0.3.21"
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3  
          Retry min limit:7   RTS thr:off   
          Power Management:off
          Link Quality=49/100  Signal level=28/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions
```

all run frome livecd. now, please, tell me where do we stand and what to do next.

---

### Post by FrodoB on 2006-11-24
Well, it looks good, several people besides myself have been able to use these acx111 devices quite well and Edgy does have built-in kernel drivers.

In fact if you are still running a liveCD and using WEP you should be able to go to the:

System -> Adminstration -> Networking 

panel and fill it out and associate with the access point and get to the net, give it a try.

The only thing I note is that if you install from the Alternate CD the driver will work up through the install and not be there upon reboot. To  get it back you have to install the linux-restricted-modules for your kernel.

If you can install with the regular CD live will be much easier.

---

