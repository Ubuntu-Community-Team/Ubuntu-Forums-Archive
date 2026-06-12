---
title: "eth0 troubles"
date: 2010-07-15
forum: New to Ubuntu
---

### Post by C. M .Hughes on 2010-07-15
I'm having troubles with my ethernet connection- it sometimes works and sometimes doesn't. 

Here is the output from ifconfig

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:888 (888.0 B)  TX bytes:888 (888.0 B)


Here are the contents of my /etc/network/interfaces

iface lo inet loopback

I have already tried adding the following lines to it

auto eth0
iface eth0 inet dhcp

I have no idea where to go next- if anyone has any ideas, I would greatly appreciate it.

---

### Post by andrewthomas on 2010-07-15
do you have NetworkManager installed?

---

### Post by alphacrucis2 on 2010-07-15
> **C. M .Hughes said:**
> I'm having troubles with my ethernet connection- it sometimes works and sometimes doesn't. 

Here is the output from ifconfig

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:888 (888.0 B)  TX bytes:888 (888.0 B)


Here are the contents of my /etc/network/interfaces

iface lo inet loopback

I have already tried adding the following lines to it

auto eth0
iface eth0 inet dhcp

I have no idea where to go next- if anyone has any ideas, I would greatly appreciate it.

Maybe a faulty ethernet cable/bad connection. Replacing the cable should be a fairly painless thing to try. Worth eliminating that possibility anyway.


Edit: Sorry I didn't look at your ifconfig properly. Looks like the ethernet card is not even being recognised so it isn't a simple cable fault. Can you list the output of this:


```
sudo lshw -C network
```

---

### Post by C. M .Hughes on 2010-07-16
Many thanks for your suggestion. Here is the output from the command

sudo lshw -C network

*-network UNCLAIMED     

       description: Ethernet controller
       	product: BCM4401-B0 100Base-TX
       	vendor: Broadcom Corporation
       	physical id: 0       
	bus info: pci@0000:03:00.0       
	version: 02       
	width: 32 bits       
	clock: 33MHz       
	capabilities: pm bus_master cap_list       
	configuration: latency=64
  
*-network DISABLED       
	description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 5a:e0:ec:7d:ef:9f
       capabilities: ethernet physical
       configuration: broadcast=yes
	 driver=bridge driverversion=2.3
	 firmware=N/A link=yes multicast=yes

I have a dual boot with Windows 7, which recognizes the ethernet cable. 

Thanks again.

---

### Post by cavalier911 on 2010-07-16
Requires the b44 kernel module.
```
lsmod
```
Do you see b44 in the list?
```
modinfo b44
```
See if somehow it was added to your /etc/modprobe.d/blacklist.conf
Do you have a wireless adapter,if so what driver is it using?
If you have b43,ssb,and/or ndiswrapper there can be conflicts.

---

### Post by C. M .Hughes on 2010-07-18
Many thanks for your response. 

It's a strange situation, because sometimes my wireless card & ethernet port work, and sometimes they don't. 

Here is the code when they *are working*:

```
lsmod (when working)
Module                  Size  Used by
nls_iso8859_1          12032  1 
nls_cp437              13696  1 
vfat                   18816  1 
fat                    58272  1 vfat
binfmt_misc            16776  1 
radeon                342816  2 
drm                    96424  3 radeon
ppdev                  15620  0 
bridge                 56212  0 
stp                    10500  1 bridge
bnep                   20224  2 
input_polldev          11912  0 
joydev                 18368  0 
lp                     17156  0 
parport                42220  2 ppdev,lp
snd_hda_intel         436148  3 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                83076  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
b44                    35984  0 
snd_rawmidi            29696  1 snd_seq_midi
ssb                    41220  1 b44
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
mii                    13312  1 b44
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ieee80211_crypt_tkip    16896  0 
snd_timer              29704  2 snd_pcm,snd_seq
ati_agp                14988  0 
uvcvideo               63368  0 
psmouse                61972  0 
wl                   1281364  0 
video                  25872  0 
dcdbas                 15264  0 
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ricoh_mmc              11904  0 
agpgart                42696  2 drm,ati_agp
i2c_piix4              18448  0 
sdhci_pci              15232  0 
sdhci                  23940  1 sdhci_pci
k8temp                 12416  0 
compat_ioctl32          9344  1 uvcvideo
videodev               41600  1 uvcvideo
v4l1_compat            21764  2 uvcvideo,videodev
serio_raw              13444  0 
pcspkr                 10496  0 
shpchp                 40212  0 
output                 11008  1 video
snd                    62756  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
ieee80211_crypt        13444  2 ieee80211_crypt_tkip,wl
ohci1394               38576  0 
ieee1394               94660  1 ohci1394
usb_storage            99648  1 
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
```

