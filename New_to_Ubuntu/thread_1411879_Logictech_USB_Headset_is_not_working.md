---
title: "Logictech USB Headset is not working"
date: 2010-02-20
forum: New to Ubuntu
---

### Post by vipin.balakrishnan on 2010-02-20
Hi all,

   I'm not able to here any sound from my logictech USB Headset. Can anybody help me on this issue.

I'm struggling because of this issue from past 4 months. Please anyone help me. This is my syste, log information

```


!!################################
!!ALSA Information Script v 0.4.59
!!################################

!!Script ran on: Sat Feb 20 19:40:50 UTC 2010


!!Linux Distribution
!!------------------

Ubuntu 8.04.4 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 8.04.4 LTS"


!!DMI Information
!!---------------

Manufacturer:                                      
Product Name:                                      


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

snd_ca0106
saa7134_alsa


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

 0 [CA0106         ]: CA0106 - CA0106
                      Audigy SE [SB0570] at 0x1040 irq 19
 1 [SAA7134        ]: SAA7134 - SAA7134
                      saa7134[0] at 0xe3001000 irq 22


!!PCI Soundcards installed in the system
!!--------------------------------------

05:01.0 Multimedia controller: Philips Semiconductors SAA7134/SAA7135HL Video Broadcast Decoder (rev 01)
05:03.0 Multimedia audio controller: Creative Labs SB Audigy LS


!!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------

01:00.0 0300: 10de:0402 (rev a1) (prog-if 00 [VGA controller])
	Subsystem: 1682:2286
--
05:03.0 0401: 1102:0007
	Subsystem: 1102:100a


!!Modprobe options (Sound related)
!!--------------------------------

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-usx2y: index=-2
snd-usb-caiaq: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-usx2y: index=-2
snd-usb-caiaq: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388


!!Loaded sound module options
!!--------------------------

!!Module: snd_ca0106
	enable : Y,Y,Y,Y,Y,Y,Y,Y
	id : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
	index : -1,-1,-1,-1,-1,-1,-1,-1
	subsystem : 0,0,0,0,0,0,0,0

!!Module: saa7134_alsa
	debug : 0
	enable : 1,1,1,1,1,1,1,1
	index : -2,-1,-1,-1,-1,-1,-1,-1


!!ALSA Device nodes
!!-----------------

crw-rw----  1 root audio 116,  0 Feb 21 00:48 /dev/snd/controlC0
crw-rw----  1 root audio 116, 32 Feb 21 00:48 /dev/snd/controlC1
crw-rw----  1 root audio 116,  8 Feb 21 00:48 /dev/snd/midiC0D0
crw-rw----  1 root audio 116, 24 Feb 21 00:48 /dev/snd/pcmC0D0c
crw-rw----  1 root audio 116, 16 Feb 21 00:49 /dev/snd/pcmC0D0p
crw-rw----  1 root audio 116, 25 Feb 21 00:48 /dev/snd/pcmC0D1c
crw-rw----  1 root audio 116, 17 Feb 21 00:49 /dev/snd/pcmC0D1p
crw-rw----  1 root audio 116, 26 Feb 21 00:48 /dev/snd/pcmC0D2c
crw-rw----  1 root audio 116, 18 Feb 21 00:48 /dev/snd/pcmC0D2p
crw-rw----  1 root audio 116, 27 Feb 21 00:48 /dev/snd/pcmC0D3c
crw-rw----  1 root audio 116, 19 Feb 21 00:48 /dev/snd/pcmC0D3p
crw-rw----  1 root audio 116, 56 Feb 21 00:48 /dev/snd/pcmC1D0c
crw-rw----  1 root audio 116,  1 Feb 21 00:48 /dev/snd/seq
crw-rw----  1 root audio 116, 33 Feb 21 00:48 /dev/snd/timer


!!ALSA configuration files
!!------------------------

!!User specific config file (~/.asoundrc)

# ALSA library configuration file

# Include settings that are under the control of asoundconf(1).
# (To disable these settings, comment out this line.)
</home/vipinb/.asoundrc.asoundconf>

pcm.s5 {
    type route
    slave.pcm surround40
    slave.channels 4
    ttable.0.0 1
    ttable.1.1 1
    ttable.2.2 1
    ttable.3.3 1
}

pcm.!default {
  type                  plug
  slave.pcm            s5
}




!!asoundconf-generated config file

# ALSA library configuration file managed by asoundconf(1).
#
# MANUAL CHANGES TO THIS FILE WILL BE OVERWRITTEN!
#
# Manual changes to the ALSA library configuration should be implemented
# by editing the ~/.asoundrc file, not by editing this file.
!defaults.pcm.card Headset
defaults.ctl.card Headset
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


!!System wide config file (/etc/asound.conf)

pcm.card0 {
  type hw
  card 0
# mmap_emulation true
}

#pcm.dmix0 {
#  type dmix 
#  ipc_key 34521 
#  slave {
#    pcm "card0" 
#  }
#}

pcm.dmix0 {
        type dmix
        ipc_key 1024 ## needs to be a power of 2
        slave {
                pcm "hw:0"
                period_time 0
                period_size 1024
                buffer_size 8192
              # format S16_LE
                rate 44100 ## not necessary
        }
#slowptr true
}

pcm.dsnoop0 {
  type dsnoop 
  ipc_key 2048
  slave {
    pcm "card0" 
  #  rate 48000
  }
}

pcm.asym0 {
  type asym 
  playback.pcm "dmix0" 
  capture.pcm "dsnoop0"
}

pcm.pasym0 {
  type plug 
  slave.pcm "asym0"
}

# 'dsp0' is expected by OSS emulation etc.
pcm.dsp0 {
  type                  plug
  slave.pcm            "asym0"
}

ctl.dsp0 {
    type                hw
    card                0
}

pcm.!default {
  type                  plug
  slave.pcm            "asym0"
}

ctl.!default {
    type                hw
    card                0
}


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: SAA7134 [SAA7134], device 0: SAA7134 PCM [SAA7134 PCM]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [CA0106]

Card hw:0 'CA0106'/'Audigy SE [SB0570] at 0x1040 irq 19'
  Mixer name	: ''
  Components	: ''
  Controls      : 29
  Simple ctrls  : 17
Simple mixer control 'Line in',0
  Capabilities: cvolume
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 255
  Front Left: Capture 145 [57%] [-31.00dB]
  Front Right: Capture 145 [57%] [-31.00dB]
Simple mixer control 'Mic',0
  Capabilities: cvolume
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 255
  Front Left: Capture 145 [57%] [-31.00dB]
  Front Right: Capture 145 [57%] [-31.00dB]
Simple mixer control 'Phone',0
  Capabilities: cvolume
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 255
  Front Left: Capture 145 [57%] [-31.00dB]
  Front Right: Capture 145 [57%] [-31.00dB]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'IEC958 Center/LFE',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 145 [57%] [-15.50dB]
  Front Right: Playback 145 [57%] [-15.50dB]
Simple mixer control 'IEC958 Front',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 145 [57%] [-15.50dB]
  Front Right: Playback 145 [57%] [-15.50dB]
Simple mixer control 'IEC958 Rear',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 145 [57%] [-15.50dB]
  Front Right: Playback 145 [57%] [-15.50dB]
Simple mixer control 'IEC958 Unknown',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 145 [57%] [-15.50dB]
  Front Right: Playback 145 [57%] [-15.50dB]
Simple mixer control 'Aux',0
  Capabilities: cvolume
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 255
  Front Left: Capture 0 [0%] [-99999.99dB]
  Front Right: Capture 0 [0%] [-99999.99dB]
Simple mixer control 'Analog Center/LFE',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 145 [57%] [-15.50dB] [on]
  Front Right: Playback 145 [57%] [-15.50dB] [on]
Simple mixer control 'Analog Front',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 145 [57%] [-15.50dB] [on]
  Front Right: Playback 145 [57%] [-15.50dB] [on]
Simple mixer control 'Analog Rear',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 145 [57%] [-15.50dB] [on]
  Front Right: Playback 145 [57%] [-15.50dB] [on]
Simple mixer control 'Analog Side',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 145 [57%] [-15.50dB] [on]
  Front Right: Playback 145 [57%] [-15.50dB] [on]
Simple mixer control 'Analog Source',0
  Capabilities: cenum
  Items: 'Phone' 'Mic' 'Line in' 'Aux'
  Item0: 'Line in'
Simple mixer control 'CAPTURE feedback',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 145 [57%] [-15.50dB]
  Front Right: Playback 145 [57%] [-15.50dB]
Simple mixer control 'Digital Source',0
  Capabilities: cenum
  Items: 'IEC958 out' 'i2s mixer out' 'IEC958 in' 'i2s in' 'AC97 in' 'SRC out'
  Item0: 'i2s in'
Simple mixer control 'Shared Mic/Line in',0
  Capabilities: cenum
  Items: 'Line in' 'Mic in'
  Item0: 'Line in'

!!-------Mixer controls for card 1 [SAA7134]

Card hw:1 'SAA7134'/'saa7134[0] at 0xe3001000 irq 22'
  Mixer name	: 'SAA7134 Mixer'
  Components	: ''
  Controls      : 6
  Simple ctrls  : 3
Simple mixer control 'Line',1
  Capabilities: volume cswitch
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 20
  Front Left: 0 [0%] Capture [on]
  Front Right: 0 [0%] Capture [on]
Simple mixer control 'Line',2
  Capabilities: volume cswitch
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 20
  Front Left: 0 [0%] Capture [on]
  Front Right: 0 [0%] Capture [on]
Simple mixer control 'Video',0
  Capabilities: volume cswitch
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 20
  Front Left: 20 [100%] Capture [on]
  Front Right: 20 [100%] Capture [on]


!!Alsactl output
!!-------------

--startcollapse--
state.CA0106 {
	control.1 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 255'
		iface MIXER
		name 'Analog Front Playback Volume'
		value.0 145
		value.1 145
	}
	control.2 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 255'
		iface MIXER
		name 'Analog Rear Playback Volume'
		value.0 145
		value.1 145
	}
	control.3 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 255'
		iface MIXER
		name 'Analog Center/LFE Playback Volume'
		value.0 145
		value.1 145
	}
	control.4 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 255'
		iface MIXER
		name 'Analog Side Playback Volume'
		value.0 145
		value.1 145
	}
	control.5 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 255'
		iface MIXER
		name 'IEC958 Front Playback Volume'
		value.0 145
		value.1 145
	}
	control.6 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 255'
		iface MIXER
		name 'IEC958 Rear Playback Volume'
		value.0 145
		value.1 145
	}
	control.7 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 255'
		iface MIXER
		name 'IEC958 Center/LFE Playback Volume'
		value.0 145
		value.1 145
	}
	control.8 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 255'
		iface MIXER
		name 'IEC958 Unknown Playback Volume'
		value.0 145
		value.1 145
	}
	control.9 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 255'
		iface MIXER
		name 'CAPTURE feedback Playback Volume'
		value.0 145
		value.1 145
	}
	control.10 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface PCM
		name 'IEC958 Playback Mask'
		value ffffffff00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
	}
	control.11 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface PCM
		name 'IEC958 Playback Mask'
		index 1
		value ffffffff00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
	}
	control.12 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface PCM
		name 'IEC958 Playback Mask'
		index 2
		value ffffffff00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
	}
	control.13 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface PCM
		name 'IEC958 Playback Mask'
		index 3
		value ffffffff00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
	}
	control.14 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Switch'
		value false
	}
	control.15 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 'IEC958 out'
		comment.item.1 'i2s mixer out'
		comment.item.2 'IEC958 in'
		comment.item.3 'i2s in'
		comment.item.4 'AC97 in'
		comment.item.5 'SRC out'
		iface MIXER
		name 'Digital Source Capture Enum'
		value 'i2s in'
	}
	control.16 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 Phone
		comment.item.1 Mic
		comment.item.2 'Line in'
		comment.item.3 Aux
		iface MIXER
		name 'Analog Source Capture Enum'
		value 'Line in'
	}
	control.17 {
		comment.access 'read write'
		comment.type IEC958
		comment.count 1
		iface PCM
		name 'IEC958 Playback Default'
		value '0492100200000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.18 {
		comment.access 'read write'
		comment.type IEC958
		comment.count 1
		iface PCM
		name 'IEC958 Playback Default'
		index 1
		value '0492100200000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.19 {
		comment.access 'read write'
		comment.type IEC958
		comment.count 1
		iface PCM
		name 'IEC958 Playback Default'
		index 2
		value '0492100200000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.20 {
		comment.access 'read write'
		comment.type IEC958
		comment.count 1
		iface PCM
		name 'IEC958 Playback Default'
		index 3
		value '0492100200000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.21 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 255'
		iface MIXER
		name 'Phone Capture Volume'
		value.0 145
		value.1 145
	}
	control.22 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 255'
		iface MIXER
		name 'Mic Capture Volume'
		value.0 145
		value.1 145
	}
	control.23 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 255'
		iface MIXER
		name 'Line in Capture Volume'
		value.0 145
		value.1 145
	}
	control.24 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 255'
		iface MIXER
		name 'Aux Capture Volume'
		value.0 0
		value.1 0
	}
	control.25 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 'Line in'
		comment.item.1 'Mic in'
		iface MIXER
		name 'Shared Mic/Line in Capture Switch'
		value 'Line in'
	}
	control.26 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Analog Front Playback Switch'
		value true
	}
	control.27 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Analog Rear Playback Switch'
		value true
	}
	control.28 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Analog Center/LFE Playback Switch'
		value true
	}
	control.29 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Analog Side Playback Switch'
		value true
	}
}
state.SAA7134 {
	control.1 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 20'
		iface MIXER
		name 'Video Volume'
		value.0 20
		value.1 20
	}
	control.2 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Video Capture Switch'
		value.0 true
		value.1 true
	}
	control.3 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 20'
		iface MIXER
		name 'Line Volume'
		index 1
		value.0 0
		value.1 0
	}
	control.4 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Line Capture Switch'
		index 1
		value.0 true
		value.1 true
	}
	control.5 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 20'
		iface MIXER
		name 'Line Volume'
		index 2
		value.0 0
		value.1 0
	}
	control.6 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Line Capture Switch'
		index 2
		value.0 true
		value.1 true
	}
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
binfmt_misc
af_packet
rfcomm
l2cap
bluetooth
vboxnetadp
vboxnetflt
vboxdrv
ppdev
ipv6
acpi_cpufreq
cpufreq_ondemand
cpufreq_stats
freq_table
cpufreq_conservative
cpufreq_userspace
cpufreq_powersave
dock
container
sbs
sbshc
video
output
battery
iptable_filter
ip_tables
x_tables
ac
lm85
hwmon_vid
i2c_i801
lp
snd_ca0106
snd_ac97_codec
snd_seq_dummy
snd_usb_audio
saa7134_alsa
snd_pcm_oss
snd_mixer_oss
snd_pcm
snd_seq_oss
snd_usb_lib
snd_seq_midi
usbhid
hid
snd_rawmidi
snd_seq_midi_event
snd_hwdep
tuner
tea5767
tda8290
tuner_simple
mt20xx
tea5761
snd_seq
snd_timer
snd_seq_device
nvidia
snd
saa7134
soundcore
compat_ioctl32
videobuf_dma_sg
videobuf_core
ir_kbd_i2c
ac97_bus
i2c_core
serio_raw
ir_common
videodev
snd_page_alloc
button
psmouse
v4l2_common
v4l1_compat
intel_agp
iTCO_wdt
iTCO_vendor_support
shpchp
evdev
parport_pc
parport
agpgart
pci_hotplug
pcspkr
ext3
jbd
mbcache
sg
sr_mod
cdrom
sd_mod
ata_generic
ata_piix
pata_acpi
ehci_hcd
e100
mii
libata
scsi_mod
uhci_hcd
usbcore
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

[   40.878253] NVRM: loading NVIDIA UNIX x86 Kernel Module  169.12  Thu Feb 14 17:53:07 PST 2008
[   40.979691] saa7134 ALSA driver for DMA sound loaded
[   40.979727] saa7134[0]/alsa: saa7134[0] at 0xe3001000 irq 22 registered as card -2





```

---

### Post by cariboo on 2010-02-20
The first thing to check is if your headset is detected when you plug it in. Check the output of dmesg just after you plug the device in. THis is what I get:

```
[20665.050047] usb 2-3: new full speed USB device using ohci_hcd and address 6
[20665.268196] usb 2-3: configuration #1 chosen from 1 choice
[20665.502167] input: HID 0d8c:000c as /devices/pci0000:00/0000:00:02.0/usb2/2-3/2-3:1.3/input/input7
[20665.502250] generic-usb 0003:0D8C:000C.0005: input,hidraw4: USB HID v1.00 Device [HID 0d8c:000c] on usb-0000:00:02.0-3/input3
```

Once you are sure the device is detected, right click on the speaker icon in the top panel and select preferences, you should see you device when you click the hardware tab. From there it should be just a matter of enabling it on the output tab.

---

