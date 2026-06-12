---
title: "Wifi not connecting"
date: 2011-05-15
forum: New to Ubuntu
---

### Post by superiorunderling on 2011-05-15
So, i just installed ubuntu 10.04 on my macbook 2,1.  Everything works just fine except for the wifi.  The wifi seems to be working since i can see the drop down menu with the different wireless networks.  The only issue is when i choose the one i want.  It goes for a while as though its connecting and then wont connect. I have no idea what to do about it and I've looked around but cant seem to find anyone with the same problem.  If anyone could help it would be much appreciated.

---

### Post by jtarin on 2011-05-15
> **superiorunderling said:**
> So, i just installed ubuntu 10.04 on my macbook 2,1.  Everything works just fine except for the wifi.  The wifi seems to be working since i can see the drop down menu with the different wireless networks.  The only issue is when i choose the one i want.  It goes for a while as though its connecting and then wont connect. I have no idea what to do about it and I've looked around but cant seem to find anyone with the same problem.  If anyone could help it would be much appreciated.In a terminal issue the following three separate commands and post the results here.
```
lspci
```
```
lsmod
```
```
ifconfig
```

---

### Post by superiorunderling on 2011-05-15
lspci:
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:07.0 Performance counters: Intel Corporation Device 27a3 (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 22)
02:00.0 Network controller: Atheros Communications Inc. AR5008 Wireless Network Adapter (rev 01)
03:03.0 FireWire (IEEE 1394): Agere Systems FW322/323 (rev 61)





lsmod

Module                  Size  Used by
binfmt_misc             6587  1 
rfcomm                 33421  4 
ppdev                   5259  0 
sco                     7885  2 
bridge                 45614  0 
stp                     1655  1 bridge
bnep                    9436  2 
l2cap                  30624  16 rfcomm,bnep
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
snd_hda_codec_idt      52010  1 
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_hda_intel          22069  2 
snd_hda_codec          74201  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
i915                  287810  3 
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
drm_kms_helper         29329  1 i915
drm                   162345  4 i915,drm_kms_helper
arc4                    1153  2 
ath9k                 306138  0 
mac80211              205402  1 ath9k
ath                     7611  1 ath9k
snd_seq_dummy           1338  0 
i2c_algo_bit            5028  1 i915
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
cfg80211              126528  3 ath9k,mac80211,ath
applesmc               20069  0 
snd_rawmidi            19056  1 snd_seq_midi
video                  17375  1 i915
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
led_class               2864  2 ath9k,applesmc
lp                      7028  0 
snd_timer              19098  2 snd_pcm,snd_seq
output                  1871  1 video
parport                32635  2 ppdev,lp
input_polldev           2482  1 applesmc
btusb                  10957  2 
mbp_nvidia_bl           1835  0 
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
isight_firmware         1906  0 
appletouch              8368  0 
snd                    54180  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
bluetooth              49892  9 rfcomm,sco,bnep,l2cap,btusb
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
intel_agp              24375  2 i915
agpgart                31724  2 drm,intel_agp
joydev                  8740  0 
hid_apple               4346  0 
usbhid                 36110  0 
hid                    67096  2 hid_apple,usbhid
usb_storage            39841  1 
ohci1394               26950  0 
ieee1394               81181  1 ohci1394
sky2                   40807  0 



ifconfig

eth0      Link encap:Ethernet  HWaddr 00:19:e3:43:d4:59  
          inet addr:192.168.1.69  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::219:e3ff:fe43:d459/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10583 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6303 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14730987 (14.7 MB)  TX bytes:521349 (521.3 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1b:63:cb:ce:b4  
          inet6 addr: fe80::21b:63ff:fecb:ceb4/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:395 (395.0 B)  TX bytes:2433 (2.4 KB)

---

### Post by jtarin on 2011-05-15
Everything look fine and should be connected.Is this a shared network? Maybe your set to "open" instead of "shared" network?

---

### Post by Uboo boo on 2011-05-16
> **superiorunderling said:**
> So, i just installed ubuntu 10.04 on my macbook 2,1. Everything works just fine except for the wifi. The wifi seems to be working since i can see the drop down menu with the different wireless networks. The only issue is when i choose the one i want. It goes for a while as though its connecting and then wont connect. I have no idea what to do about it and I've looked around but cant seem to find anyone with the same problem. If anyone could help it would be much appreciated.
 
 
Hi, I am having the same problem as the user above. But I am using a Dell Vostro 1400. With Ubuntu 10.10 The different wireless networks appear. But the one that I wish to use lags in to connecting and then disconnects totally. 
 
If you dont mind please can you assist me also, would be greatly appreciated.
 
Thanks.

---

### Post by wildmanne39 on 2011-05-16
> **Uboo boo said:**
> Hi, I am having the same problem as the user above. But I am using a Dell Vostro 1400. With Ubuntu 10.10 The different wireless networks appear. But the one that I wish to use lags in to connecting and then disconnects totally. 
 
If you dont mind please can you assist me also, would be greatly appreciated.
 
Thanks.
Hi, first we need to know what wireless card you have, so put the commands in to the terminal that you saw in the post above yours, and post them back here so we can look at them.:D

---

