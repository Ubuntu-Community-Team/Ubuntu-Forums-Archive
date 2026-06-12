---
title: "Intel wifi link 5100 not work"
date: 2010-04-28
forum: New to Ubuntu
---

### Post by jordiv2009 on 2010-04-28
I install ubuntu 10.04 few days ago. But i don't get wifi link work. I reinstall all drivers several times. Any help would be appreciated. Thanks.

More info:

lspci

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
07:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040T PCI-E Fast Ethernet Controller (rev 12)
**[COLOR=Red]08:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100[/COLOR]**
0a:01.0 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
0a:01.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 02)
0a:01.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)

~$ sudo lshw -C network

  *-network               
       description: Ethernet interface
       product: 88E8040T PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 12
       serial: 00:23:8b:39:f5:70
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.25 duplex=full firmware=N/A ip=192.168.1.35 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:28 memory:b8400000-b8403fff ioport:3000(size=256)
 **[COLOR=Red] *-network UNCLAIMED[/COLOR]**
       description: Network controller
       product: Wireless WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:b8800000-b8801fff

---

### Post by mikewhatever on 2010-04-28
> **jordiv2009 said:**
> ... I reinstall all drivers several times. ...

What does this mean? What did you do exactly?

---

### Post by jordiv2009 on 2010-04-29
My english is so bad. I am sorry.

My wired network works OK. But my wireless network don't work.

After access to the  help of ubuntu, internet and network section, resolution of problems  with wireless networks, and the response to "sudo lshw-C network", you  can see in my previous post , they  propose to my reinstalling the drivers. And I did. But do not get the expected  result. Still off work wifi network with the same result  "unclaimed" when "sudo lshw-C network".


I hope  my problem is clearer,
best regards.[IMG]http://www.google.es/images/cleardot.gif[/IMG]

---

### Post by mikewhatever on 2010-04-29
Who proposed reinstalling the driver? Can you post a link to the instructions. If not, post the commands you used.

---

### Post by jordiv2009 on 2010-04-29
I get it at

[https://help.ubuntu.com/9.10/internet/C/troubleshooting-wireless.html](https://help.ubuntu.com/9.10/internet/C/troubleshooting-wireless.html)

---

### Post by mikewhatever on 2010-04-29
I've googled your wireless card model, and here's what it says:

[https://help.ubuntu.com/community/WifiDocs/Driver/Intel%20WiFi%20Link%205100](https://help.ubuntu.com/community/WifiDocs/Driver/Intel%20WiFi%20Link%205100)
```
Intel WiFi Link 5100 is compatible with Ubuntu 9.04+ 32-bit and 64-bit.
```

In other words, you did not need to reinstall any of the drivers.
According to the link you posted, if the output of 'lshw' says 'Unclaimed', the user is advised to use a Windows driver through installing Ndiswrapper. Have you done that?

---

### Post by jordiv2009 on 2010-04-29
Yes, I did it

---

### Post by mikewhatever on 2010-04-29
Right, let's remove it, then reboot, and then we'll try to figure out what was wrong in te first place.

Applications->Accessories->Terminal, use the following commands:

```
sudo apt-get purge ndisgtk ndiswrapper-common ndiswrapper-utils

sudo apt-get --purge autoremove
```

Now reboot, and if the wireless doesn't work, post the outputs of:

```
lsmod

sudo lshw -C network
```

Last but not least, is there a button/switch to turn the wireles on/off?

---

### Post by jordiv2009 on 2010-04-29
Here you are:

~$ lsmod

Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_hda_codec_intelhdmi    15191  1 
snd_hda_codec_conexant    23826  1 
snd_hda_intel          20384  2 
snd_hda_codec          79300  3 snd_hda_codec_intelhdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep               5668  1 snd_hda_codec
snd_pcm_oss            34571  0 
snd_mixer_oss          13961  1 snd_pcm_oss
snd_pcm                71489  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1498  0 
snd_seq_oss            27658  0 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_seq_midi            4621  0 
joydev                  8708  0 
snd_rawmidi            19141  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                48170  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              18720  2 snd_pcm,snd_seq
snd_seq_device          6052  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    55971  19 snd_hda_codec_intelhdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  283218  3 
drm_kms_helper         29297  1 i915
drm                   163143  4 i915,drm_kms_helper
sdhci_pci               5502  0 
sdhci                  15654  1 sdhci_pci
led_class               2864  1 sdhci
uvcvideo               57022  0 
videodev               34361  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
intel_agp              24473  2 i915
soundcore               6620  1 snd
snd_page_alloc          7236  2 snd_hda_intel,snd_pcm
ndiswrapper           184867  0 
i2c_algo_bit            5028  1 i915
psmouse                63245  0 
serio_raw               3978  0 
agpgart                31788  2 drm,intel_agp
video                  17375  1 i915
output                  1871  1 video
lp                      7028  0 
parport                32635  2 ppdev,lp
usbhid                 36174  0 
hid                    67032  1 usbhid
ohci1394               27238  0 
ieee1394               81213  1 ohci1394
sky2                   41040  0 
ahci                   32040  2


~$ sudo lshw -C network
 
  *-network               
       description: Ethernet interface
       product: 88E8040T PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 12
       serial: 00:23:8b:39:f5:70
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.25 duplex=full firmware=N/A ip=192.168.1.35 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:28 memory:b8400000-b8403fff ioport:3000(size=256)
  *-network UNCLAIMED
       description: Network controller
       product: Wireless WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:b8800000-b8801fff

---

### Post by jordiv2009 on 2010-04-29
Of course, the wireless switch is on.

---

### Post by mikewhatever on 2010-04-29
Although removed, the ndiswrapper module is still loaded.
```
ndiswrapper 184867 0 
```

Try removing it and the loading the native module:

> sudo rmmod ndiswrapper

sudo modprobe iwlagn

---

### Post by sussa on 2010-04-30
I'm having the same problem. Although I can connect to the internet, browsing is really slow. 

Here's my first topic on this issue: [http://ubuntuforums.org/showthread.php?t=1466892]("http://ubuntuforums.org/showthread.php?t=1466892")

Thanks!

---

### Post by mikewhatever on 2010-05-01
> **sussa said:**
> I'm having the same problem. Although I can connect to the internet, browsing is really slow. 

Here's my first topic on this issue: [http://ubuntuforums.org/showthread.php?t=1466892]("http://ubuntuforums.org/showthread.php?t=1466892")

Thanks!

Actually, your problem is not the same at all.

---

### Post by sussa on 2010-05-01
Ops, so I'm sorry for getting things wrong. I'm really a newbie, and I thought the problems were similar. My bad :)

But if you have any idea about how to solve my problem, I'd be glad to hear :)

Thanks!

---

