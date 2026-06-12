---
title: "[SOLVED] No Sound in Ubuntu 8.10"
date: 2009-01-08
forum: New to Ubuntu
---

### Post by delpol on 2009-01-08
I am new to ubuntu, just installed ver. 8.10 and updated the system. I want to learn LINUX due to my job. I am liking it already.

I am having issues with my sound. There is no sound in my system. My onboard sound card is recognized as per the command line when i checked. volume is all full and speakers are in working condition and turned on.

Please assist me in get this sound going in my new system. I have "XFX nForce 680i LT SLI" motherboard with onboard sound "nvidia"

I am new so please if someone can please assist me step by step that would be much appreciated.

thanks
rmbrar

---

### Post by Tim Sharitt on 2009-01-08
The problem for mos people running 8.10 seems to be pulseaudio. Switching to alsa may get you going. First go to System > Preferences > Sound. Every thing is probably set to Autodetect. Change your playback options to ALSA and hit the test button to see if that works. If it does work, you should be good to go.

There are ways to get PulseAudio working for various card. If you want ot get it working you should be able to find a way to get it going by searching the forums.

If switching to ALSA doesn't fix your problem, post back and I'm sure someone can give you some guidance.

Welcome to Linux and good luck!

---

### Post by rmallett on 2009-01-08
This may sound dumb, but I had major issues with getting my sound to work even though all drivers and hardware claimed to be fine... I plugged my speakers into a different set of inputs in the back of the computer (which I had never used in years of having this computer) and it worked. 

But I reinstalled ubuntu and played with alsa for hours before I tried this...

---

### Post by bwoods_finest on 2009-01-08
> **Tim Sharitt said:**
> The problem for mos people running 8.10 seems to be pulseaudio. Switching to alsa may get you going. First go to System > Preferences > Sound. Every thing is probably set to Autodetect. Change your playback options to ALSA and hit the test button to see if that works. If it does work, you should be good to go.

There are ways to get PulseAudio working for various card. If you want ot get it working you should be able to find a way to get it going by searching the forums.

If switching to ALSA doesn't fix your problem, post back and I'm sure someone can give you some guidance.

Welcome to Linux and good luck!
naa alsa did not really work for me... i switched it to oss and it worked fine... thanks a a lot.. i finally have sound on ubuntu

---

### Post by Tim Sharitt on 2009-01-08
> **bwoods_finest said:**
> naa alsa did not really work for me... i switched it to oss and it worked fine... thanks a a lot.. i finally have sound on ubuntu
Good point, oss usually works when all else fails. Atleast that has been my experience.

---

### Post by kansasnoob on 2009-01-08
> **rmallett said:**
> This may sound dumb, but I had major issues with getting my sound to work even though all drivers and hardware claimed to be fine... I plugged my speakers into a different set of inputs in the back of the computer (which I had never used in years of having this computer) and it worked. 

But I reinstalled ubuntu and played with alsa for hours before I tried this...

Been there and done that more than once :redface:

---

### Post by kansasnoob on 2009-01-08
Outside of being plugged in wrong, I'd start here:

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by delpol on 2009-01-09
I tried selecting the OSS and when i click on test, all i hear is continuous beep. i tired playing a radio station or you tube still there is no sound. Now its bit annoying. can this be resolved somehow. i still have issues with setting up email, thats gonna be next chapter.
please help

thanks

---

### Post by Tim Sharitt on 2009-01-09
> **delpol said:**
> I tried selecting the OSS and when i click on test, all i hear is continuous beep. i tired playing a radio station or you tube still there is no sound. Now its bit annoying. can this be resolved somehow. i still have issues with setting up email, thats gonna be next chapter.
please help

thanks
The continuous beep is what you should here when you click test.

---

### Post by WitchCraft on 2009-01-09
You need to recompile the latest alsa driver.

[http://ubuntuforums.org/showthread.php?p=4011326](http://ubuntuforums.org/showthread.php?p=4011326)

[ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.18a.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.18a.tar.bz2)

---

### Post by delpol on 2009-01-09
> **kansasnoob said:**
> Outside of being plugged in wrong, I'd start here:

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)
i tried this method and it worked. thanks a lot kansasnoob.

---

