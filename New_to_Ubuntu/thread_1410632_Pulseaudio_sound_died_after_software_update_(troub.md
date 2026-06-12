---
title: "Pulseaudio sound died after software update (troubleshooting guides did not help)"
date: 2010-02-19
forum: New to Ubuntu
---

### Post by spiffman on 2010-02-19
I've researched the problem profusely and am still pulling my hair out. 

I used to have working sound (Karmic Amd64), then did a software update, which installed little more than a current kernel, linux-image-2.6.31-20, from my previous 2.6.31-19. Now, I open up sound preferences and in output I get "dummy output".

I have followed [[COLOR="blue"]this howto[/COLOR]]("https://help.ubuntu.com/community/HdaIntelSoundHowto") and [[COLOR="Blue"]this other howto[/COLOR]]("https://help.ubuntu.com/community/SoundTroubleshootingProcedure").

As a result, after compiling alsa from source, alsa audio worked again, I could successfully use aplay, alsamixer, and play xmms2 through alsa. HOWEVER pulseaudio still fails miserably, even freezes up many audio applications, like amarok, which I used to use constantly.

my audio device is:

```
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
```

and using the module snd-hda-intel

Thank you in advance!

---

### Post by spiffman on 2010-02-19
Ok, I installed a new kernel (2.6.32.8 ), then I uninstalled pulseaudio, "rm -rf ~/.pulse*", and reinstalled pulseaudio, then rebooted. Now, alsa sound doesn't work. so i recompiled alsa from source, but still no luck

Exhibit A:
```
chai@chai-desktop:~$ aplay -l
aplay: device_list:223: no soundcards found...
chai@chai-desktop:~$ cat /proc/asound/cards 
--- no soundcards ---

```

Exhibit B:
```
chai@chai-desktop:~$ lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
chai@chai-desktop:~$ modinfo snd-hda-intel
filename:       /lib/modules/2.6.32.8/kernel/sound/pci/hda/snd-hda-intel.ko
description:    Intel HDA driver
license:        GPL
...and a bunch of other crap about the snd-hda-intel module
```

the module is loaded, alsa compiled with no problems, lspci can see the audio controller. Audio in sound preferences still shows "dummy audio" as output. what am i missing here?

---

