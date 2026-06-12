---
title: "My new 9.04 XUbuntu install has no sound"
date: 2010-02-04
forum: New to Ubuntu
---

### Post by Chris Edgell on 2010-02-04
I had begun to see the great divide between the new install on Machine #2 (tester) and Machine #1 (primary).

I was realizing that all the packages I'd installed would be missing from the newly installed OS.

While wishing that I HAD kept a list of of all Synaptic Package that I'd installed, I discovered that I had no sound.

---

### Post by Chris Edgell on 2010-02-04
It will be interesting.  I don't know why I didn't take this seriously yesterday; now I see that I'm in the same boat with all those people who couldn't get their sound to work.  I'm lucky that I have another machine while I try to get this figured out.

---

### Post by Rex Bouwense on 2010-02-05
Here you go Christine.  See [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting).

---

### Post by Chris Edgell on 2010-02-05
Thank you, Rex.  It looks like just what I need.  I can hardly wait to sit down and try all this out.

---

### Post by no2498 on 2010-02-05
right click the volume button up top
sound preference try sys sounds first an try diff settings

---

### Post by Chris Edgell on 2010-02-05
no2498, right click on the speaker up top shows a greyed out mixer, greyed out properties...active, I get, move, remove, add new items, customize panels.

I have thoroughly checked the aumixer, the gui for the mixer, and the terminal for alsamixer.

NOW, Rex, I did begin to go through all those instructions...at one point it said 3 packages upgraded, 2 newly installed, 3 to remove, 1 not upgraded.

I found somewhere my sound card" C-Media CM18738 (Alsa Mixer)
Chip:  CMedia PCI

---

### Post by Chris Edgell on 2010-02-06
Okay, I'm going to try to be more precise.  I am thinking about doing a reinstall: but I would like to find out first if it's just my sound card.

Let me print this:

chris@chris-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
card 0: CMI8738 [C-Media CMI8738], device 0: CMI8738-MC6 [C-Media PCI DAC/ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CMI8738 [C-Media CMI8738], device 1: CMI8738-MC6 [C-Media PCI 2nd DAC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CMI8738 [C-Media CMI8738], device 2: CMI8738-MC6 [C-Media PCI IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
chris@chris-desktop:~$

Can anyone glean any facts for me about my sound, from this information shown above?

OR what do you think about this way to go (shall I try it before I try the reinstall...can it hurt?)

Taken from:[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

"Refreshing/Reinstalling the drivers:

Sometimes, sound might be configured correctly, but for some reason or another (tinkering) it stops working. If this is the case, you can purge your custom changes, and restore your system to a clean base. This may clear up your problem, and restore you to a working state.

Open a terminal and type sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2. This will purge any custom configurations that you've made, and any hand-compiled modules that you've built, and restore your sound stack to the "Official" Ubuntu core. You can also do this as two separate steps: sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils and then sudo apt-get install linux-sound-base alsa-base alsa-utils , but this may result in some other packages which depend on the sound-base and alsa-utils from being removed, such as gdm and ubuntu-desktop. If this happens, then do sudo apt-get install gdm ubuntu-desktop."

---

### Post by Chris Edgell on 2010-02-06
I have marked this thread as solved because I have reinstalled.  I don't want to be running two threads on the same subject and so I intend to proceed by asking each question as it comes along.  I'm thinking that maybe it should be in another forum, but it's all such absolute beginner stuff, I'm starting out here and if I get moved...so be it.

---

