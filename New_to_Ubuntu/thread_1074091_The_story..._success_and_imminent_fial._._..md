---
title: "The story... success and imminent fial. . ."
date: 2009-02-18
forum: New to Ubuntu
---

### Post by 3dmoneydotws on 2009-02-18
HI THERE!!

Here is my story:

I have been quad booting Vista, Win 7 Beta, Ubuntu, and Kubuntu for the past month. I decided to Format and go with Kubuntu :yay:

Well I HAD the sound figured out on a thread found here a few days ago, then I formatted, (never writing the thread address down) and I cant find it now GRRRR>

Another Acer 6920 Aspire nightmare... I have searched, and this is my command results... HEEALP! ;) 


ryski3@ryski3-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC889 Analog [ALC889 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
ryski3@ryski3-laptop:~$ cat /proc/asound/devices
  2:        : timer
  3:        : sequencer
  4: [ 0- 4]: digital audio capture
  5: [ 0- 0]: digital audio playback
  6: [ 0- 0]: digital audio capture
  7: [ 0]   : control
ryski3@ryski3-laptop:~$

---

### Post by abn91c on 2009-02-18
did you try maybe sudo modprobe snd-alc889

---

### Post by 3dmoneydotws on 2009-02-18
> **abn91c said:**
> did you try maybe sudo modprobe snd-alc889
\
\
ryski3@ryski3-laptop:~$ sudo modprobe snd-alc889
[sudo] password for ryski3:
FATAL: Module snd_alc889 not found.
ryski3@ryski3-laptop:~$

---

### Post by abn91c on 2009-02-18
page one of this guide worked for me in the past [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by HavocXphere on 2009-02-19
Here is what worked for me in the past:

Most of the time these sound issues are simply that something is muted that shouldn't be.

Run alsamixer in a konsole and make sure nothing is muted. Then rightclick on the sound-control icon at the bottom right of your screen. Select "Select Master channel" and then select the one you want to be controlling. Then open system settings and select sound. Make sure your device is at the top of the list for all the scenarios.

And then select a default device for ALSA:
[QUOTE=Get a list]asoundconf list[/QUOTE]
[QUOTE=Select a default]asoundconf set-default-device [device_name_from_listing_goes_here][/QUOTE]

And finally note that some apps have their output hidden in very funky places. e.g VLC:
Select ALSA in Output module. At bottom left, select Show settings->All. Select Audio->Output Module->ALSA-> And then select your device here. It sometimes forgets this setting...very annoying...but it appears to be a sideeffect of a gtk app running on KDE.

---

