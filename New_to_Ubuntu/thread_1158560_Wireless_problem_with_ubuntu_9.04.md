---
title: "Wireless problem with ubuntu 9.04"
date: 2009-05-13
forum: New to Ubuntu
---

### Post by Torleif67 on 2009-05-13
I have an HP G7000 laptop where i run Ubuntu 8.10 on. Everything works fine for me but then i upgraded to Ubuntu 9.04 the other day and since then i cannot connect to the internet with wireless connection.

Under network connection, wired i have Autho eth0, wireless is missing completely from the list. How do i get my wireless back working again?

Here are some info regarding my computer from the terminal:

uname -a
code:
Linux lybeth-laptop 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux

lspci | grep -i net
code:
01:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

iwconfig
code:
lo no wireless extensions.

eth0 no wireless extensions.

pan0 no wireless extensions.


ifconfig
code.
eth0 Link encap:Ethernet HWaddr 00:1b:38:f5:44:86
inet6 addr: fe80::21b:38ff:fef5:4486/64 Scope:Link
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:1151 errors:0 dropped:0 overruns:0 frame:0
TX packets:1264 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:1091266 (1.0 MB) TX bytes:194526 (194.5 KB)
Interrupt:16 Base address:0x1000

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:24 errors:0 dropped:0 overruns:0 frame:0
TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:1664 (1.6 KB) TX bytes:1664 (1.6 KB)


This is what i have under hardware drivers:

Alternate "madwifi" driver for Atheros wireless LAN cards.

Only activate this driver if you have problems with your wireless LAN connection.

The free "ath5k" driver should work with most Atheros cards nowadays, but on some computers this alternate (but proprietary) driver still works better, or at all.

But if i activate this driver as it says, nothing will happen. I still cannot use my wireless... 

Is there anybody around who knows anything about this who could please help me?

Torleif

---

### Post by coffeeaddict22 on 2009-05-13
Hi,
Could you try ```
lshw -C network
``` and post the results of that back?  There's a driver problem, and that's one of the few places that clearly tells you what the driver is...

---

### Post by lkraemer on 2009-05-13
67,
Make sure you have a wired LAN connection.  Then you should be able to
go to: SYSTEM -> ADMINISTRATION -> HARDWARE DRIVERS and ENABLE the Wifi
Restricted Drivers.  This will download the firmware to your system, if you have a wired connection. Reboot.

If this works there should be folders b43 and b43legacy under /lib/firmware
and each folder should have some *.fw files in it.

Open a Terminal window and cut/paste each command one at a time.

```

lshw -C network
lsmod
ndiswrapper -l
cat /etc/modprobe.d/blacklist     OR for 9.04 use cat /etc/modprobe.d/blacklist.conf
iwconfig 
cd /
cd /lib/firmware
ls -alt
cd /b43
ls -alt

```
Then post the output, separated so it is easy to read, as this will give
us a clue as to what is loaded and blacklisted. Do this before you proceed!


The next steps will be determined by what you post from the previous
request.

If this were a fresh install, it might have been easier, but you should still be able to get it working.


lkraemer

---

### Post by Torleif67 on 2009-05-13
> **coffeeaddict22 said:**
> Hi,
Could you try ```
lshw -C network
``` and post the results of that back?  There's a driver problem, and that's one of the few places that clearly tells you what the driver is...


should run this program as super-user.
  *-network UNCLAIMED     
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 10
       serial: 00:1b:38:f5:44:86
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.101 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 56:0f:c0:56:f1:94
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

---

### Post by Torleif67 on 2009-05-14
lshw -C network

lybeth@lybeth-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 10
       serial: 00:1b:38:f5:44:86
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.101 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 56:0f:c0:56:f1:94
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
lybeth@lybeth-laptop:~$

---

### Post by Torleif67 on 2009-05-14
lsmod

Module                  Size  Used by
nls_iso8859_1          12032  0 
nls_cp437              13696  0 
vfat                   18816  0 
fat                    58272  1 vfat
usb_storage            82880  0 
i915                   65540  2 
drm                    96296  3 i915
binfmt_misc            16776  1 
ppdev                  15620  0 
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
input_polldev          11912  0 
ath_pci                99224  0 
wlan                  210288  1 ath_pci
ath_hal               198864  1 ath_pci
lp                     17156  0 
parport                42220  2 ppdev,lp
joydev                 18368  0 
snd_hda_intel         435636  2 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
intel_agp              34108  1 
agpgart                42696  3 drm,intel_agp
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
pcspkr                 10496  0 
snd                    62628  13 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
iTCO_wdt               19108  0 
iTCO_vendor_support    11652  1 iTCO_wdt
psmouse                61972  0 
uvcvideo               63240  0 
compat_ioctl32          9344  1 uvcvideo
videodev               41600  1 uvcvideo
v4l1_compat            21764  2 uvcvideo,videodev
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
serio_raw              13316  0 
video                  25360  0 
output                 11008  1 video
8139too                32128  0 
8139cp                 27776  0 
mii                    13312  2 8139too,8139cp
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
lybeth@lybeth-laptop:~$

