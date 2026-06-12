---
title: "Atheros... Argh..."
date: 2011-01-16
forum: New to Ubuntu
---

### Post by sullid on 2011-01-16
I've been at this for hours. If you have any ideas I'll try them out - last resort being that my netbook becomes like a medicine ball but for frisbee golf. 
I can't get a connection either through the ethernet port or the wireless. Both seem to be visible to the system, but are labeled 'disabled.'
I'd like to solve this problem w/o having to 'make' anything. I say that because when I tried to 'make' madwifi I discovered that the complier isn't installed. Saving that for later, I'm hoping that I can get connected to the internet before I need to try to install the complier. Let me know what you think.
Oh, and it's an ASUS 1201HAB, and the wireless card is an Atheros AR8132, and I'm running Ubuntu Netbook Remix 10.10 that I installed with a live usb. 

**iwconfig**
```

lo        no wireless extensions.

eth0	no wireless extensions.

wlan0	IEEE 802.11bgn ESSID:off/any
        Mode:Managed  Access Point: Not-Associated   Tx-Power=off
        Retry  long limit:7   RTS thr:off   Fragment thr:off
        Power Management:off
```
**ifconfig**```
 
eth0  
	Link encap:Ethernet  HWaddr 90:e6:ba:f3:ff:00
	UP BROADCAST MULTICAST  MTU:1500  Metric:1
	RX packets:0 errors:0 dropped:0 overruns:0 frame:0
	TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
	collisions:0 txqueuelen:1000
 	RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
	Interrupt:40 

lo    
	Link encap:Local Loopback
	inet addr:127.0.0.1  
	Mask:255.0.0.0          
	inet6 addr: ::1/128 Scope:Host          
	UP LOOPBACK RUNNING  MTU:16436  Metric:1          
	RX packets:656 errors:0 dropped:0 overruns:0 frame:0          
	TX packets:656 errors:0 dropped:0 overruns:0 carrier:0          
	collisions:0 txqueuelen:0           
	RX bytes:51856 (51.8 KB)  
	TX bytes:51856 (51.8 KB)

```

**sudo lshw -C network**
```
  *-network               
       description: Ethernet interface
       product: AR8132 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: c0
       serial: 90:e6:ba:f3:ff:00
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.0.2-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:40 memory:fbfc0000-fbffffff ioport:e880(size=128)
  *-network DISABLED
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlan0
       version: 01
       serial: 00:25:d3:d6:c4:ba
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.35-22-generic firmware=N/A latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:fbef0000-fbefffff
```

**lspci -v**
```

00:00.0 Host bridge: Intel Corporation System Controller Hub (SCH Poulsbo) (rev 07)
	
	Subsystem: ASUSTeK Computer Inc. Device 83ce	
	Flags: bus master, fast devsel, latency 0

00:02.0 VGA compatible controller: Intel Corporation System Controller Hub (SCH Poulsbo) Graphics Controller (rev 07) (prog-if 00 [VGA controller])	
	Subsystem: ASUSTeK Computer Inc. Device 83ce	
	Flags: bus master, fast devsel, latency 0, IRQ 5	
	Memory at f3f80000 (32-bit, non-prefetchable) [size=512K]	
	I/O ports at c880 [size=8]	
	Memory at d0000000 (32-bit, non-prefetchable) [size=256M]
	Memory at f3f40000 (32-bit, non-prefetchable) [size=256K]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation System Controller Hub (SCH Poulsbo) HD Audio Controller (rev 07)

	Subsystem: ASUSTeK Computer Inc. Device 83ce
	Flags: bus master, fast devsel, latency 0, IRQ 23
	Memory at f3f38000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation System Controller Hub (SCH Poulsbo) PCI Express Port 1 (rev 07) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: fbf00000-fbffffff
	Prefetchable memory behind bridge: 80000000-801fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation System Controller Hub (SCH Poulsbo) PCI Express Port 2 (rev 07) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=02, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: f4000000-fbefffff
	Prefetchable memory behind bridge: cc000000-cfffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB UHCI #1 (rev 07) (prog-if 00 [UHCI])
	Subsystem: ASUSTeK Computer Inc. Device 83ce
	Flags: bus master, fast devsel, latency 0, IRQ 20
	I/O ports at b880 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB UHCI #2 (rev 07) (prog-if 00 [UHCI])
	Subsystem: ASUSTeK Computer Inc. Device 83ce
	Flags: bus master, fast devsel, latency 0, IRQ 21
	I/O ports at c080 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB UHCI #3 (rev 07) (prog-if 00 [UHCI])
	Subsystem: ASUSTeK Computer Inc. Device 83ce
	Flags: bus master, fast devsel, latency 0, IRQ 18
	I/O ports at c480 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB EHCI #1 (rev 07) (prog-if 20 [EHCI])
	Subsystem: ASUSTeK Computer Inc. Device 83ce
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at f3f37c00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1f.0 ISA bridge: Intel Corporation System Controller Hub (SCH Poulsbo) LPC Bridge (rev 07)
	Subsystem: ASUSTeK Computer Inc. Device 83ce
	Flags: fast devsel
	Kernel modules: lpc_sch

00:1f.1 IDE interface: Intel Corporation System Controller Hub (SCH Poulsbo) IDE Controller (rev 07) (prog-if 80 [Master])
	Subsystem: ASUSTeK Computer Inc. Device 83ce
	Flags: bus master, fast devsel, latency 0
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
	I/O ports at ffa0 [size=16]
	Kernel driver in use: pata_sch
	Kernel modules: pata_sch

01:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
	Subsystem: Device 1a3b:1089
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at fbef0000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: ath9k
	Kernel modules: ath9k

03:00.0 Ethernet controller: Atheros Communications AR8132 Fast Ethernet (rev c0)
	Subsystem: ASUSTeK Computer Inc. Device 14e5
	Flags: bus master, fast devsel, latency 0, IRQ 40
	Memory at fbfc0000 (64-bit, non-prefetchable) [size=256K]
	I/O ports at e880 [size=128]
	Capabilities: <access denied>
	Kernel driver in use: atl1c
	Kernel modules: atl1c

```

