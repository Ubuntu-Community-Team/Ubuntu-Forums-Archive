---
title: "Unable to mute headphones with speakers"
date: 2010-12-08
forum: New to Ubuntu
---

### Post by Nidhogg62 on 2010-12-08
I recently built a new computer, and installed Ubuntu 10.04 64-bit as my  primary operating system. My problem is that I am unable to disable my  speakers when I plug in my headphones in the front jack. I can hear the  sound coming from the headphones, but it doesn't mute the speakers. I'm  aware that this is oft-recurring problem, yet unlike in most cases I am  using a desktop not laptop and the suggested fixes have so far  disappointed.

I'm listing the different steps I took to correct the problem, but I am  new to running Linux, and haven't tried to fix a sound problem before,  so there's a chance that I made a mistake along the way.


I. I've tested to see if I would experience the same problem under a  Windows 7 boot, and it detects the headphones and mutes the speakers  normally.

II. Using the menu, I went to System > Preferences > Sound  Preferences and clicked on the Output tab. I switched the Connector  setting from "Analog Output" to "Analog Headphones" and while this did  mute my speakers it also muted the headphones.

III. I pulled up alsamixer in a terminal, but muting any of the  Headphone, Front, Surround, Center, LFE, or Side channels mutes the  Master volume as well, so unless I made a mistake I can't use that to  switch between speakers and headphones.

IV. I tried specifying the sound model parameters in  /etc/modprobe.d/alsa-base.conf as I have seen suggested, but that had no  impact. It's possible I selected the wrong model, and I will be  including the file later.

V. I updated ALSA from v1.0.21 to 1.0.23 for alsa-driver, alsa-lib, alsa-utils, and alsa-firmware. No luck.


I'm using the audio chipset on my motherboard, not a sound card: a Gigabyte GA-EP45T-USB3P, with a Realtek ALC889 chipset.

Running  $ cat /proc/asound/card0/codec#* | grep Codec
yields Codec: Realtek ALC889

My aplay -l output is

```

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC889 Analog [ALC889 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC889 Digital [ALC889 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic [HD-Audio Generic], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```and here is my alsa-base.conf file
```

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
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS &&  { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe  --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS  && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer  $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist  snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS  && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ;  /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi  $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist  snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1  $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist  snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx  $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist  snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS  && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
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

#Added 4 December 2010, to attempt to fix headphone problem
options snd-hda-intel model=6stack-dig


```and here is my lspci -v output (pared down to audio devices)

```

00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
        Subsystem: Giga-byte Technology Device a002
        Flags: bus master, fast devsel, latency 0, IRQ 29
        Memory at fdff8000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

01:00.1 Audio device: ATI Technologies Inc Juniper HDMI Audio [Radeon HD 5700 Series]
        Subsystem: PC Partner Limited Device aa58
        Flags: bus master, fast devsel, latency 0, IRQ 30
        Memory at fdcfc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

```Thank you. I appreciate any help that is given.

---

### Post by lotharmat on 2010-12-08
If you type this command

```
amixer sset Speaker 0
```

Does that work? - I had bound that to super+down-arrow to mute the speaker when headphones were plugged in.

However, following an update, my laptop now mutes the speaker on its own when headphones are plugged in. I'm not sure what update it was but it was fairly recent.

To get the sound back on again - replace the 0 with 100. (percentages)

---

### Post by Nidhogg62 on 2010-12-08
Using
```
amixer sset Speaker 0
```has no effect, probably because I'm not on a laptop, so I get
```
amixer: Unable to find simple control 'Speaker',0
```I did try that with the Front channel as well
```
amixer sset Front 0
```which decreased the speaker volume but didn't mute it (multiple channels being fed through the same speakers?) and had the effect of muting the headphones.

---

### Post by Nidhogg62 on 2010-12-11
Bump?

---

### Post by Calais225 on 2010-12-11
I'm no expert but I had subscribed to this thread because I had the same problem.  What worked for me was to add the computer model for my Dell laptop as per the edit you mentioned in step IV of your original message.

Fortunately another forum member had the same problem and the same computer and he found the solution.

I just lucked out and followed along.

Hope you find a solution.  I read every thread I could find on this issue but it turned out to be just one additional line of code.

Keep trying, keep posting.

---

