---
title: "I *do* want sound through my speakers and headphones at the same time"
date: 2009-12-29
forum: New to Ubuntu
---

### Post by EssexEagle on 2009-12-29
Under Jaunty I had a bug which meant that when I plugged something into my headphone jack I would still get sound out of my speakers as well.  This was excellent, as I could feed the headphones output into my hi-fi and listen to things through both my hi-fi speakers and my laptop speakers at the same time, which sounded way better than just one set of speakers alone.

Sadly, in Karmic this bug seems to have been fixed.  Is there any way of getting this behaviour to return?  I have Googled but, unsurprisingly, most people out there are trying to fix the bug not unfix it!

(I imagine a good start would be working out what sound card I have - I'm afraid I don't even know how to do that!)

---

### Post by audiomick on 2009-12-29
might be easier to just get a Y cord and feed the speaker output to the speakers and the hi-fi. You should be able to get one at most electronic markets.

---

### Post by LowSky on 2009-12-29
> **audiomick said:**
> might be easier to just get a Y cord and feed the speaker output to the speakers and the hi-fi. You should be able to get one at most electronic markets.

](*,) NO it isn't simpler!!! 


EssexEagle to find out what sound card you have open up the terminal application and type this command

```
lspci
``` that l is lower case L, post your results here

---

### Post by EssexEagle on 2009-12-29
> **LowSky said:**
> EssexEagle to find out what sound card you have open up the terminal application and type this command

```
lspci
``` that l is lower case L, post your results here


lspci gives:
```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)
04:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
```

---

### Post by audiomick on 2009-12-29
> **LowSky said:**
> ](*,) NO it isn't simpler!!! 




That's what I'd do, after 25 years as a sound tech.:)
But I'll happily bow to your opinion!

---

### Post by Jenkins1 on 2009-12-29
I loved this bug I want it back two although it would be good to create a button linked to a script to activate/deactivate the bug.

---

### Post by LowSky on 2009-12-29
> **audiomick said:**
> That's what I'd do, after 25 years as a sound tech.:)
But I'll happily bow to your opinion!

EDITED: Your solution wouldn't turn off his laptop speakers


BTW EssexEagle: This is your audio chipset

```

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
```


now we need to edit this file

```
/etc/modprobe.d/alsa-base
``` to do so in terminal again type

```
gksu gedit/etc/modprobe.d/alsa-base
``` with that file I will know what we might be able to edit.

---

### Post by rax0 on 2009-12-29
um, I don't think that was a bug in Jaunty, you had to check "headphones" (or something) in the volume properties, but I'm not sure :) and if it is a bug, I still have it :P

In karmic, go to your Sound Preferences>Hardware and change the profile to "Analog Stereo Duplex" Now go to "Output" and choose "Analog Output".

that's my configuration.

---

### Post by LowSky on 2009-12-29
> **audiomick said:**
> That's what I'd do, after 25 years as a sound tech.:)
But I'll happily bow to your opinion!

> **rax0 said:**
> um, I don't think that was a bug in Jaunty, you had to check "headphones" (or something) in the volume properties, but I'm not sure :) and if it is a bug, I still have it :P

In karmic, go to your Sound Preferences>Hardware and change the profile to "Analog Stereo Duplex" Now go to "Output" and choose "Analog Output".

that's my configuration.

this should work for most people, except there was a bug with some intel chipsets that didn't behave correctly regarding this feature.

---

### Post by audiomick on 2009-12-29
> **LowSky said:**
> Your solution would still turn off his laptop speakers


Course it would, if you plug into the headphone jack. I was assuming a desktop with speakers attached. Need to read more carefully, sorry!

---

### Post by LowSky on 2009-12-29
> **audiomick said:**
> Course it would, if you plug into the headphone jack. I was assuming a desktop with speakers attached. Need to read more carefully, sorry!

Except it wasn't my reading but my typing -- I meant it wouldn't work, because he wants his laptop speakers (that are built into the laptop) to work, when he plugs into his speaker system. When you plug in a stereo calbe into a headphone jack it normally turns those speakers off, and sound will only come from those connected.

---

### Post by EssexEagle on 2009-12-29
> **rax0 said:**
> In karmic, go to your Sound Preferences>Hardware and change the profile to "Analog Stereo Duplex" Now go to "Output" and choose "Analog Output".

that's my configuration.

I'm not sure where to find Sound Preferences.  Is that for Gnome?  Because I'm using KDE.


> **LowSky said:**
> now we need to edit this file

```
/etc/modprobe.d/alsa-base
``` to do so in terminal again type

```
gksu gedit/etc/modprobe.d/alsa-base
``` with that file I will know what we might be able to edit.

*/etc/modprobe.d/alsa-base* doesn't exist.  However, there is */etc/modprobe.d/alsa-base.conf* - the contents of this file are:
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
# Power down HDA controllers after 10 idle seconds
options snd-hda-intel power_save=10 power_save_controller=N
```

---

### Post by LowSky on 2009-12-29
/etc/modprobe.d/alsa-base.conf is the right file, sorry I'm at work and typing horribly today


This might work if, it doesn't its very easy to change

all I did was add a # to a line of the code (look for the line I highlighted [COLOR="Red"]RED[/COLOR], that # means that the OS will skip that line of information, take it out and it will be like before...I hope.... try it out

Once done reboot the computer and check for the desired effect, if not change it back and I'll dig further

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
[COLOR="Red"]# options snd-cmipci mpu_port=0x330 fm_port=0x388[/COLOR]
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Power down HDA controllers after 10 idle seconds
options snd-hda-intel power_save=10 power_save_controller=N
```

---

### Post by EssexEagle on 2009-12-30
> **LowSky said:**
> /etc/modprobe.d/alsa-base.conf is the right file, sorry I'm at work and typing horribly today


This might work if, it doesn't its very easy to change

all I did was add a # to a line of the code (look for the line I highlighted [COLOR="Red"]RED[/COLOR], that # means that the OS will skip that line of information, take it out and it will be like before...I hope.... try it out

Once done reboot the computer and check for the desired effect, if not change it back and I'll dig further



Unfortunately that has no effect :-(  Any other thoughts?

I appreciate your help on this, btw :-)

---

### Post by glubbdrubb on 2009-12-30
Did you restart after making the change?

---

### Post by EssexEagle on 2009-12-30
> **glubbdrubb said:**
> Did you restart after making the change?

Yep, I restarted alsa at first, then restarted the whole computer and still no joy.

---

### Post by EssexEagle on 2010-01-01
Anyone have any ideas?

---

### Post by stepstools on 2010-04-01
Sorry if this topic is a bit old, but I am also looking for a way to do this.  Does anyone have any ideas?

---

