---
title: "Wifi Not Connecting In Lenovo B40-70 Laptop"
date: 2015-08-12
forum: Networking &amp; Wireless
---

### Post by pradeep16 on 2015-08-12
Hi All,

I have ubuntu 12.04 64 bit installed. As I try connecting to a wireless  connection, it asks for credentials and then every 2 minutes it asks for  credentials again. Just doesn't connect. 

```
$ uname -a
Linux user-Lenovo-B40-70 3.2.0-38-generic #61-Ubuntu SMP Tue Feb 19 12:20:02 UTC 2013 i686 i686 i386 GNU/Linux
```

```
$ lspci

00:00.0 Host bridge: Intel Corporation Device 0a04 (rev 0b)
00:02.0 VGA compatible controller: Intel Corporation Device 0a16 (rev 0b)
00:03.0 Audio device: Intel Corporation Device 0a0c (rev 0b)
00:14.0 USB controller: Intel Corporation Device 9c31 (rev 04)
00:16.0 Communication controller: Intel Corporation Device 9c3a (rev 04)
00:1b.0 Audio device: Intel Corporation Device 9c20 (rev 04)
00:1c.0 PCI bridge: Intel Corporation Device 9c10 (rev e4)
00:1c.1 PCI bridge: Intel Corporation Device 9c12 (rev e4)
00:1c.2 PCI bridge: Intel Corporation Device 9c14 (rev e4)
00:1c.3 PCI bridge: Intel Corporation Device 9c16 (rev e4)
00:1d.0 USB controller: Intel Corporation Device 9c26 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Device 9c43 (rev 04)
00:1f.2 SATA controller: Intel Corporation Device 9c03 (rev 04)
00:1f.3 SMBus: Intel Corporation Device 9c22 (rev 04)
02:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5229 (rev 01)
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 10)
09:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device b723

```
```
$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.
```

```
$ lsmod

Module                  Size  Used by
snd_hda_codec_realtek   174313  0 
rfcomm                 38139  12 
bnep                   17830  2 
parport_pc             32114  0 
ppdev                  12849  0 
snd_hda_intel          32765  2 
snd_hda_codec         109562  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
uvcvideo               67203  0 
videodev               86588  1 uvcvideo
snd_pcm                80916  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
joydev                 17393  0 
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
btusb                  17948  2 
bluetooth             158479  23 rfcomm,bnep,btusb
snd                    62218  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              14635  1 snd
ideapad_laptop         17890  0 
video                  19115  0 
sparse_keymap          13658  1 ideapad_laptop
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
psmouse                96718  0 
serio_raw              13027  0 
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
r8169                  56368  0 
```

```
$ sudo lshw -C network

  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 10
       serial: f0:76:1c:21:ee:b5
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=N/A ip=192.168.1.2 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:62 ioport:4000(size=256) memory:b2504000-b2504fff memory:b2500000-b2503fff
  *-network UNCLAIMED
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: ioport:3000(size=256) memory:b2400000-b2403fff

```
```
$ iwlist scan

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.
```



Note:The wired connection is working perfectly fine.Please let me know, if more  info. is needed. Would greatly appreciate any help.

Thanks In Adv.,
Pradeep Kumar G.

---

### Post by ajgreeny on 2015-08-12
See my answer to your other thread at [http://ubuntuforums.org/showthread.php?t=2290483&p=13337361#post13337361](http://ubuntuforums.org/showthread.php?t=2290483&p=13337361#post13337361).

---

