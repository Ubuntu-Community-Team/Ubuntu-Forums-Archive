---
title: "Sound problem!"
date: 2010-02-02
forum: New to Ubuntu
---

### Post by naval9 on 2010-02-02
I am new to ubuntu and i have installed Karmic amd64 on my presario laptop.

Everything is working fine, except there is a constant (humming) sound in the background.
When i try to kill pulseaudio, the sound stops for a while, but resumes again in 5-7 seconds when pulseaudio re-spawns!

Any help would be appreciated! Thanks :)

---

### Post by Sealbhach on 2010-02-02
It might be a microphone? Maybe you could mute it or turn the volume down.

.

---

### Post by naval9 on 2010-02-02
No its not the microphone, i have already muted it.
I think there may be a problem with the driver?

---

### Post by Sealbhach on 2010-02-03
Maybe install aumix, it's got some more sound volume controls on it, and experiment with it until the buzzing goes away.

.

---

### Post by edanto on 2010-05-07
I too have this humming sound, 

Sadly I'm a complete amateur when it comes to ubuntu and have no idea how to install aumix as advised above. (well I guess I could figure that out, but I would be afraid I wouldn't uninstall whatever I should, and make things worse)

For me, as a total newb, how can I go about diagnosing and solving this problem, please?

---

### Post by lidex on 2010-05-08
Check your levels in alsamixer.
```
 alsamixer 
```
Press F6 to select the correct soundcard.
Press F3 to show playback levels. F4 selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.

---

### Post by edanto on 2010-05-08
Ah, that seems to have done something, thanks.  This is a tricky one though.

I dropped the level on the 'Mic' item to about 20 and the humming was inaudible, but with headphones on I could still hear the humming until I mute that channel.

When Mic is set to 20, I tried to use Skpye Call Test to see if my Mic would work and it won't.  Tried internal and external Mic, and neither recorded anything.

I ran the script you provided in the other thread and here are the results (Mic channel is set to 16, where the humming is just on the threshold of being audible)

