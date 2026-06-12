---
title: "DVD VERY choppy"
date: 2009-09-18
forum: New to Ubuntu
---

### Post by trachys on 2009-09-18
I finally got around to doing regionset, and had high expectations. But graphics all over the place, sound choppy. 

Using VLC.

I have no idea what's wrong. 

Some specs: 
Processor	        2x Intel(R) Pentium(R) Dual CPU T3400 @ 2.16GHz
Memory	                3050MB (394MB used)
Operating System	Ubuntu 9.04

Audio Adapter	        HDA-Intel - HDA Intel

Loaded Kernel Modules

isofs	
udf	                Universal Disk Format Filesystem
crc_itu_t	        CRC ITU-T V.41 calculations
i915	                Intel Graphics
drm	                DRM shared core routines
binfmt_misc	
ppdev	
bridge	
stp	
bnep	                Bluetooth BNEP ver 1.3
input_polldev	        Generic implementation of a polled input device
lp	
parport	
snd_hda_intel	        Intel HDA driver
snd_pcm_oss	        PCM OSS emulation for ALSA.
snd_mixer_oss	        Mixer OSS emulation for ALSA.
snd_pcm	                Midlevel PCM code for ALSA.
arc4	                ARC4 Cipher Algorithm
snd_seq_dummy	        ALSA sequencer MIDI-through client
ecb	                ECB block cipher algorithm
snd_seq_oss	        OSS-compatible sequencer module
snd_seq_midi	        Advanced Linux Sound Architecture sequencer MIDI synth.
iwlagn	                Intel(R) Wireless WiFi Link AGN driver for Linux
iwlcore	iwl core
snd_rawmidi	        Midlevel RawMidi code for ALSA.
uvcvideo	        USB Video Class driver
snd_seq_midi_event	MIDI byte <-> sequencer event coder
joydev	                Joystick device interfaces
compat_ioctl32	
led_class	        LED Class Interface
iTCO_wdt	        Intel TCO WatchDog Timer Driver
snd_seq	                Advanced Linux Sound Architecture sequencer.
snd_timer	        ALSA timer interface
psmouse	                PS/2 mouse driver
videodev	        Device registrar for Video4Linux drivers v2
video	                ACPI Video Driver
mac80211	        IEEE 802.11 subsystem
snd_seq_device	        ALSA sequencer device management
intel_agp	
serio_raw	        Raw serio driver
usbhid	                USB HID core driver
v4l1_compat	        v4l(1) compatibility layer for v4l2 drivers.
iTCO_vendor_support	Intel TCO Vendor Specific WatchDog Timer Driver Support
output	                Display Output Switcher Lowlevel Control Abstraction
pcspkr	                PC Speaker beeper driver
agpgart	                AGP GART driver
snd	                Advanced Linux Sound Architecture driver for soundcards.
cfg80211	        wireless configuration support
fujitsu_laptop	        Fujitsu laptop extras support
soundcore	        Core sound module
snd_page_alloc	        Memory allocator for ALSA system.
usb_storage	        USB Mass Storage driver for Linux
sky2	                Marvell Yukon 2 Gigabit Ethernet driver
fbcon	
tileblit	        Tile Blitting Operation
font	                Console Fonts
bitblit	                Bit Blitting Operation
softcursor	        Generic software cursor

---

### Post by desperado665 on 2009-09-18
try disabling compiz while playing dvd's. Right click on empty desktop and choose desktop settings. There you should be able to turn off desktop effects. Compiz eats up quite a bit of video resources.

---

### Post by mapes12 on 2009-09-18
Hi

Have you installed the none free codecs: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by trachys on 2009-09-18
Thanks desperado665, preferences are already set to No Effects.

Thanks mapes12, yes they're installed.

---

### Post by coolbrook on 2009-09-18
Which version of VLC?  What are the results with an alternate media player?

---

### Post by trachys on 2009-09-18
Thanks coolbrook.

I just tried with Move Player (Xine) and was told I haven't installed libdvdcss. I thought I had .. 

So I try again, here's what I see: 

 sudo /usr/share/doc/libdvdread4/install-css.sh 

[...]  

2009-09-18 16:58:04 (26.5 KB/s) - `/tmp/dvdcss-EALIgh/libdvdcss.deb' saved [36812/36812]

(Reading database ... 205973 files and directories currently installed.)
Preparing to replace libdvdcss2 1.2.10-0.2medibuntu1 (using .../dvdcss-EALIgh/libdvdcss.deb) ...
Unpacking replacement libdvdcss2 ...
Setting up libdvdcss2 (1.2.10-0.2medibuntu1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place


What's 'deferred processing'?

The VLC is 0.9.9a Grishenko.

---

### Post by trachys on 2009-09-18
:(

---

### Post by NoaHall on 2009-09-18
Well, update vlc to the latest version (1).

Is your graphics card installed? If not, install it, via System -> Admin -> Hardware Drivers

---

### Post by trachys on 2009-09-18
Thanks, NoaHall. 

Nothing lists for System -> Admin -> Hardware Drivers. I'm told that "No proprietary drivers are in use on this system."

I'm working on the PPA for VLC now.

---

### Post by NoaHall on 2009-09-18
Hm. That could be your problem, your graphics card.

---

### Post by trachys on 2009-09-18
Thanks, but I'm not sure what Flash has to do with this?

Why can't I install libdvdcss??

---

### Post by NoaHall on 2009-09-18
I didn't mention flash? That's my sig :D

Have you enabled the repos for it?

---

### Post by trachys on 2009-09-18
Heh thought that was your sig, but it wasn't on your previous post, so.

libdvdcss2 is installed. And ubuntu-restricted-extras 31. Is there something else I need?

(And I upgraded VLC, no better.)

---

### Post by SunnyRabbiera on 2009-09-18
> **trachys said:**
> Heh thought that was your sig, but it wasn't on your previous post, so.

libdvdcss2 is installed. And ubuntu-restricted-extras 31. Is there something else I need?

(And I upgraded VLC, no better.)

you didnt try movie player?
This might be your vid card, for some vid cards have odd side effects like this.

---

### Post by trachys on 2009-09-18
Thanks, SunnyRabbiera. Yeh I tried Movie Player, the output was worse than VLC or Xine.

I don't often have problems with video files, just DVDs.

(Though I can't find a decoder that will give me sound for youtube vids.)

---

### Post by shae on 2009-09-19
I believe your problem is with your video card.  Here is a great guide for trying to fix it: [https://wiki.ubuntu.com/X/Troubleshooting/IntelPerformance](https://wiki.ubuntu.com/X/Troubleshooting/IntelPerformance)

---

### Post by mapes12 on 2009-09-19
> **NoaHall said:**
> Hm. That could be your problem, your graphics card.Could we have a look at it please. In Terminal ```
sudo lshw -C display

```

---

### Post by trachys on 2009-09-19
Thanks shae, I'll check the wiki link now.

Thank you mapes12, here's the outuput:


  *-display:0 UNCLAIMED   
       description: VGA compatible controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list
       configuration: latency=0
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0

---

### Post by NoaHall on 2009-09-19
Yep, it's your graphics card. Not much can be done, as far as I know.

---

### Post by trachys on 2009-09-19
Damn.

---

