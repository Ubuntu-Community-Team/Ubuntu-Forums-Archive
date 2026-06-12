---
title: "Ubuntu hangs with blinking underscore"
date: 2010-09-30
forum: New to Ubuntu
---

### Post by lbrty on 2010-09-30
Once in a while Ubuntu 10.04 hangs when starting up. It has been doing this since I first installed Ubuntu (about 5 months ago). A blinking underscore appears in the top left corner of the black screen about 1 out of 10 times from a cold boot. It is fairly random. I must do a hard reboot in order for Ubuntu to get to the login screen. After the hard reboot everything is fine.

I have also noticed a separate issue that may be causing/contributing to Ubuntu hanging. The HP Laptop that I am using has a SD-MS/Pro-MMC-XD slot for flash memory. I always have an SD card inserted for immediate backup purposes (8GB). I have to unmount the SD card (but I do not physically eject it) before going into suspend mode. If I do not unmount the SD card and place the laptop in suspend the laptop will hang, will not go into suspend (power is still on), and the screen turns black (illuminated).

I do have a dual-boot setup (WinXP Pro for magicJack).

Laptop Hardware:
HP Pavilion dv4
Ubuntu 10.04.1 32-bit with all updates
Intel Core 2 Duo T6600 2.20 GHz
Mobile 4 Series Chipset Integrated Graphics Controller
4GB DDR3 RAM
320GB SATA hard drive

lspci output:
```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
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
02:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
04:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller
04:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller
04:00.3 System peripheral: JMicron Technology Corp. MS Host Controller
04:00.4 System peripheral: JMicron Technology Corp. xD Host Controller
```lsusb output:
```
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 005: ID 045e:00d1 Microsoft Corp. Optical Mouse with Tilt Wheel
Bus 005 Device 004: ID 06e6:c200 Tiger Jet Network, Inc. Internet Phone
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 174f:1107 Syntek 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```lsmod output:
```
Module                  Size  Used by
vmnet                  41018  15 
parport_pc             26250  0 
vmblock                10766  1 
vsock                  37367  0 
vmci                   52974  2 vsock
vmmon                  63160  6 
r8169                  34300  0 
mii                     4381  1 r8169
nls_utf8                1069  0 
isofs                  29250  0 
nls_iso8859_1           3249  1 
nls_cp437               4919  1 
vfat                    8933  1 
fat                    47767  1 vfat
binfmt_misc             6587  1 
vboxdrv               191010  0 
ppdev                   5259  0 
snd_hda_codec_intelhdmi    11622  1 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
snd_hda_codec_idt      51978  1 
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
arc4                    1153  2 
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_usb_audio          75861  0 
snd_hda_intel          22133  4 
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_hda_codec          74201  3 snd_hda_codec_intelhdmi,snd_hda_codec_idt,snd_hda_intel
snd_seq_dummy           1338  0 
snd_pcm                70918  5 snd_usb_audio,snd_hda_intel,snd_pcm_oss,snd_hda_codec
i915                  286926  3 
psmouse                63245  0 
drm_kms_helper         29297  1 i915
snd_usb_lib            15833  1 snd_usb_audio
snd_seq_oss            26726  0 
drm                   163098  4 i915,drm_kms_helper
b43                   164132  0 
uvcvideo               57118  0 
snd_seq_midi            4557  0 
videodev               34361  1 uvcvideo
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
joydev                  8708  0 
snd_rawmidi            19056  2 snd_usb_lib,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
v4l1_compat            13251  2 uvcvideo,videodev
hp_accel               11144  0 
snd_timer              19098  2 snd_pcm,snd_seq
mmc_block               8258  2 
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd_hwdep               5412  2 snd_usb_audio,snd_hda_codec
mac80211              205402  1 b43
snd                    54148  21 snd_hda_codec_intelhdmi,snd_hda_codec_idt,snd_usb_audio,snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_hda_codec,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device,snd_hwdep
lis3lv02d               6096  1 hp_accel
cfg80211              126496  2 b43,mac80211
input_polldev           2482  1 lis3lv02d
soundcore               6620  1 snd
sdhci_pci               5502  0 
sdhci                  15654  1 sdhci_pci
snd_page_alloc          7172  2 snd_hda_intel,snd_pcm
serio_raw               3978  0 
led_class               2864  3 b43,hp_accel,sdhci
intel_agp              24415  2 i915
lirc_ene0100            6600  0 
jmb38x_ms               7407  0 
lirc_dev                8884  1 lirc_ene0100
i2c_algo_bit            5028  1 i915
memstick                8237  1 jmb38x_ms
lp                      7028  0 
video                  17375  1 i915
agpgart                31788  2 drm,intel_agp
output                  1871  1 video
parport                32635  3 parport_pc,ppdev,lp
usbhid                 36174  0 
usb_storage            39585  0 
hid                    67032  1 usbhid
ahci                   32232  3 
ssb                    38902  1 b43
```

