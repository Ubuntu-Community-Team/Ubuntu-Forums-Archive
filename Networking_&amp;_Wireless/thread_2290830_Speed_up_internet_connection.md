---
title: "Speed up internet connection"
date: 2015-08-15
forum: Networking &amp; Wireless
---

### Post by oldsoundguy on 2015-08-15
Been gone from here for a while, as not had any problems to speak of. NOW we have  a problem.  Was running 12.04 and my internet speed on wired was HORRIBLE compared to the 90mb with my Win 7 (separate computers with same MB/Memory .. FireFox browsers on both).  So updated to 14.04 (took a while, but the install went with just a few minor hicups.  AND the speed increased to 30 .. why not 90?  What am I doing wrong?  Anyone with a clue?

---

### Post by kerry_s on 2015-08-15
it could be many thing.

try swapping the cable with your windows box, to rule out the wire. 
whats the distance of the 2 to the router ?
is the ethernet card or motherboard old(if using built in) ?

---

### Post by oldsoundguy on 2015-08-15
New cables on both boxes. distance is equal.  These are identical chassis. Utilizing built in eithernet.  
In checking the connection it says it is a 100m connection .. does not run that fast by any means and I would really like to get thing thing up to speed.

---

### Post by kerry_s on 2015-08-16
is your internet service fast enough ?

it's not always going to run at full speed, that would burn stuff up/out, it does bursts/chunks/bits of data, it's suppose to ramp up according to need/use.

---

### Post by oldsoundguy on 2015-08-16
Yes, it is fast enough.  100+ on the download and they are going to boost it again next week.  Just had the new modem installed last week.  I have a plugged in XP (believe it or not .. used for Adobe and other photography programs) and it is running in the 70+ area. I have the Win7 (laptop) (wireless) and it is running at 90+  .....  The 14.04 is running 30+.

---

### Post by praseodym on 2015-08-16
Please run the wireless-script from the sticky thread and show the outputs. Is it about LAN or wireless?

---

### Post by oldsoundguy on 2015-08-16
praseodym, it is HARD WIRED into the router.  UPDATED from 12.04 to 14.04 yesterday and gained speed from 18 to 30+. BUT it is no where NEAR the speed of either the wired XP computer or the wireless Win10 laptop.  The XP box is an identical twin to the Ubuntu box, they sit right next to each other with the same length of cable,  so it has to be something in the software.

I AM planning to put in a PCI-E  10/100/1000 card in each of the hardwired boxes in the near future, but need to get this software glitch ironed out first.

---

### Post by oldsoundguy on 2015-08-17
Anyone else have any ideas?

---

### Post by oldsoundguy on 2015-08-17
I checked my wired connection

Interface: ETH1
Hardware: 00:13:21:1F:F3
Driver (blank)
speed: 1000Mb/s

Really think the issue is in the software.

---

### Post by praseodym on 2015-08-17
Lets check the hardware:
```

lspci -nnk
lsmod
ifconfig -a
route -n
```

---

### Post by oldsoundguy on 2015-08-17
I really have no idea what this says, but here it is:

dave@dave-desktop-mediaroom:~$ lspci -nnk
00:00.0 Host bridge [0600]: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub [8086:2580] (rev 04)
	Subsystem: Hewlett-Packard Company Device [103c:3005]
	Kernel driver in use: agpgart-intel
00:02.0 VGA compatible controller [0300]: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller [8086:2582] (rev 04)
	Subsystem: Hewlett-Packard Company Device [103c:3005]
	Kernel driver in use: i915
00:1c.0 PCI bridge [0604]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 [8086:2660] (rev 03)
	Kernel driver in use: pcieport
00:1c.1 PCI bridge [0604]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 [8086:2662] (rev 03)
	Kernel driver in use: pcieport
00:1d.0 USB controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 [8086:2658] (rev 03)
	Subsystem: Hewlett-Packard Company Device [103c:3005]
	Kernel driver in use: uhci_hcd
00:1d.1 USB controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 [8086:2659] (rev 03)
	Subsystem: Hewlett-Packard Company Device [103c:3005]
	Kernel driver in use: uhci_hcd
00:1d.2 USB controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 [8086:265a] (rev 03)
	Subsystem: Hewlett-Packard Company Device [103c:3005]
	Kernel driver in use: uhci_hcd
00:1d.3 USB controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 [8086:265b] (rev 03)
	Subsystem: Hewlett-Packard Company Device [103c:3005]
	Kernel driver in use: uhci_hcd
00:1d.7 USB controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller [8086:265c] (rev 03)
	Subsystem: Hewlett-Packard Company Device [103c:3005]
	Kernel driver in use: ehci-pci
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev d3)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge [8086:2640] (rev 03)
	Kernel driver in use: lpc_ich
00:1f.1 IDE interface [0101]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller [8086:266f] (rev 03)
	Subsystem: Hewlett-Packard Company Device [103c:3005]
	Kernel driver in use: ata_piix
00:1f.2 IDE interface [0101]: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller [8086:2651] (rev 03)
	Subsystem: Hewlett-Packard Company Device [103c:3005]
	Kernel driver in use: ata_piix
05:04.0 Multimedia audio controller [0401]: Creative Labs SB Live! EMU10k1 [1102:0002] (rev 07)
	Subsystem: Creative Labs Device [1102:806b]
	Kernel driver in use: snd_emu10k1
