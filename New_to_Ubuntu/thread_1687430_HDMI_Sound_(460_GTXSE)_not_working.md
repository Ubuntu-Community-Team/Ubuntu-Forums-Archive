---
title: "HDMI Sound (460 GTXSE) not working"
date: 2011-02-13
forum: New to Ubuntu
---

### Post by yt_l9 on 2011-02-13
I'm unable to get any sound to work via the hdmi on my new video card.  I have 3 sound cards including the onboard -the other is a turtle beach that I had before which works just fine.

It seems to show up as an option but nothing is playing.  It's not muted in alsa mixer as shown in the third picture.

josh@HTPC:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CMI8738 [C-Media CMI8738], device 0: CMI8738-MC6 [C-Media PCI DAC/ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CMI8738 [C-Media CMI8738], device 1: CMI8738-MC6 [C-Media PCI 2nd DAC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CMI8738 [C-Media CMI8738], device 2: CMI8738-MC6 [C-Media PCI IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 7: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 8: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 9: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

josh@HTPC:~$ aplay -L
default
pulse
    Playback/recording through the PulseAudio sound server
front:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, ALC888 Digital
    IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    Direct sample mixing device
dmix:CARD=Intel,DEV=1
    HDA Intel, ALC888 Digital
    Direct sample mixing device
dsnoop:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    Direct sample snooping device
dsnoop:CARD=Intel,DEV=1
    HDA Intel, ALC888 Digital
    Direct sample snooping device
hw:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    Direct hardware device without any conversions
hw:CARD=Intel,DEV=1
    HDA Intel, ALC888 Digital
    Direct hardware device without any conversions
plughw:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    Hardware device with all software conversions
plughw:CARD=Intel,DEV=1
    HDA Intel, ALC888 Digital
    Hardware device with all software conversions
front:CARD=CMI8738,DEV=0
    C-Media CMI8738, C-Media PCI DAC/ADC
    Front speakers
rear:CARD=CMI8738,DEV=0
    C-Media CMI8738, C-Media PCI 2nd DAC
    Rear speakers
surround40:CARD=CMI8738,DEV=0
    C-Media CMI8738, C-Media PCI 2nd DAC
    4.0 Surround output to Front and Rear speakers
surround41:CARD=CMI8738,DEV=0
    C-Media CMI8738, C-Media PCI 2nd DAC
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=CMI8738,DEV=0
    C-Media CMI8738, C-Media PCI 2nd DAC
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=CMI8738,DEV=0
    C-Media CMI8738, C-Media PCI 2nd DAC
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
iec958:CARD=CMI8738,DEV=0
    C-Media CMI8738, C-Media PCI DAC/ADC
    IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=CMI8738,DEV=0
    C-Media CMI8738, C-Media PCI DAC/ADC
    Direct sample mixing device
dmix:CARD=CMI8738,DEV=1
    C-Media CMI8738, C-Media PCI 2nd DAC
    Direct sample mixing device
dmix:CARD=CMI8738,DEV=2
    C-Media CMI8738, C-Media PCI IEC958
    Direct sample mixing device
dsnoop:CARD=CMI8738,DEV=0
    C-Media CMI8738, C-Media PCI DAC/ADC
    Direct sample snooping device
dsnoop:CARD=CMI8738,DEV=1
    C-Media CMI8738, C-Media PCI 2nd DAC
    Direct sample snooping device
dsnoop:CARD=CMI8738,DEV=2
    C-Media CMI8738, C-Media PCI IEC958
    Direct sample snooping device
hw:CARD=CMI8738,DEV=0
    C-Media CMI8738, C-Media PCI DAC/ADC
    Direct hardware device without any conversions
hw:CARD=CMI8738,DEV=1
    C-Media CMI8738, C-Media PCI 2nd DAC
    Direct hardware device without any conversions
hw:CARD=CMI8738,DEV=2
    C-Media CMI8738, C-Media PCI IEC958
    Direct hardware device without any conversions
plughw:CARD=CMI8738,DEV=0
    C-Media CMI8738, C-Media PCI DAC/ADC
    Hardware device with all software conversions
plughw:CARD=CMI8738,DEV=1
    C-Media CMI8738, C-Media PCI 2nd DAC
    Hardware device with all software conversions
plughw:CARD=CMI8738,DEV=2
    C-Media CMI8738, C-Media PCI IEC958
    Hardware device with all software conversions
hdmi:CARD=NVidia,DEV=0
    HDA NVidia, NVIDIA HDMI
    HDMI Audio Output
hdmi:CARD=NVidia,DEV=1
    HDA NVidia, NVIDIA HDMI
    HDMI Audio Output
hdmi:CARD=NVidia,DEV=2
    HDA NVidia, NVIDIA HDMI
    HDMI Audio Output
hdmi:CARD=NVidia,DEV=3
    HDA NVidia, NVIDIA HDMI
    HDMI Audio Output
dmix:CARD=NVidia,DEV=3
    HDA NVidia, NVIDIA HDMI
    Direct sample mixing device
dmix:CARD=NVidia,DEV=7
    HDA NVidia, NVIDIA HDMI
    Direct sample mixing device
dmix:CARD=NVidia,DEV=8
    HDA NVidia, NVIDIA HDMI
    Direct sample mixing device
dmix:CARD=NVidia,DEV=9
    HDA NVidia, NVIDIA HDMI
    Direct sample mixing device
dsnoop:CARD=NVidia,DEV=3
    HDA NVidia, NVIDIA HDMI
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=7
    HDA NVidia, NVIDIA HDMI
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=8
    HDA NVidia, NVIDIA HDMI
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=9
    HDA NVidia, NVIDIA HDMI
    Direct sample snooping device
hw:CARD=NVidia,DEV=3
    HDA NVidia, NVIDIA HDMI
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=7
    HDA NVidia, NVIDIA HDMI
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=8
    HDA NVidia, NVIDIA HDMI
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=9
    HDA NVidia, NVIDIA HDMI
    Direct hardware device without any conversions
plughw:CARD=NVidia,DEV=3
    HDA NVidia, NVIDIA HDMI
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=7
    HDA NVidia, NVIDIA HDMI
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=8
    HDA NVidia, NVIDIA HDMI
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=9
    HDA NVidia, NVIDIA HDMI
    Hardware device with all software conversions


Any help is greatly appreciated.

[IMG]http://i55.tinypic.com/14toizo.png[/IMG]
[IMG]http://i52.tinypic.com/3324fa0.png[/IMG]
[IMG]http://i55.tinypic.com/287ghue.png[/IMG]

---

### Post by Hedgehog1 on 2011-02-13
I don't see the 'HDA NVidia' in the : Preference >> Sound >> Output.

Do you have the Proprietary NVidia driver loaded?  The open source ones do not support audio over HDMI for NVidia cards.

I have never tried this with 3 sound cards - you are in new territory for me.

---

### Post by yt_l9 on 2011-02-14
Yes, I'm using the proprietary drivers from nvidia.  You can just ignore the other two cards as they aren't in use for the Ubuntu system; I'm dual booting and actually considering giong triple.  I've always wanted to use FreeBSD- but that's neither here nor there.  =D

The hdmi out should be the only one there, gt140 or whatever it is, as I've disabled the others.  Of course I'm at work and it's not showing the images so I can't say for certain the exact name.  If I enable the other two then I will have all three show up as options.  I know the other ones are the on-board and turtle-beach riveriera which worked before I got my new graphics card.

Here is the card if it helps any. (which I got because I read it worked the best out of the box with Ubuntu somewhere, and it sort of does.)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16814261088](http://www.newegg.com/Product/Product.aspx?Item=N82E16814261088)

Not that it matters too much but this pc is attached to the living room tv so I use it for movies with boxee.  The only thing I can come up with is purchasing a receiver and having everything go through that while using the optical sound port from my Riviera sound card.

I don't want to remove the Riviera quite yet because I'm planning on using it for my other OS but if I have to then I suppose I have to.

---

### Post by Hedgehog1 on 2011-02-14
yt_l9,
 
I know this can be done.  My GT430 card is feed video/audio into the Samsung TV, and thene the samsung TV feeds the audio via HDMI to the reciever using the ARC (Audio Return Channel).
 
The thing is - I only get sound to out of HDMI when I select the HDA nvidia output device.

---

### Post by yt_l9 on 2011-02-15
are you telling me that the gf104 hdmi device is not what I need to select as the primary output device?  That's the only hdmi I have on the computer so I'm a little confused as to where else to turn.  I tried messing around with Alsamixer, I even reinstalled the alsa files.  Do you have any idea what else I could try?  

As far as I can see the system see's something as my hdmi output and I'm assuming it's correct.  I've set it as the main, only actually, output source but I still get no sound at all.  Any help is greatly appreciated.

---

### Post by Jos31 on 2011-10-08
Hi,

Solved this issue by finding the working device with aplay
```

jos@maxou:~$ aplay -l
**** Liste des Périphériques Matériels PLAYBACK ****
carte 0: SB [HDA ATI SB], périphérique 0: VT1818S Analog [VT1818S Analog]
  Sous-périphériques: 2/2
  Sous-périphérique #0: subdevice #0
  Sous-périphérique #1: subdevice #1
carte 0: SB [HDA ATI SB], périphérique 1: VT1818S Digital [VT1818S Digital]
  Sous-périphériques: 1/1
  Sous-périphérique #0: subdevice #0
carte 1: NVidia [HDA NVidia], périphérique 3: HDMI 0 [HDMI 0]
  Sous-périphériques: 1/1
  Sous-périphérique #0: subdevice #0
**carte 1: NVidia [HDA NVidia], périphérique 7: HDMI 0 [HDMI 0]**
  Sous-périphériques: 0/1
  Sous-périphérique #0: subdevice #0
carte 1: NVidia [HDA NVidia], périphérique 8: HDMI 0 [HDMI 0]
  Sous-périphériques: 1/1
  Sous-périphérique #0: subdevice #0
carte 1: NVidia [HDA NVidia], périphérique 9: HDMI 0 [HDMI 0]
  Sous-périphériques: 1/1
  Sous-périphérique #0: subdevice #0

```

I've tried all the combinaison to find the working one:
```

aplay -D **plughw:1,7** /usr/share/sounds/alsa/Front_Left.wav

```

Once found (here card 1, device 7), i've done this:

```

echo "defaults.pcm.device **7**" >> .asoundrc

```

Then reboot, and HF :)

---

