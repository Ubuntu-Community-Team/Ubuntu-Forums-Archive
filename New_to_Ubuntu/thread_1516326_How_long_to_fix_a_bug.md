---
title: "How long to fix a bug/"
date: 2010-06-23
forum: New to Ubuntu
---

### Post by gordon33 on 2010-06-23
Hello All

How long of a wait to fix a Ubuntu Bug?

I am one of those people who's lap top will not connect to the wire less router.  

I see on: [https://bugs.launchpad.net/ubuntu/+bug/459625](https://bugs.launchpad.net/ubuntu/+bug/459625)   the bug has been reported.  Or at least a simaluar Bug is reported.

Gordon33

---

### Post by eltonw on 2010-06-23
> **gordon33 said:**
> Hello All

How long of a wait to fix a Ubuntu Bug?

I am one of those people who's lap top will not connect to the wire less router.  

I see on: [https://bugs.launchpad.net/ubuntu/+bug/459625](https://bugs.launchpad.net/ubuntu/+bug/459625)   the bug has been reported.  Or at least a simaluar Bug is reported.

Gordon33

It would first help YOU if you posted some info on your hardware, especially:machine brand, type of network card, and router (if any). Look also in the Networking forum. Most likely a fix has been found for your problem. Some fixes include installation of a newer kernel (if the current driver does not work).
):P

---

### Post by gordon33 on 2010-06-23
Hello eltonw, and All  

I have  a HP laptop with Ubuntu 10.4 the router is a Netgear.  The wireless connection worked before I down loaded the last Ubuntu updates a few weeks ago.  

Another lab top was able to connect to the wireless router.  

My experience is minimal.  I only know a2 Terminal commands to use to trouble shoot this.

I will need directions on installing annew kernal if it is needed.

Thank you for any help.

lshw -C network

gordon@gordon-laptop:~$  sudo lshw -C network

[sudo] password for gordon: 

  *-network               

       description: Ethernet interface

       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller

       vendor: Realtek Semiconductor Co., Ltd.

       physical id: 0

       bus info: pci@0000:01:00.0

       logical name: eth0

       version: 02

       serial: 00:1f:16:76:dc:4b

       size: 100MB/s

       capacity: 100MB/s

       width: 64 bits

       clock: 33MHz

       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation

       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.3 latency=0 link=yes multicast=yes port=MII speed=100MB/s

       resources: irq:27 ioport:3000(size=256) memory:d0410000-d0410fff(prefetchable) memory:d0400000-d040ffff(prefetchable) memory:d0420000-d043ffff(prefetchable)

  *-network DISABLED

       description: Wireless interface

       product: AR5001 Wireless Network Adapter

       vendor: Atheros Communications Inc.

       physical id: 0

       bus info: pci@0000:02:00.0

       logical name: wlan0

       version: 01

       serial: 00:24:2b:af:c5:33

       width: 64 bits

       clock: 33MHz

       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless

       configuration: broadcast=yes driver=ath5k latency=0 multicast=yes wireless=IEEE 802.11bg

       resources: irq:17 memory:d2600000-d260ffff

gordon@gordon-laptop:~$ 


lspci
gordon@gordon-laptop:~$ lspci

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)

00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)

00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)

00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)

00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)

00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)

00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)

00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)

00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)

00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)

00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)

00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)

00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)

00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)

00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)

00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)

00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)

01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

02:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)

gordon@gordon-laptop:~$ 


gordon33

---

### Post by ghetto2ivy on 2010-06-23
If its MS, the answer is about 7-8 years.

In my experience, workarounds in the linux community take around 2-3 months, with a broad patch about 6 months later if its actually a bug. Depending on how many people it affects, the fewer the people the longer the time (Many people = hours, a couple dozen 4 months). Also consider that the issue might not be ubuntu per se, but somewhere upstream or at the hardware level.

I'm also not sure that what you describe is the bug you linked to. 

Do you know if a driver is loaded for your wireless card? 
```
sudo lsmod
```

As a general rule I tell newcomers to ubuntu to always boot the livecd before upgrading ubuntu versions. If it works on the live cd, it will work on install, if it doesn't you will need to do some work. In which case you can simply live with your current Ubuntu version until such time as its fixed.

---

### Post by gordon33 on 2010-06-23
Hello ghetto2ivy


gordon@gordon-laptop:~$ sudo lsmod
[sudo] password for gordon: 
Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
uvcvideo               56990  0 
videodev               34361  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
snd_hda_codec_intelhdmi    11622  1 
vgastate                8961  1 vga16fb
snd_hda_codec_conexant    22577  1 
snd_hda_intel          21877  2 
snd_hda_codec          74201  3 snd_hda_codec_intelhdmi,snd_hda_codec_conexant,snd_hda_intel
arc4                    1153  2 
joydev                  8708  0 
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
ath5k                 121792  0 
mac80211              204922  1 ath5k
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ath                     7611  1 ath5k
snd_timer              19098  2 snd_pcm,snd_seq
i915                  282354  3 
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              126485  3 ath5k,mac80211,ath
drm_kms_helper         29297  1 i915
snd                    54148  17 snd_hda_codec_intelhdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   162471  4 i915,drm_kms_helper
soundcore               6620  1 snd
lp                      7028  0 
psmouse                63245  0 
led_class               2864  1 ath5k
i2c_algo_bit            5028  1 i915
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
intel_agp              24177  2 i915
serio_raw               3978  0 
parport                32635  2 ppdev,lp
agpgart                31724  2 drm,intel_agp
video                  17375  1 i915
output                  1871  1 video
usb_storage            39425  0 
r8169                  33980  0 
mii                     4381  1 r8169
ahci                   32008  2

---

