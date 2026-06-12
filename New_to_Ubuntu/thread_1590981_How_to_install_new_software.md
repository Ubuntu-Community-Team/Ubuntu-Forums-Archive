---
title: "How to install new software?"
date: 2010-10-08
forum: New to Ubuntu
---

### Post by taiChip on 2010-10-08
i just installed ubuntu 9.10 and i´m a complete newbie
so sorry but i have to ask this.

i want to install aircrack-ng
to get drivers for my dlink dwl-122 (wi-fi usb).
i downloaded the file aircrack-ng-1.1.tar.gz 
and have it in my home-folder.
instructions are simple enough:
open your package manager and install 'aircrack-ng' package
but i can´t find it in the package manager.
in which folder should i place it?

thanks,
peter

---

### Post by sandyd on 2010-10-08
> **taiChip said:**
> i just installed ubuntu 9.10 and i´m a complete newbie
so sorry but i have to ask this.

i want to install aircrack-ng
to get drivers for my dlink dwl-122 (wi-fi usb).
i downloaded the file aircrack-ng-1.1.tar.gz 
and have it in my home-folder.
instructions are simple enough:
open your package manager and install 'aircrack-ng' package
but i can´t find it in the package manager.
in which folder should i place it?

thanks,
peter
that wireless adaptor should be supported since 9.04
just use the network manager (top right hand side of the screen)
to connect to wifi networks.

if it doesn't work, post output of
```

lsmod
sudo ifconfig -l

```

---

### Post by The Cog on 2010-10-08
menu System > Administration > Synaptic Package Manager.
Search for aircrack, mark it for installation and apply.

No need to download zip files.

---

### Post by Davor Posavec on 2010-10-08
Kmenu > Applications >  Ubuntu Software Centar

---

### Post by pricetech on 2010-10-08
OP has Ubuntu listed as his / her OS, so System - Administration - Synaptic is where it should be.

Not sure which repo aircrack is in, so you may need to:
System - Administration - Software Sources
and add additional repos.  If you do, then use the Reload button in Synaptic afterwards.

---

### Post by taiChip on 2010-10-08
i think i must install aircrack-ng first to be able to
add any packages, i haven´t done it because
i can´t browse to my home folder in the terminal.
how do get there and then:
cd aircrack-ng-1.1
 make
 make install

the wireless tab is empty in the network connections


lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 2001:3700 D-Link Corp. [hex] DWL-122 802.11b
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 04e8:663e Samsung Electronics Co., Ltd 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

lsmode
Module                  Size  Used by
nls_iso8859_1           3740  1 
nls_cp437               5372  1 
vfat                   10716  1 
fat                    51452  1 vfat
binfmt_misc             8356  1 
snd_intel8x0           30168  2 
snd_ac97_codec        101216  1 snd_intel8x0
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
psmouse                56180  0 
serio_raw               5280  0 
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
ppdev                   6688  0 
cdc_acm                16544  0 
parport_pc             31940  1 
snd_seq_midi            6432  0 
prism2_usb            165524  0 
shpchp                 32272  0 
snd_rawmidi            22208  1 snd_seq_midi
iptable_filter          3100  0 
lp                      8964  0 
parport                35340  3 ppdev,parport_pc,lp
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
ip_tables              11692  1 iptable_filter
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
x_tables               16544  1 ip_tables
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_intel8x0,snd_pcm
fbcon                  36640  72 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
floppy                 54916  0 
tg3                   109600  0 
i915                  221064  3 
drm                   159584  3 i915
i2c_algo_bit            5760  1 i915
intel_agp              27484  2 i915
agpgart                34988  2 drm,intel_agp
video                  19380  1 i915
output                  2780  1 video


sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0f:20:33:aa:57  
          inet6 addr: fe80::20f:20ff:fe33:aa57/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:2222 (2.2 KB)
          Interrupt:20 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:11:95:f2:4d:2e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by 3rdalbum on 2010-10-08
> **taiChip said:**
> i think i must install aircrack-ng first to be able to
add any packages, i haven´t done it because
i can´t browse to my home folder in the terminal.
how do get there and then:
cd aircrack-ng-1.1
 make
 make install

No, install Aircrack from the package manager.

> the wireless tab is empty in the network connections

Yes, it shows networks that you have connected to. To see available networks, use the Network Manager applet on your top panel.

---

### Post by taiChip on 2010-10-08
found my adpter now in network manager, thanks!

when i try to 'add downloaded packages' in packet manger
the aircrack folder is shaded so i can´t choose it.
must i select a specific file or the whole folder?

---

### Post by cgroza on 2010-10-08
You need to install it, not add it.

---

### Post by taiChip on 2010-10-08
ok, but do i have to uncompress the aircrack-ng-1.1.tar.gz
and in that case which file do use to install the pack?

---

### Post by LowSky on 2010-10-08
> **The Cog said:**
> menu System > Administration > Synaptic Package Manager.
Search for aircrack, mark it for installation and apply.

No need to download zip files.

This is all you need to do. very simple

---

### Post by taiChip on 2010-10-08
after the search i get it in the left window, mark it, package window is still empty,
 and the whole package menu is shaded so i can 'mark it for installation'

---

### Post by taiChip on 2010-10-09
i didn´t have a working internet connection in ubuntu
and had downloaded the tar.gz version of the app earlier
which i was using, that´s why the package installation failed.
found [http://packages.ubuntu.com/karmic/](http://packages.ubuntu.com/karmic/) today and it
solved everything.

thanks!

---

