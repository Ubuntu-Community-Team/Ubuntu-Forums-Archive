---
title: "ndiswrapper help"
date: 2008-01-09
forum: Networking &amp; Wireless
---

### Post by fissionmailed on 2008-01-09
Ok, I have a Toshiba Satellite with what Ubuntu says is a AR5006EG.  I tried the madwifi but I couldn't get it too work. :\  So I want with the ndiswrapper and all.  I finally found a windows driver to work with ndiswrapper.  I install it with using this instructions. 
[http://ubuntuforums.org/archive/index.php/t-590093.html](http://ubuntuforums.org/archive/index.php/t-590093.html)

It shows a wlan0 in network settings but it shows nothing in Network Monitor and I restarted too.

lspci shows 

```

00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:04.0 PCI bridge: ATI Technologies Inc Unknown device 7914
00:05.0 PCI bridge: ATI Technologies Inc Unknown device 7915
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon X1200 Series
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
0e:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
14:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
14:06.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
14:06.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
14:06.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
14:06.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)

```
I know it's not that useful but I'm trying to post any info that could be useful.

ifconfig
```

eth0      Link encap:Ethernet  HWaddr 00:A0:D1:94:A0:0F  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:1B:9E:85:6A:38  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18 Memory:f8200000-f8210000 
```

iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

I'm at a loss, :confused:

Edit: now my wired internet isn't working.  >_<

---

### Post by NullHead on 2008-01-09
I sometimes have trouble getting ndiswrapper to modprobe so I have to install it from source. Go[ here]("http://sourceforge.net/project/showfiles.php?group_id=93482&package_id=99148&release_id=562382") and download the source and then install build-essential. So install build-essential ```
sudo apt-get install build-essential
``` and then unpack, move to the directory and then make the driver. ```
cd "were you unpacked the archive"
make
sudo make install
```

Then modprobe ndiswrapper ```
sudo modprobe ndiswrapper
```

I also add a line to /etc/rc.local

```
sudo gedit /etc/rc.local
```

"modprobe ndiswrapper"

---

### Post by fissionmailed on 2008-01-09
> **NullHead said:**
> I sometimes have trouble getting ndiswrapper to modprobe so I have to install it from source. Go[ here]("http://sourceforge.net/project/showfiles.php?group_id=93482&package_id=99148&release_id=562382") and download the source and then install build-essential. So install build-essential ```
sudo apt-get install build-essential
``` and then unpack, move to the directory and then make the driver. ```
cd "were you unpacked the archive"
make
sudo make install
```

Then modprobe ndiswrapper ```
sudo modprobe ndiswrapper
```

I also add a line to /etc/rc.local

```
sudo gedit /etc/rc.local
```

"modprobe ndiswrapper"

I've done everything except adding that to the rc.local file.  Sadly this didn't work. :\

Edit: when I get back from my physics class I'm going to reinstall ubuntu and try it again to see it that works.

---

### Post by NullHead on 2008-01-09
ok also you must add the line before the "exit 0" otherwise it won't take effect.

---

### Post by fissionmailed on 2008-01-09
> **NullHead said:**
> ok also you must add the line before the "exit 0" otherwise it won't take effect.

Yeah, I figured that out.  Taking that C++ class did something, :lolflag:

the this part of the steps in the thread I followed earlier 
14.Now we need to load the driver into the memory: In the terminal type:
sudo depmod -a
sudo modprobe ndiswrapper
and
tail /var/log/messages
Check for error messages. I get:

I got this 

```
Jan  9 18:43:31 fission kernel: [  399.133106] scsi 5:0:0:0: Direct-Access     SanDisk  Cruzer Mini      0.3  PQ: 0 ANSI: 2
Jan  9 18:43:31 fission kernel: [  399.134690] sd 5:0:0:0: [sdb] 2001888 512-byte hardware sectors (1025 MB)
Jan  9 18:43:31 fission kernel: [  399.134936] sd 5:0:0:0: [sdb] Write Protect is off
Jan  9 18:43:31 fission kernel: [  399.135834] sd 5:0:0:0: [sdb] 2001888 512-byte hardware sectors (1025 MB)
Jan  9 18:43:31 fission kernel: [  399.136084] sd 5:0:0:0: [sdb] Write Protect is off
Jan  9 18:43:31 fission kernel: [  399.136094]  sdb: sdb1
Jan  9 18:43:31 fission kernel: [  399.136498] sd 5:0:0:0: [sdb] Attached SCSI removable disk
Jan  9 18:43:31 fission kernel: [  399.136543] sd 5:0:0:0: Attached scsi generic sg1 type 0
Jan  9 18:43:52 fission kernel: [  408.201699] ndiswrapper version 1.51 loaded (smp=yes, preempt=no)
Jan  9 18:43:52 fission kernel: [  408.221384] usbcore: registered new interface driver ndiswrapper
```

I dunno if that's any help.  :\

Turned my comp off and then on, still not showing up in the network monitor.  I'm trying the WPA sup though now, seeing it I can get into my own wireless.

---

### Post by fissionmailed on 2008-01-11
Ok, it was really simple. >_<

I was following the instructions in that thread, using ndisgtk.  It didn't load the drivers that were suppose to be used, but it did load other drivers.  So I thought that it was loading the right ones.  I finally got the idea of going in in the terminal and trying the other one. It worked like a charm. 

Lesson learned, don't trust GUIs. :lolflag:

---

