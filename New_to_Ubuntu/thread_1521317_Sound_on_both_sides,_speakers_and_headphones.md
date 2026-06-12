---
title: "Sound on both sides, speakers and headphones"
date: 2010-06-30
forum: New to Ubuntu
---

### Post by dreKion on 2010-06-30
Hello friends!

I have searched all they can about this topic in the forum and I think I've tried many of them ...

I have the latest drivers ALSA: 1.0.23

My laptop is an Acer Aspire 8943G Ethos

My Device (ALC670)

```
drekion @ drekion-laptop: ~ $ aplay-l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC670 Analog [ALC670 Analog]
  Gadgets: 1 / 1
  Gadget # 0: subdevice # 0
card 0: Intel [HDA Intel], device 1: ALC670 Digital [ALC670 Digital]
  Gadgets: 1 / 1
  Gadget # 0: subdevice # 0
Card 1: Generic [Generic HD-Audio], device 3: ATI HDMI [ATI HDMI]
  Gadgets: 1 / 1
  Gadget # 0: subdevice # 0
drekion @ drekion-laptop: ~ $
```


Following occurs:

The 5.1 works perfectly but when I connect the headphones several speakers are turned off and stays in 2.1 and is also heard in the headphones ...

I tried to edit / etc / modprobe.d / alsa-base.conf

and I have the following: "options snd-hda-intel model = auto"

Also I tried with "acer", "acer-aspire", "acer-aspire-8940g"

Any ideas?


The driver disk of Win7 says this "Realtek Audio Codec ALC669X"


Solution: [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/656625]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/656625")

---

### Post by fordfrog on 2010-07-19
i have exactly the same problem with kernel 2.6.34 (alsa drivers from kernel) on gentoo. did not find the solution yet either.

---

### Post by dreKion on 2010-08-10
I have the solution!

In model we will write this "[COLOR=#000000][FONT=Times New Roman][FONT=sans-serif]lenovo-101e",

with this the headphones works fine and the speakers are turn off automatic


[/FONT][/FONT][/COLOR]

---

### Post by mbrekk@gmail.com on 2010-08-23
I have also problems with my Acer Aspire 8943G ( no Ethos). It is only sound in left front and left rear speaker. No sound in headphone when jack is plugged in (but still sound in left speakers). I have not been able to get any reaction form the mic or mic-jack either. Have not tried the line-in jack. 

Kernel is 2.6.32-24-generic #41-Ubuntu SMP Thu Aug 19 01:38:40 UTC 2010 x86_64 GNU/Linux.

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: Generic [HD-Audio Generic], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

aplay -L
pulse
    Playback/recording through the PulseAudio sound server
front:CARD=Intel,DEV=0
    HDA Intel, HDA Generic
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, HDA Generic
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, HDA Generic
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, HDA Generic
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, HDA Generic
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, HDA Generic
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
hdmi:CARD=Generic
    HD-Audio Generic, ATI HDMI
    HDMI Audio Output

I have not tried to use the sound on the HDMI port.

Form dmesg
[   11.514953] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   11.515019] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   11.671042] HDA Intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   11.671094] HDA Intel 0000:01:00.1: setting latency timer to 64
........
[   14.444396] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
[ 4522.406817] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.

When i open volume control. I only see left and right channels, no surround channels. 

My windows 7 is overwritten and I am not able to see what what the name of the sound driver, but AlsaMixer v1.0.22 reporting  Realtek ID 670 as the chip.

Is there anybody out there having an idea what to do. Have tried a lot of options in alsa-base.conf, also what suggested in this tread, but nothing seems to help.

---

### Post by mbrekk@gmail.com on 2010-08-23
May be the solution:
[https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules](https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules)

At least i have sound in all speakers and headphones works.
Still I have to make the Mic's work, but it will an other day.

---

### Post by dreKion on 2010-12-01
The solution is here:

[http://people.canonical.com/~diwic/temp/alsa-hda-diwic-acer-8943g-dkms_1.0.23.diwic_all.deb]("http://people.canonical.com/~diwic/temp/alsa-hda-diwic-acer-8943g-dkms_1.0.23.diwic_all.deb")



[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/656625]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/656625")

---

