---
title: "HELP!! 8.04 sound problem"
date: 2010-02-15
forum: New to Ubuntu
---

### Post by pello on 2010-02-15
dear all,
I'm new at this ubuntu OS, I've installed ubuntu 8.04 and tried several step-by-step instruction on handling it yet it seemed I still cannot play any sound.

used the update manager, and according to 

sudo apt-get update

I think I've already get the updates I can. also I'm using creative inspire 2.1 2400 as speaker

please Help.

this is my alsa configuration 
[http://www.alsa-project.org/db/?f=f6e02e68ca3e6438adb4f44b965b39b7c4c80807](http://www.alsa-project.org/db/?f=f6e02e68ca3e6438adb4f44b965b39b7c4c80807)

!!################################
!!ALSA Information Script v 0.4.58
!!################################

!!Script ran on: Fri Feb 12 09:53:00 UTC 2010


!!Linux Distribution
!!------------------

Ubuntu 8.04.4 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 8.04.4 LTS"


!!DMI Information
!!---------------

Manufacturer:      IBM
Product Name:      2197KDQ


!!Kernel Information
!!------------------

Kernel release:    2.6.24-27-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.16
Library version:    1.0.15
Utilities version:  1.0.15


!!Loaded ALSA modules
!!-------------------

snd_trident
snd_mpu401


!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes

ESound Daemon:
      Installed - Yes (/usr/bin/esd)
      Running - No


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [SI7018         ]: SI7018 - SiS SI7018
                      SiS SI7018 PCI Audio at 0xe000, irq 5
 1 [UART           ]: MPU-401 UART - MPU-401 UART
                      MPU-401 UART at 0x330, irq 10


!!PCI Soundcards installed in the system
!!--------------------------------------

00:01.4 Multimedia audio controller: Silicon Integrated Systems [SiS] SiS PCI Audio Accelerator (rev 01)


!!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------

00:01.4 0401: 1039:7018 (rev 01)
	Subsystem: 1014:01b7


!!Modprobe options (Sound related)
!!--------------------------------

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-usx2y: index=-2
snd-usb-caiaq: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388


!!Loaded sound module options
!!--------------------------

!!Module: snd_trident
	enable : Y,Y,Y,Y,Y,Y,Y,Y
	id : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
	index : -1,-1,-1,-1,-1,-1,-1,-1
	pcm_channels : 32,32,32,32,32,32,32,32
	wavetable_size : 8192,8192,8192,8192,8192,8192,8192,8192

!!Module: snd_mpu401
	enable : Y,N,N,N,N,N,N,N
	id : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
	index : -2,-2,-2,-2,-2,-2,-2,-2
	irq : 10,65535,65535,65535,65535,65535,65535,65535
	pnp : Y,Y,Y,Y,Y,Y,Y,Y
	port : 816,1,1,1,1,1,1,1
	uart_enter : Y,Y,Y,Y,Y,Y,Y,Y


!!AC97 Codec information
!!---------------------------
--startcollapse--

0-0/0: Cirrus Logic CS4299 rev 4

PCI Subsys Vendor: 0x0000
PCI Subsys Device: 0x0000

Capabilities     : -headphone out-
DAC resolution   : 20-bit
ADC resolution   : 18-bit
3D enhancement   : Crystal Semi 3D Stereo Enhancement

Current setup
Mic gain         :  0dB [ 0dB]
POP path         : pre 3D
Sim. stereo      : off
3D enhancement   : off
Loudness         : off
Mono output      : MIX
Mic select       : Mic1
ADC/DAC loopback : off

0:00 = 0000
0:02 = 0000
0:04 = 0000
0:06 = 0000
0:08 = 0000
0:0a = 0000
0:0c = 0000
0:0e = 0000
0:10 = 0000
0:12 = 0000
0:14 = 0000
0:16 = 0000
0:18 = 0000
0:1a = 0000
0:1c = 0000
0:1e = 0000
0:20 = 0000
0:22 = 0000
0:24 = 0000
0:26 = 0000
0:28 = 0000
0:2a = 0000
0:2c = 0000
0:2e = 0000
0:30 = 0000
0:32 = 0000
0:34 = 0000
0:36 = 0000
0:38 = 0000
0:3a = 0000
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
0:5c = 0000
0:5e = 0000
0:60 = 0000
0:62 = 0000
0:64 = 0000
0:66 = 0000
0:68 = 0000
0:6a = 0000
0:6c = 0000
0:6e = 0000
0:70 = 0000
0:72 = 0000
0:74 = 0000
0:76 = 0000
0:78 = 0000
0:7a = 0000
0:7c = 0000
0:7e = 0000
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----  1 root audio 116,  0 Feb 12 10:34 /dev/snd/controlC0
crw-rw----  1 root audio 116, 32 Feb 12 10:34 /dev/snd/controlC1
crw-rw----  1 root audio 116, 40 Feb 12 10:34 /dev/snd/midiC1D0
crw-rw----  1 root audio 116, 24 Feb 12 10:36 /dev/snd/pcmC0D0c
crw-rw----  1 root audio 116, 16 Feb 12 16:33 /dev/snd/pcmC0D0p
crw-rw----  1 root audio 116, 17 Feb 12 15:14 /dev/snd/pcmC0D1p
crw-rw----  1 root audio 116,  1 Feb 12 10:34 /dev/snd/seq
crw-rw----  1 root audio 116, 33 Feb 12 10:34 /dev/snd/timer


!!ALSA configuration files
!!------------------------

!!User specific config file (~/.asoundrc)

# ALSA library configuration file

# Include settings that are under the control of asoundconf(1).
# (To disable these settings, comment out this line.)
</home/unisosdem/.asoundrc.asoundconf>



!!asoundconf-generated config file

# ALSA library configuration file managed by asoundconf(1).
#
# MANUAL CHANGES TO THIS FILE WILL BE OVERWRITTEN!
#
# Manual changes to the ALSA library configuration should be implemented
# by editing the ~/.asoundrc file, not by editing this file.
!defaults.pcm.card SI7018
defaults.ctl.card SI7018
defaults.pcm.device 0
defaults.pcm.subdevice -1
defaults.pcm.nonblock 1
defaults.pcm.ipc_key 5678293
defaults.pcm.ipc_gid audio
defaults.pcm.ipc_perm 0660
defaults.pcm.dmix.max_periods 0
defaults.pcm.dmix.rate 48000
defaults.pcm.dmix.format S16_LE
defaults.pcm.dmix.card defaults.pcm.card
defaults.pcm.dmix.device defaults.pcm.device
defaults.pcm.dsnoop.card defaults.pcm.card
defaults.pcm.dsnoop.device defaults.pcm.device
defaults.pcm.front.card defaults.pcm.card
defaults.pcm.front.device defaults.pcm.device
defaults.pcm.rear.card defaults.pcm.card
defaults.pcm.rear.device defaults.pcm.device
defaults.pcm.center_lfe.card defaults.pcm.card
defaults.pcm.center_lfe.device defaults.pcm.device
defaults.pcm.side.card defaults.pcm.card
defaults.pcm.side.device defaults.pcm.device
defaults.pcm.surround40.card defaults.pcm.card
defaults.pcm.surround40.device defaults.pcm.device
defaults.pcm.surround41.card defaults.pcm.card
defaults.pcm.surround41.device defaults.pcm.device
defaults.pcm.surround50.card defaults.pcm.card
defaults.pcm.surround50.device defaults.pcm.device
defaults.pcm.surround51.card defaults.pcm.card
defaults.pcm.surround51.device defaults.pcm.device
defaults.pcm.surround71.card defaults.pcm.card
defaults.pcm.surround71.device defaults.pcm.device
defaults.pcm.iec958.card defaults.pcm.card
defaults.pcm.iec958.device defaults.pcm.device
defaults.pcm.modem.card defaults.pcm.card
defaults.pcm.modem.device defaults.pcm.device
defaults.rawmidi.card 0
defaults.rawmidi.device 0
defaults.rawmidi.subdevice -1
defaults.hwdep.card 0
defaults.hwdep.device 0
defaults.timer.class 2
defaults.timer.sclass 0
defaults.timer.card 0
defaults.timer.device 0
defaults.timer.subdevice 0
defaults.namehint.showall off
defaults.namehint.basic on
defaults.namehint.extended off
pcm.!default { type pulse }
ctl.!default { type pulse }


!!System wide config file (/etc/asound.conf)

pcm.pulse {
    type pulse
}
ctl.pulse {
    type pulse
}
pcm.!default {
    type pulse
}
ctl.!default {
    type pulse
}


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: SI7018 [SiS SI7018], device 0: trident_dx_nx [Trident 4DWave]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 0: SI7018 [SiS SI7018], device 1: trident_dx_nx IEC958 [Trident 4DWave IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: SI7018 [SiS SI7018], device 0: trident_dx_nx [Trident 4DWave]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [SI7018]

Card hw:0 'SI7018'/'SiS SI7018 PCI Audio at 0xe000, irq 5'
  Mixer name	: 'Cirrus Logic CS4299 rev 4,0x800f800f PßP'
  Components	: 'AC97a:43525934 AC97m:800f800f'
  Controls      : 170
  Simple ctrls  : 153
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 63
  Mono:
  Front Left: Playback 48 [76%] [-22.50dB] [on]
  Front Right: Playback 48 [76%] [-22.50dB] [on]
Simple mixer control 'Master Mono',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 25 [81%] [-9.00dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 22 [71%] [-13.50dB] [on]
  Front Right: Playback 22 [71%] [-13.50dB] [on]
Simple mixer control '3D Control - Center',0
  Capabilities: volume volume-joined
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 15
  Mono: 0 [0%]
Simple mixer control '3D Control - Depth',0
  Capabilities: volume volume-joined
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 15
  Mono: 0 [0%]
Simple mixer control '3D Control - Switch',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'PCM',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 25 [81%] [3.00dB] [on]
  Front Right: Playback 25 [81%] [3.00dB] [on]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 22 [71%] [-1.50dB] [on] Capture [off]
  Front Right: Playback 22 [71%] [-1.50dB] [on] Capture [off]
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 25 [81%] [3.00dB] [on] Capture [off]
  Front Right: Playback 25 [81%] [3.00dB] [on] Capture [off]
Simple mixer control 'Mic',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [-34.50dB] [on]
  Front Left: Capture [on]
  Front Right: Capture [on]
Simple mixer control 'Mic Boost ( 20dB)',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Mic Select',0
  Capabilities: enum
  Items: 'Mic1' 'Mic2'
  Item0: 'Mic1'
Simple mixer control 'Video',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [-34.50dB] [off] Capture [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off] Capture [off]
Simple mixer control 'Phone',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [-34.50dB] [off]
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'IEC958',1
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'PC Speaker',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 15
  Mono: Playback 0 [0%] [-45.00dB] [off]
Simple mixer control 'Aux',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [-34.50dB] [off] Capture [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off] Capture [off]
Simple mixer control 'Mono Output Select',0
  Capabilities: enum
  Items: 'Mix' 'Mic'
  Item0: 'Mix'
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch cswitch-joined
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 0 [0%] [0.00dB] [on]
  Front Right: Capture 0 [0%] [0.00dB] [on]
Simple mixer control 'Mix',0
  Capabilities: cswitch cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Mix Mono',0
  Capabilities: cswitch cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Caller ID',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'External Amplifier',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Off-hook',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]

!!-------Mixer controls for card 1 [UART]

Card hw:1 'UART'/'MPU-401 UART at 0x330, irq 10'
  Mixer name	: ''
  Components	: ''
  Controls      : 0
  Simple ctrls  : 0


!!Alsactl output
!!-------------

--startcollapse--
state.SI7018 {
	control.1 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Master Playback Switch'
		value true
	}
	control.2 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 63'
		iface MIXER
		name 'Master Playback Volume'
		value.0 48
		value.1 48
	}
	control.3 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Headphone Playback Switch'
		value true
	}
	control.4 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		iface MIXER
		name 'Headphone Playback Volume'
		value.0 22
		value.1 22
	}
	control.5 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Master Mono Playback Switch'
		value true
	}
	control.6 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 31'
		iface MIXER
		name 'Master Mono Playback Volume'
		value 25
	}
	control.7 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'PC Speaker Playback Switch'
		value false
	}
	control.8 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 15'
		iface MIXER
		name 'PC Speaker Playback Volume'
		value 0
	}
	control.9 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Phone Playback Switch'
		value false
	}
	control.10 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 31'
		iface MIXER
		name 'Phone Playback Volume'
		value 0
	}
	control.11 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Mic Playback Switch'
		value true
	}
	control.12 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 31'
		iface MIXER
		name 'Mic Playback Volume'
		value 0
	}
	control.13 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Mic Boost ( 20dB)'
		value false
	}
	control.14 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Line Playback Switch'
		value true
	}
	control.15 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		iface MIXER
		name 'Line Playback Volume'
		value.0 22
		value.1 22
	}
	control.16 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'CD Playback Switch'
		value true
	}
	control.17 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		iface MIXER
		name 'CD Playback Volume'
		value.0 25
		value.1 25
	}
	control.18 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Video Playback Switch'
		value false
	}
	control.19 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		iface MIXER
		name 'Video Playback Volume'
		value.0 0
		value.1 0
	}
	control.20 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Aux Playback Switch'
		value false
	}
	control.21 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		iface MIXER
		name 'Aux Playback Volume'
		value.0 0
		value.1 0
	}
	control.22 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'PCM Playback Switch'
		value true
	}
	control.23 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		iface MIXER
		name 'PCM Playback Volume'
		value.0 25
		value.1 25
	}
	control.24 {
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
	control.25 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Capture Switch'
		value true
	}
	control.26 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 15'
		iface MIXER
		name 'Capture Volume'
		value.0 0
		value.1 0
	}
	control.27 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name '3D Control - Switch'
		value false
	}
	control.28 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 Mix
		comment.item.1 Mic
		iface MIXER
		name 'Mono Output Select'
		value Mix
	}
	control.29 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 Mic1
		comment.item.1 Mic2
		iface MIXER
		name 'Mic Select'
		value Mic1
	}
	control.30 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 15'
		iface MIXER
		name '3D Control - Center'
		value 0
	}
	control.31 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 15'
		iface MIXER
		name '3D Control - Depth'
		value 0
	}
	control.32 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Con Mask'
		value '0fff000f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.33 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Pro Mask'
		value cf00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
	}
	control.34 {
		comment.access 'read write'
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Default'
		value '0082000200000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.35 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Switch'
		value false
	}
	control.36 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'External Amplifier'
		value true
	}
	control.37 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Off-hook Switch'
		value false
	}
	control.38 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Caller ID Switch'
		value false
	}
	control.39 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 1023'
		iface MIXER
		name 'PCM Front Playback Volume'
		value 1013
	}
	control.40 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 1023'
		iface MIXER
		name 'PCM Front Playback Volume'
		index 1
		value 1013
	}
	control.41 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 1023'
		iface MIXER
		name 'PCM Front Playback Volume'
		index 2
		value 1013
	}
	control.42 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 1023'
		iface MIXER
		name 'PCM Front Playback Volume'
		index 3
		value 1013
	}
	control.43 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 1023'
		iface MIXER
		name 'PCM Front Playback Volume'
		index 4
		value 1013
	}
	control.44 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 1023'
		iface MIXER
		name 'PCM Front Playback Volume'
		index 5
		value 1013
	}
	control.45 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 1023'
		iface MIXER
		name 'PCM Front Playback Volume'
		index 6
		value 1013
	}
	control.46 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 1023'
		iface MIXER
		name 'PCM Front Playback Volume'
		index 7
		value 1013
	}
	control.47 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 1023'
		iface MIXER
		name 'PCM Front Playback Volume'
		index 8
		value 1013
	}
	control.48 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 1023'
		iface MIXER
		name 'PCM Front Playback Volume'
		index 9
		value 1013
	}
	control.49 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 1023'
		iface MIXER
		name 'PCM Front Playback Volume'
		index 10
		value 1013
	}
	control.50 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 1023'
		iface MIXER
		name 'PCM Front Playback Volume'
		index 11
		value 1013
	}
	control.51 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 1023'
		iface MIXER
		name 'PCM Front Playback Volume'
		index 12
		value 1013
	}
	control.52 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 1023'
		iface MIXER
		name 'PCM Front Playback Volume'
		index 13
		value 1013
	}
	control.53 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 1023'
		iface MIXER
		name 'PCM Front Playback Volume'
		index 14
		value 1013
	}
	control.54 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 1023'
		iface MIXER
		name 'PCM Front Playback Volume'
		index 15
		value 1013
	}
	control.55 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 1023'
		iface MIXER
		name 'PCM Front Playback Volume'
		index 16
		value 1013
	}
	control.56 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 1023'
		iface MIXER
		name 'PCM Front Playback Volume'
		index 17
		value 1013
	}
	control.57 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 1023'
		iface MIXER
		name 'PCM Front Playback Volume'
		index 18
		value 1013
	}
	control.58 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 1023'
		iface MIXER
		name 'PCM Front Playback Volume'
		index 19
		value 1013
	}
	control.59 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 1023'
		iface MIXER
		name 'PCM Front Playback Volume'
		index 20
		value 1013
	}
	control.60 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 1023'
		iface MIXER
		name 'PCM Front Playback Volume'
		index 21
		value 1013
	}
	control.61 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 1023'
		iface MIXER
		name 'PCM Front Playback Volume'
		index 22
		value 1013
	}
	control.62 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 1023'
		iface MIXER
		name 'PCM Front Playback Volume'
		index 23
		value 1013
	}
	control.63 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 1023'
		iface MIXER
		name 'PCM Front Playback Volume'
		index 24
		value 1013
	}
	control.64 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 1023'
		iface MIXER
		name 'PCM Front Playback Volume'
		index 25
		value 1013
	}
	control.65 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 1023'
		iface MIXER
		name 'PCM Front Playback Volume'
		index 26
		value 1013
	}
	control.66 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 1023'
		iface MIXER
		name 'PCM Front Playback Volume'
		index 27
		value 1013
	}
	control.67 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 1023'
		iface MIXER
		name 'PCM Front Playback Volume'
		index 28
		value 1013
	}
	control.68 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 1023'
		iface MIXER
		name 'PCM Front Playback Volume'
		index 29
		value 1013
	}
	control.69 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 1023'
		iface MIXER
		name 'PCM Front Playback Volume'
		index 30
		value 1013
	}
	control.70 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 1023'
		iface MIXER
		name 'PCM Front Playback Volume'
		index 31
		value 1013
	}
	control.71 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 127'
		iface MIXER
		name 'PCM Pan Playback Control'
		value 64
	}
	control.72 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 127'
		iface MIXER
		name 'PCM Pan Playback Control'
		index 1
		value 64
	}
	control.73 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 127'
		iface MIXER
		name 'PCM Pan Playback Control'
		index 2
		value 64
	}
	control.74 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 127'
		iface MIXER
		name 'PCM Pan Playback Control'
		index 3
		value 64
	}
	control.75 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 127'
		iface MIXER
		name 'PCM Pan Playback Control'
		index 4
		value 64
	}
	control.76 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 127'
		iface MIXER
		name 'PCM Pan Playback Control'
		index 5
		value 64
	}
	control.77 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 127'
		iface MIXER
		name 'PCM Pan Playback Control'
		index 6
		value 64
	}
	control.78 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 127'
		iface MIXER
		name 'PCM Pan Playback Control'
		index 7
		value 64
	}
	control.79 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 127'
		iface MIXER
		name 'PCM Pan Playback Control'
		index 8
		value 64
	}
	control.80 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 127'
		iface MIXER
		name 'PCM Pan Playback Control'
		index 9
		value 64
	}
	control.81 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 127'
		iface MIXER
		name 'PCM Pan Playback Control'
		index 10
		value 64
	}
	control.82 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 127'
		iface MIXER
		name 'PCM Pan Playback Control'
		index 11
		value 64
	}
	control.83 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 127'
		iface MIXER
		name 'PCM Pan Playback Control'
		index 12
		value 64
	}
	control.84 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 127'
		iface MIXER
		name 'PCM Pan Playback Control'
		index 13
		value 64
	}
	control.85 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 127'
		iface MIXER
		name 'PCM Pan Playback Control'
		index 14
		value 64
	}
	control.86 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 127'
		iface MIXER
		name 'PCM Pan Playback Control'
		index 15
		value 64
	}
	control.87 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 127'
		iface MIXER
		name 'PCM Pan Playback Control'
		index 16
		value 64
	}
	control.88 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 127'
		iface MIXER
		name 'PCM Pan Playback Control'
		index 17
		value 64
	}
	control.89 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 127'
		iface MIXER
		name 'PCM Pan Playback Control'
		index 18
		value 64
	}
	control.90 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 127'
		iface MIXER
		name 'PCM Pan Playback Control'
		index 19
		value 64
	}
	control.91 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 127'
		iface MIXER
		name 'PCM Pan Playback Control'
		index 20
		value 64
	}
	control.92 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 127'
		iface MIXER
		name 'PCM Pan Playback Control'
		index 21
		value 64
	}
	control.93 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 127'
		iface MIXER
		name 'PCM Pan Playback Control'
		index 22
		value 64
	}
	control.94 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 127'
		iface MIXER
		name 'PCM Pan Playback Control'
		index 23
		value 64
	}
	control.95 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 127'
		iface MIXER
		name 'PCM Pan Playback Control'
		index 24
		value 64
	}
	control.96 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 127'
		iface MIXER
		name 'PCM Pan Playback Control'
		index 25
		value 64
	}
	control.97 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 127'
		iface MIXER
		name 'PCM Pan Playback Control'
		index 26
		value 64
	}
	control.98 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 127'
		iface MIXER
		name 'PCM Pan Playback Control'
		index 27
		value 64
	}
	control.99 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 127'
		iface MIXER
		name 'PCM Pan Playback Control'
		index 28
		value 64
	}
	control.100 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 127'
		iface MIXER
		name 'PCM Pan Playback Control'
		index 29
		value 64
	}
	control.101 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 127'
		iface MIXER
		name 'PCM Pan Playback Control'
		index 30
		value 64
	}
	control.102 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 127'
		iface MIXER
		name 'PCM Pan Playback Control'
		index 31
		value 64
	}
	control.103 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 127'
		iface MIXER
		name 'PCM Reverb Playback Volume'
		value 0
	}
	control.104 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 127'
		iface MIXER
		name 'PCM Reverb Playback Volume'
		index 1
		value 0
	}
	control.105 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 127'
		iface MIXER
		name 'PCM Reverb Playback Volume'
		index 2
		value 0
	}
	control.106 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 127'
		iface MIXER
		name 'PCM Reverb Playback Volume'
		index 3
		value 0
	}
	control.107 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 127'
		iface MIXER
		name 'PCM Reverb Playback Volume'
		index 4
		value 0
	}
	control.108 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 127'
		iface MIXER
		name 'PCM Reverb Playback Volume'
		index 5
		value 0
	}
	control.109 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 127'
		iface MIXER
		name 'PCM Reverb Playback Volume'
		index 6
		value 0
	}
	control.110 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 127'
		iface MIXER
		name 'PCM Reverb Playback Volume'
		index 7
		value 0
	}
	control.111 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 127'
		iface MIXER
		name 'PCM Reverb Playback Volume'
		index 8
		value 0
	}
	control.112 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 127'
		iface MIXER
		name 'PCM Reverb Playback Volume'
		index 9
		value 0
	}
	control.113 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 127'
		iface MIXER
		name 'PCM Reverb Playback Volume'
		index 10
		value 0
	}
	control.114 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 127'
		iface MIXER
		name 'PCM Reverb Playback Volume'
		index 11
		value 0
	}
	control.115 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 127'
		iface MIXER
		name 'PCM Reverb Playback Volume'
		index 12
		value 0
	}
	control.116 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 127'
		iface MIXER
		name 'PCM Reverb Playback Volume'
		index 13
		value 0
	}
	control.117 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 127'
		iface MIXER
		name 'PCM Reverb Playback Volume'
		index 14
		value 0
	}
	control.118 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 127'
		iface MIXER
		name 'PCM Reverb Playback Volume'
		index 15
		value 0
	}
	control.119 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 127'
		iface MIXER
		name 'PCM Reverb Playback Volume'
		index 16
		value 0
	}
	control.120 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 127'
		iface MIXER
		name 'PCM Reverb Playback Volume'
		index 17
		value 0
	}
	control.121 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 127'
		iface MIXER
		name 'PCM Reverb Playback Volume'
		index 18
		value 0
	}
	control.122 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 127'
		iface MIXER
		name 'PCM Reverb Playback Volume'
		index 19
		value 0
	}
	control.123 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 127'
		iface MIXER
		name 'PCM Reverb Playback Volume'
		index 20
		value 0
	}
	control.124 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 127'
		iface MIXER
		name 'PCM Reverb Playback Volume'
		index 21
		value 0
	}
	control.125 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 127'
		iface MIXER
		name 'PCM Reverb Playback Volume'
		index 22
		value 0
	}
	control.126 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 127'
		iface MIXER
		name 'PCM Reverb Playback Volume'
		index 23
		value 0
	}
	control.127 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 127'
		iface MIXER
		name 'PCM Reverb Playback Volume'
		index 24
		value 0
	}
	control.128 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 127'
		iface MIXER
		name 'PCM Reverb Playback Volume'
		index 25
		value 0
	}
	control.129 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 127'
		iface MIXER
		name 'PCM Reverb Playback Volume'
		index 26
		value 0
	}
	control.130 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 127'
		iface MIXER
		name 'PCM Reverb Playback Volume'
		index 27
		value 0
	}
	control.131 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 127'
		iface MIXER
		name 'PCM Reverb Playback Volume'
		index 28
		value 0
	}
	control.132 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 127'
		iface MIXER
		name 'PCM Reverb Playback Volume'
		index 29
		value 0
	}
	control.133 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 127'
		iface MIXER
		name 'PCM Reverb Playback Volume'
		index 30
		value 0
	}
	control.134 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 127'
		iface MIXER
		name 'PCM Reverb Playback Volume'
		index 31
		value 0
	}
	control.135 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 127'
		iface MIXER
		name 'PCM Chorus Playback Volume'
		value 0
	}
	control.136 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 127'
		iface MIXER
		name 'PCM Chorus Playback Volume'
		index 1
		value 0
	}
	control.137 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 127'
		iface MIXER
		name 'PCM Chorus Playback Volume'
		index 2
		value 0
	}
	control.138 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 127'
		iface MIXER
		name 'PCM Chorus Playback Volume'
		index 3
		value 0
	}
	control.139 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 127'
		iface MIXER
		name 'PCM Chorus Playback Volume'
		index 4
		value 0
	}
	control.140 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 127'
		iface MIXER
		name 'PCM Chorus Playback Volume'
		index 5
		value 0
	}
	control.141 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 127'
		iface MIXER
		name 'PCM Chorus Playback Volume'
		index 6
		value 0
	}
	control.142 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 127'
		iface MIXER
		name 'PCM Chorus Playback Volume'
		index 7
		value 0
	}
	control.143 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 127'
		iface MIXER
		name 'PCM Chorus Playback Volume'
		index 8
		value 0
	}
	control.144 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 127'
		iface MIXER
		name 'PCM Chorus Playback Volume'
		index 9
		value 0
	}
	control.145 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 127'
		iface MIXER
		name 'PCM Chorus Playback Volume'
		index 10
		value 0
	}
	control.146 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 127'
		iface MIXER
		name 'PCM Chorus Playback Volume'
		index 11
		value 0
	}
	control.147 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 127'
		iface MIXER
		name 'PCM Chorus Playback Volume'
		index 12
		value 0
	}
	control.148 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 127'
		iface MIXER
		name 'PCM Chorus Playback Volume'
		index 13
		value 0
	}
	control.149 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 127'
		iface MIXER
		name 'PCM Chorus Playback Volume'
		index 14
		value 0
	}
	control.150 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 127'
		iface MIXER
		name 'PCM Chorus Playback Volume'
		index 15
		value 0
	}
	control.151 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 127'
		iface MIXER
		name 'PCM Chorus Playback Volume'
		index 16
		value 0
	}
	control.152 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 127'
		iface MIXER
		name 'PCM Chorus Playback Volume'
		index 17
		value 0
	}
	control.153 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 127'
		iface MIXER
		name 'PCM Chorus Playback Volume'
		index 18
		value 0
	}
	control.154 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 127'
		iface MIXER
		name 'PCM Chorus Playback Volume'
		index 19
		value 0
	}
	control.155 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 127'
		iface MIXER
		name 'PCM Chorus Playback Volume'
		index 20
		value 0
	}
	control.156 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 127'
		iface MIXER
		name 'PCM Chorus Playback Volume'
		index 21
		value 0
	}
	control.157 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 127'
		iface MIXER
		name 'PCM Chorus Playback Volume'
		index 22
		value 0
	}
	control.158 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 127'
		iface MIXER
		name 'PCM Chorus Playback Volume'
		index 23
		value 0
	}
	control.159 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 127'
		iface MIXER
		name 'PCM Chorus Playback Volume'
		index 24
		value 0
	}
	control.160 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 127'
		iface MIXER
		name 'PCM Chorus Playback Volume'
		index 25
		value 0
	}
	control.161 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 127'
		iface MIXER
		name 'PCM Chorus Playback Volume'
		index 26
		value 0
	}
	control.162 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 127'
		iface MIXER
		name 'PCM Chorus Playback Volume'
		index 27
		value 0
	}
	control.163 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 127'
		iface MIXER
		name 'PCM Chorus Playback Volume'
		index 28
		value 0
	}
	control.164 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 127'
		iface MIXER
		name 'PCM Chorus Playback Volume'
		index 29
		value 0
	}
	control.165 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 127'
		iface MIXER
		name 'PCM Chorus Playback Volume'
		index 30
		value 0
	}
	control.166 {
		comment.access 'read write inactive'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 127'
		iface MIXER
		name 'PCM Chorus Playback Volume'
		index 31
		value 0
	}
	control.167 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Switch'
		index 1
		value false
	}
	control.168 {
		comment.access 'read write'
		comment.type IEC958
		comment.count 1
		iface PCM
		device 1
		name 'IEC958 Playback Default'
		index 1
		value '0082000200000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.169 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface PCM
		device 1
		name 'IEC958 Playback Mask'
		index 1
		value ffffffff00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
	}
	control.170 {
		comment.access 'read write inactive'
		comment.type IEC958
		comment.count 1
		iface PCM
		device 1
		name 'IEC958 Playback PCM Stream'
		index 1
		value '0082000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
}
state.UART {
	control {
	}
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
usb_storage
libusual
ipv6
af_packet
sis
drm
rfcomm
l2cap
bluetooth
ppdev
speedstep_lib
cpufreq_userspace
cpufreq_stats
cpufreq_ondemand
freq_table
cpufreq_conservative
cpufreq_powersave
sbs
sbshc
container
dock
video
output
battery
iptable_filter
ip_tables
x_tables
nls_iso8859_1
nls_cp437
vfat
fat
ac
sbp2
lp
parport_pc
parport
snd_mpu401
snd_trident
snd_ac97_codec
evdev
ac97_bus
analog
snd_pcm_oss
snd_mixer_oss
gameport
snd_pcm
snd_page_alloc
snd_util_mem
snd_mpu401_uart
snd_seq_dummy
button
snd_seq_oss
snd_seq_midi
snd_rawmidi
snd_seq_midi_event
snd_seq
pcspkr
snd_timer
snd_seq_device
shpchp
snd
pci_hotplug
i2c_sis630
soundcore
sis_agp
i2c_core
agpgart
ext3
jbd
mbcache
usbhid
sg
hid
sr_mod
cdrom
sd_mod
pata_sis
ata_generic
floppy
ohci1394
ieee1394
ohci_hcd
pata_acpi
usbcore
sis900
mii
libata
scsi_mod
thermal
processor
fan
fbcon
tileblit
font
bitblit
softcursor
fuse


!!ALSA/HDA dmesg
!!------------------

[   68.694777] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   70.159574] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/ac97/ac97_codec.c:2160: MC'97 1 converters and GPIO not ready (0x800f)
[   70.179043] gameport: Trident 4DWave is pci0000:00:01.4/gameport0, speed 2711kHz
[   73.216123] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/trident/../../alsa-kernel/pci/trident/trident_main.c:159: ac97 codec read TIMEOUT [0x54/0x800fc0d4]!!!
[   74.437425] lp0: using parport0 (interrupt-driven).
--
[17867.514932] usb 2-1.4: USB disconnect, address 11
[22763.066569] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/trident/../../alsa-kernel/pci/trident/trident_main.c:159: ac97 codec read TIMEOUT [0xe/0x800fc00e]!!!
[22763.095803] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/trident/../../alsa-kernel/pci/trident/trident_main.c:159: ac97 codec read TIMEOUT [0x20/0x800fc020]!!!
[22763.125465] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/trident/../../alsa-kernel/pci/trident/trident_main.c:159: ac97 codec read TIMEOUT [0x28/0x800fc028]!!!
[22763.151294] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/trident/../../alsa-kernel/pci/trident/trident_main.c:159: ac97 codec read TIMEOUT [0x3c/0x800fc03c]!!!
[22763.184964] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/trident/../../alsa-kernel/pci/trident/trident_main.c:159: ac97 codec read TIMEOUT [0x0/0x800fc000]!!!
[22763.214079] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/trident/../../alsa-kernel/pci/trident/trident_main.c:159: ac97 codec read TIMEOUT [0x2/0x800fc002]!!!
[22763.243929] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/trident/../../alsa-kernel/pci/trident/trident_main.c:159: ac97 codec read TIMEOUT [0x4/0x800fc004]!!!
[22763.274609] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/trident/../../alsa-kernel/pci/trident/trident_main.c:159: ac97 codec read TIMEOUT [0x6/0x800fc006]!!!
[22763.303479] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/trident/../../alsa-kernel/pci/trident/trident_main.c:159: ac97 codec read TIMEOUT [0x8/0x800fc008]!!!
[22763.333074] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/trident/../../alsa-kernel/pci/trident/trident_main.c:159: ac97 codec read TIMEOUT [0xa/0x800fc00a]!!!
[22763.362599] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/trident/../../alsa-kernel/pci/trident/trident_main.c:159: ac97 codec read TIMEOUT [0xc/0x800fc00c]!!!
[22763.393393] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/trident/../../alsa-kernel/pci/trident/trident_main.c:159: ac97 codec read TIMEOUT [0xe/0x800fc00e]!!!
[22763.421846] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/trident/../../alsa-kernel/pci/trident/trident_main.c:159: ac97 codec read TIMEOUT [0x10/0x800fc010]!!!
[22763.456016] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/trident/../../alsa-kernel/pci/trident/trident_main.c:159: ac97 codec read TIMEOUT [0x12/0x800fc012]!!!
[22763.484925] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/trident/../../alsa-kernel/pci/trident/trident_main.c:159: ac97 codec read TIMEOUT [0x14/0x800fc014]!!!
[22763.512594] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/trident/../../alsa-kernel/pci/trident/trident_main.c:159: ac97 codec read TIMEOUT [0x16/0x800fc016]!!!
[22763.541187] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/trident/../../alsa-kernel/pci/trident/trident_main.c:159: ac97 codec read TIMEOUT [0x18/0x800fc018]!!!
[22763.569937] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/trident/../../alsa-kernel/pci/trident/trident_main.c:159: ac97 codec read TIMEOUT [0x1a/0x800fc01a]!!!
[22763.598706] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/trident/../../alsa-kernel/pci/trident/trident_main.c:159: ac97 codec read TIMEOUT [0x1c/0x800fc01c]!!!
[22763.626412] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/trident/../../alsa-kernel/pci/trident/trident_main.c:159: ac97 codec read TIMEOUT [0x1e/0x800fc01e]!!!
[22763.654328] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/trident/../../alsa-kernel/pci/trident/trident_main.c:159: ac97 codec read TIMEOUT [0x20/0x800fc020]!!!
[22763.681986] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/trident/../../alsa-kernel/pci/trident/trident_main.c:159: ac97 codec read TIMEOUT [0x22/0x800fc022]!!!
[22763.710614] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/trident/../../alsa-kernel/pci/trident/trident_main.c:159: ac97 codec read TIMEOUT [0x24/0x800fc024]!!!
[22763.738768] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/trident/../../alsa-kernel/pci/trident/trident_main.c:159: ac97 codec read TIMEOUT [0x26/0x800fc026]!!!
[22763.768592] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/trident/../../alsa-kernel/pci/trident/trident_main.c:159: ac97 codec read TIMEOUT [0x28/0x800fc028]!!!
[22763.795287] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/trident/../../alsa-kernel/pci/trident/trident_main.c:159: ac97 codec read TIMEOUT [0x2a/0x800fc02a]!!!
[22763.822614] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/trident/../../alsa-kernel/pci/trident/trident_main.c:159: ac97 codec read TIMEOUT [0x2c/0x800fc02c]!!!
[22763.850319] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/trident/../../alsa-kernel/pci/trident/trident_main.c:159: ac97 codec read TIMEOUT [0x2e/0x800fc02e]!!!
[22763.882030] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/trident/../../alsa-kernel/pci/trident/trident_main.c:159: ac97 codec read TIMEOUT [0x30/0x800fc030]!!!
[22763.912952] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/trident/../../alsa-kernel/pci/trident/trident_main.c:159: ac97 codec read TIMEOUT [0x32/0x800fc032]!!!
[22763.940780] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/trident/../../alsa-kernel/pci/trident/trident_main.c:159: ac97 codec read TIMEOUT [0x34/0x800fc034]!!!
[22763.967338] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/trident/../../alsa-kernel/pci/trident/trident_main.c:159: ac97 codec read TIMEOUT [0x36/0x800fc036]!!!
[22763.996851] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/trident/../../alsa-kernel/pci/trident/trident_main.c:159: ac97 codec read TIMEOUT [0x38/0x800fc038]!!!
[22764.024519] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/trident/../../alsa-kernel/pci/trident/trident_main.c:159: ac97 codec read TIMEOUT [0x3a/0x800fc03a]!!!
[22764.054040] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/trident/../../alsa-kernel/pci/trident/trident_main.c:159: ac97 codec read TIMEOUT [0x3c/0x800fc03c]!!!
[22764.082561] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/trident/../../alsa-kernel/pci/trident/trident_main.c:159: ac97 codec read TIMEOUT [0x3e/0x800fc03e]!!!
[22764.113629] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/trident/../../alsa-kernel/pci/trident/trident_main.c:159: ac97 codec read TIMEOUT [0x40/0x800fc040]!!!
[22764.142301] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/trident/../../alsa-kernel/pci/trident/trident_main.c:159: ac97 codec read TIMEOUT [0x42/0x800fc042]!!!
[22764.172715] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/trident/../../alsa-kernel/pci/trident/trident_main.c:159: ac97 codec read TIMEOUT [0x44/0x800fc044]!!!
[22764.200662] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/trident/../../alsa-kernel/pci/trident/trident_main.c:159: ac97 codec read TIMEOUT [0x46/0x800fc046]!!!
[22764.229556] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/trident/../../alsa-kernel/pci/trident/trident_main.c:159: ac97 codec read TIMEOUT [0x48/0x800fc048]!!!
[22764.259156] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/trident/../../alsa-kernel/pci/trident/trident_main.c:159: ac97 codec read TIMEOUT [0x4a/0x800fc04a]!!!
[22764.289709] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/trident/../../alsa-kernel/pci/trident/trident_main.c:159: ac97 codec read TIMEOUT [0x4c/0x800fc04c]!!!
[22764.318390] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/trident/../../alsa-kernel/pci/trident/trident_main.c:159: ac97 codec read TIMEOUT [0x4e/0x800fc04e]!!!
[22764.367533] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/trident/../../alsa-kernel/pci/trident/trident_main.c:159: ac97 codec read TIMEOUT [0x50/0x800fc050]!!!
[22764.397020] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/trident/../../alsa-kernel/pci/trident/trident_main.c:159: ac97 codec read TIMEOUT [0x52/0x800fc052]!!!
[22764.423733] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/trident/../../alsa-kernel/pci/trident/trident_main.c:159: ac97 codec read TIMEOUT [0x54/0x800fc054]!!!
[22764.461980] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/trident/../../alsa-kernel/pci/trident/trident_main.c:159: ac97 codec read TIMEOUT [0x56/0x800fc056]!!!
[22764.493275] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/trident/../../alsa-kernel/pci/trident/trident_main.c:159: ac97 codec read TIMEOUT [0x58/0x800fc058]!!!
[22764.521975] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/trident/../../alsa-kernel/pci/trident/trident_main.c:159: ac97 codec read TIMEOUT [0x5a/0x800fc05a]!!!
[22764.549696] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/trident/../../alsa-kernel/pci/trident/trident_main.c:159: ac97 codec read TIMEOUT [0x5c/0x800fc05c]!!!
[22764.577626] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/trident/../../alsa-kernel/pci/trident/trident_main.c:159: ac97 codec read TIMEOUT [0x5e/0x800fc05e]!!!
[22764.606207] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/trident/../../alsa-kernel/pci/trident/trident_main.c:159: ac97 codec read TIMEOUT [0x60/0x800fc060]!!!
[22764.635967] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/trident/../../alsa-kernel/pci/trident/trident_main.c:159: ac97 codec read TIMEOUT [0x62/0x800fc062]!!!
[22764.664646] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/trident/../../alsa-kernel/pci/trident/trident_main.c:159: ac97 codec read TIMEOUT [0x64/0x800fc064]!!!
[22764.692585] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/trident/../../alsa-kernel/pci/trident/trident_main.c:159: ac97 codec read TIMEOUT [0x66/0x800fc066]!!!
[22764.721285] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/trident/../../alsa-kernel/pci/trident/trident_main.c:159: ac97 codec read TIMEOUT [0x68/0x800fc068]!!!
[22764.750172] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/trident/../../alsa-kernel/pci/trident/trident_main.c:159: ac97 codec read TIMEOUT [0x6a/0x800fc06a]!!!
[22764.777876] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/trident/../../alsa-kernel/pci/trident/trident_main.c:159: ac97 codec read TIMEOUT [0x6c/0x800fc06c]!!!
[22764.805772] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/trident/../../alsa-kernel/pci/trident/trident_main.c:159: ac97 codec read TIMEOUT [0x6e/0x800fc06e]!!!
[22764.833405] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/trident/../../alsa-kernel/pci/trident/trident_main.c:159: ac97 codec read TIMEOUT [0x70/0x800fc070]!!!
[22764.865377] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/trident/../../alsa-kernel/pci/trident/trident_main.c:159: ac97 codec read TIMEOUT [0x72/0x800fc072]!!!
[22764.893665] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/trident/../../alsa-kernel/pci/trident/trident_main.c:159: ac97 codec read TIMEOUT [0x74/0x800fc074]!!!
[22764.924277] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/trident/../../alsa-kernel/pci/trident/trident_main.c:159: ac97 codec read TIMEOUT [0x76/0x800fc076]!!!
[22764.951335] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/trident/../../alsa-kernel/pci/trident/trident_main.c:159: ac97 codec read TIMEOUT [0x78/0x800fc078]!!!
[22764.982830] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/trident/../../alsa-kernel/pci/trident/trident_main.c:159: ac97 codec read TIMEOUT [0x7a/0x800fc07a]!!!
[22765.009544] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/trident/../../alsa-kernel/pci/trident/trident_main.c:159: ac97 codec read TIMEOUT [0x7c/0x800fc07c]!!!
[22765.038266] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/trident/../../alsa-kernel/pci/trident/trident_main.c:159: ac97 codec read TIMEOUT [0x7e/0x800fc07e]!!!

---

### Post by mörgæs on 2010-02-15
Perhaps this will help: 
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
I know it is an old thread, but still there is some good advice here.

Is there sound if you try a 9.04 live cd? 
[http://releases.ubuntu.com/9.04/](http://releases.ubuntu.com/9.04/)

---

