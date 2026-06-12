---
title: "Sound has stopped all of a sudden"
date: 2008-12-18
forum: New to Ubuntu
---

### Post by Swerve1000 on 2008-12-18
Hi,

My sound has stopped working all of a sudden.

I'm using 8.10 Desktop

My onboard sound card is a Realtek ALC655 chip.

I get no sound at all, including login.

I did an update (can't remember what though) and it's quite possible that it stopped after this update.

Kernel version is 2.6.27-9-generic

I have gone to System>Preferences>Sound and tried setting all the top 4 settings to autodetect and  ALC655 (ALSA) but it makes no difference.

The hardware works fine in Windows.

I'm pretty stuck, it was working fine before.

If anyone can help me, that would be great.

Many thanks!

---

### Post by lovelyvik293 on 2008-12-18
Open the terminal and use
```

alsamixer

```
You can increase or decrease sound from here.

---

### Post by Swerve1000 on 2008-12-18
Thanks but turning it up won't work. 

When I select SiS SI7012 with ALC655 SiS SI7012 (ALSA)

I get the following:
> 
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: 
Could not open audio device for playback.

---

### Post by Swerve1000 on 2008-12-18
Has anyone else had this problem before? 

I still cannot get sound. Perhaps I need to do a complete re-install :confused:

---

### Post by Swerve1000 on 2008-12-18
> **Open a terminal and type** sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2. **This will purge any custom configurations that you've made, and any hand-compiled modules that you've built, and restore your sound stack to the "Official" Ubuntu core.**

I have tried this and it also has not made any difference, I still no sound at all.


cat /proc/asound/cards

gives:
>  0 [SI7012         ]: ICH - SiS SI7012
                      SiS SI7012 with ALC655 at irq 18

---

### Post by arizonalarry2 on 2008-12-19
Same thing happened to me , I'm going to start working on it tomorrow - here's a post that may help ( post #1272 )- [http://ubuntuforums.org/showthread.php?t=205449&page=128](http://ubuntuforums.org/showthread.php?t=205449&page=128)

---

### Post by Swerve1000 on 2008-12-19
Thanks arizonalarry2,

I will look at this.

I have also filed a bug report about the issue.

---

### Post by gackt on 2008-12-19
No sound at all or there is a buzzing sound (and only that buzzing sound) when you play any sound?

It happen to me too but i get buzzing sound instead of no sound at all, here is what i do:
1. open volume control from sound tray
2. mute all
3. preferences - deselect all
4. get back to preferense, select what you deselect back then
5. increase the pcm and master

That's it.

---

### Post by pmains on 2008-12-19
Is it possible that your permissions got screwed up? You can "cat /etc/group | grep audio" to see if you're a member of the audio group.

---

### Post by deh on 2008-12-19
I have the same problem.  Toshiba Satellite laptop, L355.  Sound quit on me today.  Works fine with Vista.  I tried all the suggestions in the earlier posts with no success.  The little speaker icon in the upper right corner has a red circle with a slash through it.  The sound tests don't produce any sound and they did OK a yesterday.  The only thing that I've done with the Ubuntu was to run ekiga for the first time yesterday evening (and the echo test did not produce any audio), and I think there were some Ubuntu updates last night.

I'm stumped as what to do, other than re-install.

---

### Post by ThrobbingBrain66 on 2008-12-19
Try this link

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by Swerve1000 on 2008-12-21
I know how frustrating it can be.

Here is another thread which may help you, it did me.

[http://ubuntuforums.org/showthread.php?t=1015992](http://ubuntuforums.org/showthread.php?t=1015992)

---

### Post by PhonicLynx on 2008-12-24
Those new patches made my system work for the majority. Things like MPlayer now work again and don't go crackly like they were.

However, Now I have no sound when using FireFox when watching things like you-tube or any other flash. Nor sure if its related or not though... anyone know what could be causing it?

---

