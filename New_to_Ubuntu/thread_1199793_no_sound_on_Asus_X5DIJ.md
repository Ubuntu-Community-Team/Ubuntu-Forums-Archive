---
title: "no sound on Asus X5DIJ"
date: 2009-06-29
forum: New to Ubuntu
---

### Post by DIDI2002 on 2009-06-29
Hi  users,
I just installed Ubuntu 9.04 on my laptop, an Asus X5DIJ, and everything is working fine, but sound. There is a volume bar in the systray, but there's just no audible sound.
The laptop seems to be using an Intel GM45 chipset...should be quite common, so i suppose it's supported by Ubuntu.

I'll gladly take any advice to get my sound up and running.

thanks in advance.

didi2002

---

### Post by LowSky on 2009-06-29
right click on the icon go to preferences, and enables all the stuff that is not checked. make sure nothing is muted

---

### Post by DIDI2002 on 2009-06-29
Hi Lowsky, thanks for your help.
I checked all options to show up in the mixer, unmuted them all and turned everything up to 100%, including 'main', 'front' and 'pcm', but when i play an mp3 file or click the "test" button in the sound options, there's just no sound.
Ubuntu works great on my desktop machine, but i never experienced sound problems before (sound is working on Windows xp btw, so the hardware is working fine)

---

### Post by halitech on 2009-06-29
whats the output of
```
lshw -C sound
``` and [code]aplay -l{/code]

---

### Post by DIDI2002 on 2009-06-29
```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: VT1708S Analog [VT1708S Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1

```

and 

```

lshw -C sound
  *-usb                   
       description: Video
       product: CNF7129
       vendor: Chicony Electronics Co., Ltd.
       physical id: 3
       bus info: usb@1:3
       version: 15.15
       serial: SN0001
       capabilities: usb-2.00
       configuration: driver=uvcvideo maxpower=500mA speed=480.0MB/s
  *-multimedia
       description: Audio device
       product: 82801I (ICH9 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:22 memory:fdef4000-fdef7fff

```

I'm confused that it shows a USB device, as i dont have anything plugged into my USB ports as of now

regards

didi2002

---

### Post by halitech on 2009-06-29
there is some info here on that chipset

[http://ubuntuforums.org/showthread.php?t=1189124](http://ubuntuforums.org/showthread.php?t=1189124)

---

### Post by DIDI2002 on 2009-06-29
[LEFT]Ok, i read through [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto), but I still didn't notice any reason for my sound not to work.

```
cat /proc/asound/card0/codec#* | grep Codec
Codec: VIA VT1708S

```But i have no idea what "model" option this would imply..maybe Asus?

I googled my sound card, and it's listed on 
[http://www.alsa-project.org/main/index.php/Changes_v1.0.17_v1.0.18](http://www.alsa-project.org/main/index.php/Changes_v1.0.17_v1.0.18)

```
ALSA: HDA patch_via.c: Add VT1708S and VT1702 support

```So it should work somehow, right?

*edit*: I just updated to ALSA 1.0.20 , following this guide: [http://ubuntuforums.org/showthread.php?p=6589810](http://ubuntuforums.org/showthread.php?p=6589810)
still no sound :(

```
alsactl -v
alsactl version 1.0.20

```
[/LEFT]

---

### Post by DIDI2002 on 2009-07-01
yeah i got it
use hda_analyzer and turn on EADP in the node 0x1c
sad thing is, it only works for the current session, but i'm trying to figure out how to set this in patch_via.c

---

### Post by henrywsu on 2009-07-16
your solution is exactly dead on to fix the problem:

1. install 9.0.4
reboot
2. update package via update manager
reboot
3. apt-get install build-essential
reboot
4. update alsa package, tried a few times (AlsaUpgrade-1.0.x-rev-1.17.sh)
reboot
5. run hda_analyzer ([www.alsa-project.org/main/index.php/HDA_Analyzer](www.alsa-project.org/main/index.php/HDA_Analyzer))
6. Turn on EAPD to on on 0x1c, say no to revert

However, have you been able to make any progress on doing the last step in a more automated fashion?

---

### Post by Erdnal on 2009-07-22
Hello, i have the same computer, the same problem.
The solution with the EAPD turned on worked but no completely.
A while after the beginning of a song or of a video, the sound turn off automatically but it seems that it's doing it only with VLC.
Anyway, is there a way to automatize ?
Nobody finds this way ?

---

### Post by Erdnal on 2009-07-22
nobody know how to automatize that ?

---

### Post by Erdnal on 2009-07-23
I find the way to automatize that manipulation.
Download and decompress that [(http://www.megaupload.com/?d=THJMRYIL)]("http://www.megaupload.com/?d=THJMRYIL") in a folder.
Go to System>Preferences>Applications on Startup and add this " sudo '/path/hda-analyzer/hda_analyzer.py' "

After a reboot, it will ask for your password but EAPD will be automatically checked.

Thanks to obiwankennedy

---

