---
title: "(wireless)Inability to get connected by DHCP"
date: 2010-10-08
forum: New to Ubuntu
---

### Post by Edric Technology on 2010-10-08
Folks, I'm Edric and user of Ubuntu 10.04 Netbook. I downloaded the iso file and so on... I have it installed in my pendrive. My problem is, I can't recognise wireless networks. It seems that my LG X130 netbook have an inability to get an adress by DHCP. My wireless card is a Ralink 802.11n Wireless LAN Card. May someone help me, please? I'm just a beginner and don't know much about this. Thanks! I attached an image so that you can see for yourself the wireless card name.

[IMG]http://lh3.ggpht.com/_AHtIGUIt1Os/TK8WcBdz52I/AAAAAAAAADc/HdIUoeZHQEE/s640/hardware.png[/IMG]

---

### Post by migs73 on 2010-10-08
Boot into ubuntu from your pen drive and then open terminal (Applications> Accessories > Terminal) and type in ```
lspci
``` and then enter and post the output back here. This will let us know if Ubuntu can see the card.

---

### Post by Edric Technology on 2010-10-08
Ok, thank migs73! These are the results:

-------------------------------------------------------------------

ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00.02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display Controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definiton Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801 GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
00:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8102E PCI Express Fast Ethernet controller (rev 02)
02:00.0 Network controller: RaLink RT3090 Wireless 802.11n 1T/1R PCIe

----------------------------------------------

What should I do now?

---

### Post by Hippytaff on 2010-10-08
> 
02:00.0 Network controller: RaLink RT3090 Wireless 802.11n 1T/1R PCIe

 
Your pci wirless card uses a ralink RT3090 driver. The issue could be down to a number of driver related problems...quite common.
 
```

lsmod

```
what does this return?

---

### Post by Edric Technology on 2010-10-08
It returns:

-----------------------------------------------------------------------------------

```
Module               Size       Used by
binfmt_misc          6587       1
ppdev                  5259       0
lp                        7028       0
dm_crypt            11331       0
parport               32635       2 ppdev, lp
rfcomm              33421       4
snd_hda_codec_realtek  203168   1
sco                      7885       2
snd_hda_intel     21877       2
bridge                45582       0
snd_hda_codec   74201       2 snd_hda_codec_realtek,
snd_hda_intel

stp                     1655       1 bridge
snd_hwdep         5412       1 snd_hda_codec
snd_pcm_oss    35308       0
snd_mixer_oss  13746       1 snd_pcm_oss
bnep                  9436       2
snd_pcm           70662       3 snd_hda_intel,
snd_hda_codec, snd_pcm_oss

snd_seq_dummy   1338       0
l2cap               30624       16 rfcomm, bnep
joydev               8708       0
snd_seq_oss     26726       0
snd_seq_midi     4557       0
snd_rawmidi     19056       1 snd_seq_midi
snd_seq_midi_event   6003       2 snd_seq_oss, snd_seq_midi
snd_seq           47263       6 snd_seq_dummy, snd_seq_oss,
snd_seq_midi, snd_seq_midi_event

snd_timer        19098       2 snd_pcm, snd_seq
snd_seq_device       5700       5 snd_seq_dummy, snd_seq_oss,
snd_seq_midi, snd_rawmidi, snd_seq

uvcvideo         56990       0
btusb             10925       2
videodev        34361       1 uvcvideo
snd                54148       16 snd_hda_codec_realtek,
snd_hda_intel, snd_hda_codec, snd_hwdep, snd_pcm_oss,
snd_mixer_oss, snd_pcm, snd_seq_oss, snd_rawmidi,
snd_seq, snd_timer, snd_seq_device

v4l1_compat   13251       2 uvcvideo, videodev
bluetooth        49892       9 rfcomm, sco, bnep, l2cap, btusb
psmouse         63245       0
soundcore         6620       1 snd
serio_raw         3978       0
rt3090sta      674216       0
snd_page_alloc       7076       2 snd_hda_intel, snd_pcm
squashfs        20680       1
aufs             149050       1
nls_iso8859_1    3249       1
nls_cp437        4919       1
vfat                 8901       1
fat                 47767       1 vfat
dm_raid45      81647       0
xor                15028       1 dm_raid45
fbcon             35102       71
tileblit              2031       1 fbcon
font                 7557       1 fbcon
bitblit               4707       1 fbcon
softcursor        1189       1 bitblit
vga16fb         11385       0
vgastate          8961       1 vga16fb
i915             282354       4
drm_kms_helper      29297       1 i915
drm             162471       5 i915, drm_kms_helper
usb_storage   39425       1
i2c_algo_bit     5028       1 i915
intel_agp       24177       2 i915
r8169           33884       0
ahci              32008       0
video            17375       1 i915
mii                  4381       1 r8169
agpgart          31724       2 drm, intel_agp
output             1781       1 video

```---------------------------------------------------------------------------------------------

---

### Post by Hippytaff on 2010-10-09
rt3090sta - this is the driver for the wireless card - you need to look into blacklisting and nsdiwrapper
have a read of post with similar rallink issues, if you need any assistance then post back :-)

---

### Post by Edric Technology on 2010-10-09
Ok, thank you again, Hippytaff. I'll check it out, it will take at least 24 hour, cause I have some tasks this weekend. I'll post back until Sunday or Monday.

---

### Post by Edric Technology on 2010-10-09
Hippytaff, I just took a look at the forums as you suggested and found a thread aimed to solve problems with the Ralink wireless card, and then I found something that probably will help me. Unhappily I'm busy this weekend and I'll need some spare time to solve this problem. When I have it solved I'll post here, until there I'll post some partials about the problem. I hopingly think I'll have this problem solve soon, because I found at the Ralink tech's site, the link with the software for my card RT3090PCIe. By the way, that's the thread I just found: [http://ubuntuforums.org/showthread.php?t=1476007&highlight=ralink+card](http://ubuntuforums.org/showthread.php?t=1476007&highlight=ralink+card)

Thanks, again!

---

### Post by Edric Technology on 2010-10-14
Hippytaff, I really couldn't handle the problem yet! I'm searching through the threads and hope I'll solve that problem soon. Thank you for all. I did all what was asked to do in that thread I have mentioned before, but without results. I couldn't do neither the second step, because the terminal wasn't behaving like waited.

Thank you and all the others too.

---

### Post by Edric Technology on 2010-10-23
Hello, friends! Hippytaff, thank you for every help you gave me! 4 days ago I had my problem solved! I tried many different manners that I could but without results. So I decided to install the new version of Ubuntu, 10.10... the result was quick! The wireless was up and running! Now I can navigate through the web! Now I can call it "netbook"! Thank you, Lord! Thank you Ubuntu developers around the world!

:guitar:

---

