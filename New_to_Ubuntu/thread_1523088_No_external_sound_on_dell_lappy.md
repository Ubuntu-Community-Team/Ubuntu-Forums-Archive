---
title: "No external sound on dell lappy"
date: 2010-07-03
forum: New to Ubuntu
---

### Post by Ducatiboy Stu on 2010-07-03
I am having a lot of trouble getting my external speaker to work on my Dell 630m laptop.with 10.04

The sound card is an Intell HDA. Sigmatel STAC9200

I have tried various setting, including using IEC958 selections, and get nothing.

The internall speakers mute when I plug in the speakersm but no sound

have run alsamixer in term, etc  :(

---

### Post by Ducatiboy Stu on 2010-07-06
Anyone....

---

### Post by lidex on 2010-07-07
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by Ducatiboy Stu on 2010-07-08
laptop is Dell Inspiron 630m with Intell Sigmatec onboard sound
```

ncts@ncts-laptop:~$ uname -a
Linux ncts-laptop 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 07:54:58 UTC 2010 i686 GNU/Linux
ncts@ncts-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
ncts@ncts-laptop:~$ dpkg -l | grep "alsa"
ii  alsa-base                             1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                            1.0.22-0ubuntu5                                 ALSA utilities
ii  alsamixergui                          0.9.0rc2-1-9                                    graphical soundcard mixer for ALSA soundcard driver
ii  bluez-alsa                            4.60-0ubuntu8                                   Bluetooth audio support
ii  gstreamer0.10-alsa                    0.10.28-1                                       GStreamer plugin for ALSA
ii  libesd-alsa0                          0.2.41-6ubuntu1                                 Enlightened Sound Daemon (ALSA) - transitional package
rc  libsdl1.2debian-alsa                  1.2.13-4ubuntu4                                 Simple DirectMedia Layer (with X11 and ALSA options)
ii  libsnack2-alsa                        2.2.10-dfsg1-9                                  Sound extension to Tcl/Tk and Python/Tkinter - Tcl/Tk li
ii  libsox-fmt-alsa                       14.3.0-1.1build1                                SoX alsa format I/O library
ncts@ncts-laptop:~$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: SigmaTel STAC9200

==> /proc/asound/card0/codec#1 <==
Codec: Conexant ID 2bfa

```

---

### Post by lidex on 2010-07-08
OK, try this. Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=dell-m21 
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab.

---

### Post by Ducatiboy Stu on 2010-07-09
Tried that... still no sound via external headphone output

Tried using all the different outputs/hardware in system>pref>sound 

```
# 
 gksudo gedit /etc/modprobe.d/alsa-base.conf

autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
options snd-hda-intel model=dell-m21

```

---

### Post by lidex on 2010-07-09
OK. Leave that option in alsa-base.conf and follow the alsa-upgrade link in my sig to get v. 1.0.23

---

### Post by Ducatiboy Stu on 2010-07-10
Tried the scripts... the installed OK

But still no sound from the headphone jack.... :(

---

### Post by lidex on 2010-07-10
Install gnome-alsamixer and use it to make sure that output is enabled and not muted.
 **Gnome-alsamixer**
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```
**Use 'Edit -> Sound Card Properties' menu to enable elements.**
Soundcard tab to select / adjust levels.
To install:
```
sudo apt-get install gnome-alsamixer
```
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab.

---

### Post by Ducatiboy Stu on 2010-07-10
Mm... still no joy  :(

---

### Post by lidex on 2010-07-10
Try fiddling with the alsa-base.conf options. Change the value 'dell-m21' to:
```
ref
auto
dell-d21
dell-d22
dell-d23
```
Maybe first try with nothing at all, since the upgrade may have altered your config. Remember to use only one line at a time and reboot for changes to take effect. I **Think** this command will achieve same results, but no guarantees:
```
sudo alsa force-reload
```

---

### Post by ahmednady on 2010-07-10
I Have the same problem as u but couldnt solve it
i'm using [B]Creative Labs Ectiva EV1938
[/B]

---

