---
title: "PB netbook dot-m wireless not working / alternative driver installation failed"
date: 2013-09-19
forum: Networking &amp; Wireless
---

### Post by ale3 on 2013-09-19
Dear ubuntu support,

i've just installed ubuntu 12.04 on my packard bell dot-m (intel atom z520, 2gb ram) and trought cable Lan internet works perfectelly but the installation of the alternative drivers suggested by the system encounter an error, so i don't have wireless at all.

can you pls help me to fix the problem, otherwise a netbook without wireless is basically useless :)

thanks


ps: i attached a screenshot of what the system shows me: the error page. also asked me to check the log file. but i'm new about it so i dunno how to find it.


thanks for helping me

Ale

---

### Post by praseodym on 2013-09-19
Please open a terminal with CTRL+ALT+T and show the outputs of:
```

uname -a
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
```

---

### Post by ale3 on 2013-09-19
here we go. btw, thanks for the fast reply. if anything's missing let me know.





|ale@ale-netbook:~$ uname -a
Linux ale-netbook 3.8.0-30-generic #44~precise1-Ubuntu SMP Fri Aug 23 17:33:45 UTC 2013 i686 i686 i386 GNU/Linux
ale@ale-netbook:~$ lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
	Subsystem: Acer Incorporated [ALI] Device [1025:0256]
	Kernel driver in use: r8169
--
03:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
	Subsystem: Foxconn International, Inc. T77H106.00 Wireless Half-size Mini PCIe Card [105b:e01b]
	Kernel modules: ssb
ale@ale-netbook:~$ lsusb
Bus 001 Device 002: ID 04f2:b175 Chicony Electronics Co., Ltd 4-Port Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
ale@ale-netbook:~$ lsmod
Module                  Size  Used by
dm_crypt               22555  0 
bnep                   17852  2 
rfcomm                 38400  0 
bluetooth             211435  10 bnep,rfcomm
parport_pc             27612  0 
coretemp               13324  0 
ppdev                  12849  0 
kvm_intel             127786  0 
snd_hda_codec_realtek    65004  1 
uvcvideo               72250  0 
joydev                 17329  0 
snd_hda_intel          38819  3 
kvm                   384557  1 kvm_intel
snd_hda_codec         118650  2 snd_hda_codec_realtek,snd_hda_intel
videobuf2_core         39385  1 uvcvideo
i2c_isch               12671  0 
videodev               96131  2 uvcvideo,videobuf2_core
acer_wmi               27980  0 
videobuf2_vmalloc      12920  1 uvcvideo
videobuf2_memops       13042  1 videobuf2_vmalloc
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                85934  2 snd_hda_intel,snd_hda_codec
sparse_keymap          13658  1 acer_wmi
snd_seq_midi           13132  0 
snd_rawmidi            25157  1 snd_seq_midi
psmouse                82769  0 
snd_seq_midi_event     14475  1 snd_seq_midi
microcode              18433  0 
serio_raw              13031  0 
snd_seq                51593  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
lpc_sch                12727  0 
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
mac_hid                13077  0 
snd                    57014  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         18398  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
pata_acpi              12886  0 
wmi                    18744  1 acer_wmi
pata_sch               12711  1 
r8169                  62532  0 
gma500_gfx            173832  2 
drm_kms_helper         47749  1 gma500_gfx
drm                   233935  3 gma500_gfx,drm_kms_helper
i2c_algo_bit           13316  1 gma500_gfx
video                  19116  2 acer_wmi,gma500_gfx
ale@ale-netbook:~$ iwconfig
lo        no wireless extensions.


eth0      no wireless extensions.


ale@ale-netbook:~$ rfkill list
0: acer-wireless: Wireless LAN
	Soft blocked: no
	Hard blocked: no
ale@ale-netbook:~$

---

### Post by praseodym on 2013-09-20
Install this package:
```

sudo apt-get install firmware-b43-lpphy-installer
sudo modprobe -rfv b43
sudo modprobe -v b43
```
Check:
```

iwconfig
dmesg | grep b43
iwlist chan
sudo iwlist scan
```

---

