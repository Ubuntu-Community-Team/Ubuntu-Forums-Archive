---
title: "Ati Graphics Driver"
date: 2010-08-27
forum: New to Ubuntu
---

### Post by Feyerbrand on 2010-08-27
I have this computer that could run World of Warcraft, Starcraft, etc amazingly.  I uninstall windows XP and toss on ubuntu 10.04.  Looks great, all the windows and everything are awesome.  I do the regedit on wine and try to run the games.  It runs so slow and choppy I was shocked at the poor quality.  I try to run them through xterm, even worse.  I think that my computer doesn't have the graphics driver installed and I don't know where to get one for the card.  

I used the code 
```
lspci
```

and here are the results

```
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a2)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a2)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a2)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.2 Multimedia audio controller: nVidia Corporation MCP51 AC97 Audio Controller (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 VGA compatible controller: ATI Technologies Inc RV370 [Sapphire X550 Silent]
03:00.1 Display controller: ATI Technologies Inc RV370 secondary [Sapphire X550 Silent]
04:07.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem

```

what should I do?

---

### Post by jtarin on 2010-08-27
Do the command ```
lsmod 
```and see if you have the RV370 module loaded. If yes then edit /etc/modprobe.d/radeon-kms.conf and change options radeon modeset=1 to options radeon modeset=0 which, the 2.6.30 kernel gave the best video performance for mid range ATI cards.

---

### Post by Feyerbrand on 2010-08-27
> **jtarin said:**
> Do the command ```
lsmod 
```and see if you have the RV370 module loaded. If yes then edit /etc/modprobe.d/radeon-kms.conf and change options radeon modeset=1 to options radeon modeset=0 which, the 2.6.30 kernel gave the best video performance for mid range ATI cards.

I did the command
```
lsmod
```

and this is what i got

```
Module                  Size  Used by
binfmt_misc             6587  1 
radeon                674824  0 
ttm                    49943  1 radeon
drm_kms_helper         29297  1 radeon
drm                   162409  3 radeon,ttm,drm_kms_helper
agpgart                31724  2 ttm,drm
i2c_algo_bit            5028  1 radeon
snd_intel8x0           25588  2 
snd_ac97_codec        100646  1 snd_intel8x0
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
fbcon                  35102  71 
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
tileblit                2031  1 fbcon
font                    7557  1 fbcon
snd                    54148  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
bitblit                 4707  1 fbcon
ppdev                   5259  0 
softcursor              1189  1 bitblit
parport_pc             25962  1 
soundcore               6620  1 snd
lp                      7028  0 
parport                32635  3 ppdev,parport_pc,lp
vga16fb                11385  1 
vgastate                8961  1 vga16fb
k8temp                  3024  0 
i2c_nforce2             5199  0 
snd_page_alloc          7076  2 snd_intel8x0,snd_pcm
psmouse                63245  0 
serio_raw               3978  0 
usb_storage            39425  0 
sata_nv                19440  0 
forcedeth              49556  0 
pata_amd                8766  2 

```

---

### Post by AlphaLexman on 2010-08-27
Most likely, you need to download the proprietary ATI driver for linux.

---

### Post by Feyerbrand on 2010-08-27
> **AlphaLexman said:**
> Most likely, you need to download the proprietary ATI driver for linux.

I have tried downloading the driver but it doesn't want to run the file.  I have been all over tonight from thread to thread trying to find a solution and I have tried five or six different methods but to no success.  I have the file downloaded and I am willing to take any angle to get this working.  I recently tried doing

```
sudo sh ./ati-driver-installer-8.42.3-x86.x86_64.run --buildpkg Ubuntu/lucid
```

and the result

```
Created directory fglrx-install.geiIgz
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.42.3....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
Generating package: Ubuntu/lucid
Requested package is not supported.
Removing temporary directory: fglrx-install.geiIgz
fred@Fred:~$ sudo sh ./ati-driver-installer-8.42.3-x86.x86_64.run
Created directory fglrx-install.7hhScK
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.42.3....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================

Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.32-24-generic; make sure that the version is being
correctly set by --iscurrentdistro

Removing temporary directory: fglrx-install.7hhScK

```

---

### Post by cascade9 on 2010-08-27
[FONT=monospace]That is an X550 card (well, 2 X550s is crossfire actually from the look of it), and support was dropped by ATI for the X-xxx cards a while ago. 

As far as I know, there is no way to get the ATI drivers for the X550 to work on ubuntu 10.04. The only drivers that work are the open source versions...
[/FONT]

---

### Post by Feyerbrand on 2010-08-27
> **cascade9 said:**
> [FONT=monospace]That is an X550 card (well, 2 X550s is crossfire actually from the look of it), and support was dropped by ATI for the X-xxx cards a while ago. 

As far as I know, there is no way to get the ATI drivers for the X550 to work on ubuntu 10.04. The only drivers that work are the open source versions...
[/FONT]  well in my honest opinion any driver is better than no driver at all... because right now I can't even run starcraft with wine on this computer without having the slowest choppiest screen I have witnessed since 1997...

---

### Post by cascade9 on 2010-08-28
You will be runnign the opensoruce driver (or else you wouldnt be gettign any video at all). 

Its possible that updating to the newest version of the open soruce driver will help, but that is about all you can do.

---

### Post by krzpob on 2013-02-14
IMO last official ATI driver with support for this card is version 9.3. This version is only fo kernal in version v2. 
Running command ```
sh ati-driver-installer-9-3-x86.x86_64.run --listpkg
```
 give that last supported version of ubuntu is 9.04.

---

### Post by howefield on 2013-02-14
Old thread closed.

---