```
b44 (when working)
filename:       /lib/modules/2.6.28-17-generic/kernel/drivers/net/b44.ko
version:        2.0
license:        GPL
description:    Broadcom 44xx/47xx 10/100 PCI ethernet driver
author:         Felix Fietkau, Florian Schirmer, Pekka Pietikainen, David S. Miller
srcversion:     3BE8797BEDC5DB3938AC9CF
alias:          ssb:v4243id0806rev*
alias:          pci:v000014E4d0000170Csv*sd*bc*sc*i*
alias:          pci:v000014E4d00004402sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004401sv*sd*bc*sc*i*
depends:        ssb,mii
vermagic:       2.6.28-17-generic SMP mod_unload modversions 586 
parm:           b44_debug:B44 bitmapped debugging message enable value (int)
```

I'll post the output from these commands when they're not working- should be in the next couple of days! :D

---

### Post by C. M .Hughes on 2010-07-20
> **cavalier911 said:**
> Requires the b44 kernel module.
```
lsmod
```
Do you see b44 in the list?
```
modinfo b44
```
See if somehow it was added to your /etc/modprobe.d/blacklist.conf
Do you have a wireless adapter,if so what driver is it using?
If you have b43,ssb,and/or ndiswrapper there can be conflicts.

Here's the code when it's not working:

```
lsmod (when not working)
Module                  Size  Used by
nls_iso8859_1          12032  1 
nls_cp437              13696  1 
vfat                   18816  1 
fat                    58272  1 vfat
usb_storage            99648  1 
binfmt_misc            16776  1 
radeon                342816  2 
drm                    96424  3 radeon
ppdev                  15620  0 
bridge                 56212  0 
stp                    10500  1 bridge
bnep                   20224  2 
input_polldev          11912  0 
joydev                 18368  0 
lp                     17156  0 
parport                42220  2 ppdev,lp
snd_hda_intel         436148  5 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                83076  3 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
psmouse                61972  0 
video                  25872  0 
uvcvideo               63368  0 
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
dcdbas                 15264  0 
shpchp                 40212  0 
serio_raw              13444  0 
ati_agp                14988  0 
i2c_piix4              18448  0 
pcspkr                 10496  0 
output                 11008  1 video
compat_ioctl32          9344  1 uvcvideo
videodev               41600  1 uvcvideo
v4l1_compat            21764  2 uvcvideo,videodev
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ricoh_mmc              11904  0 
sdhci_pci              15232  0 
sdhci                  23940  1 sdhci_pci
snd                    62756  18 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
agpgart                42696  2 drm,ati_agp
k8temp                 12416  0 
soundcore              15200  1 snd
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
ohci1394               38576  0 
ieee1394               94660  1 ohci1394
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
```

b44 (when not working)
nothing!

---

### Post by Linux000 on 2010-07-20
Is that a plugin card to your computer or built in? And could you post the output of ```
lspci
``` when it is working and not working.

---

### Post by cavalier911 on 2010-07-20
b44(broadcomm ethernet)depends on ssb which has a known conflict with sta(broadcomm wireless adapter)
None are loaded when the ethernet fails.
This assumes you don't need the wireless adapter.
Blacklist autoload of sta:
```
sudo nano /etc/modprobe.d/blacklist.conf
```
Add: 
blacklist sta
Load on boot ssb and b44:
```
sudo nano /etc/modules
```
Add:
ssb
b44

---

### Post by C. M .Hughes on 2010-07-20
> **Linux000 said:**
> Is that a plugin card to your computer or built in? And could you post the output of ```
lspci
``` when it is working and not working.

It's a built in card. I have attached the output from lspci when it works- I'll post the output when it's not working the next time it doesn't work!

Thanks so much.

---

### Post by C. M .Hughes on 2010-07-20
Thanks cavalier911, I'll give it a go. Should I do this when it's working or not working?

---

### Post by cavalier911 on 2010-07-20
Hold off on the changes,next time eth0 stop's working see if dmesg has some errors related to loading b44 module.
```
dmesg | grep b44
```

---

### Post by C. M .Hughes on 2010-07-21
Here's the output from dmesg|grep b44

[   12.202871] b44 0000:03:00.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   12.260121] b44.c:v2.0
[  112.816218] b44: eth0: Link is up at 100 Mbps, full duplex.
[  112.816228] b44: eth0: Flow control is off for TX and off for RX.

---