---

### Post by Torleif67 on 2009-05-14
ndiswrapper -l

The program 'ndiswrapper' is currently not installed.  You can install it by typing:
sudo apt-get install ndiswrapper-common
bash: ndiswrapper: command not found

---

### Post by Torleif67 on 2009-05-14
cat /etc/modprobe.d/blacklist

cat: /etc/modprobe.d/blacklist: No such file or directory

---

### Post by Torleif67 on 2009-05-14
iwconfig 

lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

---

### Post by Torleif67 on 2009-05-14
cd /
lybeth@lybeth-laptop:/$ cd /lib/firmware
lybeth@lybeth-laptop:/lib/firmware$ ls -alt
total 6544
drwxr-xr-x  6 root root  12288 2009-05-08 07:13 .
drwxr-xr-x 19 root root  12288 2009-05-08 07:11 ..
drwxr-xr-x 13 root root   4096 2009-05-08 00:30 acx
lrwxrwxrwx  1 root root     14 2009-05-08 00:30 NPE-B -> NPE-B.01020201
lrwxrwxrwx  1 root root     14 2009-05-08 00:30 NPE-C -> NPE-C.02020201
drwxr-xr-x  2 root root   4096 2009-05-08 00:30 zd1211
drwxr-xr-x 15 root root   4096 2009-05-08 00:26 2.6.28-11-generic
drwxr-xr-x 14 root root   4096 2009-04-15 22:32 2.6.27-11-generic
-rw-r--r--  1 root root 132978 2009-04-03 05:46 ql2322_fw.bin
-rw-r--r--  1 root root 206500 2009-04-03 05:46 ql2400_fw.bin
-rw-r--r--  1 root root   8192 2009-04-03 05:46 rt2561.bin
-rw-r--r--  1 root root   8192 2009-04-03 05:46 rt2561s.bin
-rw-r--r--  1 root root   8192 2009-04-03 05:46 rt2661.bin
-rw-r--r--  1 root root   8192 2009-04-03 05:46 rt2860.bin
-rw-r--r--  1 root root   4096 2009-04-03 05:46 rt2870.bin
-rw-r--r--  1 root root   2048 2009-04-03 05:46 rt73.bin
-rw-r--r--  1 root root  62484 2009-04-03 05:46 zd1201-ap.fw
-rw-r--r--  1 root root  70612 2009-04-03 05:46 zd1201.fw
-rw-r--r--  1 root root  22622 2009-04-03 05:46 aic94xx-seq.fw
-rw-r--r--  1 root root  30348 2009-04-03 05:46 atmel_at76c502_3com.bin
-rw-r--r--  1 root root  35184 2009-04-03 05:46 atmel_at76c502_3com-wpa.bin
-rw-r--r--  1 root root  31764 2009-04-03 05:46 atmel_at76c502.bin
-rw-r--r--  1 root root  31764 2009-04-03 05:46 atmel_at76c502d.bin
-rw-r--r--  1 root root  35276 2009-04-03 05:46 atmel_at76c502d-wpa.bin
-rw-r--r--  1 root root  31776 2009-04-03 05:46 atmel_at76c502e.bin
-rw-r--r--  1 root root  35272 2009-04-03 05:46 atmel_at76c502e-wpa.bin
-rw-r--r--  1 root root  35276 2009-04-03 05:46 atmel_at76c502-wpa.bin
-rw-r--r--  1 root root  28156 2009-04-03 05:46 atmel_at76c503-i3861.bin
-rw-r--r--  1 root root  28032 2009-04-03 05:46 atmel_at76c503-i3863.bin
-rw-r--r--  1 root root  35372 2009-04-03 05:46 atmel_at76c503-rfmd-0.90.2-140.bin
-rw-r--r--  1 root root  37800 2009-04-03 05:46 atmel_at76c503-rfmd-acc.bin
-rw-r--r--  1 root root  37956 2009-04-03 05:46 atmel_at76c503-rfmd.bin
-rw-r--r--  1 root root  35180 2009-04-03 05:46 atmel_at76c504_2958-wpa.bin
-rw-r--r--  1 root root  39928 2009-04-03 05:46 atmel_at76c504a_2958-wpa.bin
-rw-r--r--  1 root root  31748 2009-04-03 05:46 atmel_at76c504.bin
-rw-r--r--  1 root root  35196 2009-04-03 05:46 atmel_at76c504c-wpa.bin
-rw-r--r--  1 root root  37005 2009-04-03 05:46 atmel_at76c505a-rfmd2958.bin
-rw-r--r--  1 root root  36992 2009-04-03 05:46 atmel_at76c505-rfmd2958.bin
-rw-r--r--  1 root root  35528 2009-04-03 05:46 atmel_at76c505-rfmd.bin
-rw-r--r--  1 root root  31824 2009-04-03 05:46 atmel_at76c506.bin
-rw-r--r--  1 root root  35228 2009-04-03 05:46 atmel_at76c506-wpa.bin
-rw-r--r--  1 root root 114688 2009-04-03 05:46 BCM2033-FW.BIN
-rw-r--r--  1 root root   3245 2009-04-03 05:46 BCM2033-MD.BIN
-rw-r--r--  1 root root  32522 2009-04-03 05:46 dvb-fe-cx24116.fw
-rw-r--r--  1 root root  12772 2009-04-03 05:46 dvb-fe-or51132-qam.fw
-rw-r--r--  1 root root  17532 2009-04-03 05:46 dvb-fe-or51132-vsb.fw
-rw-r--r--  1 root root   8518 2009-04-03 05:46 dvb-fe-or51211.fw
-rw-r--r--  1 root root  24478 2009-04-03 05:46 dvb-fe-tda10046.fw
-rw-r--r--  1 root root 239956 2009-04-03 05:46 dvb-ttpci-01.fw
-rw-r--r--  1 root root  12700 2009-04-03 05:46 dvb-usb-af9015.fw
-rw-r--r--  1 root root  10757 2009-04-03 05:46 dvb-usb-avertv-a800-02.fw
-rw-r--r--  1 root root   9025 2009-04-03 05:46 dvb-usb-bluebird-01.fw
-rw-r--r--  1 root root  34306 2009-04-03 05:46 dvb-usb-dib0700-1.10.fw
-rw-r--r--  1 root root  33768 2009-04-03 05:46 dvb-usb-dib0700-1.20.fw
-rw-r--r--  1 root root   9180 2009-04-03 05:46 dvb-usb-dibusb-5.0.0.11.fw
-rw-r--r--  1 root root   7558 2009-04-03 05:46 dvb-usb-dibusb-6.0.0.8.fw
-rw-r--r--  1 root root   7431 2009-04-03 05:46 dvb-usb-dtt200u-01.fw
-rw-r--r--  1 root root   3360 2009-04-03 05:46 dvb-usb-tvwalkert.fw
-rw-r--r--  1 root root   4286 2009-04-03 05:46 dvb-usb-umt-010-02.fw
-rw-r--r--  1 root root  10752 2009-04-03 05:46 dvb-usb-vp702x-01.fw
-rw-r--r--  1 root root  10752 2009-04-03 05:46 dvb-usb-vp7045-01.fw
-rw-r--r--  1 root root   8480 2009-04-03 05:46 dvb-usb-wt220u-02.fw
-rw-r--r--  1 root root  12902 2009-04-03 05:46 dvb-usb-wt220u-fc03.fw
-rw-r--r--  1 root root   8518 2009-04-03 05:46 dvb-usb-wt220u-zl0353-01.fw
-rw-r--r--  1 root root 209190 2009-04-03 05:46 ipw2100-1.3.fw
-rw-r--r--  1 root root 201138 2009-04-03 05:46 ipw2100-1.3-i.fw
-rw-r--r--  1 root root 196458 2009-04-03 05:46 ipw2100-1.3-p.fw
-rw-r--r--  1 root root 191142 2009-04-03 05:46 ipw2200-bss.fw
-rw-r--r--  1 root root 185660 2009-04-03 05:46 ipw2200-ibss.fw
-rw-r--r--  1 root root 187836 2009-04-03 05:46 ipw2200-sniffer.fw
-rw-r--r--  1 root root 112128 2009-04-03 05:46 isl3877
-rw-r--r--  1 root root  29024 2009-04-03 05:46 isl3886
-rw-r--r--  1 root root  30060 2009-04-03 05:46 isl3887usb_bare
-rw-r--r--  1 root root  93996 2009-04-03 05:46 isl3890
-rw-r--r--  1 root root  29468 2009-04-03 05:46 isl3890usb
-rw-r--r--  1 root root 149652 2009-04-03 05:46 iwlwifi-3945-1.ucode
-rw-r--r--  1 root root 149816 2009-04-03 05:46 iwlwifi-3945-2.ucode
-rw-r--r--  1 root root 187608 2009-04-03 05:46 iwlwifi-4965-1.ucode
-rw-r--r--  1 root root 187764 2009-04-03 05:46 iwlwifi-4965-2.ucode
-rw-r--r--  1 root root 345008 2009-04-03 05:46 iwlwifi-5000-1.ucode
-rw-r--r--  1 root root 118884 2009-04-03 05:46 lbtf_usb.bin
-rw-r--r--  1 root root  76802 2009-04-03 05:46 ql2100_fw.bin
-rw-r--r--  1 root root  84566 2009-04-03 05:46 ql2200_fw.bin
-rw-r--r--  1 root root 123170 2009-04-03 05:46 ql2300_fw.bin
-rw-r--r--  1 root root 141200 2009-04-03 05:46 v4l-cx23418-apu.fw
-rw-r--r--  1 root root 158332 2009-04-03 05:46 v4l-cx23418-cpu.fw
-rw-r--r--  1 root root  16382 2009-04-03 05:46 v4l-cx23418-dig.fw
-rw-r--r--  1 root root 262144 2009-04-03 05:46 v4l-cx2341x-dec.fw
-rw-r--r--  1 root root 376836 2009-04-03 05:46 v4l-cx2341x-enc.fw
-rw-r--r--  1 root root 155648 2009-04-03 05:46 v4l-cx2341x-init.mpg
-rw-r--r--  1 root root  16382 2009-04-03 05:46 v4l-cx23885-avcore-01.fw
-rw-r--r--  1 root root 376836 2009-04-03 05:46 v4l-cx23885-enc.fw
-rw-r--r--  1 root root  16382 2009-04-03 05:46 v4l-cx25840.fw
-rw-r--r--  1 root root   8192 2009-04-03 05:46 v4l-pvrusb2-24xxx-01.fw
-rw-r--r--  1 root root   8192 2009-04-03 05:46 v4l-pvrusb2-29xxx-01.fw
-rw-r--r--  1 root root  15664 2009-02-14 05:30 NPE-C.02020201
-rw-r--r--  1 root root  15664 2009-02-14 05:30 NPE-B.01020201