```

!!################################
!!ALSA Information Script v 0.4.59
!!################################

!!Script ran on: Sat May  8 08:48:00 UTC 2010


!!Linux Distribution
!!------------------

Ubuntu 10.04 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.04 LTS"


!!DMI Information
!!---------------

Manufacturer:      Hewlett-Packard
Product Name:      HP Compaq nc6120 (PY505ET#ABU)


!!Kernel Information
!!------------------

Kernel release:    2.6.32-22-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.21
Library version:    1.0.22
Utilities version:  1.0.22


!!Loaded ALSA modules
!!-------------------

snd_intel8x0


!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes

ESound Daemon:
      Installed - Yes (/usr/bin/esd)
      Running - No

Jack:
      Installed - Yes (/usr/bin/jackd)
      Running - No


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [ICH6           ]: ICH4 - Intel ICH6
                      Intel ICH6 with AD1981B at irq 21


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)


!!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------

00:1e.2 0401: 8086:266e (rev 03)
	Subsystem: 103c:099c


!!Modprobe options (Sound related)
!!--------------------------------

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-usb-caiaq: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2


!!Loaded sound module options
!!--------------------------

!!Module: snd_intel8x0
	ac97_clock : 0
	ac97_quirk : <NULL>
	buggy_irq : N
	buggy_semaphore : N
	enable : N
	id : <NULL>
	index : -1
	joystick : 0
	spdif_aclink : 0
	xbox : N


!!AC97 Codec information
!!---------------------------
--startcollapse--

0-0/0: Analog Devices AD1981B

PCI Subsys Vendor: 0x103c
PCI Subsys Device: 0x099c

Flags: 10
Capabilities     : -headphone out-
DAC resolution   : 20-bit
ADC resolution   : 16-bit
3D enhancement   : No 3D Stereo Enhancement

Current setup
Mic gain         :  0dB [ 0dB]
POP path         : pre 3D
Sim. stereo      : off
3D enhancement   : off
Loudness         : off
Mono output      : MIX
Mic select       : Mic1
ADC/DAC loopback : off
Extended ID      : codec=0 rev=1 AMAP DSA=0 VRA
Extended status  : VRA
PCM front DAC    : 44100Hz
PCM ADC          : 44100Hz



AD18XX configuration
Unchained        : 0x1000,0x0000,0x0000
Chained          : 0x0000,0x0000,0x0000

0:00 = 0090
0:02 = 0404
0:04 = 0404
0:06 = 801f
0:08 = 0000
0:0a = 0000
0:0c = 0008
0:0e = 001a
0:10 = 0404
0:12 = 0606
0:14 = 0000
0:16 = 0808
0:18 = 0808
0:1a = 0000
0:1c = 0303
0:1e = 0000
0:20 = 0000
0:22 = 0000
0:24 = 0000
0:26 = 000f
0:28 = 0601
0:2a = 0031
0:2c = ac44
0:2e = 0000
0:30 = 0000
0:32 = ac44
0:34 = 0000
0:36 = 0000
0:38 = 0000
0:3a = 2000
0:3c = 0000
0:3e = 0000
0:40 = 0000
0:42 = 0000
0:44 = 0000
0:46 = 0000
0:48 = 0000
0:4a = 0000
0:4c = 0000
0:4e = 0000
0:50 = 0000
0:52 = 0000
0:54 = 0000
0:56 = 0000
0:58 = 0000
0:5a = 0000
0:5c = 4000
0:5e = 0000
0:60 = 8080
0:62 = 0000
0:64 = 8000
0:66 = 0000
0:68 = 0000
0:6a = 0000
0:6c = 0000
0:6e = 0000
0:70 = 0000
0:72 = 180c
0:74 = 1001
0:76 = 2050
0:78 = 0000
0:7a = 0000
0:7c = 4144
0:7e = 5374
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----  1 root audio 116, 10 May  7 22:24 /dev/snd/controlC0
crw-rw----  1 root audio 116,  9 May  7 22:38 /dev/snd/pcmC0D0c
crw-rw----  1 root audio 116,  8 May  8 09:28 /dev/snd/pcmC0D0p
crw-rw----  1 root audio 116,  7 May  7 22:24 /dev/snd/pcmC0D1c
crw-rw----  1 root audio 116,  6 May  7 22:24 /dev/snd/pcmC0D2c
crw-rw----  1 root audio 116,  5 May  7 22:24 /dev/snd/pcmC0D3c
crw-rw----  1 root audio 116,  4 May  7 22:24 /dev/snd/pcmC0D4p
crw-rw----  1 root audio 116,  3 May  7 22:24 /dev/snd/seq
crw-rw----  1 root audio 116,  2 May  7 22:24 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  60 May  7 22:24 .
drwxr-xr-x 3 root root 240 May  7 22:24 ..
lrwxrwxrwx 1 root root  12 May  7 22:24 pci-0000:00:1e.2 -> ../controlC0


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 1: Intel ICH - MIC ADC [Intel ICH6 - MIC ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 2: Intel ICH - MIC2 ADC [Intel ICH6 - MIC2 ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 3: Intel ICH - ADC2 [Intel ICH6 - ADC2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [ICH6]

Card hw:0 'ICH6'/'Intel ICH6 with AD1981B at irq 21'
  Mixer name	: 'Analog Devices AD1981B'
  Components	: 'AC97a:41445374'
  Controls      : 25
  Simple ctrls  : 18
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 27 [87%] [-6.00dB] [on]
  Front Right: Playback 27 [87%] [-6.00dB] [on]
Simple mixer control 'Master Mono',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [-46.50dB] [off]
Simple mixer control 'Headphone Jack Sense',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 23 [74%] [0.00dB] [on]
  Front Right: Playback 23 [74%] [0.00dB] [on]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 27 [87%] [6.00dB] [on] Capture [off]
  Front Right: Playback 27 [87%] [6.00dB] [on] Capture [off]
Simple mixer control 'Line Jack Sense',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 25 [81%] [3.00dB] [on] Capture [off]
  Front Right: Playback 25 [81%] [3.00dB] [on] Capture [off]
Simple mixer control 'Mic',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 5 [16%] [-27.00dB] [on]
  Front Left: Capture [on]
  Front Right: Capture [on]
Simple mixer control 'Mic Boost ( 20dB)',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Mic Select',0
  Capabilities: enum
  Items: 'Mic1' 'Mic2'
  Item0: 'Mic1'
Simple mixer control 'Video',0
  Capabilities: cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Phone',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 23 [74%] [0.00dB] [on]
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Aux',0
  Capabilities: pvolume pswitch cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 23 [74%] [0.00dB] [on] Capture [off]
  Front Right: Playback 23 [74%] [0.00dB] [on] Capture [off]
Simple mixer control 'Mono Output Select',0
  Capabilities: enum
  Items: 'Mix' 'Mic'
  Item0: 'Mix'
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 3 [20%] [4.50dB] [on]
  Front Right: Capture 3 [20%] [4.50dB] [on]
Simple mixer control 'Mix',0
  Capabilities: cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Mix Mono',0
  Capabilities: cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Stereo Mic',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]


!!Alsactl output
!!-------------

--startcollapse--
state.ICH6 {
	control.1 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Master Playback Switch'
		value.0 true
		value.1 true
	}
	control.2 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -4650
		comment.dbmax 0
		iface MIXER
		name 'Master Playback Volume'
		value.0 27
		value.1 27
	}
	control.5 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Master Mono Playback Switch'
		value false
	}
	control.6 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 31'
		comment.dbmin -4650
		comment.dbmax 0
		iface MIXER
		name 'Master Mono Playback Volume'
		value 0
	}
	control.7 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Phone Playback Switch'
		value true
	}
	control.8 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'Phone Playback Volume'
		value 23
	}
	control.9 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Mic Playback Switch'
		value true
	}
	control.10 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'Mic Playback Volume'
		value 5
	}
	control.11 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Mic Boost ( 20dB)'
		value false
	}
	control.12 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Line Playback Switch'
		value.0 true
		value.1 true
	}
	control.13 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'Line Playback Volume'
		value.0 27
		value.1 27
	}
	control.14 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'CD Playback Switch'
		value.0 true
		value.1 true
	}
	control.15 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'CD Playback Volume'
		value.0 25
		value.1 25
	}
	control.16 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Aux Playback Switch'
		value.0 true
		value.1 true
	}
	control.17 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'Aux Playback Volume'
		value.0 23
		value.1 23
	}
	control.18 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'PCM Playback Switch'
		value.0 true
		value.1 true
	}
	control.19 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'PCM Playback Volume'
		value.0 23
		value.1 23
	}
	control.20 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 2
		comment.item.0 Mic
		comment.item.1 CD
		comment.item.2 Video
		comment.item.3 Aux
		comment.item.4 Line
		comment.item.5 Mix
		comment.item.6 'Mix Mono'
		comment.item.7 Phone
		iface MIXER
		name 'Capture Source'
		value.0 Mic
		value.1 Mic
	}
	control.21 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Capture Switch'
		value.0 true
		value.1 true
	}
	control.22 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 15'
		comment.dbmin 0
		comment.dbmax 2250
		iface MIXER
		name 'Capture Volume'
		value.0 3
		value.1 3
	}
	control.23 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 Mix
		comment.item.1 Mic
		iface MIXER
		name 'Mono Output Select'
		value Mix
	}
	control.24 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 Mic1
		comment.item.1 Mic2
		iface MIXER
		name 'Mic Select'
		value Mic1
	}
	control.25 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Stereo Mic'
		value true
	}
	control.26 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Headphone Jack Sense'
		value true
	}
	control.27 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Line Jack Sense'
		value true
	}
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
isofs
udf
crc_itu_t
binfmt_misc
michael_mic
arc4
lib80211_crypt_tkip
ipt_REJECT
ipt_LOG
xt_limit
xt_tcpudp
ipt_addrtype
xt_state
rfcomm
sco
ip6table_filter
fbcon
tileblit
font
bitblit
softcursor
ip6_tables
vga16fb
bridge
stp
snd_intel8x0
vgastate
bnep
snd_ac97_codec
nf_nat_irc
nf_conntrack_irc
l2cap
ac97_bus
nf_nat_ftp
snd_pcm_oss
snd_mixer_oss
nf_nat
nf_conntrack_ipv4
snd_pcm
joydev
i915
snd_seq_dummy
nf_defrag_ipv4
snd_seq_oss
nf_conntrack_ftp
drm_kms_helper
nf_conntrack
snd_seq_midi
drm
snd_rawmidi
snd_seq_midi_event
snd_seq
intel_agp
iptable_filter
i2c_algo_bit
psmouse
snd_timer
tifm_7xx1
pcmcia
serio_raw
video
agpgart
ipw2200
snd_seq_device
irda
sdhci_pci
libipw
yenta_socket
rsrc_nonstatic
tifm_core
sdhci
ppdev
led_class
ip_tables
lp
snd
output
pcmcia_core
parport_pc
soundcore
x_tables
parport
crc_ccitt
btusb
snd_page_alloc
lib80211
bluetooth
ohci1394
tg3
ieee1394


!!ALSA/HDA dmesg
!!------------------



```

