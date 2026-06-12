---
title: "Help!  I cannot connect my wireless"
date: 2007-04-24
forum: Networking &amp; Wireless
---

### Post by Dimension7 on 2007-04-24
Ok, I give up with my old Linksys WUSB54GSv2 as I believe it's unsupported.
I got myself a new Netgear WPN311.
Here's what I have...

```

# lspci
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev a2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev a3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev a3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:07.0 Communication controller: Conexant HCF 56k Data/Fax/Voice/Spkp Modem (rev 08)
01:08.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
5:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600] (rev a2)


# iwconfig
lo       no wireless extensions.
eth0     no wireless extensions.
wifi0    no wireless extensions.
ath0     IEEE 802.11g ESSID:"dimension"  Nickname:""
         Mode:Managed  Frequency:2.457 GHz  Access Point:  00:14:BF:45:B6:BE
         Bit Rate:54 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
         Retry:off   RTS thr:off   Fragment thr:off
         Power Management:off
         Link Quality=27/94  Signal level=-65 dBm  Noise level=-92dBm
         Rx invalid nwid:137  Rx invalid crypt:0  Rx invalid frag:0
         Tx excessive retries:0  Invalid misc:0   Missed beacon:0


# ifconfig
ath0     Link encap:Ethernet  HWaddr 00:0F:B5:88:7D:11
         inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
         inet6 addr: fe80::20f:b5ff:fe88:7d11/64 Scope:Link
         UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
         RX packets:20 errors:0 dropped:0 overruns:0 frame:0
         TX packets:72 errors:0 dropped:0 overruns:0 carrier:0 
         collisions:0 txqueuelen:0
         RX bytes:3080 (3.0 KiB)  TX bytes:12728 (12.4 KiB)

eth0     Link encap:Ethernet  HWaddr 00:50:70:26:06:85
         UP BROADCAST MULTICAST  MTU:1500  Metric:1
         RX packets:0 errors:0 dropped:0 overruns:0 frame:0
         TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:1000
         RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
         Interrupt:5 Base address:0xc000

lo       Link encap:Local Loopback
         inet addr:127.0.01  Mask:255.0.0.0
         inet6 addr: ::1/128 Scope:Host
         UP LOOPBACK RUNNING  MTU:16436  Metric:1
         RX packets:34 errors:0 dropped:0 overruns:0 frame:0
         TX packets:34 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:0
         RX bytes:2073  (2.0 KiB)  TX bytes:2073  (2.0 KiB)

wifi0    Link encap:UNSPEC  HWaddr 00-0F-B5-88-7D-11-00-00-00-00-00-00-00-00-00-00
         UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
         RX packets:3233 errors:0 dropped:0 overruns:0 frame:358
         TX packets:315 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 rxqueuelen:199
         RX bytes:293803  (286.9 KiB)   TX bytes:26458  (25.8 KiB)
         Interrupt:5

```

Being a total newbie on Linux.  I'm stuck with what to do next.  Please advice on what to do next.
Thank you in advance.

---

### Post by joe007 on 2007-04-24
No expert here but assuming this is a laptop, do you have the power plugged in or DC only.  I have the same issue you are having on battery, yet work fine with AC power.

---

### Post by mshade on 2007-04-24
It looks like you're already connected -- ath0 should be your wireless chipset, as it's listed as atheros in your lspci above.

How are you connected now, etc?

---

### Post by Dimension7 on 2007-04-24
mshade, i still do not have a connection.  I'm using Windows to post here.

joe007, this is a desktop computer.

---

### Post by amniarix on 2007-04-25
The "Link Quality=27/94" from iwconfig means the interface is connected to your wireless network, and 'ifconfig' indicates it's configured with an IP (192.168.1.102), so.. presumably all you need to get right now is the routing.

Can you ping your router (likely to be 192.168.1.1 or 192.168.0.1)?  

What does 'route' print? Mine shows:

jturner@psyche:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     0      0        0 ra0
link-local      *               255.255.0.0     U     1000   0        0 ra0
default         192.168.0.1     0.0.0.0         UG    0      0        0 ra0
jturner@psyche:~$ 

Once you've established what your gateway IP is, try making it your default route with eg.:

sudo route del default
sudo route add default gw 192.168.1.1

---

### Post by Dimension7 on 2007-04-25
> **mshade said:**
> It looks like you're already connected -- ath0 should be your wireless chipset, as it's listed as atheros in your lspci above.

How are you connected now, etc?


I did install MadWiFi but did not work, installed ndiswrapper but did not worked either.
I tried a fresh install of Ubuntu, and for some reason it worked right away without any configurations or something.  Wierd!

Thank you all for your replies.

---

