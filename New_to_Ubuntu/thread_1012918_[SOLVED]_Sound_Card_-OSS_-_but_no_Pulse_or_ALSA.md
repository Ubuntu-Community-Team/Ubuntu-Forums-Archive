---
title: "[SOLVED] Sound Card -OSS - but no Pulse or ALSA"
date: 2008-12-16
forum: New to Ubuntu
---

### Post by gmgj on 2008-12-16
If I go to System, Preferences sound, if I select OSS, I can get the tests to play; however, that kills Firefox / Flash.

If I try PulseAudio 
So far, If I do  Pulse Audio Volume Control, Output Devices 
 I can show 
ALSA PCM on front:1(VIA 8237) via DMA
ALSA PCM on front:0 (C.. PCI DAC/ADV)
....

But, both the speaker icons remain muted.  Nothing I have done unmutes them.

The VIA 8237 is my onboard sound, its dead. When I swithced that from device 0 to device 1, my new cmedia based card was able to play test sounds.

---------------------------------------------------------------------

I do not know if this is important

[C-Media PCI DAC/ADC]
[C-Media PCI 2nd DAC]
[C-Media PCI IEC958]

I am at a loss as to what to do next?


---------------------------------------------------------------------  


I have tried the steps here today
[https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)

I tried the steps from here yesterday
[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

I have done the steps here:
[http://ubuntuforums.org/showthread.php?t=205449&highlight=startup+sound](http://ubuntuforums.org/showthread.php?t=205449&highlight=startup+sound)

I had the same problem with both sound devices being muted:

 

aplay -l  gives this
**** List of PLAYBACK Hardware Devices ****
card 0: CMI8738 [C-Media CMI8738], device 0: CMI8738 [C-Media PCI DAC/ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CMI8738 [C-Media CMI8738], device 1: CMI8738 [C-Media PCI 2nd DAC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CMI8738 [C-Media CMI8738], device 2: CMI8738 [C-Media PCI IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
  Subdevices: 4/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 1: V8237 [VIA 8237], device 1: VIA 8237 [VIA 8237]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
 
cat /proc/asound/modules   gives this
 0 snd_cmipci
 1 snd_via82xx

Multimedia: 
:C-Media Electronics Inc CM8738 (rev 10) 
:VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)

---

### Post by gmgj on 2008-12-16
If I go here 
[http://www.alsa-project.org/main/index.php/Matrix:Vendor-C-Media](http://www.alsa-project.org/main/index.php/Matrix:Vendor-C-Media)

I see some chipsets in blue and some in black.

the 81738 is in blue; but I am not sure what it means

---

### Post by gmgj on 2008-12-17
I am about to try this:

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

But before I do; I want to try an disable one of my soundcards

I see thi s
"sudo modprobe -r driver_name", you can load it again with "sudo modprobe driver_name"

in [http://ubuntuforums.org/showthread.php?t=1013722](http://ubuntuforums.org/showthread.php?t=1013722).

How do I figure out the driver Name?

---

### Post by gmgj on 2008-12-17
If I do this
sudo lshw

I see
*-multimedia:1
             description: Multimedia audio controller
             product: VT8233/A/8235/8237 AC97 Audio Controller
             vendor: VIA Technologies, Inc.
             physical id: 11.5
             bus info: pci@0000:00:11.5
             version: 60
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: driver=VIA 82xx Audio latency=0 module=snd_via82xx


         *-multimedia:0
             description: Multimedia audio controller
             product: CM8738
             vendor: C-Media Electronics Inc
             physical id: 8
             bus info: pci@0000:00:08.0
             version: 10
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=C-Media PCI latency=32 maxlatency=24 mingnt=2 module=snd_cmipci

If I do this, I see
 modprobe -l 
lib/modules/2.6.27-9-generic/kernel/sound/pci/snd-cmipci.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/snd-via82xx.ko

So, I try

(sudo modprobe -r driver_nam)
sudo modprobe -r snd-via82xx


and it says FATAL: Module snd_via82xx is in use.

My default soundcard is CMIPCI.

How do I disable this card?  It does not work, but its on my MOBO so its not just a matter of opening the case and pulling the card

---

### Post by gmgj on 2008-12-17
Finally,  I went into my BIOS and disabled the "AC97 Controller"  aka my VIA soundcard. I get system sounds, I get Firefox flash sounds.  Yippe!

---

