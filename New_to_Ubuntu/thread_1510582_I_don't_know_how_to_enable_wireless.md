---
title: "I don't know how to enable wireless"
date: 2010-06-15
forum: New to Ubuntu
---

### Post by bcasanov on 2010-06-15
Hi,

I have Ubuntu 10.04, with all the latest updates installed, and when I left-click on the Network Manager icon in the panel, it shows that wireless is disabled.  When I right-click, I can't enable wireless because the "Enable Wireless" option is grayed-out.

The results of the following command are:


sudo lshw -C network

```
  *-network DISABLED      
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 01
       serial: 70:1a:04:02:b5:d6
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:f69fc000-f69fffff
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 13
       serial: 00:25:64:5b:04:2e
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.25 duplex=full firmware=N/A ip=192.168.0.103 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:29 memory:f68fc000-f68fffff ioport:de00(size=256)
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

```

Just to clarify, my computer does not have a physical wireless switch that toggles enabling/disabling wireless.

---

### Post by synapsys on 2010-06-15
Just a quick thought here, have you tried flipping the wireless switch on your laptop? There is usually a switch to turn the wireless card on/off.

---

### Post by lkraemer on 2010-06-15
You can try this guide, if you wish.  
[http://ubuntuforums.org/showthread.php?t=1470146](http://ubuntuforums.org/showthread.php?t=1470146)

You should be up and running in short order.
I've tested it several times.

If you can go where you can get Hardwired Ethernet access, and do
a system update via Update Manager, then try to enable the 
Hardware Drivers, it should also work........

lk

---

### Post by bcasanov on 2010-06-30
Thank you for the guide.  In this guide though, the person recommends using the B43 driver that should be listed in Restricted Drivers rather than using ndiswrapper.  The problem is that I have no B43 driver even listed in Hardware Drivers for my Broadcom BCM4312. The only driver listed there is "Broadcom STA wireless driver" and in the description box, it says "These package contains Broadcom 802.11 Linux STA wireless driverfor use with Broadcom's BCM4311-, BCM4312-, BCM4321-, andBCM4322-based hardware."

The output of lsmod is:

```
Module                  Size  Used by
nls_iso8859_1           3249  1 
nls_cp437               4919  1 
vfat                    8933  1 
fat                    47767  1 vfat
aes_i586                7268  814 
aes_generic            26863  1 aes_i586
binfmt_misc             6587  1 
ppdev                   5259  0 
vboxdrv               191042  0 
dm_crypt               11331  0 
snd_hda_codec_idt      51978  1 
snd_hda_intel          22037  2 
snd_hda_codec          74201  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70886  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
joydev                  8708  0 
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
lib80211_crypt_tkip     7596  0 
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
psmouse                63245  0 
snd                    54148  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
wl                   1959630  0 
soundcore               6620  1 snd
serio_raw               3978  0 
usblp                  10481  0 
dell_wmi                1793  0 
lib80211                5046  2 lib80211_crypt_tkip,wl
dell_laptop             6856  0 
lp                      7028  0 
snd_page_alloc          7172  2 snd_hda_intel,snd_pcm
dcdbas                  5490  1 dell_laptop
parport                32635  2 ppdev,lp
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
usbhid                 36174  0 
i915                  285891  3 
drm_kms_helper         29297  1 i915
hid                    67032  1 usbhid
usb_storage            39457  1 
intel_agp              24415  2 i915
drm                   163034  4 i915,drm_kms_helper
i2c_algo_bit            5028  1 i915
video                  17375  1 i915
agpgart                31788  2 intel_agp,drm
ahci                   32200  2 
output                  1871  1 video
sky2                   41040  0 

```

---

### Post by Talon2 on 2010-06-30
See this thread:

[http://ubuntuforums.org/showthread.php?t=1470146](http://ubuntuforums.org/showthread.php?t=1470146)

---

### Post by anewguy on 2010-06-30
I have to assume you must be connected via hard-wire in order to run the updates.  Be aware you'll need to physically disconnect that wire from your computer before you can use your wireless.

I noticed that your list of the network interfaces shows the following for eth1, your wireless adapter:

> driver=wl0 driverversion=5.60.48.36

This would indicate it is trying to use a driver called "w10" which I have no clue what it is.

Also, I would encourage you to do the following if you haven't already:

sudo apt-get update

Then check in system/administration/hardware drivers and see if there are any other drivers listed.  Depending on what you find there, this is what I would do:

- enable what ever driver is listed there for your wireless device

Check under network manager to see if you see wireless networks now.

If not, do the lsmod again and see if any of the broadcom modules are loaded (right now they aren't loaded, nor do I see anything called "w10" that the interface claims it is using currently.

I would also encourage you to keep asking for help as we should be able to get this to work (as long as you have a wired internet connection) without the need for the firmware cutter or ndiswrapper.  I'm not against those by any means, but big strides have been made for the Broadcom chipsets and it is best to use a native driver if possible.

If worse comes to worse, you can use ndiswrapper, at which time I would encourage you to post back.  There are ways to get that working without all the typing.  Again, though, we need to save that choice for later only if we can't get things working otherwise.

Dave 

Dave ;)

---

### Post by bkratz on 2010-06-30
> **anewguy said:**
> I noticed that your list of the network interfaces shows the following for eth1, your wireless adapter:



This would indicate it is trying to use a driver called "w10" which I have no clue what it is.

Also, I would encourage you to do the following if you haven't already:

sudo apt-get update

Then check in system/administration/hardware drivers and see if there are any other drivers listed.  Depending on what you find there, this is what I would do:

- enable what ever driver is listed there for your wireless device

Check under network manager to see if you see wireless networks now.

If not, do the lsmod again and see if any of the broadcom modules are loaded (right now they aren't loaded, nor do I see anything called "w10" that the interface claims it is using currently.

Dave ;)

Dave,

WL is the name of the STA driver.

---

### Post by bcasanov on 2010-06-30
I finally got the B43 driver to display in Restricted Drivers after doing what anewguy said with working with software sources and apt-get (thank you by the way), and I have enabled it (and of course, disabled the other driver: the Broadcom STA driver).  After downloading and installing the driver and after rebooting, I still have the same problem of not being able to use my wireless.  

The output of lsmod now is:

```
Module                  Size  Used by
btrfs                 458938  0 
zlib_deflate           19568  1 btrfs
crc32c                  2519  1 
libcrc32c                875  1 btrfs
ufs                    72774  0 
qnx4                    6484  0 
hfsplus                70800  0 
hfs                    40754  0 
minix                  25197  0 
ntfs                   94919  0 
msdos                   6392  0 
jfs                   172682  0 
xfs                   515324  0 
exportfs                3437  1 xfs
reiserfs              225539  0 
usbhid                 36174  0 
hid                    67032  1 usbhid
nls_iso8859_1           3249  1 
nls_cp437               4919  1 
vfat                    8933  1 
fat                    47767  2 msdos,vfat
aes_i586                7268  940 
aes_generic            26863  1 aes_i586
binfmt_misc             6587  1 
ppdev                   5259  0 
vboxdrv               191042  0 
dm_crypt               11331  0 
arc4                    1153  2 
b43                   164132  0 
joydev                  8708  0 
snd_hda_codec_idt      51978  1 
snd_hda_intel          22037  2 
mac80211              205146  1 b43
snd_hda_codec          74201  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70886  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
dell_wmi                1793  0 
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              126517  2 b43,mac80211
dell_laptop             6856  0 
dcdbas                  5490  1 dell_laptop
usblp                  10481  0 
led_class               2864  1 b43
snd                    54148  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                63245  0 
serio_raw               3978  0 
soundcore               6620  1 snd
snd_page_alloc          7172  2 snd_hda_intel,snd_pcm
lp                      7028  0 
parport                32635  2 ppdev,lp
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
i915                  285891  3 
drm_kms_helper         29297  1 i915
drm                   163034  4 i915,drm_kms_helper
usb_storage            39457  1 
intel_agp              24415  2 i915
sky2                   41040  0 
ssb                    38671  1 b43
ahci                   32200  2 
i2c_algo_bit            5028  1 i915
agpgart                31788  2 drm,intel_agp
video                  17375  1 i915
output                  1871  1 video

```

and the output of sudo lshw -C network now is:

```
  *-network               
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f69fc000-f69fffff
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 13
       serial: 00:25:64:5b:04:2e
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.25 duplex=full firmware=N/A ip=192.168.0.103 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:29 memory:f68fc000-f68fffff ioport:de00(size=256)
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 70:1a:04:02:b5:d6
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

```
I don't think I see any module conflicts or anything, but I might be wrong.  What should I do?

---

### Post by bcasanov on 2010-06-30
I went to /etc/modprobe.d/blacklist.conf and removed "blacklist bcm43xx" and then I restarted.  This is now the output of lsmod:
```
Module                  Size  Used by
nls_iso8859_1           3249  1 
nls_cp437               4919  1 
vfat                    8933  1 
fat                    47767  1 vfat
aes_i586                7268  1140 
aes_generic            26863  1 aes_i586
binfmt_misc             6587  1 
ppdev                   5259  0 
vboxdrv               191042  0 
dm_crypt               11331  0 
arc4                    1153  2 
b43                   164132  0 
joydev                  8708  0 
mac80211              205146  1 b43
snd_hda_codec_idt      51978  1 
cfg80211              126517  2 b43,mac80211
snd_hda_intel          22037  4 
snd_hda_codec          74201  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70886  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
led_class               2864  1 b43
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
dell_wmi                1793  0 
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
dell_laptop             6856  0 
dcdbas                  5490  1 dell_laptop
usblp                  10481  0 
ssb                    38671  1 b43
snd                    54148  19 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                63245  0 
serio_raw               3978  0 
soundcore               6620  1 snd
snd_page_alloc          7172  2 snd_hda_intel,snd_pcm
lp                      7028  0 
parport                32635  2 ppdev,lp
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
usbhid                 36174  0 
vga16fb                11385  0 
vgastate                8961  1 vga16fb
hid                    67032  1 usbhid
i915                  285891  3 
usb_storage            39457  1 
drm_kms_helper         29297  1 i915
drm                   163034  4 i915,drm_kms_helper
i2c_algo_bit            5028  1 i915
ahci                   32200  2 
intel_agp              24415  2 i915
sky2                   41040  0 
agpgart                31788  2 drm,intel_agp
video                  17375  1 i915
output                  1871  1 video

```

---

### Post by bcasanov on 2010-07-02
I tried the Ubuntu 10.04 LiveCD, and during that session, I tried something I did not think to do before.  First, though, I tried all methods to attempt to get wireless through enabling the B43 driver, and I did not have success on the LiveCD, which should have worked by all accounts. On my laptop, there is a key with a wireless tower icon on it, and I basically thought that I might as well try anything, including trying out this key I was unfamiliar with, and after I had pushed the key, I had wireless.  Now I know that this key acts as a physical on/off wireless toggle switch.  After the LiveCD session, I tried this discovery out on my Ubuntu install, and it worked!

---

### Post by Paddy Landau on 2010-07-03
That's a good lesson for everyone!

I'm glad you got it solved.

---

