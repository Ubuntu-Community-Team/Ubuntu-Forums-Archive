---
title: "Help with wireless internet access bcm4311"
date: 2010-10-07
forum: New to Ubuntu
---

### Post by fixmetwo on 2010-10-07
read everything tried everything to the point of confusion.
please look at code and help fix mt wireless.

```


me@ubuntu:~$ lspci

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 02)
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
07:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
me@ubuntu:~$ lsusb
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0c45:62c0 Microdia Sonix USB 2.0 Camera
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
me@ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:19 memory:b6000000-b6003fff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1a:73:63:54:f0
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
me@ubuntu:~$ lsmod
Module                  Size  Used by
binfmt_misc             7960  1 
ppdev                   6375  0 
snd_hda_codec_conexant    28841  1 
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
vga16fb                12757  0 
vgastate                9857  1 vga16fb
joydev                 11072  0 
arc4                    1473  2 
snd_hda_intel          25677  2 
snd_hda_codec          85759  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87882  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31219  0 
snd_seq_midi            5829  0 
snd_rawmidi            23420  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23649  2 snd_pcm,snd_seq
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
nouveau               515227  2 
ttm                    60847  1 nouveau
drm_kms_helper         30742  1 nouveau
b43                   182322  0 
uvcvideo               62467  0 
snd                    71106  16  snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac80211              238448  1 b43
videodev               40518  1 uvcvideo
v4l1_compat            15495  2 uvcvideo,videodev
v4l2_compat_ioctl32    12020  1 videodev
drm                   199204  4 nouveau,ttm,drm_kms_helper
ricoh_mmc               3416  0 
sdhci_pci               6700  0 
sdhci                  17928  1 sdhci_pci
soundcore               8052  1 snd
k8temp                  3912  0 
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
cfg80211              148546  2 b43,mac80211
led_class               3764  2 b43,sdhci
i2c_algo_bit            6024  1 nouveau
edac_core              45423  0 
edac_mce_amd            9278  0 
psmouse                64576  0 
serio_raw               4918  0 
i2c_nforce2             6099  0 
video                  20623  0 
output                  2503  1 video
lp                      9336  0 
parport                37160  2 ppdev,lp
ohci1394               30260  0 
ieee1394               94771  1 ohci1394
ssb                    45092  1 b43
pata_amd               11962  0 
forcedeth              55592  0 
sata_nv                23778  1 
me@ubuntu:~$ ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
bcmwl5 : driver installed
    device (14E4:4311) present (alternate driver: ssb)
me@ubuntu:~$ cat /etc/modprobe.d/blacklist.conf
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
me@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:ff/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:ff   Fragment thr:ff
          Power Management:ff
          


me@ubuntu:~$ cd wdriv
me@ubuntu:~/wdriv$ ll
total 2652
drwx------  2 me me   4096 2010-10-02 15:32 ./
drwxr-xr-x 33 me me   4096 2010-10-07 11:47 ../
-rwxr-xr-x  1 me me 983552 2007-08-13 14:46 bcmwl564.sys*
-rwxr-xr-x  1 me me 803496 2007-08-13 14:46 bcmwl5.inf*
-rwxr-xr-x  1 me me 822272 2007-08-13 14:46 bcmwl5.sys*
-rwxr-xr-x  1 me me  21358 2010-10-02 01:14 ndisgtk_0.8.5-1_amd64.deb*
-rwxr-xr-x  1 me me  21668 2010-10-02 01:13 ndiswrapper-common_1.54-2ubuntu1_all.deb*
-rwxr-xr-x  1 me me  36986 2010-10-02 01:13 ndiswrapper-utils-1.9_1.54-2ubuntu1_amd64.deb*
me@ubuntu:~/wdriv$ sudo ndiswrapper -i bcmwl5.inf
[sudo] password for me: 
driver bcmwl5 is already installed
me@ubuntu:~/wdriv$ sudo ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
bcmwl5 : driver installed
    device (14E4:4311) present (alternate driver: ssb)
me@ubuntu:~/wdriv$ sudo depmod -a
me@ubuntu:~/wdriv$ sudo modprobe ndiswrapper
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
me@ubuntu:~/wdriv$ sudo ndiswrapper -m
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive



me@ubuntu:~/wdriv$ lsmod
Module                  Size  Used by
ndiswrapper           244768  0 
binfmt_misc             7960  1 
ppdev                   6375  0 
snd_hda_codec_conexant    28841  1 
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
vga16fb                12757  0 
vgastate                9857  1 vga16fb
joydev                 11072  0 
arc4                    1473  2 
snd_hda_intel          25677  2 
snd_hda_codec          85759  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87882  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31219  0 
snd_seq_midi            5829  0 
snd_rawmidi            23420  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23649  2 snd_pcm,snd_seq
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
nouveau               515227  2 
ttm                    60847  1 nouveau
drm_kms_helper         30742  1 nouveau
b43                   182322  0 
uvcvideo               62467  0 
snd                    71106  16  snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac80211              238448  1 b43
videodev               40518  1 uvcvideo
v4l1_compat            15495  2 uvcvideo,videodev
v4l2_compat_ioctl32    12020  1 videodev
drm                   199204  4 nouveau,ttm,drm_kms_helper
ricoh_mmc               3416  0 
sdhci_pci               6700  0 
sdhci                  17928  1 sdhci_pci
soundcore               8052  1 snd
k8temp                  3912  0 
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
cfg80211              148546  2 b43,mac80211
led_class               3764  2 b43,sdhci
i2c_algo_bit            6024  1 nouveau
edac_core              45423  0 
edac_mce_amd            9278  0 
psmouse                64576  0 
serio_raw               4918  0 
i2c_nforce2             6099  0 
video                  20623  0 
output                  2503  1 video
lp                      9336  0 
parport                37160  2 ppdev,lp
ohci1394               30260  0 
ieee1394               94771  1 ohci1394
ssb                    45092  1 b43
pata_amd               11962  0 
forcedeth              55592  0 
sata_nv                23778  1 
me@ubuntu:~/wdriv$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:24:53:e2:dc  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:156 errors:0 dropped:0 overruns:0 frame:0
          TX packets:156 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:12208 (12.2 KB)  TX bytes:12208 (12.2 KB)

me@ubuntu:~/wdriv$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID: off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr: off   Fragment thr: off
          Power Management:ff
          
me@ubuntu:~/wdriv$ echo ndiswrapper | sudo tee -a /etc/modules
ndiswrapper
me@ubuntu:~/wdriv$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...       ############################[ OK ] 
me@ubuntu:~/wdriv$ sudo iwconfig Wlan0 essid "netgear"
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device Wlan0 ; No such device.
me@ubuntu:~/wdriv$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr: off   Fragment thr: off
          Power Management: off
          
me@ubuntu:~/wdriv$

```

