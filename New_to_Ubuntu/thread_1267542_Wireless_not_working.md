---
title: "Wireless not working"
date: 2009-09-15
forum: New to Ubuntu
---

### Post by 3rr0r on 2009-09-15
Hi everyone!

I'm dual booting XP and ubuntu and for some reason it won't connect to my wireless.  It works on XP but not on ubuntu even though it shows the card in network manager. 

I have WPA2 setup and I know the card supports it since it works on XP.  Even when I try to connect in Ubuntu it only gives me the option of WPA/WPA2 and to enter the passphrase (auto-detect I guess?) either way, any ideas why it might not work?

---

### Post by 3rr0r on 2009-09-15
I tried editing the network connections to put in an IP address manually and it won't let me save the configs I put in...

---

### Post by Geoff918 on 2009-09-15
Hmm, not saving the settings? Something is not right here.

From the CLI (terminal) try editing the following:

sudo [vi / nano / gedit, whichever you prefer] /etc/network/interfaces

check what the settings are, edit as necessary.

Then;

sudo /etc/init.d/networking restart

(or alternately you could go the long route and do a sudo /etc/init.d/networking stop, sudo /etc/init.d/networking start)

after you're done check:

ifconfig -a

that should give you an output of the current settings. P.S. ifconfig may need to be run as sudo, I don't rightly remember off the top of my head.

---

### Post by 3rr0r on 2009-09-15
> **Geoff918 said:**
> Hmm, not saving the settings? Something is not right here.

From the CLI (terminal) try editing the following:

sudo [vi / nano / gedit, whichever you prefer] /etc/network/interfaces

check what the settings are, edit as necessary.


It only has
```
auto lo
iface lo inet loopback
```
What should I type for my wireless? wlan0?  And despite not being listed, it still shows up in Net Manager...odd?  Also, it lists my card as wlan0 with IPv4 address then as wmaster0 with a the same initial mac but then chained with -00-00-00-00 ... really long address (not IPv6).


EDIT: tried just adding "iface wlan0" and the restart didn't work.
```

 *Reconfiguring network interfaces...
/etc/network/interfaces:3: too few paramters for iface line
ifdown: couldn't read interfaces file "/etc/network/interfaces"
/etc/network/interfaces:3: too few paramters for iface line
ifup: couldn't read interfaces file "/etc/network/interfaces"
```

---

### Post by N9NE on 2009-09-15
Can you post "ifconfig" & "iwconfig" please and we can have a better idea as how we can help you.

Thanks'

---

### Post by 3rr0r on 2009-09-15
> **N9NE said:**
> Can you post "ifconfig" & "iwconfig" please and we can have a better idea as how we can help you.

Thanks'

ifconfig
```

3rr0r@box:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:06:df:28:a9:99  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:122 errors:0 dropped:0 overruns:0 frame:0
          TX packets:122 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9400 (9.4 KB)  TX bytes:9400 (9.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:2d:12:bd:6f:d3  
          inet6 addr: fe80::213:2ff:febd:64b3/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:183 errors:0 dropped:0 overruns:0 frame:0
          TX packets:135 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:20679 (20.6 KB)  TX bytes:20758 (20.7 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-2D-12-BD-6F-D3-34-62-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

iwconfig
```

3rr0r@box:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:""  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.
```

---

### Post by N9NE on 2009-09-15
Hmm , What seems to be the problem is that after looking at your iwconfig that it is "Not-Associated" .
Try this; Whatever is in italics including the brackets are replaced by your settings

Essid: Basically your Wireless network name ( linksys, home, etc. )

Key: Network Password

[B]
sudo /etc/init.d/networking start[/B]


**sudo iwconfig wlan0 essid ***<insert essid> ***key ***<insert key>*
Run **ifconfig** again and see if you are **Associated**

If Yes , Then Run

**sudo dhclient wlan0**

---

### Post by 3rr0r on 2009-09-15
I ran
```
 sudo iwconfig wlan0 essid <net_name> key <key>
```
without the <> of course and I got a 
```
bash: !: event not found
```

I do have a an exclamantion character at the end of my key...

---

### Post by N9NE on 2009-09-15
Try The below steps ; just once more if anything please, on the last step make sure there is one space between the word essid and the actual essid name. Same goes for "KEY"
[B]
sudo [/B]**/etc/init.d/networking restart**
[B]sudo ifconfig wlan0 up
sudo iwconfig wlan0 mode managed
sudo iwconfig wlan0 essid <network name> key <password>[/B]

THANKS!

---

### Post by 3rr0r on 2009-09-15
```

3rr0r@box:~$ sudo /etc/init.d/networking restart
[sudo] password for 3rr0r: 
 * Reconfiguring network interfaces...                                   [ OK ] 
