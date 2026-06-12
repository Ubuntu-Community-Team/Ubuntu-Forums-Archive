---
title: "Problems with HDMI Audio &amp; Video &amp; NVIDIA drivers"
date: 2011-04-13
forum: New to Ubuntu
---

### Post by Uhura on 2011-04-13
I've had the following system working more or less ok for a couple of months using VGA cable for video and an audio-out cable for audio:
Zotac Zbox HD-ID11.
NVIDIA® Next-Generation ION&#8482; (w/512MB DDR3)
Intel® Atom&#8482; D510 (dual-core) (1.66 GHz)
Western Digital Scorpio Blue 500GB Sata 8MB Cache 2.5 Inch Internal Hard Drive 
Kingston Value ram 800Mhz DDR2 CL6 SO DIMM
Ubuntu 10.04

Today I finally got hold of an HDMI cable and now I'm having the following problems:
1. Screen resolution is messed up; the top, bottom and both sides of the screen are cut off, and the graphics is terrible.
2. No audio whatsoever.

Things I've tried:

I've tried resetting the resolution via System>Admin>NVIDIA X server settings, but makes no difference. The edges of the screen are always cropped.

I've tried following the instructions in this howto: [http://ubuntuforums.org/showthread.php?t=1668737](http://ubuntuforums.org/showthread.php?t=1668737)
but I didn't get past step 1 because although my NVIDIA driver kernel version appears to be correct, when I check whether the system can see the nvidia audio devices, I get no nvidia devices at all. Output as follows:

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

So I tried to follow the instructions in this link: [https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules](https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules)

but the current version of the kernel; 2.6.32-30-generic, doesnt match any of the "linux-alsa-driver-modules" packages in the synaptic package manager (they only go up to 2.6.32-29), and there are no instructions on what to do in this case because it assumes that the matching module will be there. 

And so now I'm stuck! Any help would be much appreciated :0)

---

### Post by Hedgehog1 on 2011-04-14
First, lets solve the 'overscan' settings so your image in not clipped when using HDMI:

Please set your 'overscan compensation' to zero:

[IMG]http://img25.imageshack.us/img25/9540/overscan.png[/IMG]

Also, many HDTVs need to be set to a true 1920x1080 mode when using them as a monitor.  Mine toggles to it from the remote.


-------------------------------

As for the sound over HDMI with nVidia and 10.04 - I don't think it is possible until you get to 10.10; then that link you were following will work.  It got my system running.  In 11.04 (natty) it can be setup with just the GUI - but don't install it yet.  There are still a number of bugs to iron out of natty.



***The Hedge***

:KS

---

### Post by Uhura on 2011-04-14
Hi, thanks for responding to my post!

> **Hedgehog1 said:**
> First, lets solve the 'overscan' settings so your image in not clipped when using HDMI:

Please set your 'overscan compensation' to zero:

Ok, the overscan settings were already at zero, I've attached a screenshot to show what the other settings are at.

> **Hedgehog1 said:**
>  Also, many HDTVs need to be set to a true 1920x1080 mode when using them as a monitor.  Mine toggles to it from the remote.

I had the manual resolution set to 800x600 because when I set it to 1920x1080 the fonts are all so tiny I'd need a magnifying glass to read them. Nonetheless I tried changing them as you suggested, and the screen remained cropped. The specs of the TV might make a difference here; its a small 19 inch LCD TV, more like HD-ready than full HD. (Oki V19B-PHDUVI) The manual is pretty confusing but says that the max resolution from a PC is 1600x1200, but then gives a list of compatible HDMI modes, the highest of which is 1080P. I don't really understand all that, but it may help! Oh and the remote has a button called "HDMI control", but when I press it nothing happens and the manual says the button is functionless!!

> **Hedgehog1 said:**
>  As for the sound over HDMI with nVidia and 10.04 - I don't think it is possible until you get to 10.10; then that link you were following will work.  It got my system running.  In 11.04 (natty) it can be setup with just the GUI - but don't install it yet.  There are still a number of bugs to iron out of natty.

Should I just upgrade to 10.10 and see what happens? I was originally told not to install 10.10 because it isn't fully supported or something? 

Thanks

---

### Post by Uhura on 2011-04-14
Update: I just tried *increasing* the overscan compensation to see if that would do anything, and the screen started to shrink....when I got to 105 it fits the screen with only a tiny wasted black strip at the top, but no more cropping! So it looks like the image problem is solved, or at least worked-around. 

Although there's still the problem that the NVIDIA drivers aren't being used and no NVIDIA devices are being recognised.

---

### Post by lindomsd on 2011-04-14
Ubuntu us detectecting the audio chipset as the incorrect type and to fix it you need to change the file /etc/modprobe.d/alsa-base.conf – the last line that currently reads: 