---

### Post by lidex on 2010-05-08
There may be other inputs to mute. And what about mic boost? Try using gnome-alsamixer to fiddle with enabling different elements in "Edit>Soundcard properties", then tweak them on the soundcard tab.

In alsamixer, press F4 to show your capture devices. I notice your drivers are mismatched. Use the alsa-upgrade-script link in my sig to fix that.

---

### Post by edanto on 2010-05-08
The alsa upgrade went well, and now the drivers seem to be matched, if I'm interpreting this correctly.

The hum persists.

```

!!################################
!!ALSA Information Script v 0.4.59
!!################################

!!Script ran on: Sat May  8 23:26:14 UTC 2010


!!Linux Distribution
!!------------------

Ubuntu 10.04 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.04 LTS"


!!DMI Information
!!---------------

Manufacturer:      Hewlett-Packard
Product Name:      HP Compaq nc6120 (PY505ET#ABU)


!!Kernel Information
!!------------------

Kernel release:    2.6.32-22-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.22.1
Library version:    1.0.22
Utilities version:  1.0.22


!!Loaded ALSA modules
!!-------------------

snd_intel8x0


!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes

ESound Daemon:
      Installed - Yes (/usr/bin/esd)
      Running - No

Jack:
      Installed - Yes (/usr/bin/jackd)
      Running - No


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [ICH6           ]: ICH4 - Intel ICH6
                      Intel ICH6 with AD1981B at irq 21


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)


!!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------

00:1e.2 0401: 8086:266e (rev 03)
	Subsystem: 103c:099c


!!Modprobe options (Sound related)
!!--------------------------------

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-usb-caiaq: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2


!!Loaded sound module options
!!--------------------------

!!Module: snd_intel8x0
	ac97_clock : 0
	ac97_quirk : <NULL>
	buggy_irq : N
	buggy_semaphore : N
	enable : N
	id : <NULL>
	index : -1
	joystick : 0
	spdif_aclink : 0
	xbox : N


!!AC97 Codec information
!!---------------------------
--startcollapse--

0-0/0: Analog Devices AD1981B

PCI Subsys Vendor: 0x103c
PCI Subsys Device: 0x099c

Flags: 10
Capabilities     : -headphone out-
DAC resolution   : 20-bit
ADC resolution   : 16-bit
3D enhancement   : No 3D Stereo Enhancement

Current setup
Mic gain         :  0dB [ 0dB]
POP path         : pre 3D
Sim. stereo      : off
3D enhancement   : off
Loudness         : off
Mono output      : MIX
Mic select       : Mic1
ADC/DAC loopback : off
Extended ID      : codec=0 rev=1 AMAP DSA=0 VRA
Extended status  : VRA
PCM front DAC    : 48000Hz
PCM ADC          : 44100Hz



AD18XX configuration
Unchained        : 0x1000,0x0000,0x0000
Chained          : 0x0000,0x0000,0x0000

0:00 = 0090
0:02 = 0000
0:04 = 0000
0:06 = 801f
0:08 = 0000
0:0a = 0000
0:0c = 0008
0:0e = 0011
0:10 = 0404
0:12 = 0606
0:14 = 0000
0:16 = 0808
0:18 = 0808
0:1a = 0000
0:1c = 0505
0:1e = 0000
0:20 = 0000
0:22 = 0000
0:24 = 0000
0:26 = 000f
0:28 = 0601
0:2a = 0031
0:2c = bb80
0:2e = 0000
0:30 = 0000
0:32 = ac44
0:34 = 0000
0:36 = 0000
0:38 = 0000
0:3a = 2000
0:3c = 0000
0:3e = 0000
0:40 = 0000
0:42 = 0000
0:44 = 0000
0:46 = 0000
0:48 = 0000
0:4a = 0000
0:4c = 0000
0:4e = 0000
0:50 = 0000
0:52 = 0000
0:54 = 0000
0:56 = 0000
0:58 = 0000
0:5a = 0000
0:5c = 4000
0:5e = 0000
0:60 = 8080
0:62 = 0000
0:64 = 8000
0:66 = 0000
0:68 = 0000
0:6a = 0000
0:6c = 0000
0:6e = 0000
0:70 = 0000
0:72 = 1804
0:74 = 1001
0:76 = 2050
0:78 = 0000
0:7a = 0000
0:7c = 4144
0:7e = 5374
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----  1 root audio 116,  0 May  8 18:34 /dev/snd/controlC0
crw-rw----  1 root audio 116, 24 May  8 18:34 /dev/snd/pcmC0D0c
crw-rw----  1 root audio 116, 16 May  8 23:30 /dev/snd/pcmC0D0p
crw-rw----  1 root audio 116, 25 May  8 18:34 /dev/snd/pcmC0D1c
crw-rw----  1 root audio 116, 26 May  8 18:34 /dev/snd/pcmC0D2c
crw-rw----  1 root audio 116, 27 May  8 18:34 /dev/snd/pcmC0D3c
crw-rw----  1 root audio 116, 20 May  8 18:34 /dev/snd/pcmC0D4p
crw-rw----  1 root audio 116,  1 May  8 18:34 /dev/snd/seq
crw-rw----  1 root audio 116, 33 May  8 18:34 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  60 May  8 18:34 .
drwxr-xr-x 3 root root 240 May  8 18:34 ..
lrwxrwxrwx 1 root root  12 May  8 18:34 pci-0000:00:1e.2 -> ../controlC0


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 1: Intel ICH - MIC ADC [Intel ICH6 - MIC ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 2: Intel ICH - MIC2 ADC [Intel ICH6 - MIC2 ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 3: Intel ICH - ADC2 [Intel ICH6 - ADC2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [ICH6]

Card hw:0 'ICH6'/'Intel ICH6 with AD1981B at irq 21'
  Mixer name	: 'Analog Devices AD1981B'
  Components	: 'AC97a:41445374'
  Controls      : 25
  Simple ctrls  : 18
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [0.00dB] [on]
  Front Right: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'Master Mono',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [-46.50dB] [off]
Simple mixer control 'Headphone Jack Sense',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 23 [74%] [0.00dB] [on]
  Front Right: Playback 23 [74%] [0.00dB] [on]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 27 [87%] [6.00dB] [on] Capture [off]
  Front Right: Playback 27 [87%] [6.00dB] [on] Capture [off]
Simple mixer control 'Line Jack Sense',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 25 [81%] [3.00dB] [on] Capture [off]
  Front Right: Playback 25 [81%] [3.00dB] [on] Capture [off]
Simple mixer control 'Mic',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 14 [45%] [-13.50dB] [on]
  Front Left: Capture [on]
  Front Right: Capture [on]
Simple mixer control 'Mic Boost ( 20dB)',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Mic Select',0
  Capabilities: enum
  Items: 'Mic1' 'Mic2'
  Item0: 'Mic1'
Simple mixer control 'Video',0
  Capabilities: cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Phone',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 23 [74%] [0.00dB] [on]
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Aux',0
  Capabilities: pvolume pswitch cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 23 [74%] [0.00dB] [on] Capture [off]
  Front Right: Playback 23 [74%] [0.00dB] [on] Capture [off]
Simple mixer control 'Mono Output Select',0
  Capabilities: enum
  Items: 'Mix' 'Mic'
  Item0: 'Mix'
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 5 [33%] [7.50dB] [on]
  Front Right: Capture 5 [33%] [7.50dB] [on]
Simple mixer control 'Mix',0
  Capabilities: cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Mix Mono',0
  Capabilities: cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Stereo Mic',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]


!!Alsactl output
!!-------------

--startcollapse--
state.ICH6 {
	control.1 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Master Playback Switch'
		value.0 true
		value.1 true
	}
	control.2 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -4650
		comment.dbmax 0
		iface MIXER
		name 'Master Playback Volume'
		value.0 31
		value.1 31
	}
	control.5 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Master Mono Playback Switch'
		value false
	}
	control.6 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 31'
		comment.dbmin -4650
		comment.dbmax 0
		iface MIXER
		name 'Master Mono Playback Volume'
		value 0
	}
	control.7 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Phone Playback Switch'
		value true
	}
	control.8 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'Phone Playback Volume'
		value 23
	}
	control.9 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Mic Playback Switch'
		value true
	}
	control.10 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'Mic Playback Volume'
		value 14
	}
	control.11 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Mic Boost ( 20dB)'
		value false
	}
	control.12 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Line Playback Switch'
		value.0 true
		value.1 true
	}
	control.13 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'Line Playback Volume'
		value.0 27
		value.1 27
	}
	control.14 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'CD Playback Switch'
		value.0 true
		value.1 true
	}
	control.15 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'CD Playback Volume'
		value.0 25
		value.1 25
	}
	control.16 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Aux Playback Switch'
		value.0 true
		value.1 true
	}
	control.17 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'Aux Playback Volume'
		value.0 23
		value.1 23
	}
	control.18 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'PCM Playback Switch'
		value.0 true
		value.1 true
	}
	control.19 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'PCM Playback Volume'
		value.0 23
		value.1 23
	}
	control.20 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 2
		comment.item.0 Mic
		comment.item.1 CD
		comment.item.2 Video
		comment.item.3 Aux
		comment.item.4 Line
		comment.item.5 Mix
		comment.item.6 'Mix Mono'
		comment.item.7 Phone
		iface MIXER
		name 'Capture Source'
		value.0 Mic
		value.1 Mic
	}
	control.21 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Capture Switch'
		value.0 true
		value.1 true
	}
	control.22 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 15'
		comment.dbmin 0
		comment.dbmax 2250
		iface MIXER
		name 'Capture Volume'
		value.0 5
		value.1 5
	}
	control.23 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 Mix
		comment.item.1 Mic
		iface MIXER
		name 'Mono Output Select'
		value Mix
	}
	control.24 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 Mic1
		comment.item.1 Mic2
		iface MIXER
		name 'Mic Select'
		value Mic1
	}
	control.25 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Stereo Mic'
		value true
	}
	control.26 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Headphone Jack Sense'
		value true
	}
	control.27 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Line Jack Sense'
		value true
	}
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
usbhid
hid
usb_storage
isofs
udf
crc_itu_t
snd_intel8x0
binfmt_misc
michael_mic
arc4
lib80211_crypt_tkip
snd_ac97_codec
rfcomm
ac97_bus
sco
bridge
stp
bnep
snd_pcm_oss
l2cap
snd_mixer_oss
snd_pcm
snd_seq_dummy
snd_seq_oss
snd_seq_midi
snd_rawmidi
fbcon
tileblit
font
snd_seq_midi_event
bitblit
softcursor
vga16fb
vgastate
snd_seq
pcmcia
ipt_REJECT
ipt_LOG
xt_limit
xt_tcpudp
ipt_addrtype
joydev
snd_timer
xt_state
snd_seq_device
ip6table_filter
ip6_tables
nf_nat_irc
nf_conntrack_irc
nf_nat_ftp
nf_nat
snd
nf_conntrack_ipv4
nf_defrag_ipv4
nf_conntrack_ftp
nf_conntrack
iptable_filter
i915
ip_tables
ipw2200
sdhci_pci
drm_kms_helper
soundcore
x_tables
tifm_7xx1
libipw
yenta_socket
ppdev
sdhci
intel_agp
snd_page_alloc
drm
i2c_algo_bit
btusb
bluetooth
tifm_core
lib80211
irda
crc_ccitt
rsrc_nonstatic
pcmcia_core
led_class
psmouse
serio_raw
parport_pc
agpgart
video
output
lp
parport
ohci1394
tg3
ieee1394


!!ALSA/HDA dmesg
!!------------------



```

