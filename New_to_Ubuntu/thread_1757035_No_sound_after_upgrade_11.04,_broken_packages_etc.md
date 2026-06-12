---
title: "No sound after upgrade 11.04, broken packages etc"
date: 2011-05-13
forum: New to Ubuntu
---

### Post by DayLite on 2011-05-13
Ok, I really made a mistake and need help. I thought I would upgrade 10.10 on my laptop. It is a Dell Latitude D600. I have 2 partitions, Windows XP Professional and now, Ubuntu 11.04.

The install didn't show any 'red flags', and so I thought :(. 

I have **no sound**, and I keep on getting , '**fix broken packages**'. Pulse audio cannot be installed, neither OpenShot, which was removed during upgrade.

How do I just write over 11.04 with a 'fresh install' keeping my XP. I have no disk space to install alongside, like the choice in the Live CD. I don't want to format because it will remove Windows XP.

Can you troubleshoot for me?  Tell me what to write in the terminal to tell you what is going on.

---

### Post by wildmanne39 on 2011-05-13
> **DayLite said:**
> Ok, I really made a mistake and need help. I thought I would upgrade 10.10 on my laptop. It is a Dell Latitude D600. I have 2 partitions, Windows XP Professional and now, Ubuntu 11.04.

The install didn't show any 'red flags', and so I thought :(. 

I have **no sound**, and I keep on getting , '**fix broken packages**'. Pulse audio cannot be installed, neither OpenShot, which was removed during upgrade.

How do I just write over 11.04 with a 'fresh install' keeping my XP. I have no disk space to install alongside, like the choice in the Live CD. I don't want to format because it will remove Windows XP.

Can you troubleshoot for me?  Tell me what to write in the terminal to tell you what is going on.

Hi, first you might try to fix the broken packages one way is to go into synaptic package manager and in the drop down menu there is a tab that says fix broken packages. Also the natty live cd has an option to let you reinstall over the exiting operating system, however I do not recommend it, It would be better to do a fresh install from the live cd if you are determined to reinstall and it will let you reinstall with out messing up your windows partition as long as you are careful. I hope this helps.:)

---

### Post by DayLite on 2011-05-13
> **wildmanne39 said:**
> Hi, first you might try to fix the broken packages one way is to go into synaptic package manager and in the drop down menu there is a tab that says fix broken packages. Also the natty live cd has an option to let you reinstall over the exiting operating system, however I do not recommend it, It would be better to do a fresh install from the live cd if you are determined to reinstall and it will let you reinstall with out messing up your windows partition as long as you are careful. I hope this helps.:)

Thank you for responding. I already went to the synaptic package manager, and it was blank when I asked it to fix broken packages, none were listed. 

I did get my sound back. My laptop has a deck and I moved the external speakers from the decks microphone plug, directly to my computer microphone plug.

I did first follow the steps in [SoundTroubleshootingProcedure]("https://help.ubuntu.com/community/SoundTroubleshootingProcedure").