05:04.1 Input device controller [0980]: Creative Labs SB Live! Game Port [1102:7002] (rev 07)
	Subsystem: Creative Labs Gameport Joystick [1102:0020]
	Kernel driver in use: Emu10k1_gameport
40:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express [14e4:1677] (rev 01)
	Subsystem: Hewlett-Packard Company Device [103c:3005]
	Kernel driver in use: tg3
dave@dave-desktop-mediaroom:~$ lsmod
Module                  Size  Used by
cfg80211              409394  0 
bnep                   18895  2 
rfcomm                 53664  0 
bluetooth             342208  10 bnep,rfcomm
binfmt_misc            13140  1 
dm_crypt               22589  0 
gpio_ich               13229  0 
uvcvideo               71309  0 
videobuf2_vmalloc      13048  1 uvcvideo
snd_emu10k1_synth      13007  0 
videobuf2_memops       13170  1 videobuf2_vmalloc
videobuf2_core         39258  1 uvcvideo
snd_emux_synth         33529  1 snd_emu10k1_synth
snd_seq_midi_emul      13432  1 snd_emux_synth
videodev              108503  2 uvcvideo,videobuf2_core
snd_seq_virmidi        13220  1 snd_emux_synth
snd_usb_audio         128498  1 
snd_usbmidi_lib        24367  1 snd_usb_audio
snd_emu10k1           145346  3 snd_emu10k1_synth
snd_util_mem           13821  2 snd_emux_synth,snd_emu10k1
snd_hwdep              13272  3 snd_usb_audio,snd_emux_synth,snd_emu10k1
snd_ac97_codec        105709  1 snd_emu10k1
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                85501  3 snd_usb_audio,snd_ac97_codec,snd_emu10k1
snd_page_alloc         14230  2 snd_pcm,snd_emu10k1
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  2 snd_seq_virmidi,snd_seq_midi
snd_rawmidi            25135  4 snd_usbmidi_lib,snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_seq                55383  5 snd_seq_midi_event,snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_midi
snd_seq_device         14137  5 snd_seq,snd_rawmidi,snd_emu10k1_synth,snd_emu10k1,snd_seq_midi
snd_timer              28584  3 snd_pcm,snd_seq,snd_emu10k1
snd                    60939  21 snd_usb_audio,snd_ac97_codec,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_emu10k1_synth,snd_usbmidi_lib,snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_seq_device,snd_seq_midi_emul,snd_seq_midi
soundcore              12600  1 snd
emu10k1_gp             12541  0 
gameport               15189  2 emu10k1_gp
serio_raw              13230  0 
lpc_ich                16864  0 
shpchp                 32128  0 
mac_hid                13037  0 
parport_pc             31981  1 
ppdev                  17391  0 
smsc47b397             13409  0 
lp                     13299  0 
parport                40836  3 lp,ppdev,parport_pc
usb_storage            48417  0 
psmouse                95402  0 
i915                  710018  4 
tg3                   152160  0 
pata_acpi              12886  0 
ptp                    18445  1 tg3
wmi                    18673  0 
video                  18903  1 i915
i2c_algo_bit           13197  1 i915
floppy                 55416  0 
drm_kms_helper         48868  1 i915
drm                   244037  5 i915,drm_kms_helper
pps_core               18799  1 ptp
dave@dave-desktop-mediaroom:~$ ifconfig -a
eth1      Link encap:Ethernet  HWaddr 00:13:21:00:1f:f3  
          inet addr:10.0.0.4  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: 2601:1c1:8400:e184:213:21ff:fe00:1ff3/64 Scope:Global
          inet6 addr: 2601:1c1:8400:e184:11da:ea88:8dca:c9bb/64 Scope:Global
          inet6 addr: fe80::213:21ff:fe00:1ff3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:750469 errors:0 dropped:3 overruns:0 frame:0
          TX packets:553439 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:552414954 (552.4 MB)  TX bytes:170627743 (170.6 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:204268 errors:0 dropped:0 overruns:0 frame:0
          TX packets:204268 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:22032930 (22.0 MB)  TX bytes:22032930 (22.0 MB)

dave@dave-desktop-mediaroom:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.0.0.1        0.0.0.0         UG    0      0        0 eth1
10.0.0.0        0.0.0.0         255.255.255.0   U     1      0        0 eth1
dave@dave-desktop-mediaroom:~$

---

### Post by kerry_s on 2015-08-17
your speed is just fine, seems you been reading the loopback.

it says your using ipv6, if you don't want that:
go into to "edit connections" & turn ipv6 to "ignore" instead of automatic.

---

### Post by oldsoundguy on 2015-08-17
Thanks for the reply

put ivp6 to sleep .. ran test .. still poor results from the same site I used to test the Windows boxes.

---

### Post by kerry_s on 2015-08-17
> **oldsoundguy said:**
> Thanks for the reply

put ivp6 to sleep .. ran test .. still poor results from the same site I used to test the Windows boxes.

i'm guessing the sites wrong, probably can't get past ubuntu firewall, so it's only reading the loop back.

this is what ubuntu says from your output above:
```
RX bytes:552414954 (552.4 MB) TX bytes:170627743 (170.6 MB)
```

---

### Post by oldsoundguy on 2015-08-17
OK, NOW I understand the loopback reference.

Thanks .. will mark as solved.

---