**lsmod**```

Module                  Size  Used by
rt73usb                22442  0 
crc_itu_t               1383  1 rt73usb
rt2500usb	       18049  0 
rt2x00usb               9779  2 rt73usb,rt2500usb
rt2x00lib              27275  3 rt73usb,rt2500usb,rt2x00usb
nls_iso8859_1           3261  1 
nls_cp437               4931  1 
vfat                    9201  1 
fat                    48240  1 vfat
usb_storage            40172  1 
binfmt_misc             6599  1 
parport_pc             26058  0 
ppdev                   5556  0 
snd_hda_codec_realtek   217980  1 
arc4                    1165  2
snd_hda_intel          22107  2 
joydev                  8735  0 
snd_hda_codec          87552  2 snd_hda_codec_realtek,snd_hda_intel
ath9k                  88756  0 
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
ath9k_common            5982  1 ath9k
snd_seq_midi            4588  0 
ath9k_hw              292297  2 ath9k,ath9k_common
snd_rawmidi            17783  1 snd_seq_midi
ath                     8153  2 ath9k,ath9k_hw
mac80211              231541  4 rt2x00usb,rt2x00lib,ath9k,ath9k_common
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               55847  0 
eeepc_wmi               2899  0 
sparse_keymap           3145  1 eeepc_wmi
cfg80211              144470  5 rt2x00lib,ath9k,ath9k_common,ath,mac80211
snd                    49006  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                59033  0 
videodev               43098  1 uvcvideo
v4l1_compat            13359  2 uvcvideo,videodev
video                  18712  0 
serio_raw               4022  0 
led_class               2633  2 rt2x00lib,ath9k
soundcore                880  1 snd
lpc_sch                 1761  0 
output                  1883  1 video
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
atl1c                  29949  0 
pata_sch                1975  2d 

```

---

### Post by taseedorf on 2011-01-16
try sudo iwconfig wlan0 mode adhoc
then wait
then try
sudo iwconfig wlan0 mode managed

( i remember there being a bug....)...

or, just shut down iwconfig and turn it back on...

sudo iwconfig wlan0 down
sudo iwconfig wlan0 up

i think those are the commands, maybe not...if not, google them and you'll find 'em...

you dont need ANY madwifi garbage....just ath5k  also.... you can try to switch the wifi on via a hotkey that you might of disabled it accidently??

---

### Post by ubaidillah on 2011-01-16
Have you try from BIOS? I use Lenovo S10-3,when i have problems with the Wifi Switch i need to do hard reset from CMOS Battery.

---