lybeth@lybeth-laptop:/lib/firmware$ cd /b43
bash: cd: /b43: No such file or directory
lybeth@lybeth-laptop:/lib/firmware$ ls -alt
total 6544
drwxr-xr-x  6 root root  12288 2009-05-08 07:13 .
drwxr-xr-x 19 root root  12288 2009-05-08 07:11 ..
drwxr-xr-x 13 root root   4096 2009-05-08 00:30 acx
lrwxrwxrwx  1 root root     14 2009-05-08 00:30 NPE-B -> NPE-B.01020201
lrwxrwxrwx  1 root root     14 2009-05-08 00:30 NPE-C -> NPE-C.02020201
drwxr-xr-x  2 root root   4096 2009-05-08 00:30 zd1211
drwxr-xr-x 15 root root   4096 2009-05-08 00:26 2.6.28-11-generic
drwxr-xr-x 14 root root   4096 2009-04-15 22:32 2.6.27-11-generic
-rw-r--r--  1 root root 132978 2009-04-03 05:46 ql2322_fw.bin
-rw-r--r--  1 root root 206500 2009-04-03 05:46 ql2400_fw.bin
-rw-r--r--  1 root root   8192 2009-04-03 05:46 rt2561.bin
-rw-r--r--  1 root root   8192 2009-04-03 05:46 rt2561s.bin
-rw-r--r--  1 root root   8192 2009-04-03 05:46 rt2661.bin
-rw-r--r--  1 root root   8192 2009-04-03 05:46 rt2860.bin
-rw-r--r--  1 root root   4096 2009-04-03 05:46 rt2870.bin
-rw-r--r--  1 root root   2048 2009-04-03 05:46 rt73.bin
-rw-r--r--  1 root root  62484 2009-04-03 05:46 zd1201-ap.fw
-rw-r--r--  1 root root  70612 2009-04-03 05:46 zd1201.fw
-rw-r--r--  1 root root  22622 2009-04-03 05:46 aic94xx-seq.fw
-rw-r--r--  1 root root  30348 2009-04-03 05:46 atmel_at76c502_3com.bin
-rw-r--r--  1 root root  35184 2009-04-03 05:46 atmel_at76c502_3com-wpa.bin
-rw-r--r--  1 root root  31764 2009-04-03 05:46 atmel_at76c502.bin
-rw-r--r--  1 root root  31764 2009-04-03 05:46 atmel_at76c502d.bin
-rw-r--r--  1 root root  35276 2009-04-03 05:46 atmel_at76c502d-wpa.bin
-rw-r--r--  1 root root  31776 2009-04-03 05:46 atmel_at76c502e.bin
-rw-r--r--  1 root root  35272 2009-04-03 05:46 atmel_at76c502e-wpa.bin
-rw-r--r--  1 root root  35276 2009-04-03 05:46 atmel_at76c502-wpa.bin
-rw-r--r--  1 root root  28156 2009-04-03 05:46 atmel_at76c503-i3861.bin
-rw-r--r--  1 root root  28032 2009-04-03 05:46 atmel_at76c503-i3863.bin
-rw-r--r--  1 root root  35372 2009-04-03 05:46 atmel_at76c503-rfmd-0.90.2-140.bin
-rw-r--r--  1 root root  37800 2009-04-03 05:46 atmel_at76c503-rfmd-acc.bin
-rw-r--r--  1 root root  37956 2009-04-03 05:46 atmel_at76c503-rfmd.bin
-rw-r--r--  1 root root  35180 2009-04-03 05:46 atmel_at76c504_2958-wpa.bin
-rw-r--r--  1 root root  39928 2009-04-03 05:46 atmel_at76c504a_2958-wpa.bin
-rw-r--r--  1 root root  31748 2009-04-03 05:46 atmel_at76c504.bin
-rw-r--r--  1 root root  35196 2009-04-03 05:46 atmel_at76c504c-wpa.bin
-rw-r--r--  1 root root  37005 2009-04-03 05:46 atmel_at76c505a-rfmd2958.bin
-rw-r--r--  1 root root  36992 2009-04-03 05:46 atmel_at76c505-rfmd2958.bin
-rw-r--r--  1 root root  35528 2009-04-03 05:46 atmel_at76c505-rfmd.bin
-rw-r--r--  1 root root  31824 2009-04-03 05:46 atmel_at76c506.bin
-rw-r--r--  1 root root  35228 2009-04-03 05:46 atmel_at76c506-wpa.bin
-rw-r--r--  1 root root 114688 2009-04-03 05:46 BCM2033-FW.BIN
-rw-r--r--  1 root root   3245 2009-04-03 05:46 BCM2033-MD.BIN
-rw-r--r--  1 root root  32522 2009-04-03 05:46 dvb-fe-cx24116.fw
-rw-r--r--  1 root root  12772 2009-04-03 05:46 dvb-fe-or51132-qam.fw
-rw-r--r--  1 root root  17532 2009-04-03 05:46 dvb-fe-or51132-vsb.fw
-rw-r--r--  1 root root   8518 2009-04-03 05:46 dvb-fe-or51211.fw
-rw-r--r--  1 root root  24478 2009-04-03 05:46 dvb-fe-tda10046.fw
-rw-r--r--  1 root root 239956 2009-04-03 05:46 dvb-ttpci-01.fw
-rw-r--r--  1 root root  12700 2009-04-03 05:46 dvb-usb-af9015.fw
-rw-r--r--  1 root root  10757 2009-04-03 05:46 dvb-usb-avertv-a800-02.fw
-rw-r--r--  1 root root   9025 2009-04-03 05:46 dvb-usb-bluebird-01.fw
-rw-r--r--  1 root root  34306 2009-04-03 05:46 dvb-usb-dib0700-1.10.fw
-rw-r--r--  1 root root  33768 2009-04-03 05:46 dvb-usb-dib0700-1.20.fw
-rw-r--r--  1 root root   9180 2009-04-03 05:46 dvb-usb-dibusb-5.0.0.11.fw
-rw-r--r--  1 root root   7558 2009-04-03 05:46 dvb-usb-dibusb-6.0.0.8.fw
-rw-r--r--  1 root root   7431 2009-04-03 05:46 dvb-usb-dtt200u-01.fw
-rw-r--r--  1 root root   3360 2009-04-03 05:46 dvb-usb-tvwalkert.fw
-rw-r--r--  1 root root   4286 2009-04-03 05:46 dvb-usb-umt-010-02.fw
-rw-r--r--  1 root root  10752 2009-04-03 05:46 dvb-usb-vp702x-01.fw
-rw-r--r--  1 root root  10752 2009-04-03 05:46 dvb-usb-vp7045-01.fw
-rw-r--r--  1 root root   8480 2009-04-03 05:46 dvb-usb-wt220u-02.fw
-rw-r--r--  1 root root  12902 2009-04-03 05:46 dvb-usb-wt220u-fc03.fw
-rw-r--r--  1 root root   8518 2009-04-03 05:46 dvb-usb-wt220u-zl0353-01.fw
-rw-r--r--  1 root root 209190 2009-04-03 05:46 ipw2100-1.3.fw
-rw-r--r--  1 root root 201138 2009-04-03 05:46 ipw2100-1.3-i.fw
-rw-r--r--  1 root root 196458 2009-04-03 05:46 ipw2100-1.3-p.fw
-rw-r--r--  1 root root 191142 2009-04-03 05:46 ipw2200-bss.fw
-rw-r--r--  1 root root 185660 2009-04-03 05:46 ipw2200-ibss.fw
-rw-r--r--  1 root root 187836 2009-04-03 05:46 ipw2200-sniffer.fw
-rw-r--r--  1 root root 112128 2009-04-03 05:46 isl3877
-rw-r--r--  1 root root  29024 2009-04-03 05:46 isl3886
-rw-r--r--  1 root root  30060 2009-04-03 05:46 isl3887usb_bare
-rw-r--r--  1 root root  93996 2009-04-03 05:46 isl3890
-rw-r--r--  1 root root  29468 2009-04-03 05:46 isl3890usb
-rw-r--r--  1 root root 149652 2009-04-03 05:46 iwlwifi-3945-1.ucode
-rw-r--r--  1 root root 149816 2009-04-03 05:46 iwlwifi-3945-2.ucode
-rw-r--r--  1 root root 187608 2009-04-03 05:46 iwlwifi-4965-1.ucode
-rw-r--r--  1 root root 187764 2009-04-03 05:46 iwlwifi-4965-2.ucode
-rw-r--r--  1 root root 345008 2009-04-03 05:46 iwlwifi-5000-1.ucode
-rw-r--r--  1 root root 118884 2009-04-03 05:46 lbtf_usb.bin
-rw-r--r--  1 root root  76802 2009-04-03 05:46 ql2100_fw.bin
-rw-r--r--  1 root root  84566 2009-04-03 05:46 ql2200_fw.bin
-rw-r--r--  1 root root 123170 2009-04-03 05:46 ql2300_fw.bin
-rw-r--r--  1 root root 141200 2009-04-03 05:46 v4l-cx23418-apu.fw
-rw-r--r--  1 root root 158332 2009-04-03 05:46 v4l-cx23418-cpu.fw
-rw-r--r--  1 root root  16382 2009-04-03 05:46 v4l-cx23418-dig.fw
-rw-r--r--  1 root root 262144 2009-04-03 05:46 v4l-cx2341x-dec.fw
-rw-r--r--  1 root root 376836 2009-04-03 05:46 v4l-cx2341x-enc.fw
-rw-r--r--  1 root root 155648 2009-04-03 05:46 v4l-cx2341x-init.mpg
-rw-r--r--  1 root root  16382 2009-04-03 05:46 v4l-cx23885-avcore-01.fw
-rw-r--r--  1 root root 376836 2009-04-03 05:46 v4l-cx23885-enc.fw
-rw-r--r--  1 root root  16382 2009-04-03 05:46 v4l-cx25840.fw
-rw-r--r--  1 root root   8192 2009-04-03 05:46 v4l-pvrusb2-24xxx-01.fw
-rw-r--r--  1 root root   8192 2009-04-03 05:46 v4l-pvrusb2-29xxx-01.fw
-rw-r--r--  1 root root  15664 2009-02-14 05:30 NPE-C.02020201
-rw-r--r--  1 root root  15664 2009-02-14 05:30 NPE-B.01020201
lybeth@lybeth-laptop:/lib/firmware$