[CODE   	 	 	 	 	 	  joan@joan-laptop:~$ wget -O alsa-info.sh http://www.alsa-project.org/alsa-info.sh  
 

 --2011-05-12 22:14:19--  http://www.alsa-project.org/alsa-info.sh
 

 Resolving www.alsa-project.org... 77.48.224.243
 

 Connecting to www.alsa-project.org|77.48.224.243|:80... connected.
 

 HTTP request sent, awaiting response... 302 Found
 

 Location: http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh [following]
 

 --2011-05-12 22:14:22--  http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh
 

 Resolving git.alsa-project.org... 77.48.224.243
 

 Reusing existing connection to www.alsa-project.org:80.
 

 HTTP request sent, awaiting response... 200 OK
 

 Length: unspecified [text/plain]
 

 Saving to: `alsa-info.sh'
 

 

 

     [   <=>                                 ] 27,247      57.8K/s   in 0.5s     
 

 

 

 2011-05-12 22:14:24 (57.8 KB/s) - `alsa-info.sh' saved [27247]
 

 

 

 joan@joan-laptop:~$ bash alsa-info.sh --stdout  
 

 upload=true&script=true&cardinfo=
 

 !!################################
 

 !!ALSA Information Script v 0.4.60
 

 !!################################
 

 

 

 !!Script ran on: Fri May 13 05:14:44 UTC 2011
 

 

 

 

 

 !!Linux Distribution
 

 !!------------------
 

 

 

 Ubuntu 11.04 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 11.04"
 

 

 

 

 

 !!DMI Information
 

 !!---------------
 

 

 

 Manufacturer:      Dell Computer Corporation
 

 Product Name:      Latitude D600                    
 

 Product Version:    
 

 

 

 

 

 !!Kernel Information
 

 !!------------------
 

 

 

 Kernel release:    2.6.38-8-generic
 

 Operating System:  GNU/Linux
 

 Architecture:      i686
 

 Processor:         i686
 

 SMP Enabled:       Yes
 

 

 

 

 

 !!ALSA Version
 

 !!------------
 

 

 

 Driver version:     1.0.23
 

 Library version:    1.0.23
 

 Utilities version:  1.0.23
 

 

 

 

 

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
 

 

 

 

 

 !!Soundcards recognised by ALSA
 

 !!-----------------------------
 

 

 

  0 [I82801DBICH4   ]: ICH4 - Intel 82801DB-ICH4
 

                       Intel 82801DB-ICH4 with STAC9750,51 at irq 5
 

 

 

 

 

 !!PCI Soundcards installed in the system
 

 !!--------------------------------------
 

 

 

 00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
 

 

 

 

 

 !!Advanced information - PCI Vendor/Device/Subsystem ID's
 

 !!--------------------------------------------------------
 

 

 

 00:1f.5 0401: 8086:24c5 (rev 01)
 

 	Subsystem: 1028:011d
 

 

 

 

 

 !!Modprobe options (Sound related)
 

 !!--------------------------------
 

 

 

 snd-atiixp-modem: index=-2
 

 snd-intel8x0m: index=-2
 

 snd-via82xx-modem: index=-2
 

 snd-usb-audio: index=-2
 

 snd-usb-caiaq: index=-2
 

 snd-usb-ua101: index=-2
 

 snd-usb-us122l: index=-2
 

 snd-usb-usx2y: index=-2
 

 snd-cmipci: mpu_port=0x330 fm_port=0x388
 

 snd-pcsp: index=-2
 

 snd-usb-audio: index=-2
 

 

 

 

 

 !!Loaded sound module options
 

 !!--------------------------
 

 

 

 !!Module: snd_intel8x0
 

 	ac97_clock : 0
 

 	ac97_quirk : (null)
 

 	buggy_irq : N
 

 	buggy_semaphore : N
 

 	enable : N
 

 	id : (null)
 

 	index : -1
 

 	joystick : 0
 

 	spdif_aclink : 0
 

 	xbox : N
 

 

 

 

 

 !!AC97 Codec information
 

 !!---------------------------
 

 --startcollapse--
 

 

 

 0-0/0: SigmaTel STAC9750,51
 

 

 

 PCI Subsys Vendor: 0x1028
 

 PCI Subsys Device: 0x011d
 

 

 

 Flags: 0
 

 Capabilities     : -headphone out-
 

 DAC resolution   : 20-bit
 

 ADC resolution   : 20-bit
 

 3D enhancement   : SigmaTel 3D Enhancement
 

 

 

 Current setup
 

 Mic gain         : +0dB [+0dB]
 

 POP path         : pre 3D
 

 Sim. stereo      : off
 

 3D enhancement   : off
 

 Loudness         : off
 

 Mono output      : MIX
 

 Mic select       : Mic1
 

 ADC/DAC loopback : off
 

 Extended ID      : codec=0 rev=1 AMAP DSA=0 SPDIF VRA
 

 Extended status  : SPCV SPDIF=10/11 SPDIF VRA
 

 PCM front DAC    : 44100Hz
 

 PCM ADC          : 44100Hz
 

 SPDIF Control    : Consumer PCM Copyright Category=0x2 Generation=1 Rate=48kHz
 

 

 

 0:00 = 6a90
 

 0:02 = 0000
 

 0:04 = 0000
 

 0:06 = 801f
 

 0:08 = 0000
 

 0:0a = 801e
 

 0:0c = 801f
 

 0:0e = 801f
 

 0:10 = 9f1f
 

 0:12 = 0606
 

 0:14 = 9f1f
 

 0:16 = 9f1f
 

 0:18 = 0000
 

 0:1a = 0000
 

 0:1c = 0f0f
 

 0:1e = 0000
 

 0:20 = 0000
 

 0:22 = 0000
 

 0:24 = 0000
 

 0:26 = 000f
 

 0:28 = 0605
 

 0:2a = 0435
 

 0:2c = ac44
 

 0:2e = 0000
 

 0:30 = 0000
 

 0:32 = ac44
 

 0:34 = 0000
 

 0:36 = 0000
 

 0:38 = 0000
 

 0:3a = 2820
 

 0:3c = 0000
 

 0:3e = 0100
 

 0:40 = 0000
 

 0:42 = 0000
 

 0:44 = 0000
 

 0:46 = 0000
 

 0:48 = 0000
 

 0:4a = 0000
 

 0:4c = 0003
 

 0:4e = ffff
 

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
 

 0:6c = 0002
 

 0:6e = 1000
 

 0:70 = 0000
 

 0:72 = 0000
 

 0:74 = 0800
 

 0:76 = 0000
 

 0:78 = 0000
 

 0:7a = 0000
 

 0:7c = 8384
 

 0:7e = 7650
 

 --endcollapse--
 

 

 

 

 

 !!ALSA Device nodes
 

 !!-----------------
 

 

 

 crw-rw----+ 1 root audio 116,  8 May 12 22:11 /dev/snd/controlC0
 

 crw-rw----+ 1 root audio 116,  7 May 12 22:11 /dev/snd/pcmC0D0c
 

 crw-rw----+ 1 root audio 116,  6 May 12 22:11 /dev/snd/pcmC0D0p
 

 crw-rw----+ 1 root audio 116,  5 May 12 22:11 /dev/snd/pcmC0D1c
 

 crw-rw----+ 1 root audio 116,  4 May 12 22:11 /dev/snd/pcmC0D2c
 

 crw-rw----+ 1 root audio 116,  3 May 12 22:11 /dev/snd/pcmC0D3c
 

 crw-rw----+ 1 root audio 116,  2 May 12 22:11 /dev/snd/pcmC0D4p
 

 crw-rw----+ 1 root audio 116,  1 May 12 22:11 /dev/snd/seq
 

 crw-rw----+ 1 root audio 116, 33 May 12 22:11 /dev/snd/timer
 

 

 

 /dev/snd/by-path:
 

 total 0
 

 drwxr-xr-x 2 root root  60 May 12 22:11 .
 

 drwxr-xr-x 3 root root 240 May 12 22:11 ..
 

 lrwxrwxrwx 1 root root  12 May 12 22:11 pci-0000:00:1f.5 -> ../controlC0
 

 

 

 

 

 !!Aplay/Arecord output
 

 !!------------
 

 

 

 APLAY
 

 

 

 **** List of PLAYBACK Hardware Devices ****
 

 card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
 

   Subdevices: 1/1
 

   Subdevice #0: subdevice #0
 

 card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
 

   Subdevices: 1/1
 

   Subdevice #0: subdevice #0
 

 

 

 ARECORD
 

 

 

 **** List of CAPTURE Hardware Devices ****
 

 card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
 

   Subdevices: 1/1
 

   Subdevice #0: subdevice #0
 

 card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 1: Intel ICH - MIC ADC [Intel 82801DB-ICH4 - MIC ADC]
 

   Subdevices: 1/1
 

   Subdevice #0: subdevice #0
 

 card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 2: Intel ICH - MIC2 ADC [Intel 82801DB-ICH4 - MIC2 ADC]
 

   Subdevices: 1/1
 

   Subdevice #0: subdevice #0
 

 card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 3: Intel ICH - ADC2 [Intel 82801DB-ICH4 - ADC2]
 

   Subdevices: 1/1
 

   Subdevice #0: subdevice #0
 

 

 

 !!Amixer output
 

 !!-------------
 

 

 

 !!-------Mixer controls for card 0 [I82801DBICH4]
 

 

 

 Card hw:0 'I82801DBICH4'/'Intel 82801DB-ICH4 with STAC9750,51 at irq 5'
 

   Mixer name	: 'SigmaTel STAC9750,51'
 

   Components	: 'AC97a:83847650'
 

   Controls      : 38
 

   Simple ctrls  : 24
 

 Simple mixer control 'Master',0
 

   Capabilities: pvolume pswitch pswitch-joined penum
 

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
 

 Simple mixer control 'Headphone',0
 

   Capabilities: pvolume pswitch pswitch-joined penum
 

   Playback channels: Front Left - Front Right
 

   Limits: Playback 0 - 31
 

   Mono:
 

   Front Left: Playback 31 [100%] [0.00dB] [on]
 

   Front Right: Playback 31 [100%] [0.00dB] [on]
 

 Simple mixer control '3D Control - Center',0
 

   Capabilities: volume volume-joined penum
 

   Playback channels: Mono
 

   Capture channels: Mono
 

   Limits: 0 - 15
 

   Mono: 0 [0%]
 

 Simple mixer control '3D Control - Depth',0
 

   Capabilities: volume volume-joined penum
 

   Playback channels: Mono
 

   Capture channels: Mono
 

   Limits: 0 - 15
 

   Mono: 0 [0%]
 

 Simple mixer control '3D Control - Switch',0
 

   Capabilities: pswitch pswitch-joined penum
 

   Playback channels: Mono
 

   Mono: Playback [off]
 

 Simple mixer control 'PCM',0
 

   Capabilities: pvolume pswitch pswitch-joined penum
 

   Playback channels: Front Left - Front Right
 

   Limits: Playback 0 - 31
 

   Mono:
 

   Front Left: Playback 31 [100%] [12.00dB] [on]
 

   Front Right: Playback 31 [100%] [12.00dB] [on]
 

 Simple mixer control 'PCM Out Path & Mute',0
 

   Capabilities: enum
 

   Items: 'pre 3D' 'post 3D'
 

   Item0: 'pre 3D'
 

 Simple mixer control 'Line',0
 

   Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive penum
 

   Capture exclusive group: 0
 

   Playback channels: Front Left - Front Right
 

   Capture channels: Front Left - Front Right
 

   Limits: Playback 0 - 31
 

   Front Left: Playback 0 [0%] [-34.50dB] [off] Capture [off]
 

   Front Right: Playback 0 [0%] [-34.50dB] [off] Capture [off]
 

 Simple mixer control 'CD',0
 

   Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive penum
 

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
 

   Mono: Playback 0 [0%] [-34.50dB] [off]
 

   Front Left: Capture [on]
 

   Front Right: Capture [on]
 

 Simple mixer control 'Mic Boost (+20dB)',0
 

   Capabilities: pswitch pswitch-joined penum
 

   Playback channels: Mono
 

   Mono: Playback [off]
 

 Simple mixer control 'Mic Select',0
 

   Capabilities: enum
 

   Items: 'Mic1' 'Mic2'
 

   Item0: 'Mic1'
 

 Simple mixer control 'Video',0
 

   Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive penum
 

   Capture exclusive group: 0
 

   Playback channels: Front Left - Front Right
 

   Capture channels: Front Left - Front Right
 

   Limits: Playback 0 - 31
 

   Front Left: Playback 0 [0%] [-34.50dB] [off] Capture [off]
 

   Front Right: Playback 0 [0%] [-34.50dB] [off] Capture [off]
 

 Simple mixer control 'Phone',0
 

   Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-exclusive penum
 

   Capture exclusive group: 0
 

   Playback channels: Mono
 

   Capture channels: Front Left - Front Right
 

   Limits: Playback 0 - 31
 

   Mono: Playback 0 [0%] [-34.50dB] [off]
 

   Front Left: Capture [off]
 

   Front Right: Capture [off]
 

 Simple mixer control 'IEC958',0
 

   Capabilities: pswitch pswitch-joined penum
 

   Playback channels: Mono
 

   Mono: Playback [on]
 

 Simple mixer control 'IEC958 Playback AC97-SPSA',0
 

   Capabilities: volume volume-joined penum
 

   Playback channels: Mono
 

   Capture channels: Mono
 

   Limits: 0 - 3
 

   Mono: 3 [100%]
 

 Simple mixer control 'Beep',0
 

   Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
 

   Playback channels: Mono
 

   Limits: Playback 0 - 15
 

   Mono: Playback 0 [0%] [-45.00dB] [off]
 

 Simple mixer control 'Aux',0
 

   Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive penum
 

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
 

   Capabilities: cvolume cswitch cswitch-joined penum
 

   Capture channels: Front Left - Front Right
 

   Limits: Capture 0 - 15
 

   Front Left: Capture 15 [100%] [22.50dB] [on]
 

   Front Right: Capture 15 [100%] [22.50dB] [on]
 

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
 

 Simple mixer control 'External Amplifier',0
 

   Capabilities: pswitch pswitch-joined penum
 

   Playback channels: Mono
 

   Mono: Playback [on]
 

 

 

 

 

 !!Alsactl output
 

 !!-------------
 

 

 

 --startcollapse--
 

 state.I82801DBICH4 {
 

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
 

 		comment.range '0 - 31'
 

 		comment.dbmin -4650
 

 		comment.dbmax 0
 

 		iface MIXER
 

 		name 'Master Playback Volume'
 

 		value.0 31
 

 		value.1 31
 

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
 

 		comment.dbmin -4650
 

 		comment.dbmax 0
 

 		iface MIXER
 

 		name 'Headphone Playback Volume'
 

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
 

 		name 'Beep Playback Switch'
 

 		value false
 

 	}
 

 	control.8 {
 

 		comment.access 'read write'
 

 		comment.type INTEGER
 

 		comment.count 1
 

 		comment.range '0 - 15'
 

 		comment.dbmin -4500
 

 		comment.dbmax 0
 

 		iface MIXER
 

 		name 'Beep Playback Volume'
 

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
 

 		comment.dbmin -3450
 

 		comment.dbmax 1200
 

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
 

 		value false
 

 	}
 

 	control.12 {
 

 		comment.access 'read write'
 

 		comment.type INTEGER
 

 		comment.count 1
 

 		comment.range '0 - 31'
 

 		comment.dbmin -3450
 

 		comment.dbmax 1200
 

 		iface MIXER
 

 		name 'Mic Playback Volume'
 

 		value 0
 

 	}
 

 	control.13 {
 

 		comment.access 'read write'
 

 		comment.type BOOLEAN
 

 		comment.count 1
 

 		iface MIXER
 

 		name 'Mic Boost (+20dB)'
 

 		value false
 

 	}
 

 	control.14 {
 

 		comment.access 'read write'
 

 		comment.type BOOLEAN
 

 		comment.count 1
 

 		iface MIXER
 

 		name 'Line Playback Switch'
 

 		value false
 

 	}
 

 	control.15 {
 

 		comment.access 'read write'
 

 		comment.type INTEGER
 

 		comment.count 2
 

 		comment.range '0 - 31'
 

 		comment.dbmin -3450
 

 		comment.dbmax 1200
 

 		iface MIXER
 

 		name 'Line Playback Volume'
 

 		value.0 0
 

 		value.1 0
 

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
 

 		comment.dbmin -3450
 

 		comment.dbmax 1200
 

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
 

 		comment.dbmin -3450
 

 		comment.dbmax 1200
 

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
 

 		comment.dbmin -3450
 

 		comment.dbmax 1200
 

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
 

 		comment.dbmin -3450
 

 		comment.dbmax 1200
 

 		iface MIXER
 

 		name 'PCM Playback Volume'
 

 		value.0 31
 

 		value.1 31
 

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
 

 		comment.dbmin 0
 

 		comment.dbmax 2250
 

 		iface MIXER
 

 		name 'Capture Volume'
 

 		value.0 15
 

 		value.1 15
 

 	}
 

 	control.27 {
 

 		comment.access 'read write'
 

 		comment.type ENUMERATED
 

 		comment.count 1
 

 		comment.item.0 'pre 3D'
 

 		comment.item.1 'post 3D'
 

 		iface MIXER
 

 		name 'PCM Out Path & Mute'
 

 		value 'pre 3D'
 

 	}
 

 	control.28 {
 

 		comment.access 'read write'
 

 		comment.type BOOLEAN
 

 		comment.count 1
 

 		iface MIXER
 

 		name '3D Control - Switch'
 

 		value false
 

 	}
 

 	control.29 {
 

 

 

 I got these instructions on Sound Troubleshooting from [COLOR=#000080]_[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)_[/COLOR]
 ][/CODE]

---