3rr0r@box:~$ sudo ifconfig wlan0 up
3rr0r@box:~$ sudo iwconfig wlan0 mode managed
3rr0r@box:~$ sudo iwconfig wlan0 essid Lite key x%7a8s9DDKJdjie&*@_92807f89s7d89f789sa7hb@*&#*&$Bi1838490!
bash: !: event not found
3rr0r@box:~$
```

(not my actual key but might as well be... mine is just as long and crazy)

---

### Post by N9NE on 2009-09-15
Hmm try this please, and post the result.

**lspci -vv**

and if you mind me asking why is your network key so long? 

Thanks;

---

### Post by 3rr0r on 2009-09-16
Its long because I try to be secure (WPA2 + AES)  WPA is only as strong as the passwphrase you use.


3rr0r@box:~$ lspci -vv
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
	Subsystem: Toshiba America Info Systems Device ff00
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
	Latency: 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
	Subsystem: Toshiba America Info Systems Device ff00
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at d0200000 (32-bit, non-prefetchable) [size=512K]
	Region 1: I/O ports at 1800 [size=8]
	Region 2: Memory at c0000000 (32-bit, prefetchable) [size=256M]
	Region 3: Memory at d0300000 (32-bit, non-prefetchable) [size=256K]
	Capabilities: <access denied>
	Kernel modules: intelfb

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
	Subsystem: Toshiba America Info Systems Device ff00
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Region 0: Memory at d0280000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
	Subsystem: Toshiba America Info Systems Device ff00
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 22
	Region 0: Memory at d0340000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	Memory behind bridge: d0100000-d01fffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
	Subsystem: Toshiba America Info Systems Device ff00
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 23
	Region 4: I/O ports at 1820 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
	Subsystem: Toshiba America Info Systems Device ff00
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin B routed to IRQ 19
	Region 4: I/O ports at 1840 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
	Subsystem: Toshiba America Info Systems Device ff00
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin C routed to IRQ 18
	Region 4: I/O ports at 1860 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
	Subsystem: Toshiba America Info Systems Device ff00
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin D routed to IRQ 16
	Region 4: I/O ports at 1880 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) (prog-if 20)
	Subsystem: Toshiba America Info Systems Device ff00
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 23
	Region 0: Memory at d0544000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01)
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Bus: primary=00, secondary=05, subordinate=09, sec-latency=64
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: d0000000-d00fffff
	Prefetchable memory behind bridge: 0000000088000000-000000008bffffff
	Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
	Subsystem: Toshiba America Info Systems Device ff00
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt, intel-rng

00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02) (prog-if 80 [Master])
	Subsystem: Toshiba America Info Systems Device ff00
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin B routed to IRQ 19
	Region 0: I/O ports at 01f0 [size=8]
	Region 1: I/O ports at 03f4 [size=1]
	Region 2: I/O ports at 0170 [size=8]
	Region 3: I/O ports at 0374 [size=1]
	Region 4: I/O ports at 18b0 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
	Subsystem: Toshiba America Info Systems Device ff00
	Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Interrupt: pin B routed to IRQ 11
	Region 4: I/O ports at 18c0 [size=32]
	Kernel modules: i2c-i801

03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
	Subsystem: Intel Corporation Device 1040
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 2301
	Region 0: Memory at d0100000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: iwl3945
	Kernel modules: iwl3945

05:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
	Subsystem: Toshiba America Info Systems Device ff00
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 168, Cache Line Size: 128 bytes
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at d0004000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=05, secondary=06, subordinate=09, sec-latency=176
	Memory window 0: 88000000-8bfff000 (prefetchable)
	Memory window 1: 8c000000-8ffff000
	I/O window 0: 00002400-000024ff
	I/O window 1: 00002800-000028ff
	BridgeCtl: Parity- SERR- ISA- VGA- MAbort- >Reset+ 16bInt+ PostWrite+
	16-bit legacy interface ports at 0001
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket

05:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller (prog-if 10)
	Subsystem: Toshiba America Info Systems Device ff00
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32 (500ns min, 1000ns max), Cache Line Size: 64 bytes
	Interrupt: pin B routed to IRQ 17
	Region 0: Memory at d0007000 (32-bit, non-prefetchable) [size=2K]
	Region 1: Memory at d0000000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: firewire-ohci, ohci1394

05:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
	Subsystem: Toshiba America Info Systems Device ff00
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 57 (1750ns min, 1000ns max), Cache Line Size: 64 bytes
	Interrupt: pin C routed to IRQ 18
	Region 0: Memory at d0005000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: tifm_7xx1
	Kernel modules: tifm_7xx1

05:06.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller (prog-if 01)
	Subsystem: Toshiba America Info Systems Device ff00
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 57 (1750ns min, 1000ns max), Cache Line Size: 64 bytes
	Interrupt: pin D routed to IRQ 19
	Region 0: Memory at d0007800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

05:08.0 Ethernet controller: Intel Corporation PRO/100 VM Network Connection (rev 02)
	Subsystem: Toshiba America Info Systems Device ff00
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 66 (2000ns min, 14000ns max), Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 20
	Region 0: Memory at d0006000 (32-bit, non-prefetchable) [size=4K]
	Region 1: I/O ports at 2000 [size=64]
	Capabilities: <access denied>
	Kernel driver in use: e100
	Kernel modules: e100

3rr0r@box:~$

---

### Post by 3rr0r on 2009-09-16
bump

---

### Post by 3rr0r on 2009-09-16
bump

---

### Post by 3rr0r on 2009-09-18
Is it a lost cause?

---