---

### Post by Torleif67 on 2009-05-14
> **lkraemer said:**
> 67,
Make sure you have a wired LAN connection.  Then you should be able to
go to: SYSTEM -> ADMINISTRATION -> HARDWARE DRIVERS and ENABLE the Wifi
Restricted Drivers.  This will download the firmware to your system, if you have a wired connection. Reboot.

If this works there should be folders b43 and b43legacy under /lib/firmware
and each folder should have some *.fw files in it.

Open a Terminal window and cut/paste each command one at a time.

```

lshw -C network
lsmod
ndiswrapper -l
cat /etc/modprobe.d/blacklist
iwconfig 
cd /
cd /lib/firmware
ls -alt
cd /b43
ls -alt

```
Then post the output, separated so it is easy to read, as this will give
us a clue as to what is loaded and blacklisted. Do this before you proceed!


The next steps will be determined by what you post from the previous
request.

If this were a fresh install, it might have been easier, but you should still be able to get it working.


lkraemer


I posted all here for you to read. I hope i did the right thing here.
Please let me know how to go on with this... Thank you for youir help so far...

---

### Post by lkraemer on 2009-05-14
OK, good so far.  You can ignore the ndiswrapper error, I just wanted to make sure!  I need
you to run the following again, because 9.04 changed the file name according to a post I read.
```

cat /etc/modprobe.d/blacklist.conf

```
Then post the output so we can see what is blacklisted.

