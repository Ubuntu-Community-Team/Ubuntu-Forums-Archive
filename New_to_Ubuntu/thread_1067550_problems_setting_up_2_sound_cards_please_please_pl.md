---
title: "problems setting up 2 sound cards please please please please help."
date: 2009-02-12
forum: New to Ubuntu
---

### Post by palmtree0 on 2009-02-12
hi i'm having a really tough time setting up 2 sound cards. i've looked all over the internet and linux forums and it seems the more i read, the more confused i get. (sorry i'm a complete moron)

can someone please please give me detailed instructions on how to make this work?

i have a dell dimension 9150 (xps 400) with both windows xp and linux ubuntu 8.10 (upgraded). my sound cards are:
a.) Soundblaster Live! 24
b.) on board Sigmatel High Definition Audio

They both work fine in windows so i know they aren't defective. The Soundblaster Live! 24 card actually works fine with no problems in linux. however, the sigmatel produces no sound. the system recognizes both cards and no error messages come up when i try to play something through the sigmatel. if i try to play a song, the progress bar moves as if it's playing but like i said, produces no sound. if i switch the output to the SB Live, everything works fine.

Here are some terminal outputs that i hope are useful:

wind@papermoon:~$ asoundconf list
Names of available sound cards:
CA0106
Intel

wind@papermoon:~$ cat /proc/asound/cards
 0 [CA0106         ]: CA0106 - CA0106
                      Live! 7.1 24bit [SB0410] at 0xb8e0 irq 16
 1 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfebfc000 irq 16

wind@papermoon:~$ cat /proc/asound/devices
  2:        : timer
  3:        : sequencer
  4: [ 0- 0]: raw midi
  5: [ 0- 3]: digital audio playback
  6: [ 0- 3]: digital audio capture
  7: [ 0- 2]: digital audio playback
  8: [ 0- 2]: digital audio capture
  9: [ 0- 1]: digital audio playback
 10: [ 0- 1]: digital audio capture
 11: [ 0- 0]: digital audio playback
 12: [ 0- 0]: digital audio capture
 13: [ 0]   : control
 14: [ 1- 0]: digital audio playback
 15: [ 1- 0]: digital audio capture
 16: [ 1]   : control

wind@papermoon:~$ cat /proc/asound/modules
 0 snd_ca0106
 1 snd_hda_intel

wind@papermoon:~$ lspci -vv

...(here are the relevant parts)

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
	Subsystem: Dell Device 01d1
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at febfc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

...

05:04.0 Multimedia audio controller: Creative Labs SB Audigy LS
	Subsystem: Creative Labs Device 1006
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64 (500ns min, 5000ns max)
	Interrupt: pin A routed to IRQ 16
	Region 0: I/O ports at b8e0 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: CA0106
	Kernel modules: snd-ca0106

wind@papermoon:~$ aplay -l
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
card 1: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

wind@papermoon:~$ aplay -L
default:CARD=CA0106
    CA0106, CA0106
    Default Audio Device
front:CARD=CA0106,DEV=0
    CA0106, CA0106
    Front speakers
rear:CARD=CA0106,DEV=0
    CA0106, CA0106
    Rear speakers
center_lfe:CARD=CA0106,DEV=0
    CA0106, CA0106
    Center and Subwoofer speakers
side:CARD=CA0106,DEV=0
    CA0106, CA0106
    Side speakers
surround40:CARD=CA0106,DEV=0
    CA0106, CA0106
    4.0 Surround output to Front and Rear speakers
surround41:CARD=CA0106,DEV=0
    CA0106, CA0106
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=CA0106,DEV=0
    CA0106, CA0106
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=CA0106,DEV=0
    CA0106, CA0106
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=CA0106,DEV=0
    CA0106, CA0106
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=CA0106,DEV=0
    CA0106, CA0106
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)
default:CARD=Intel
    HDA Intel, STAC92xx Analog
    Default Audio Device
front:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
hdmi:CARD=Intel,DEV=0
    HDA Intel
    HDMI Audio Output

Another thing I don't understand is why does the sigmatel only have analog capabilities? shouldn't it be analog and digital?

my "/etc/modprobe.d/alsa-base" file:

# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2
options snd-hda-intel index=1
options snd-ca0106 index=0







here is my "/usr/share/alsa-source" file

### ALSA source configuration file ###
# (This file is in GNU makefile format)

# List the card drivers to be built, separated by commas. For example,
# if you want to build the drivers for the Sound Blaster 16 and the
# Yamaha YMF cards then write:
#     ALSA_CARDS="sb16, ymfpci"
# The special name "all" results in all card drivers being built.
#
ifndef ALSA_CARDS
ALSA_CARDS=""
endif

# List the card driver options, separated by commas, all on one line.
# The special name "all" results in all possible options being set.
#
# This is an advanced feature.  See ALSA's documentation for more info.
#
ifndef ALSA_CARD_OPTIONS
ALSA_CARD_OPTIONS=""
endif

# Set to "y" if you want to build the modules without ISA PnP support.
# Otherwise, set to "".
#
ifndef ALSA_NOPNP
ALSA_NOPNP=""
endif

# Set to "y" if you want to build the modules with debugging code.
# Otherwise, set to "".
#
ifndef ALSA_DEBUG
ALSA_DEBUG=""
endif






also i get this error when i try to run asoundconf-gtk

wind@papermoon:~$ asoundconf-gtk
You need to make sure asoundconf is active!
By default, asoundconf's configuration file is ~/.asoundrc.asoundconf
and must be included in ~/.asoundrc. Open this file to make sure it is!

when i got to 'preferences' then 'sound', my options for sound playback are:

+ Autodetect
- Live! 7.1 24bit [SB0410] CA0106 (ALSA)
- Live! 7.1 24bit [SB0410] CA0106 (ALSA)
- Live! 7.1 24bit [SB0410] CA0106 (ALSA)
+ Live! 7.1 24bit [SB0410] CA0106 (ALSA)
- HDA Intel STAC92xx Analog (ALSA)
+ Live! 7.1 24bit [SB0410] CA0106 (OSS)
+ Live! 7.1 24bit [SB0410] CA0106 (OSS)
- Live! 7.1 24bit [SB0410] CA0106 (OSS)
- HDA Intel STAC92xx Analog (OSS)
- HDA Intel STAC92xx Analog (OSS)
+ ALSA - Advanced Linux Sound Architecture
+ OSS - Open Sound System
- PulseAudio Sound Server

'+' means that hitting "test" will produce a beep
'-' means that hitting "test" will say testing but no beep

(I disabled PulseAudio according to this website: [http://idyllictux.wordpress.com/2008/10/29/alsa-instead-of-pulseaudio-for-ubuntu-810-intrepid-a-non-destructive-way/](http://idyllictux.wordpress.com/2008/10/29/alsa-instead-of-pulseaudio-for-ubuntu-810-intrepid-a-non-destructive-way/)


that's all i can think of now... i know it's a really really long post. i'm sorry i'm just trying to be thorough. everything i have tried so far has not worked and i've done so many things that i've lost track of all the changes, installs, reinstalls, and removals i've done so i've done the best i can to show the state of my system.

i've been trying to solve this forever and i would really really appreciate it if someone could help me resolve this as soon as possible. If there's any other information or files i need to post, please let me know. Thanks to all who can help.

---

### Post by palmtree0 on 2009-02-14
anyone? a link to a site? a hint? anything? please..

---