---

### Post by Hippytaff on 2010-10-07
so you've tried blacklisting the conflicting driver and using the windows driver with Nsdiwrapper?

---

### Post by drs305 on 2010-10-07
I used to have to jump through all sorts of hoops to get my Broadcom 4311 wireless working: blacklists, ndiswrapper, etc.

With Lucid, all I had to do is go to System, Administration, Hardware Drivers. The Broadcom STA Wireless Driver was already listed and all I had to do was activate it. 

I know that is pretty simplistic but sometimes the obvious is overlooked.

---

### Post by fixmetwo on 2010-10-07
I thought I did - my head is spinning- do you see something?

---

### Post by Locke_99GS on 2010-10-07
```

sudo su 
apt-get update
apt-get install bcmwl-kernel-source
jockey-gtk 

```
Activate the Broadcom STA driver.
```

modprobe -r b43 ssb wl
modprobe wl
service network-manager restart
exit

```

If you don't have wireless access immediately, try rebooting.

---

### Post by fixmetwo on 2010-10-07
I don' have anything listed in the hardware manager- I installed from internet download
and don't have access to update drivers and no wire to connect to dsl modem

---

### Post by Locke_99GS on 2010-10-07
Without internet connection, I assume you have a install CD?

1. Open Synaptic Pacakage Manager
2. Ensure LiveCd is in CD drive
3. Settings > Repositories > Ubuntu Software
4. Check the installable from cd and close
5. Refresh
6. Search for "bcmwl-kernel-source"
7. Mark for installation
8. Install it
9. Reboot computer

---