options snd-hda-intel power_save=10 power_save_controller=N

should be:

options snd-hda-intel model=generic power_save=10 power_save_controller=N

Reboot and the audio works.

---

### Post by ukdvder on 2011-04-14
hi, im a rookie here. by the way i support this forum stay public. :D

---

### Post by Uhura on 2011-04-14
> **lindomsd said:**
> Ubuntu us detectecting the audio chipset as the incorrect type and to fix it you need to change the file /etc/modprobe.d/alsa-base.conf – the last line that currently reads: 

options snd-hda-intel power_save=10 power_save_controller=N

should be:

options snd-hda-intel model=generic power_save=10 power_save_controller=N

Reboot and the audio works.

My modprobe.d/alsa-base.conf file doesn't contain either of those lines. Should I just add it in at the end? Here's the whole file:

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

---

### Post by Hedgehog1 on 2011-04-14
> The manual is pretty confusing but says that the max resolution from a PC is 1600x1200, but then gives a list of compatible HDMI modes, the highest of which is 1080P.

Uhura, based on this excerpt from your manual, your adjustment to 105 was the perfect thing to do.  Well Done!

As to sound, if others can come up with a way to get the sound over HDMI for nVidia on 10.04 working for you, great.  My first Ubuntu install was 10.10 2 months ago, so my experinces with pre-10.10 details is limited.

You can also stay at 10.04 and use a separate audio connection from the PC's sound connections to the TV (Or directly to the receiver if you are using one).  If the long term support of 10.04 is important, than one of these options might be best.

Going to 10.10 is also an option.  I know it is possible to setup the sound over HDMI from nVidia in 10.10.  However, 10.04 is a reliable dristro, more so than 10.10 and 11.04 which are both rolling releases (and some updates will break things for time in rolling releases).  I think a separate sound cable is a perfectly acceptable option; but it is up to you.


***The Hedge***

:KS

---

### Post by Uhura on 2011-04-15
> Uhura, based on this excerpt from your manual, your adjustment to 105 was the perfect thing to do.  Well Done!Thanks! It was more a case of random trial & error than actually knowing what I was doing or why.
:grin:

> You can also stay at 10.04 and use a separate audio connection from the PC's sound connections to the TV (Or directly to the receiver if you are using one).  If the long term support of 10.04 is important, than one of these options might be best.Ok looks like I'm stuck with a seperate audio cable for now. There's just one problem though, and that is when I've got the HDMI cable plugged in, the audio cable that worked before no longer works. Its as if ubuntu is trying to send the audio via the HDMI cable or something. When I use the VGA cable for video, I get sound, but when I use the HDMI cable for video, even though the audio cable is plugged in, there's no sound. Any ideas?

---

### Post by Hedgehog1 on 2011-04-15
> **Uhura said:**
> Thanks! It was more a case of random trial & error than actually knowing what I was doing or why.
:grin:

Ok looks like I'm stuck with a seperate audio cable for now. There's just one problem though, and that is when I've got the HDMI cable plugged in, the audio cable that worked before no longer works. Its as if ubuntu is trying to send the audio via the HDMI cable or something. When I use the VGA cable for video, I get sound, but when I use the HDMI cable for video, even though the audio cable is plugged in, there's no sound. Any ideas?

This is not unexpected.  Because HDMI was designed to carry video and audio (and other control signals) over a single cable, the hardware/OS is making assumptions.  I think you are stuck with VGA cable and Audio cable(s) for now.  I went all HDMI and had to update a fair amount of AV equipment to do it.  It is convenient, but it was **not** cost-effective.


***The Hedge*** (with the big TV)

:KS

---

### Post by Uhura on 2011-04-16
That's a pain! The VGA cable is big & ugly, & needs an adapter to fit the socket on the pc, all of which means the pc has to stick out at least 2 inches further than it does with the HDMI. Plus the audio cable has to plug in at the front and loop back round to the side of the TV. Grrr. I'm a cable-phobe :wink:
Ah well, thanks for the help with the video resolution :razz:

---

### Post by mbs72 on 2011-04-16
> **lindomsd said:**
> Ubuntu us detectecting the audio chipset as the incorrect type and to fix it you need to change the file /etc/modprobe.d/alsa-base.conf – the last line that currently reads: 

options snd-hda-intel power_save=10 power_save_controller=N

should be:

options snd-hda-intel model=generic power_save=10 power_save_controller=N

Reboot and the audio works.

I just added this string and got sound over HDMI (video card NVIDIA GeForce GTS 450). Something is wrong with quality and signal level (it's low), but I got it. So, thank you.

---