There aren't any *.fw files in /lib/firmware/b43 or /lib/firmware/b43legacy
and if you had a Wired LAN connection and went to SYSTEM -> ADMINISTRATION
-> HARDWARE DRIVERS and enabled the Hardware Drivers with a LAN connection
there should have been folders created and files inserted for the Restricted
Drivers to work.  At that point you should have re-booted.

Is that what you did?  If so, then the *.fw files aren't being created.
If we can't get them created, and the Restricted drivers working, then
we can always just blacklist accordingly and proceed.  (I couldn't make
mine work either on my Compaq Presario CQ50-139NR, but that wasn't a big
problem.)  But, we need to see what is in blacklist.conf first.


PREVIEW of what is to be done next:

Disable Hardware Restricted Drivers
Blacklist as required
Download Current MadWifi Drivers
Compile 

Here is a copy of what I use on my CQ50-139NR when a new version of Madwifi
is released:  (This assumes you know to insert ath0, or what ever your computer
uses for the Wifi, as displayed by iwconfig........and your folders are
located, and named as mine....)

If a new version of madwifi is released, and NO Kernel Update...DO:
sudo ifconfig ath0 down
cd ~/madwifi_ar5007
cd madwifi-hal-0.10.5.6-r4003-20090416
sudo make uninstall
make clean
make
sudo make install
sudo modprobe ath_pci
/etc/init.d/networking/restart OR reboot
sudo ifconfig ath0 up