### Post by ale3 on 2013-09-22
thanks i've done what you told me twice but nothign seemed to be changed unfortunately 
here the log file , after the commands:



Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  thunderbird-globalmenu
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  b43-fwcutter
The following NEW packages will be installed:
  b43-fwcutter firmware-b43-lpphy-installer
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 22.3 kB of archives.
After this operation, 110 kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) precise/main b43-fwcutter i386 1:015-9 [18.9 kB]
Get:2 [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) precise/multiverse firmware-b43-lpphy-installer all 1:015-9 [3,390 B]
Fetched 22.3 kB in 0s (99.7 kB/s)                         
Selecting previously unselected package b43-fwcutter.
(Reading database ... 179310 files and directories currently installed.)
Unpacking b43-fwcutter (from .../b43-fwcutter_1%3a015-9_i386.deb) ...
Selecting previously unselected package firmware-b43-lpphy-installer.
Unpacking firmware-b43-lpphy-installer (from .../firmware-b43-lpphy-installer_1%3a015-9_all.deb) ...
Processing triggers for man-db ...
Setting up b43-fwcutter (1:015-9) ...
Setting up firmware-b43-lpphy-installer (1:015-9) ...
No chroot environment found. Starting normal installation
--2013-09-20 21:54:33--  [http://downloads.openwrt.org/sources/broadcom-wl-4.178.10.4.tar.bz2](http://downloads.openwrt.org/sources/broadcom-wl-4.178.10.4.tar.bz2)
Resolving downloads.openwrt.org (downloads.openwrt.org)... 78.24.191.177
Connecting to downloads.openwrt.org (downloads.openwrt.org)|78.24.191.177|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 5986780 (5.7M) [application/octet-stream]
Saving to: `broadcom-wl-4.178.10.4.tar.bz2'


100%[======================================>] 5,986,780   5.69M/s   in 1.0s    


2013-09-20 21:54:34 (5.69 MB/s) - `broadcom-wl-4.178.10.4.tar.bz2' saved [5986780/5986780]


broadcom-wl-4.178.10.4/
broadcom-wl-4.178.10.4/config/
broadcom-wl-4.178.10.4/config/wlconfig_nomimo
broadcom-wl-4.178.10.4/config/wlconfig_lx_router_apsta_1chipG
broadcom-wl-4.178.10.4/config/wlconfig_lx_wl_sdstd
broadcom-wl-4.178.10.4/config/wlconfig_lx_shared
broadcom-wl-4.178.10.4/config/diffupdate.sh
broadcom-wl-4.178.10.4/config/wlconfig_lx_router_ap_1chipG
broadcom-wl-4.178.10.4/config/wlconfig_lx_router_ap
broadcom-wl-4.178.10.4/config/wlconfig_lx_router_ap_sdstd
broadcom-wl-4.178.10.4/config/wl.mk
broadcom-wl-4.178.10.4/config/wltunable_lx_router.h
broadcom-wl-4.178.10.4/config/wlconfig_lx_router_sta
broadcom-wl-4.178.10.4/config/wl_default
broadcom-wl-4.178.10.4/config/wltunable_lx_router_1chipG.h
broadcom-wl-4.178.10.4/config/wl_hnd
broadcom-wl-4.178.10.4/config/wlconfig_lx_router_sta_1chipG
broadcom-wl-4.178.10.4/config/wlconfig_lx_router_apsta
broadcom-wl-4.178.10.4/config/wlconfig_apdef
broadcom-wl-4.178.10.4/README
broadcom-wl-4.178.10.4/linux/
broadcom-wl-4.178.10.4/linux/wl_sta.o
broadcom-wl-4.178.10.4/linux/wl.o
broadcom-wl-4.178.10.4/linux/wl_ap.o
broadcom-wl-4.178.10.4/linux/wl_apsta.o
This file is recognised as:
  filename   :  wl_apsta.o
  version    :  478.104
  MD5        :  bb8537e3204a1ea5903fe3e66b5e2763
Extracting b43/ucode5.fw
Extracting b43/pcm5.fw
Extracting b43/b0g0bsinitvals5.fw
Extracting b43/a0g0bsinitvals5.fw
Extracting b43/b0g0initvals5.fw
Extracting b43/a0g1initvals5.fw
Extracting b43/a0g0initvals5.fw
Extracting b43/a0g1bsinitvals5.fw
Extracting b43/ucode9.fw
Extracting b43/a0g1initvals9.fw
Extracting b43/a0g0bsinitvals9.fw
Extracting b43/b0g0bsinitvals9.fw
Extracting b43/b0g0initvals9.fw
Extracting b43/a0g1bsinitvals9.fw
Extracting b43/a0g0initvals9.fw
Extracting b43/ucode11.fw
Extracting b43/n0bsinitvals11.fw
Extracting b43/n0absinitvals11.fw
Extracting b43/n0initvals11.fw
Extracting b43/ucode13.fw
Extracting b43/b0g0initvals13.fw
Extracting b43/a0g1bsinitvals13.fw
Extracting b43/a0g1initvals13.fw
Extracting b43/lp0bsinitvals13.fw
Extracting b43/b0g0bsinitvals13.fw
Extracting b43/lp0initvals13.fw
Extracting b43/ucode14.fw
Extracting b43/lp0initvals14.fw
Extracting b43/lp0bsinitvals14.fw
Extracting b43/ucode15.fw
Extracting b43/lp0bsinitvals15.fw
Extracting b43/lp0initvals15.fw
Extracting b43/ucode16.fw
Extracting b43/n0bsinitvals16.fw
Extracting b43/sslpn0initvals16.fw
Extracting b43/n0initvals16.fw
Extracting b43/lp0initvals16.fw
Extracting b43/sslpn0bsinitvals16.fw
Extracting b43/lp0bsinitvals16.fw


ale@ale-netbook:~$ iwconfig
lo        no wireless extensions.


eth0      no wireless extensions.


ale@ale-netbook:~$ dmesg | grep b43
ale@ale-netbook:~$ iwlist chan
lo        no frequency information.


eth0      no frequency information.


ale@ale-netbook:~$ sudo iwlist scan
lo        Interface doesn't support scanning.


eth0      Interface doesn't support scanning.


ale@ale-netbook:~$ 






thanks again for helping!

---

### Post by praseodym on 2013-09-22
Please reboot and show the outputs of:
```

lsmod
dmesg | grep b43
iwconfig
cat /etc/resolv.conf
```

---

### Post by ale3 on 2013-09-22
ale@ale-netbook:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12617  1 
usb_storage            48053  1 
dm_crypt               22555  0 
bnep                   17852  2 
rfcomm                 38400  0 
bluetooth             211435  10 bnep,rfcomm
parport_pc             27612  0 
ppdev                  12849  0 
coretemp               13324  0 
kvm_intel             127786  0 
uvcvideo               72250  0 
kvm                   384557  1 kvm_intel
snd_hda_codec_realtek    65004  1 
i2c_isch               12671  0 
acer_wmi               27980  0 
joydev                 17329  0 
snd_hda_intel          38819  3 
snd_hda_codec         118650  2 snd_hda_codec_realtek,snd_hda_intel
videobuf2_core         39385  1 uvcvideo
videodev               96131  2 uvcvideo,videobuf2_core
sparse_keymap          13658  1 acer_wmi
snd_hwdep              13276  1 snd_hda_codec
videobuf2_vmalloc      12920  1 uvcvideo
videobuf2_memops       13042  1 videobuf2_vmalloc
snd_pcm                85934  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
psmouse                82769  0 
snd_rawmidi            25157  1 snd_seq_midi
microcode              18433  0 
serio_raw              13031  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51593  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
lpc_sch                12727  0 
mac_hid                13077  0 
snd                    57014  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         18398  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
pata_acpi              12886  0 
vesafb                 13540  0 
pata_sch               12711  3 
gma500_gfx            173832  2 
drm_kms_helper         47749  1 gma500_gfx
wmi                    18744  1 acer_wmi
r8169                  62532  0 
drm                   233935  3 gma500_gfx,drm_kms_helper
i2c_algo_bit           13316  1 gma500_gfx
video                  19116  2 acer_wmi,gma500_gfx
ale@ale-netbook:~$ dmesg | grep b43
ale@ale-netbook:~$ iwconfig
lo        no wireless extensions.


eth0      no wireless extensions.


ale@ale-netbook:~$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.0.1
search chello.hu
ale@ale-netbook:~$

---

### Post by varunendra on 2013-09-23
> **ale3 said:**
> but the installation of the alternative drivers suggested by the system encounter an error,

....but apparently did it's black magic before failing. Please do -
```
sudo apt-get purge bcmwl-kernel-source
sudo modprobe -v b43
```

Do you have your wireless now? Does it survive a reboot?

**PS:**
Please always use 'Code' box to post commands & terminal outputs. It preserves its formatting and makes your post cleaner, compact and more readable. Follow the "Using Code Tags" link in my signature to see how.

---

### Post by pshone2 on 2013-11-07
Hi 

Did it work?  I had the same problem so I have stayed on Ubuntu 11.10.  Would love to go up to the LTS.

---

