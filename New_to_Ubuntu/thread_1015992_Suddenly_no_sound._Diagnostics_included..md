---
title: "Suddenly no sound. Diagnostics included."
date: 2008-12-19
forum: New to Ubuntu
---

### Post by Swerve1000 on 2008-12-19
Following an update prompted by the icon in the top right corner of Gnome around 5 days ago, I no longer have any sound, including login. 

The hardware works fine in Windows XP.

My desktop is dual boot (XP and 8.10)

I'm using Ubuntu 8.10 i386 Desktop,
Kernel version is 2.6.27-9-generic,
Onboard sound card is a Realtek ALC655 chip.

----------------------------------------------------

Nothing is set to mute/zero, including in alsamixer ( alsamixer -Dhw ).

----------------------------------------------------

If I go System>Preferences>Sound and select SiS SI7012 with ALC655 SiS SI7012 (ALSA)

I get the following:

> audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink:
Could not open audio device for playback.

When set to Autodetect, it 'plays', but I hear nothing.

SiS SI7012 with ALC655 SiS SI7012 (OSS) > Test = 'plays', but I hear nothing.
PulseAudio Sound Server > Test = 'plays' but I hear nothing.
OSS - Open Sound System > Test = 'plays', but I hear nothing.
ALSA - Advanced Linux Sound Architecture > Test = 'plays', but I hear nothing.

---------------------------------------------------------------------------------------------------------

I tried:
> 
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2 and then rebooted.

This made no difference at all.

--------------------------------------------------------------------------------------------------------

> cat /proc/asound/cards

shows:

> 0 [SI7012 ]: ICH - SiS SI7012
SiS SI7012 with ALC655 at irq 18

-----------------------------------------------------------------------------------------------------------

