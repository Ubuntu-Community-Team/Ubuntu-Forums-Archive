---
title: "Wireless issue"
date: 2011-07-14
forum: New to Ubuntu
---

### Post by nynoah on 2011-07-14
Wireless issue....

I have a friend who is trying to use his Ubuntu system to connect to a local guest network.  For some reason the guy next to him has no problem with connecting and he is on Windows 7.  

Any ideas why he is having issues?

Ifconfi - a 
[I]eth0 Link encap:Ethernet HWaddr 00:13:a9:48:c3:00 
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:20 errors:0 dropped:0 overruns:0 frame:0
TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:1272 (1.2 KB) TX bytes:1272 (1.2 KB)

wlan0 Link encap:Ethernet HWaddr 00:18:de:62:86:9d 
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)[/I]

---

### Post by wildmanne39 on 2011-07-14
Hi, run these command in a terminal
```
sudo lshw -C network
```
```
lspci -nn
```
```
lsmod

```
and post the outcome  here by clicking on new reply and click # and paste the information between the brackets.

---

### Post by nynoah on 2011-07-14
```
*-network 
description: Wireless interface
product: PRO/Wireless 3945ABG [Golan] Network Connection
vendor: Intel Corporation
physical id: 0
bus info: pci@0000:06:00.0
logical name: wlan0
version: 02
serial: 00:18:de:62:86:9d
width: 32 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=iwl3945 latency=0 multicast=yes wireless=IEEE 802.11abg
resources: irq:28 memory:cc000000-cc000fff
*-network
description: Ethernet interface
product: PRO/100 VE Network Connection
vendor: Intel Corporation
physical id: 8
bus info: pci@0000:0a:08.0
logical name: eth0
version: 02
serial: 00:13:a9:48:c3:00
size: 10MB/s
capacity: 100MB/s
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half firmware=N/A latency=64 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10MB/s
[FONT='Liberation Serif','serif'] resources: irq:20 memory:d0005000-d0005fff ioport:6000(size=64)[/font]

Quote:
lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 02)
00:1c.2 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 3 [8086:27d4] (rev 02)
00:1c.3 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 4 [8086:27d6] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 02)
00:1f.2 IDE interface [0101]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller [8086:27c4] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 02)
06:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
0a:03.0 CardBus bridge [0607]: Texas Instruments PCIxx12 Cardbus Controller [104c:8039]
0a:03.1 FireWire (IEEE 1394) [0c00]: Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller [104c:803a]
0a:03.2 Mass storage controller [0180]: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD) [104c:803b]
[FONT='Liberation Serif','serif']0a:08.0 Ethernet controller [0200]: Intel Corporation PRO/100 VE Network Connection [8086:1092] (rev 02)[/font]

Quote:
lsmod
Module Size Used by
nls_iso8859_1 3249 1
nls_cp437 4919 1
vfat 8933 1
fat 47767 1 vfat
usb_storage 39841 1
binfmt_misc 6587 1
ppdev 5259 0
sonypi 14701 0
snd_hda_codec_idt 52042 1
fbcon 35102 71
tileblit 1999 1 fbcon
font 7557 1 fbcon
bitblit 4707 1 fbcon
softcursor 1189 1 bitblit
vga16fb 11385 0
vgastate 8961 1 vga16fb
joydev 8740 0
pcmcia 30784 0
snd_hda_intel 22069 2
snd_hda_codec 74201 2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep 5412 1 snd_hda_codec
arc4 1153 2
snd_pcm_oss 35308 0
snd_mixer_oss 13746 1 snd_pcm_oss
snd_pcm 70694 3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy 1338 0
snd_seq_oss 26722 0
snd_seq_midi 4557 0
snd_rawmidi 19056 1 snd_seq_midi
snd_seq_midi_event 6003 2 snd_seq_oss,snd_seq_midi
snd_seq 47263 6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_mid i_event
iwl3945 68727 0
snd_timer 19098 2 snd_pcm,snd_seq
snd_seq_device 5700 5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi ,snd_seq
iwlcore 106050 1 iwl3945
i915 287810 3
drm_kms_helper 29329 1 i915
gspca_vc032x 21551 0
gspca_main 21199 1 gspca_vc032x
mac80211 205402 2 iwl3945,iwlcore
tifm_7xx1 3690 0
drm 162377 4 i915,drm_kms_helper
snd 54244 16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_ hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_os s,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videodev 34361 1 gspca_main
led_class 2864 2 iwl3945,iwlcore
v4l1_compat 13251 1 videodev
yenta_socket 20408 1
rsrc_nonstatic 10015 1 yenta_socket
tifm_core 6045 1 tifm_7xx1
psmouse 63245 0
serio_raw 3978 0
cfg80211 126144 3 iwl3945,iwlcore,mac80211
pcmcia_core 32964 3 pcmcia,yenta_socket,rsrc_nonstatic
sony_laptop 28248 0
soundcore 6620 1 snd
snd_page_alloc 7076 2 snd_hda_intel,snd_pcm
intel_agp 24375 2 i915
sbp2 19448 0
agpgart 31724 2 drm,intel_agp
i2c_algo_bit 5028 1 i915
video 17375 1 i915
output 1871 1 video
lp 7028 0
parport 32635 2 ppdev,lp
e100 28211 0
mii 4381 1 e100
ohci1394 26950 0
ieee1394 81181 2 sbp2,ohci1394

```

---

### Post by wildmanne39 on 2011-07-14
Hi, yes that is what they are for, It is a starting point. Please run these in a terminal
```
sudo rmmod -f hp-wmi
sudo rfkill unblock all
rfkill list all
```
and post the outcome  here by clicking on new reply and click # and paste the information between the brackets.

---

### Post by StealthMode on 2011-07-15
Hey all, I'm the one that nynoah was trying to help. I wasnt' aware that he started a thread here, but I'll use all the help I can get! I have a thread at [http://ubuntuforums.org/showthread.php?t=1804289](http://ubuntuforums.org/showthread.php?t=1804289) . 
 
I ran "sudo rmmod -f hp-wmi and got "ERROR: Removing 'hp_wmi': No such file or directory." 
I ran "sudo rfkill unblock all" and it didn't give a response. 
I ran "rfkill list all" and got 
>  0: phy0: Wireless LAN
Soft blocked: no
Hard blocked: no

---

### Post by wildmanne39 on 2011-07-15
Hi, I will let chili help you on the other thread he is the best at this.

---