BUT, you don't have any thing that is working.

Here is what I use when a New Kernel is downloaded.

When a new Kernel has been downloaded and
your Wifi doesn't work.......DO:
cd ~/madwifi_ar5007
cd madwifi-hal-0.10.5.6-r4003-20090416  OR "The Current Version"
make clean
make
sudo make install
sudo modprobe ath_pci
sudo /etc/init.d/networking restart OR reboot

Go to:
[http://snapshots.madwifi-project.org/](http://snapshots.madwifi-project.org/)
and download the current Version madwifi-hal-0.10.5.6-current.tar.gz and extract it
to a folder under your home/login named madwifi_ar5007.  That folder will be named
something like madwifi-hal-0.10.5.6-r4016-20090429, assuming the version hasn't been
updated.  Now after we check the blacklist you can go to town and get it working.

Just realize that when you Update ubuntu, and get a New Kernel you will have to recompile
to make it work again.  No big deal after you have done it once.  (NOTE: you can always
select a previous Kernel from the Grub menu with a working Wifi until you get the time
to rework for the new Kernel.)

REF:
[http://madwifi-project.org/](http://madwifi-project.org/)
[http://madwifi-project.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi-project.org/wiki/UserDocs/FirstTimeHowTo)
 
lkraemer

---

### Post by Torleif67 on 2009-05-15
lybeth@lybeth-laptop:~$ cat /etc/modprobe.d/blacklist.conf
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

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
lybeth@lybeth-laptop:~$

---

### Post by lkraemer on 2009-05-15
OK, you're lsmod command doesn't show b43 or ssb as being used, and
ath_pci is installed.

There aren't any *.fw files in /lib/firmware/b43 or
/lib/firmware/b43legacy and if you had a Wired LAN connection and
went to SYSTEM -> ADMINISTRATION -> HARDWARE DRIVERS and enabled the Hardware Drivers with a LAN connection there should have been folders created and files inserted for the Restricted Drivers to work. At that point you should have re-booted.

Is that what you did? If so, then the *.fw files aren't being created.

I am assuming the answer was YES, but you didn't supply it......
So, I am moving forward....

Disable Hardware Restricted Drivers by going to:
SYSTEM -> ADMINISTRATION -> HARDWARE DRIVERS and DISABLE, then reboot.

Blacklist as required..... (b43 & ssb aren't in the modules listed, but blacklist them anyway)

Open a Terminal window and add the following to the blacklist.conf file right after bcm43xx.
blacklist b43
blacklist ssb

```

sudo gedit /etc/modprobe.d/blacklist.conf

```
Save the file.

Download Current MadWifi Drivers via wired LAN connection.

Go to:
[http://snapshots.madwifi-project.org/](http://snapshots.madwifi-project.org/)
and download the current Version madwifi-hal-0.10.5.6-current.tar.gz and extract it to a folder under your home/login named madwifi_ar5007. That folder will be named something like madwifi-hal-0.10.5.6-r4016-20090429, assuming the version hasn't been updated.

Just realize that when you Update ubuntu, and get a New Kernel you will have to recompile to make it work again. No big deal after you have done it once. (NOTE: you can always select a previous Kernel from the Grub menu with a working Wifi until you get the time to rework for the new Kernel.)

Here is what I use when a New Kernel is downloaded.

When a new Kernel has been downloaded and
your Wifi doesn't work.......DO:
(I am adding the first command to remove the already loaded ath_pci
but it might not really be needed, won't hurt!)
```

sudo modprobe -r ath_pci
cd ~/madwifi_ar5007
cd madwifi-hal-0.10.5.6-r4003-20090416 
make clean
make
sudo make install
sudo modprobe ath_pci
sudo /etc/init.d/networking restart 

```
Then, I'd reboot.

That should get you going, assuming no errors with the make, and your Wifi
is turned on by switch or by appropriate keystrokes to enable it.

```

iwconfig

```
should show your wifi as ath0, wlan0 or something like that.

REF:
[http://madwifi-project.org/](http://madwifi-project.org/)
[http://madwifi-project.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi-project.org/wiki/UserDocs/FirstTimeHowTo)

[http://linux.die.net/man/8/modprobe](http://linux.die.net/man/8/modprobe)

lkraemer

---

### Post by Torleif67 on 2009-05-19
I have done what you have told me to above here. But the problem is still there, no wirless conection. If i put in iwconfig in a terminal window i get this answer. What is the problem here, i can't find this out. Do i need ro reinstall the whole ubuntu again just to get this working or what can i do? Please i need more help here...

lybeth@lybeth-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

lybeth@lybeth-laptop:~$

---

### Post by lkraemer on 2009-05-20
Well, I've not seen the MadWifi drivers fail.

Basically you did the following without errors?

Downloaded the most current version of MadWifi, and
did a make, and then installed it.  ARE YOU SURE there were 
NO ERRORS displayed on the terminal window after/during the Make?

Post your output from lsmod again along with blacklist.conf.


Here is another post (#15) of the same thing I told you,
only presented different.
[http://ubuntuforums.org/showthread.php?t=991202&page=2](http://ubuntuforums.org/showthread.php?t=991202&page=2)


If these are good, I'm out of ideas.

lkraemer

---

### Post by Torleif67 on 2009-05-22
lybeth@lybeth-laptop:~$ lsmod
Module                  Size  Used by
isofs                  39844  0 
udf                    87716  1 
crc_itu_t              10112  1 udf
i915                   65540  2 
drm                    96296  3 i915
binfmt_misc            16776  1 
ppdev                  15620  0 
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
input_polldev          11912  0 
ath_pci                99224  0 
wlan                  210288  1 ath_pci
ath_hal               198864  1 ath_pci
lp                     17156  0 
parport                42220  2 ppdev,lp
joydev                 18368  0 
snd_hda_intel         435636  2 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               63240  0 
compat_ioctl32          9344  1 uvcvideo
videodev               41600  1 uvcvideo
snd                    62628  13 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                61972  0 
v4l1_compat            21764  2 uvcvideo,videodev
pcspkr                 10496  0 
soundcore              15200  1 snd
serio_raw              13316  0 
iTCO_wdt               19108  0 
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
video                  25360  0 
intel_agp              34108  1 
agpgart                42696  3 drm,intel_agp
iTCO_vendor_support    11652  1 iTCO_wdt
output                 11008  1 video
8139too                32128  0 
8139cp                 27776  0 
mii                    13312  2 8139too,8139cp
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
lybeth@lybeth-laptop:~$

---

### Post by anewguy on 2009-05-22
I'm not familiar with Atheros chipsets enough to be sure, but it looks like the "built-in" atheros module is loaded, and you want to use the madwifi from what I can make out.  Basically I think the built-in driver ath_pci interferes with the madwifi driver.  You might just be able to blacklist ath_pci.

While for a different Atheros chipset, the idea is the same - see this link:

[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules/+bug/275692]("https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules/+bug/275692")

Dave :)

---

### Post by lkraemer on 2009-05-22
Well, it's certainly worth a try.

```

sudo gedit /etc/modprobe.d/blacklist.conf

```
and add 

```

blacklist ath_pci

```
then save the file.

reboot.

Thanks Dave!

lkraemer

---

### Post by nothingspecial on 2009-05-22
******EDIT****** Sorry failed to read the final page in this thread oops. Madwifi didn`t work for me (1st time ever). It seems that the ath5k driver that worked when upgrading to jaunty suddenly stopped. For some reason it wasn`t loading and adding it to /etc/modules solved the problem. *****EDIT*******

 After finally getting support for those pesky atheros wifi cards with jaunty a pesky update comes along and breaks it.

This worked for me however one more user has tried it with negative results so I`m not promising anything.

Just open /etc/modules

```
sudo nano /etc/modules
```

This file tells ubuntu which drivers to load at boot.

Get down to the bottom of it with your arrow key and type

```
ath5k
```

Save it by pressing Ctrl O together (thats letter o not zero) then Enter

Close by pressing Ctrl X.

Reboot and see if it works.

Oh yeah and make sure you still don`t have te madwifi driver enabled in System > Administration > Hardware Drivers.

Unfortunately I spent all morning messing about trying to get my wireless back and there may be something else I did that is vital, but I`m pretty sure I put everything back as it was after each tinker if you know what I mean.

If it doesn`t work check you have the driver by typing ```
lsmod
``` and see if it`s listed.

---