I also added:
> 
# PulseAudio Fixes - [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)
deb [http://ppa.launchpad.net/psyke83/ubuntu](http://ppa.launchpad.net/psyke83/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/psyke83/ubuntu](http://ppa.launchpad.net/psyke83/ubuntu) intrepid main

to:
> 
 /etc/apt/sources.list

updated:

sudo apt-get update && sudo apt-get dist-upgrade

and rebooted, but still nothing.

--------------------------------------------------------------------------
> aplay -l

shows:

> **** List of PLAYBACK Hardware Devices ****
card 0: SI7012 [SiS SI7012], device 0: Intel ICH [SiS SI7012]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

--------------------------------------------------------------------------

> pkill pulseaudio; sleep 2; pulseaudio -vv

shows:

> I: main.c: PolicyKit refuses acquire-high-priority privilige.
I: main.c: Called SUID root and real-time/high-priority scheduling was requested in the configuration. However, we lack the necessary priviliges:
I: main.c: We are not in group 'pulse-rt' and PolicyKit refuse to grant us priviliges. Dropping SUID again.
I: main.c: For enabling real-time scheduling please acquire the appropriate PolicyKit priviliges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
I: main.c: Note that real-time/high-priority scheduling is NOT normally required. If you experience crackling or other sound anomalies, consider one or more of the above solutions.
I: main.c: High-priority scheduling enabled in configuration but now allowed by policy. Disabling forcibly.
W: ltdl-bind-now.c: Failed to find original dlopen loader.
W: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
W: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
I: main.c: This is PulseAudio 0.9.10
I: main.c: Page size is 4096 bytes
I: main.c: Fresh high-resolution timers available! Bon appetit!
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-hal-detect.so': success
I: module-hal-detect.c: Trying capability alsa
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/computer_alsa_timer
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/computer_alsa_sequencer
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_1039_7012_sound_card_0_alsa_capture_1
D: module-hal-detect.c: Loading module-alsa-sink with arguments 'device_id=0 sink_name=alsa_output.pci_1039_7012_sound_card_0_alsa_playback_0'
D: alsa-util.c: Trying front:0...
W: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
I: module-alsa-sink.c: Successfully opened device front:0.
I: module-alsa-sink.c: Successfully enabled mmap() mode.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
I: alsa-util.c: Unable to attach to mixer front:0: No such file or directory
I: alsa-util.c: Successfully attached to mixer 'hw:0'
I: alsa-util.c: Using mixer control "Master".
I: sink.c: Created sink 0 "alsa_output.pci_1039_7012_sound_card_0_alsa_playback_0" with sample spec "s16le 2ch 48000Hz"
I: source.c: Created source 0 "alsa_output.pci_1039_7012_sound_card_0_alsa_playback_0.monitor" with sample spec "s16le 2ch 48000Hz"
I: module-alsa-sink.c: Using 8 fragments of size 1760 bytes.
I: alsa-util.c: All 2 channels can be mapped to mixer channels. Using hardware volume control.
D: module-alsa-sink.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+29
I: module-alsa-sink.c: Starting playback.
I: module.c: Loaded "module-alsa-sink" (index: #0; argument: "device_id=0 sink_name=alsa_output.pci_1039_7012_sound_card_0_alsa_playback_0").
D: module-hal-detect.c: Loading module-alsa-source with arguments 'device_id=0 source_name=alsa_input.pci_1039_7012_sound_card_0_alsa_capture_0'
D: alsa-util.c: Trying front:0...
W: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
I: module-alsa-source.c: Successfully opened device front:0.
I: module-alsa-source.c: Successfully enabled mmap() mode.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
I: alsa-util.c: Unable to attach to mixer front:0: No such file or directory
I: alsa-util.c: Successfully attached to mixer 'hw:0'
I: alsa-util.c: Using mixer control "Capture".
I: source.c: Created source 1 "alsa_input.pci_1039_7012_sound_card_0_alsa_capture_0" with sample spec "s16le 2ch 48000Hz"
I: module-alsa-source.c: Using 8 fragments of size 1760 bytes.
I: alsa-util.c: All 2 channels can be mapped to mixer channels. Using hardware volume control.
D: module-alsa-source.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+28
I: module.c: Loaded "module-alsa-source" (index: #1; argument: "device_id=0 source_name=alsa_input.pci_1039_7012_sound_card_0_alsa_capture_0").
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_1039_7012_sound_card_0_alsa_control__1
I: module-hal-detect.c: Loaded 2 modules.
I: module.c: Loaded "module-hal-detect" (index: #2; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-esound-protocol-unix.so': success
I: module.c: Loaded "module-esound-protocol-unix" (index: #3; argument: "").
I: protocol-native.c: loading cookie from disk.
I: module.c: Loaded "module-native-protocol-unix" (index: #4; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-gconf.so': success
I: module.c: Loaded "module-gconf" (index: #5; argument: "").
I: module.c: Loaded "module-volume-restore" (index: #6; argument: "").
D: module-default-device-restore.c: Restored default sink 'alsa_output.pci_1039_7012_sound_card_0_alsa_playback_0'.
D: module-default-device-restore.c: No previous default source setting, ignoring.
I: module.c: Loaded "module-default-device-restore" (index: #7; argument: "").
I: module.c: Loaded "module-rescue-streams" (index: #8; argument: "").
D: module-suspend-on-idle.c: Sink alsa_output.pci_1039_7012_sound_card_0_alsa_playback_0 becomes idle.
D: module-suspend-on-idle.c: Source alsa_output.pci_1039_7012_sound_card_0_alsa_playback_0.monitor becomes idle.
D: module-suspend-on-idle.c: Source alsa_input.pci_1039_7012_sound_card_0_alsa_capture_0 becomes idle.
I: module.c: Loaded "module-suspend-on-idle" (index: #9; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-x11-publish.so': success
D: module-x11-publish.c: using already loaded auth cookie.
I: module.c: Loaded "module-x11-publish" (index: #10; argument: "").
I: main.c: Daemon startup complete.
D: module-hal-detect.c: dbus: interface=org.freedesktop.DBus, path=/org/freedesktop/DBus, member=NameAcquired
I: module-suspend-on-idle.c: Source alsa_input.pci_1039_7012_sound_card_0_alsa_capture_0 idle for too long, suspending ...
I: module-alsa-source.c: Device suspended...
I: module-suspend-on-idle.c: Source alsa_output.pci_1039_7012_sound_card_0_alsa_playback_0.monitor idle for too long, suspending ...
I: module-suspend-on-idle.c: Sink alsa_output.pci_1039_7012_sound_card_0_alsa_playback_0 idle for too long, suspending ...
I: module-alsa-sink.c: Device suspended...



Following further research I have ran the script linked to on [THIS]("https://wiki.ubuntu.com/DebuggingSoundProblems") page.

This is the result of the Automatic Sound Information Collection script is as follows:


> !!################################
!!ALSA Information Script v 0.4.52
!!################################

!!Script ran on: Fri Dec 19 17:49:14 GMT 2008


!!Linux Distribution
!!------------------

Ubuntu 8.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 8.10"


!!Kernel Information
!!------------------

Kernel release:    2.6.27-9-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.17
Library version:    
Utilities version:  1.0.17


!!Loaded ALSA modules
!!-------------------

snd_intel8x0


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [SI7012         ]: ICH - SiS SI7012
                      SiS SI7012 with ALC655 at irq 18


!!PCI Soundcards installed in the system
!!--------------------------------------

00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)


!!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------

00:02.7 0401: 1039:7012 (rev a0)
	Subsystem: 105b:0c4d


!!Modprobe options (Sound related)
!!--------------------------------

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
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

0-0/0: Realtek ALC655 rev 0

PCI Subsys Vendor: 0x105b
PCI Subsys Device: 0x0c4d

Revision         : 0x00
Compat. Class    : 0x00
Subsys. Vendor ID: 0xffff
Subsys. ID       : 0xffff

Capabilities     :
DAC resolution   : 16-bit
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
Extended ID      : codec=0 rev=2 LDAC SDAC CDAC DSA=0 SPDIF
Extended status  : SPCV LDAC SDAC CDAC SPDIF=7/8 SPDIF
SPDIF Control    : Consumer PCM Category=0x2 Generation=1 Rate=48kHz

0:00 = 0000
0:02 = 0b0b
0:04 = 0000
0:06 = 0009
0:08 = 0000
0:0a = 801e
0:0c = 801f
0:0e = 801f
0:10 = 9c1c
0:12 = 9f1f
0:14 = 0000
0:16 = 9f1f
0:18 = 9b1b
0:1a = 0000
0:1c = 0909
0:1e = 0000
0:20 = 0400
0:22 = 0000
0:24 = 0000
0:26 = 000f
0:28 = 09c4
0:2a = 05d4
0:2c = bb80
0:2e = bb80
0:30 = bb80
0:32 = bb80
0:34 = 0000
0:36 = 9c8a
0:38 = 9c9c
0:3a = 2824
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
0:64 = 0808
0:66 = 0808
0:68 = 0aea
0:6a = 8000
0:6c = 0000
0:6e = 0025
0:70 = 81e0
0:72 = 22e8
0:74 = 8000
0:76 = 0000
0:78 = 0003
0:7a = a092
0:7c = 414c
0:7e = 4760
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----  1 root audio 116, 7 2008-12-19 17:19 /dev/snd/controlC0
crw-rw----  1 root audio 116, 6 2008-12-19 17:19 /dev/snd/pcmC0D0c
crw-rw----  1 root audio 116, 5 2008-12-19 17:19 /dev/snd/pcmC0D0p
crw-rw----  1 root audio 116, 4 2008-12-19 17:19 /dev/snd/pcmC0D1c
crw-rw----  1 root audio 116, 3 2008-12-19 17:19 /dev/snd/seq
crw-rw----  1 root audio 116, 2 2008-12-19 17:19 /dev/snd/timer


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: SI7012 [SiS SI7012], device 0: Intel ICH [SiS SI7012]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: SI7012 [SiS SI7012], device 0: Intel ICH [SiS SI7012]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SI7012 [SiS SI7012], device 1: Intel ICH - MIC ADC [SiS SI7012 - MIC ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [SI7012]

Card hw:0 'SI7012'/'SiS SI7012 with ALC655 at irq 18'
  Mixer name	: 'Realtek ALC655 rev 0'
  Components	: 'AC97a:414c4760'
  Controls      : 41
  Simple ctrls  : 26
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 20 [65%] [-16.50dB] [on]
  Front Right: Playback 20 [65%] [-16.50dB] [on]
Simple mixer control 'Master Mono',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 22 [71%] [-13.50dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 4 [13%] [-28.50dB] [off]
  Front Right: Playback 4 [13%] [-28.50dB] [off]
Simple mixer control 'Surround',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 3 [10%] [-42.00dB] [off]
  Front Right: Playback 3 [10%] [-42.00dB] [off]
Simple mixer control 'Surround Jack Mode',0
  Capabilities: enum
  Items: 'Shared' 'Independent'
  Item0: 'Shared'
Simple mixer control 'Center',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 21 [68%] [-15.00dB] [off]
Simple mixer control 'LFE',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 3 [10%] [-42.00dB] [off]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 3 [10%] [-30.00dB] [off] Capture [off]
  Front Right: Playback 3 [10%] [-30.00dB] [off] Capture [off]
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [-34.50dB] [off] Capture [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off] Capture [off]
Simple mixer control 'Mic',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [-34.50dB] [off]
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
  Capabilities: cswitch cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
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
  Capabilities: pswitch pswitch-joined cswitch cswitch-joined
  Playback channels: Mono
  Capture channels: Mono
  Mono: Playback [on] Capture [off]
Simple mixer control 'IEC958 Playback AC97-SPSA',0
  Capabilities: volume volume-joined
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 3
  Mono: 1 [33%]
Simple mixer control 'IEC958 Playback Source',0
  Capabilities: enum
  Items: 'PCM' 'Analog In' 'IEC958 In'
  Item0: 'PCM'
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
  Front Left: Capture 9 [60%] [13.50dB] [on]
  Front Right: Capture 9 [60%] [13.50dB] [on]
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
Simple mixer control 'Channel Mode',0
  Capabilities: enum
  Items: '2ch' '4ch' '6ch'
  Item0: '2ch'
Simple mixer control 'Duplicate Front',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'External Amplifier',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]


!!Alsactl output
!!-------------

--startcollapse--
state.SI7012 {
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
		value.0 20
		value.1 20
	}
	control.3 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Center Playback Switch'
		value false
	}
	control.4 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 31'
		comment.dbmin -4650
		comment.dbmax 0
		iface MIXER
		name 'Center Playback Volume'
		value 21
	}
	control.5 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'LFE Playback Switch'
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
		name 'LFE Playback Volume'
		value 3
	}
	control.7 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Surround Playback Switch'
		value.0 false
		value.1 false
	}
	control.8 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -4650
		comment.dbmax 0
		iface MIXER
		name 'Surround Playback Volume'
		value.0 3
		value.1 3
	}
	control.9 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Master Mono Playback Switch'
		value true
	}
	control.10 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 31'
		comment.dbmin -4650
		comment.dbmax 0
		iface MIXER
		name 'Master Mono Playback Volume'
		value 22
	}
	control.11 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'PC Speaker Playback Switch'
		value false
	}
	control.12 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 15'
		comment.dbmin -4500
		comment.dbmax 0
		iface MIXER
		name 'PC Speaker Playback Volume'
		value 0
	}
	control.13 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Phone Playback Switch'
		value false
	}
	control.14 {
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
	control.15 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Mic Playback Switch'
		value false
	}
	control.16 {
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
	control.17 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Mic Boost ( 20dB)'
		value false
	}
	control.18 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Line Playback Switch'
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
		name 'Line Playback Volume'
		value.0 3
		value.1 3
	}
	control.20 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'CD Playback Switch'
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
		name 'CD Playback Volume'
		value.0 0
		value.1 0
	}
	control.22 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Aux Playback Switch'
		value false
	}
	control.23 {
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
	control.24 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'PCM Playback Switch'
		value false
	}
	control.25 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'PCM Playback Volume'
		value.0 4
		value.1 4
	}
	control.26 {
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
	control.27 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Capture Switch'
		value true
	}
	control.28 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 15'
		comment.dbmin 0
		comment.dbmax 2250
		iface MIXER
		name 'Capture Volume'
		value.0 9
		value.1 9
	}
	control.29 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 Mix
		comment.item.1 Mic
		iface MIXER
		name 'Mono Output Select'
		value Mix
	}
	control.30 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 Mic1
		comment.item.1 Mic2
		iface MIXER
		name 'Mic Select'
		value Mic1
	}
	control.31 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Con Mask'
		value '0fff000f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.32 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Pro Mask'
		value cf00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
	}
	control.33 {
		comment.access 'read write'
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Default'
		value '0082000200000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.34 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Switch'
		value true
	}
	control.35 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 3'
		iface MIXER
		name 'IEC958 Playback AC97-SPSA'
		value 1
	}
	control.36 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Duplicate Front'
		value false
	}
	control.37 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 Shared
		comment.item.1 Independent
		iface MIXER
		name 'Surround Jack Mode'
		value Shared
	}
	control.38 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 '2ch'
		comment.item.1 '4ch'
		comment.item.2 '6ch'
		iface MIXER
		name 'Channel Mode'
		value '2ch'
	}
	control.39 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'IEC958 Capture Switch'
		value false
	}
	control.40 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 PCM
		comment.item.1 'Analog In'
		comment.item.2 'IEC958 In'
		iface MIXER
		name 'IEC958 Playback Source'
		value PCM
	}
	control.41 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'External Amplifier'
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
xt_TCPMSS
xt_limit
xt_tcpudp
nf_nat_irc
nf_nat_ftp
ipt_LOG
ipt_MASQUERADE
xt_DSCP
ipt_REJECT
nf_conntrack_irc
nf_conntrack_ftp
xt_state
af_packet
binfmt_misc
sco
bridge
stp
rfcomm
bnep
l2cap
bluetooth
vboxdrv
ipv6
ppdev
cpufreq_userspace
cpufreq_ondemand
cpufreq_powersave
cpufreq_conservative
cpufreq_stats
freq_table
container
pci_slot
wmi
video
output
sbs
sbshc
battery
ac
lp
floppy
evdev
pcspkr
usblp
psmouse
serio_raw
snd_intel8x0
snd_ac97_codec
ac97_bus
snd_pcm_oss
snd_mixer_oss
snd_pcm
snd_seq_dummy
parport_pc
parport
snd_seq_oss
snd_seq_midi
snd_rawmidi
snd_seq_midi_event
snd_seq
snd_timer
snd_seq_device
button
snd
i2c_sis96x
soundcore
snd_page_alloc
sis_agp
i2c_core
shpchp
pci_hotplug
agpgart
iptable_nat
nf_nat
nf_conntrack_ipv4
nf_conntrack
iptable_mangle
iptable_filter
ip_tables
x_tables
ext3
jbd
mbcache
sr_mod
cdrom
sd_mod
crc_t10dif
sg
pata_acpi
pata_sis
ata_generic
ohci_hcd
ehci_hcd
libata
sis900
mii
usbcore
scsi_mod
dock
thermal
processor
fan
fbcon
tileblit
font
bitblit
softcursor
fuse




I have done everything I can think of.

I need some help with this, extremly stuck.


Many thanks!

---

### Post by Swerve1000 on 2008-12-19
I have found a solution, at last!!


[http://ubuntuforums.org/showthread.php?p=6400512#post6400512](http://ubuntuforums.org/showthread.php?p=6400512#post6400512)


:guitar:

---

