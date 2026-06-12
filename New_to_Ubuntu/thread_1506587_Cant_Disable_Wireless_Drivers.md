---
title: "Cant Disable Wireless Drivers"
date: 2010-06-10
forum: New to Ubuntu
---

### Post by [V] on 2010-06-10
I just installed Ubuntu (Lucid Lynx) a few days ago on my box. Everything is working great, except my WG111v3 USB Wireless device keeps randomly disconnecting & it is very stressful.

After doing some research, I see that this is a common problem. I believe I need to try running this device with Ndiswrappers; perhaps that will make it work because clearly the native drivers on Ubuntu are not working out.

Its my understanding that I've gotta disable my current drivers before attempting to install them. This is where I'm stuck.

lsusb returns
```

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0846:4260 NetGear, Inc. WG111(v3) 54 Mbps Wireless [RealTek RTL8187B]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```And just for kicks, lsmod returns
```

binfmt_misc             6587  1 
arc4                    1153  2 
snd_hda_codec_realtek   203168  1 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
snd_hda_intel          21877  2 
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
rtl8187                50680  0 
i915                  282354  4 
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
mac80211              204922  1 rtl8187
led_class               2864  1 rtl8187
drm_kms_helper         29297  1 i915
ppdev                   5259  0 
cfg80211              126485  2 rtl8187,mac80211
snd                    54148  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                63245  0 
eeprom_93cx6            1333  1 rtl8187
parport_pc             25962  1 
drm                   162471  5 i915,drm_kms_helper
i2c_algo_bit            5028  1 i915
serio_raw               3978  0 
lp                      7028  0 
soundcore               6620  1 snd
intel_agp              24177  2 i915
agpgart                31724  2 drm,intel_agp
video                  17375  1 i915
output                  1871  1 video
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
parport                32635  3 ppdev,parport_pc,lp
floppy                 53016  0 
e100                   28211  0 
mii                     4381  1 e100

```
so I went ahead and added to "/etc/modprobe.d/blacklist.conf"
```

blacklist RTL8187B

```I rebooted, and unfortunately my wireless card still works (lol)
Its only a matter of time before it kicks me off again.

modprobe -r RTL8187B

returns an error. I'm going to guess this is not the actual name of the driver being used?
How do i figure out the driver name so I can DESTROY IT! :D

thanks

---

### Post by c9-3Rr0r on 2010-06-10
From that i see form your lsmod command your driver is rtl8187 not like you typed in blacklist rtl8187b. Also I think that putting some module to blacklist is case sensitive so you should type it with small letters.

If that won't help u can try to rename rtl8187 module. From that I know it should be located in

** /lib/modules/'uname -r'/kernel/drivers/net/wireless/rt1818x **

**Warning** I've never try to do that way and I don't know what result of that operation can be so I advice you to make backup before trying do some changes.

---

### Post by [V] on 2010-06-10
Thanks, that worked. Had to be lower case & I removed the 'b'. What does the 'b' at the end even mean btw?

So I installed the new drivers & it still disconnected furiously. =[

I repeated the same process to try and install a seemingly broken WG311v2 PCI Card that never worked on any of my other windows boxes. And Much to my surprise it seems to be working fine now.

No random disconnects quite yet.
So for meow, case closed :D

---