---

### Post by lbrty on 2010-10-04
Anyone?

---

### Post by donkyhotay on 2010-10-04
Seems like maybe the computer isn't finding GRUB. Maybe it's trying to boot from something else like that SD card. Double-check your boot options but even if they're right try removing any non-bootable media (CD/DVD, SD cards, flash drives, etc.) and see if it goes away.

---

### Post by lbrty on 2010-10-04
The GRUB menu appears and boots into Ubuntu (normal), but then a blinking underscore appears (normal) but once in a while just hangs (at the blinking underscore) instead going to the login menu.

The SD card is always plugged in and the machine boots fine a majority of the time. If it were the SD card would it not be causing this issue all the time?

---

### Post by donkyhotay on 2010-10-06
> **lbrty said:**
> The GRUB menu appears and boots into Ubuntu (normal), but then a blinking underscore appears (normal) but once in a while just hangs (at the blinking underscore) instead going to the login menu.

The SD card is always plugged in and the machine boots fine a majority of the time. If it were the SD card would it not be causing this issue all the time?

Not necessarily, I've seen intermittent similar issues with external USB hard drives. I'd try removing it and see what happens. Intermittent issues are of course really hard to identifiy and troubleshoot by their nature so you'll want to remove it and keep it out for awhile and reboot the computer a bit to see if it goes away or not.

---

### Post by lbrty on 2010-10-07
I will give it a try. Thanks for your assistance.

Does anyone else have any recommendations?

---

### Post by jtarin on 2010-10-07
What does ```
sudo fdisk -l
``` reveal....post.

---

### Post by lbrty on 2010-10-07
sudo fdisk -l output
```

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e3a36

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551       38914   292087809    5  Extended
/dev/sda5            2551       37820   283301888   83  Linux
/dev/sda6           37820       38914     8784896   82  Linux swap / Solaris

Disk /dev/mmcblk0: 8168 MB, 8168931328 bytes
39 heads, 5 sectors/track, 81820 cylinders
Units = cylinders of 195 * 512 = 99840 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1              43       81821     7973375+   b  W95 FAT32
```

---

### Post by aeronutt on 2010-10-07
FYI, I thought I'd fixed mine of this exact same problem...but just about an hour ago it happened again. So I'm guessing 1 in 20 times or so it happens to me.

---

### Post by lbrty on 2010-10-07
@aeronutt
What type of troubleshooting did you do?

---

### Post by aeronutt on 2010-10-07
Basically, I reinstalled grub. After help from several on here:

[http://ubuntuforums.org/showthread.php?t=1578033](http://ubuntuforums.org/showthread.php?t=1578033)

---

### Post by jtarin on 2010-10-08
There's a chance an update-grub command might work before you go the whole install route....but you might try it without any peripheral devices plugged in, whether you update or reinstall.

---

### Post by lbrty on 2010-10-08
I have done that in the past, however I did have peripheral devices plugged in. I will update-grub again with no peripherals to see if that resolves the issue.

On another note, do you think it could a bug that needs to be reported?

---

### Post by jtarin on 2010-10-08
> **lbrty said:**
> I have done that in the past, however I did have peripheral devices plugged in. I will update-grub again with no peripherals to see if that resolves the issue.

On another note, do you think it could a bug that needs to be reported?It could be a bug and it could be reported, but I wouldn't get too excited about reporting it.....do a search for it before you report....it might already be in the works.

---

