---
title: "Sound stopped, sound card and ship are ok"
date: 2009-08-02
forum: New to Ubuntu
---

### Post by Commisar Jimp on 2009-08-02
My sound has been fine, but I left my computer on last night like I always do, and when I woke it up, the sound was gone, all I can hear is a faint crackling static-y sound when sound would normally play. When I entered aplay -l in the terminal it read:
card 0: NVidia [HDA NVidia], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
So I think that means it can read my sound card and chip, NVidia and ALC888. I'm pretty sure the driver for this is snd-hda-intel, but when I entered: sudo modprobe snd-hda-intel, all I got was:
WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.
I think that that means the driver is the problem, I'm not sure though.
btw, I checked the alsamixer, my speakers, and the mixer icon in the top right corner, everything is plugged in turned on and unmuted. The headphones don't work, but they never have, I assume this is because alsamixer says that the headphone jack is off, and I don't know how to change that, so I haven't been able to test whether the sound is ok with the headphones.

---

### Post by MTGap on 2009-08-02
I've had times where sound would stop, try restarting xserver (log out of your current session). That might do the trick.

---

### Post by jacklinux on 2009-08-02
> **MTGap said:**
> I've had times where sound would stop, try restarting xserver (log out of your current session). That might do the trick.
Same here, i normally have to reboot though

---

### Post by Commisar Jimp on 2009-08-02
I just rebooted, but there's still no sound. Also when song bird started up it said that it couldn't read any of my music files, specifically it said:
Your watch folder at (/media/SimpleDrive/Music) is no longer available. No changes will be made to your library but the tracks contained in your watched folder will no longer play until the watched folder becomes available again.
I'm pretty sure thats just a problem with the external hard drive I've been using the keep my music on and that it shouldn't be to hard to fix, but it started doing that this morning at the same time my sound went down so I thought I'd mention it in case they are related.

---

### Post by MTGap on 2009-08-02
Hmm... well can you try some different speakers, or possibly try them somewhere else...

---

### Post by Commisar Jimp on 2009-08-02
> **MTGap said:**
> Hmm... well can you try some different speakers, or possibly try them somewhere else...
if by some where else you mean plug them into different locations on my sound card, I've done that, all I got was some static in some of them, and silence in all the others.

---

### Post by jacklinux on 2009-08-02
> **Commisar Jimp said:**
> My sound has been fine, but I left my computer on last night like I always do, and when I woke it up, the sound was gone, all I can hear is a faint crackling static-y sound when sound would normally play. When I entered aplay -l in the terminal it read:
card 0: NVidia [HDA NVidia], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
So I think that means it can read my sound card and chip, NVidia and ALC888. I'm pretty sure the driver for this is snd-hda-intel, but when I entered: sudo modprobe snd-hda-intel, all I got was:
WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.
I think that that means the driver is the problem, I'm not sure though.
btw, I checked the alsamixer, my speakers, and the mixer icon in the top right corner, everything is plugged in turned on and unmuted. The headphones don't work, but they never have, I assume this is because alsamixer says that the headphone jack is off, and I don't know how to change that, so I haven't been able to test whether the sound is ok with the headphones.
All i could say now is to remove all the drivers and then re-update them.

---

### Post by Commisar Jimp on 2009-08-02
How do I do that?

---

### Post by MTGap on 2009-08-02
Uh no try them on another computer if possible. Usually things don't die forever while your computer is still on. (They might stop working momentarily like I've experienced often)

---

### Post by jacklinux on 2009-08-02
> **Commisar Jimp said:**
> How do I do that?
im not 100% sure, its in the hardware section of ubuntu i think.

---

### Post by Commisar Jimp on 2009-08-02
> **MTGap said:**
> Uh no try them on another computer if possible. Usually things don't die forever while your computer is still on. (They might stop working momentarily like I've experienced often)
I just tried my speakers on a different computer and they were fine, so the problem is on my machine. 
I also just looked through the menus for drivers, and the only thing that looked promising was "Hardware Drivers" but the only driver it had was for my graphics accelorator. (I'm downloading it, but I doubt it'll help my sound problem;)) in the mean time I'll keep looking.

---

### Post by gorgon on 2009-08-02
Hi there,

I think what jacklinux meant by reinstalling the drivers was to reinstall the alsa packages.

maybe you have read this:
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

it's very comprehensive and much, but if you're impatient you could scroll almost halfway down to the 'Refreshing/Reinstalling the drivers' part. If it has worked previously than that kind of reset should do..

hope that helps!

---

### Post by jacklinux on 2009-08-02
> **gorgon said:**
> Hi there,

I think what jacklinux meant by reinstalling the drivers was to reinstall the alsa packages.

maybe you have read this:
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

it's very comprehensive and much, but if you're impatient you could scroll almost halfway down to the 'Refreshing/Reinstalling the drivers' part. If it has worked previously than that kind of reset should do..

hope that helps!
Bingo! :D. thanks for clearing that up Gorgon

---

### Post by Commisar Jimp on 2009-08-02
I tried reinstalling the drivers but that didn't work, then I followed jacklinux's link to the sound troubleshooting page and followed their directions. It didn't fix the sound problem, however, at one point it had me run:wget -O alsa-info.sh [http://alsa-project.org/alsa-info.sh](http://alsa-project.org/alsa-info.sh) && bash ./alsa-info.shThat compiled a webpage with information on my sound setup, and one part said this:

!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes

ESound Daemon:
      Installed - Yes (/usr/bin/esd)
      Running - No
I'm not sure what the ESound Daemon is, but it seems like it would be importent to[FONT=Verdana] have it running, does anyone know how this is done?[/FONT]

---