As I examine the options in alsamixer, one thing is a bit unexpected.

The 'mic', 'Mic Boost' and Mic Select' are all in playback, and I would have expected that they were in capture.  Is this normal?

Mic Boost is muted, and unmuting it makes the humming far worse.  Mic is set to about 16, any higher the humming is annoying.

I can't record anything with skype test call.

When I go into Sound Preferences, there are no devices listed under 'input devices'

Hopefully these things are clues!  Thanks again.

---

### Post by lidex on 2010-05-08
Try gnome-alsamixer and enable everything in 'Edit>Soundcard Properties'. Close that and play around with options on the soundcard tab.

---

### Post by edanto on 2010-05-09
No noticeable effect of those changes.

Does this mean anything?


eoin@eoin-laptop:~$ gnome-alsamixer

** (gnome-alsamixer:27735): WARNING **: gam_toggle_get_state (). No idea what to do for mixer element "Mic Select"!

** (gnome-alsamixer:27735): WARNING **: gam_toggle_get_state (). No idea what to do for mixer element "Mono Output Select"!

** (gnome-alsamixer:27735): WARNING **: gam_toggle_get_state (). No idea what to do for mixer element "Mic Select"!

** (gnome-alsamixer:27735): WARNING **: gam_toggle_set_state (). No idea what to do for mixer element "Mic Select"!

---

### Post by edanto on 2010-05-12
I'm still annoyed by this humming, it's not going away!

Perhaps I should start a new thread.  

Is it possible to give someone knowledgeable remote access to my laptop to see if they can fix it, for a price?

---

