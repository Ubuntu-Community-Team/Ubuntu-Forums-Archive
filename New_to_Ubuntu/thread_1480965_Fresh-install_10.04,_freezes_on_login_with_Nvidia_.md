---
title: "Fresh-install 10.04, freezes on login with Nvidia drivers activated"
date: 2010-05-12
forum: New to Ubuntu
---

### Post by BlueXIV on 2010-05-12
Hi, I just installed Ubuntu on a new system build, and I cannot seem to get the nvidia proprietary graphics drivers to work. 

What happens is, when I enable the drivers, I can reboot and see the login screen in full resolution. However, when I actually log in, it freezes after a second (before the actual interface renders).

I read that Nouveau is enabled by default on 10.04, but my installation doesn't seem to have any kind of support for desktop effects or detecting a resolution larger than the default 1280x1024.

This is a fresh install on a new system of lucid, so I'm not sure if this is just a problem with lucid, but I would really like to get this working in order to use Ubuntu at a full resolution.

Thanks in advance!

I am using the Nvidia GeForce GTX470 and Ubuntu 10.04, x86-64.

Here are the devices installed, haven't installed anything yet.

> 00:00.0 Host bridge: Intel Corporation Core Processor DMI (rev 11)
00:03.0 PCI bridge: Intel Corporation Core Processor PCI Express Root Port 1 (rev 11)
00:08.0 System peripheral: Intel Corporation Core Processor System Management Registers (rev 11)
00:08.1 System peripheral: Intel Corporation Core Processor Semaphore and Scratchpad Registers (rev 11)
00:08.2 System peripheral: Intel Corporation Core Processor System Control and Status Registers (rev 11)
00:08.3 System peripheral: Intel Corporation Core Processor Miscellaneous Registers (rev 11)
00:10.0 System peripheral: Intel Corporation Core Processor QPI Link (rev 11)
00:10.1 System peripheral: Intel Corporation Core Processor QPI Routing and Protocol Registers (rev 11)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 06)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06)
00:1c.6 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 7 (rev 06)
00:1c.7 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 8 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 RAID bus controller: Intel Corporation 82801 SATA RAID Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
01:00.0 VGA compatible controller: nVidia Corporation Device 06cd (rev a3)
01:00.1 Audio device: nVidia Corporation Device 0be5 (rev a1)
03:00.0 SATA controller: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 03)
03:00.1 IDE interface: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 03)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
06:00.0 PCI bridge: PLX Technology, Inc. Device 8608 (rev ba)
07:01.0 PCI bridge: PLX Technology, Inc. Device 8608 (rev ba)
07:05.0 PCI bridge: PLX Technology, Inc. Device 8608 (rev ba)
07:07.0 PCI bridge: PLX Technology, Inc. Device 8608 (rev ba)
07:09.0 PCI bridge: PLX Technology, Inc. Device 8608 (rev ba)
08:00.0 USB Controller: NEC Corporation Device 0194 (rev 03)
09:00.0 SATA controller: Device 1b4b:9123 (rev 10)
0c:03.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev c0)

---

### Post by BlueXIV on 2010-05-12
Quick bump, any help would be greatly appreciated

---

### Post by MooPi on 2010-05-12
Can you post the results for 
```
lsmod
```

---

### Post by BlueXIV on 2010-05-12
Thanks

