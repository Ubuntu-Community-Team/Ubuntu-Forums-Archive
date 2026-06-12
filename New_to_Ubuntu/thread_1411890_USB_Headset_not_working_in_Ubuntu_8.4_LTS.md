---
title: "USB Headset not working in Ubuntu 8.4 LTS"
date: 2010-02-20
forum: New to Ubuntu
---

### Post by vipin.balakrishnan on 2010-02-20
Hi All
 
 Please anyone help me to find out a solution for this. I'm using Logictech USB Headset . As soon as  When I connect the headset I can hear the Ubuntu Login sound in headset. But after when I try to play sound using player, I'm not able to here any sound from headset. Instead of  that, I will get sound from speakers. Please anyone help me, I'm struggling with this issue from past 3 months.


I'm attaching the complete log information of my system

```

!!################################
!!ALSA Information Script v 0.4.59
!!################################

!!Script ran on: Sat Feb 20 20:00:44 UTC 2010


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
snd_usb_audio
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
 1 [Headset        ]: USB-Audio - Logitech USB Headset
                      Logitech Logitech USB Headset at usb-0000:00:1d.0-2, full speed
 2 [SAA7134        ]: SAA7134 - SAA7134
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

!!Module: snd_usb_audio
    async_unlink : Y
    device_setup : 0,0,0,0,0,0,0,0
    enable : Y,Y,Y,Y,Y,Y,Y,Y
    id : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
    index : -2,-1,-1,-1,-1,-1,-1,-1
    nrpacks : 8
    pid : -1,-1,-1,-1,-1,-1,-1,-1
    vid : -1,-1,-1,-1,-1,-1,-1,-1

!!Module: saa7134_alsa
    debug : 0
    enable : 1,1,1,1,1,1,1,1
    index : -2,-1,-1,-1,-1,-1,-1,-1


!!ALSA Device nodes
!!-----------------

crw-rw----  1 root audio 116,  0 Feb 21 01:28 /dev/snd/controlC0
crw-rw----  1 root audio 116, 32 Feb 21 01:30 /dev/snd/controlC1
crw-rw----  1 root audio 116, 64 Feb 21 01:28 /dev/snd/controlC2
crw-rw----  1 root audio 116,  8 Feb 21 01:28 /dev/snd/midiC0D0
crw-rw----  1 root audio 116, 24 Feb 21 01:28 /dev/snd/pcmC0D0c
crw-rw----  1 root audio 116, 16 Feb 21 01:29 /dev/snd/pcmC0D0p
crw-rw----  1 root audio 116, 25 Feb 21 01:28 /dev/snd/pcmC0D1c
crw-rw----  1 root audio 116, 17 Feb 21 01:29 /dev/snd/pcmC0D1p
crw-rw----  1 root audio 116, 26 Feb 21 01:28 /dev/snd/pcmC0D2c
crw-rw----  1 root audio 116, 18 Feb 21 01:28 /dev/snd/pcmC0D2p
crw-rw----  1 root audio 116, 27 Feb 21 01:28 /dev/snd/pcmC0D3c
crw-rw----  1 root audio 116, 19 Feb 21 01:28 /dev/snd/pcmC0D3p
crw-rw----  1 root audio 116, 56 Feb 21 01:30 /dev/snd/pcmC1D0c
crw-rw----  1 root audio 116, 48 Feb 21 01:30 /dev/snd/pcmC1D0p
crw-rw----  1 root audio 116, 88 Feb 21 01:28 /dev/snd/pcmC2D0c
crw-rw----  1 root audio 116,  1 Feb 21 01:28 /dev/snd/seq
crw-rw----  1 root audio 116, 33 Feb 21 01:28 /dev/snd/timer


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
card 1: Headset [Logitech USB Headset], device 0: USB Audio [USB Audio]
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
card 1: Headset [Logitech USB Headset], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: SAA7134 [SAA7134], device 0: SAA7134 PCM [SAA7134 PCM]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [CA0106]

Card hw:0 'CA0106'/'Audigy SE [SB0570] at 0x1040 irq 19'
  Mixer name    : ''
  Components    : ''
  Controls      : 29
  Simple ctrls  : 17
Simple mixer control 'Line in',0
  Capabilities: cvolume
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 255
  Front Left: Capture 255 [100%] [24.00dB]
  Front Right: Capture 255 [100%] [24.00dB]
Simple mixer control 'Mic',0
  Capabilities: cvolume
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 255
  Front Left: Capture 255 [100%] [24.00dB]
  Front Right: Capture 255 [100%] [24.00dB]
Simple mixer control 'Phone',0
  Capabilities: cvolume
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 255
  Front Left: Capture 255 [100%] [24.00dB]
  Front Right: Capture 255 [100%] [24.00dB]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'IEC958 Center/LFE',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [12.00dB]
  Front Right: Playback 255 [100%] [12.00dB]
Simple mixer control 'IEC958 Front',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [12.00dB]
  Front Right: Playback 255 [100%] [12.00dB]
Simple mixer control 'IEC958 Rear',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [12.00dB]
  Front Right: Playback 255 [100%] [12.00dB]
Simple mixer control 'IEC958 Unknown',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [12.00dB]
  Front Right: Playback 255 [100%] [12.00dB]
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
  Front Left: Playback 255 [100%] [12.00dB] [on]
  Front Right: Playback 255 [100%] [12.00dB] [on]
Simple mixer control 'Analog Front',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [12.00dB] [on]
  Front Right: Playback 255 [100%] [12.00dB] [on]
Simple mixer control 'Analog Rear',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [12.00dB] [on]
  Front Right: Playback 255 [100%] [12.00dB] [on]
Simple mixer control 'Analog Side',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [12.00dB] [on]
  Front Right: Playback 255 [100%] [12.00dB] [on]
Simple mixer control 'Analog Source',0
  Capabilities: cenum
  Items: 'Phone' 'Mic' 'Line in' 'Aux'
  Item0: 'Line in'
Simple mixer control 'CAPTURE feedback',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [12.00dB]
  Front Right: Playback 255 [100%] [12.00dB]
Simple mixer control 'Digital Source',0
  Capabilities: cenum
  Items: 'IEC958 out' 'i2s mixer out' 'IEC958 in' 'i2s in' 'AC97 in' 'SRC out'
  Item0: 'i2s in'
Simple mixer control 'Shared Mic/Line in',0
  Capabilities: cenum
  Items: 'Line in' 'Mic in'
  Item0: 'Line in'

!!-------Mixer controls for card 1 [Headset]

Card hw:1 'Headset'/'Logitech Logitech USB Headset at usb-0000:00:1d.0-2, full speed'
  Mixer name    : 'USB Mixer'
  Components    : 'USB046d:0a14'
  Controls      : 4
  Simple ctrls  : 2
Simple mixer control 'PCM',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 30
  Mono:
  Front Left: Playback 0 [0%] [-30.00dB] [on]
  Front Right: Playback 0 [0%] [-30.00dB] [on]
Simple mixer control 'Mic',0
  Capabilities: cvolume cswitch cswitch-joined
  Capture channels: Mono
  Limits: Capture 0 - 40
  Mono: Capture 0 [0%] [0.00dB] [off]

!!-------Mixer controls for card 2 [SAA7134]

Card hw:2 'SAA7134'/'saa7134[0] at 0xe3001000 irq 22'
  Mixer name    : 'SAA7134 Mixer'
  Components    : ''
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
        value.0 255
        value.1 255
    }
    control.2 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 255'
        iface MIXER
        name 'Analog Rear Playback Volume'
        value.0 255
        value.1 255
    }
    control.3 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 255'
        iface MIXER
        name 'Analog Center/LFE Playback Volume'
        value.0 255
        value.1 255
    }
    control.4 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 255'
        iface MIXER
        name 'Analog Side Playback Volume'
        value.0 255
        value.1 255
    }
    control.5 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 255'
        iface MIXER
        name 'IEC958 Front Playback Volume'
        value.0 255
        value.1 255
    }
    control.6 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 255'
        iface MIXER
        name 'IEC958 Rear Playback Volume'
        value.0 255
        value.1 255
    }
    control.7 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 255'
        iface MIXER
        name 'IEC958 Center/LFE Playback Volume'
        value.0 255
        value.1 255
    }
    control.8 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 255'
        iface MIXER
        name 'IEC958 Unknown Playback Volume'
        value.0 255
        value.1 255
    }
    control.9 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 255'
        iface MIXER
        name 'CAPTURE feedback Playback Volume'
        value.0 255
        value.1 255
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
        value.0 255
        value.1 255
    }
    control.22 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 255'
        iface MIXER
        name 'Mic Capture Volume'
        value.0 255
        value.1 255
    }
    control.23 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 255'
        iface MIXER
        name 'Line in Capture Volume'
        value.0 255
        value.1 255
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
state.Headset {
    control.1 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'PCM Playback Switch'
        value true
    }
    control.2 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 30'
        iface MIXER
        name 'PCM Playback Volume'
        value.0 0
        value.1 0
    }
    control.3 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Mic Capture Switch'
        value false
    }
    control.4 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 1
        comment.range '0 - 40'
        iface MIXER
        name 'Mic Capture Volume'
        value 0
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
usbhid
snd_seq_dummy
hid
saa7134_alsa
nvidia
snd_pcm_oss
snd_usb_audio
snd_mixer_oss
snd_usb_lib
snd_seq_oss
snd_hwdep
snd_seq_midi
snd_pcm
snd_rawmidi
snd_seq_midi_event
tuner
tea5767
tda8290
tuner_simple
mt20xx
tea5761
snd_seq
snd_timer
snd_seq_device
saa7134
snd
compat_ioctl32
videobuf_dma_sg
videobuf_core
ir_kbd_i2c
soundcore
i2c_core
ac97_bus
ir_common
serio_raw
videodev
snd_page_alloc
v4l2_common
v4l1_compat
psmouse
button
evdev
parport_pc
intel_agp
parport
agpgart
iTCO_wdt
iTCO_vendor_support
shpchp
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
libata
scsi_mod
e100
mii
ehci_hcd
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

[   34.788415] usbcore: registered new interface driver snd-usb-audio
[   35.018105] saa7134 ALSA driver for DMA sound loaded
[   35.018143] saa7134[0]/alsa: saa7134[0] at 0xe3001000 irq 22 registered as card -2




```

---

### Post by kostkon on 2010-02-20
First of all, you need to better setup your 8.04 (because it's old already) in order to use PulseAudio more effectively (i.e. with all your apps) and then install the *PulseAudio Device Chooser* utility that will allow you to send any sound from your apps to your headset. Additionally, you will be able to set your headset as the default audio device in your system and do some other additional things.

The guide can be found [here]("http://ubuntuforums.org/showthread.php?t=789578").

---

### Post by mcduck on 2010-02-20
Since it's conencted through USB the headeset is actually a soundcard of it's own. Have you tried setting the sound output to that soundcard in those applications you wish to use the headset?

---

### Post by egalvan on 2010-02-20
> **VlaamsBelang said:**
> A year or so ago I got mine working by switching to ALSA instead of PulseAudio (in system-> xxx -> sound).
...
And it worked.

Sounds easy, will have to try it.
I have a Plantronics USB Headset.

---

### Post by vipin.balakrishnan on 2010-02-20
Hi ,

 How can I do that. Can You Please tell me.

---

