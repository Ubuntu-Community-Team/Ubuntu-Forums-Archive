---
title: "Ubuntu 9.04 No sound HP 6735s"
date: 2009-07-23
forum: New to Ubuntu
---

### Post by bresdog on 2009-07-23
Evening chaps, i've already read through a tonne of other stuff regarding this. I installed Jaunty Jackalope on my laptop last night and since then i haven't been able to get any sound through the speakers but i can get sound when using headphones. I'll list  the threads i've already read through-

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)
[http://ubuntuforums.org/showthread.php?t=1088978](http://ubuntuforums.org/showthread.php?t=1088978)
[http://ubuntuforums.org/showthread.php?t=1052754&page=4](http://ubuntuforums.org/showthread.php?t=1052754&page=4)
[http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568)

Any other suggestions would be really appreciated.

Cheers

---

### Post by jimmy the saint on 2009-07-23
fire up a terminal and type
```
alsamixer
```

The interface looks primative, but I find that different channels are sometimes listed that don't show up in Ubuntus volume dialog.  Use the directional buttons to move left and right to select different channels and up and down to rais an lower the volumes.  If you see any that are all the way down, try raising them up, if you see any that have and m at the bottom, use the space bar to try to unmute it.  

I just put debian on a thinkpad and there is a hidden channel all the way to the right that is off by default for some reason.  

This may not turn out to be the problem, but both times I had no sound after an installation, this turned out to be the problem... after hours looking for a more complicated issue of course!

Good Luck.

---

### Post by bresdog on 2009-07-23
Tried it, put everything up full and unmuted the three channels that were muted and still no sound from the speakers. :confused:

---

### Post by bresdog on 2009-07-23
This is a complete stab in the dark, but if i hover over the volume control icon it says Beep:then whatever % the volume is at. Shouldn't that say Front? Also tried Kill Pulseaudio, and uninstalling it and no luck.

---

### Post by bresdog on 2009-07-24
Sorry for bumping this, but im almost finished work and id like any suggestions you can think of, so i can give them a go when i get home.

Thanks.

---

### Post by bresdog on 2009-07-26
Anyone?

---

### Post by bresdog on 2009-07-26
Anyone please? Not having any sound is a pain.
Thanks

---

### Post by bresdog on 2009-07-30
Could anyone point me in the right direction regarding this. I’ve been through all the troubleshooting threads and tried different things that were suggested, a lot of it was quite contradictory. Any suggestions would be great thanks.

---

### Post by bresdog on 2009-07-30
Got it sorted. If anyone else is running a HP laptop and having difficulty with sound i suggest following this guide. Seems to work for most HP models and Hardy, Intrepid and Jaunty.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/269027](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/269027)

---

### Post by daimaru on 2009-07-30
eventhough you solved it. did you try using the "PulseAudio Device Chooser" ? just go to playback tab righclick and send output to your speakers or headphones. worked great for me .

---

### Post by bresdog on 2009-07-31
I did try that and it made no difference. This seems to be a recurring problem on Hp laptops, found a few other sites with lots of people in the same boat, only getting sound through headphones. Tried every suggestion on these forums i could find but the problem remained, it turned out that after editing sudo gedit /etc/modprobe.d/alsa-base.conf and adding -

options snd-hda-intel model=mobile

There was one more thing needed to get the integrated speakers to work. Edit sudo gedit /etc/modprobe.d/options and add -

options snd-hda-intel model=mobile

Then reboot. Id done the first step a few times, changing the model to acer/dell/hp but i didn't know about the last step. It definitely helped. Only problem was the sound was very choppy for a while, to resolve that i used sudo killall pulseaudio and that helped.

---