> Module                  Size  Used by
isofs                  33399  1
nls_utf8                1421  1
udf                    85529  1
crc_itu_t               1715  1 udf
nls_iso8859_1           4633  0
nls_cp437               6351  0
vfat                   10802  0
fat                    55350  1 vfat
binfmt_misc             7960  1
ppdev                   6375  0
snd_hda_codec_via      33207  0
snd_hda_intel          25645  2
snd_hda_codec          85727  2 snd_hda_codec_via,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87850  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0
snd_seq_oss            31219  0
snd_seq_midi            5829  0
snd_rawmidi            23388  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
fbcon                  39270  71
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
snd_seq                57417  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
vga16fb                12757  1
vgastate                9857  1 vga16fb
snd_timer              23553  2 snd_pcm,snd_seq
snd_seq_device          6824  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
nouveau               515131  0
ttm                    60815  1 nouveau
drm_kms_helper         30742  1 nouveau
asus_atk0110           10033  0
joydev                 11072  0
snd                    70978  15 snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   198770  3 nouveau,ttm,drm_kms_helper
i2c_algo_bit            6024  1 nouveau
xhci                   40958  0
psmouse                64608  0
soundcore               8052  1 snd
serio_raw               4918  0
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
lp                      9336  0
parport                37160  2 ppdev,lp
hid_logitech            8820  0
ff_memless              5109  1 hid_logitech
ohci1394               30260  0
usbhid                 40988  1 hid_logitech
hid                    83376  2 hid_logitech,usbhid
usb_storage            49833  2
ieee1394               94675  1 ohci1394
r8169                  39554  0
mii                     5237  1 r8169
ahci                   37646  2
pata_jmicron            2747  1

---

### Post by MooPi on 2010-05-12
Your system is using the nouveau driver and not the proprietary Nvidia. Do you have the Nvidia utility in your menu after installation. If so try the utility before restarting your computer. I remember an extra step to initialize the driver after using the utility.

---

### Post by snip3r8 on 2010-05-12
As a matter of interest is this the beta or the release Lucid?I had the same problem with the beta and when i tried using the .run drivers from the nvidia site they had problems installing.Something about them not liking the kernel.

---

### Post by BlueXIV on 2010-05-12
The installation is 10.04 LTS, released version not beta. And I have tried the Nvidia drivers, I mentioned that it freezes after I login if nvidia drivers are enabled :\

---

### Post by BlueXIV on 2010-05-13
Tiny bump again,

do you guys think I should just downgrade to Karmic and try that?

---

### Post by mal1958 on 2010-05-13
That is actually your decision.  I always wait till the Second iso is out.  For this one that should be near the end of June or mid July.  I have been using Karmic with no problems and I use an Invidia GeForce 6300 card (AGP variety).  How any Linux Distro works with any particular system is a chancy thing.  But I have had more luck at getting Ubuntu to work nicely and politely with this box of mine then I have with the Windows side.

---

### Post by crashbit on 2010-07-30
> **mal1958 said:**
> That is actually your decision.  I always wait till the Second iso is out.  For this one that should be near the end of June or mid July.  I have been using Karmic with no problems and I use an Invidia GeForce 6300 card (AGP variety).  How any Linux Distro works with any particular system is a chancy thing.  But I have had more luck at getting Ubuntu to work nicely and politely with this box of mine then I have with the Windows side.

I think your problem isn't NVIDIA, I think your problem is a Marvell 9123 6G hard disk controller.

See it: 09:00.0 SATA controller: Device 1b4b:9123 (rev 10)

Connect your hard disk to another controller a test it
Thx, Crashbit

---

### Post by soldier1st on 2010-08-03
i doubt it is the Nvidia card as bad memory can cause this. did you run the memtest? also did you try the live cd before installing to see how it handled your system? i would always use the live cd to see how Linux handles your system, also according to this page your card is not listed [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsNvidia](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsNvidia)

---

### Post by moojix on 2010-08-06
I had a similar problem with my new system:

MoBo Asus P7P55D-E Premium with nVidia GT200b [GeForce GTX 285]
kernel: 2.6.32-24-generic #39-Ubuntu SMP Wed Jul 28 05:14:15 UTC 2010 x86_64 GNU/Linux

Ubuntu 10.04 install was finished, but I got a blank screen or I/O Error after reboot.

My problem was indeed the Marvell 9123 controller and my SATA3 SSD (C300-CTFDDAC256M).

I could figure out this problem only by booting from another disc and mounting the SATA3 drive manually to see the ATA error in syslog.

My Solution: disable NCQ 

/etc/default/grub
```
GRUB_CMDLINE_LINUX="libata.force=noncq"
```HTH

--
moojix

---

