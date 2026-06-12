---
title: "Wireless connectivity problems with laptop, in 10.10"
date: 2010-11-21
forum: New to Ubuntu
---

### Post by krupintupple on 2010-11-21
simply put, my wife's laptop keeps disconnecting and i have no real idea how or where to look. things will be fine for a good while, but then she'll get disconnected and i'll need to restart the router (which appears to be the easiest way to "fix" the problem); a few hours later, she'll be booted again. we've two other wireless devices and they seem to remain connected indefinitely, so i'm leaning toward this not being a router issue in general, and more of a ubuntu one.

i'm a long-time linux user, but have forgotten most of my linux knowledge since Ubuntu usually "just works' :) i hate to say this, but before we upgraded her to 10.10, it never did this, so i'm leaning toward some manner of conflict or something within the software as opposed to hardware, but stranger things eh?

---

### Post by krupintupple on 2010-11-28
could anyone at least recommend any sort of diagnostic programs or tools, or log files i could check into?

---

### Post by sandyd on 2010-11-28
> **krupintupple said:**
> could anyone at least recommend any sort of diagnostic programs or tools, or log files i could check into?

post output of
```

lsmod
lspci
iwconfig 
```

---

### Post by anewguy on 2010-11-29
Is the laptop going to sleep or hibernating?  I've read ton's of post on hibernation, and some on the "sleep" (or whatever it's called) mode that comes before that.  It seems some devices don't "wake up" - perhaps your wireless is one of those.

Dave ;)

---

### Post by krupintupple on 2010-12-05
hey all,

sorry about the wait, but here goes:

> electorb@ladytron:~$ lsmod
Module Size Used by
binfmt_misc 6587 1 
ppdev 5259 0 
joydev 8708 0 
snd_hda_codec_realtek 203604 1 
fbcon 35102 71 
tileblit 2031 1 fbcon
font 7557 1 fbcon
bitblit 4707 1 fbcon
softcursor 1189 1 bitblit
vga16fb 11385 0 
vgastate 8961 1 vga16fb
snd_hda_intel 22037 2 
snd_hda_codec 74201 2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep 5412 1 snd_hda_codec
snd_pcm_oss 35308 0 
snd_mixer_oss 13746 1 snd_pcm_oss
snd_pcm 70694 3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy 1338 0 
arc4 1153 2 
snd_seq_oss 26722 0 
snd_seq_midi 4557 0 
snd_rawmidi 19056 1 snd_seq_midi
snd_seq_midi_event 6003 2 snd_seq_oss,snd_seq_midi
iwl3945 68727 0 
snd_seq 47263 6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
iwlcore 106050 1 iwl3945
i915 287426 3 
snd_timer 19098 2 snd_pcm,snd_seq
snd_seq_device 5700 5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
coretemp 4417 0 
uvcvideo 57054 0 
drm_kms_helper 29329 1 i915
mac80211 205402 2 iwl3945,iwlcore
led_class 2864 2 iwl3945,iwlcore
psmouse 63245 0 
videodev 34361 1 uvcvideo
v4l1_compat 13251 2 uvcvideo,videodev
snd 54180 16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm 162409 4 i915,drm_kms_helper
serio_raw 3978 0 
cfg80211 126528 3 iwl3945,iwlcore,mac80211
lp 7028 0 
soundcore 6620 1 snd
snd_page_alloc 7076 2 snd_hda_intel,snd_pcm
intel_agp 24375 2 i915
i2c_algo_bit 5028 1 i915
video 17375 1 i915
output 1871 1 video
agpgart 31724 2 drm,intel_agp
parport 32635 2 ppdev,lp
usb_storage 39553 0 
ahci 32200 2 
r8169 34108 0 
mii 4381 1 r8169

electorb@ladytron:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

electorb@ladytron:~$ iwconfig
lo no wireless extensions.

eth0 no wireless extensions.

wlan0 IEEE 802.11abg ESSID:"basement" 
Mode:Managed Frequency:2.412 GHz Access Point: 00:22:B0:D4:88:20 
Bit Rate=54 Mb/s Tx-Power=15 dBm 
Retry long limit:7 RTS thr:off Fragment thr:off
Power Management:off
Link Quality=65/70 Signal level=-45 dBm 
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0 

---

### Post by krupintupple on 2011-03-05
maybe i'm thinking about this incorrectly. since this is a standard installation, where would one find the log files for ... whatever package or program controls the wireless connectivity, in 10.10? hate to sound plebian, but perhaps if i were to check there, the log might indicate what/why things are going wonky?

---

### Post by fabio.montefuscolo on 2011-03-12
I had problems with this wireless card and I found a solution in [http://axcoto.com/blog/tag/siocsifflags-operation-not-possible-due-to-rf-kill](http://axcoto.com/blog/tag/siocsifflags-operation-not-possible-due-to-rf-kill)

---

