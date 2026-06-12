---
title: "Mic problems on Dell Inspiron 1420"
date: 2008-12-16
forum: New to Ubuntu
---

### Post by ulftomas on 2008-12-16
Have been running Ubuntu for a month now and I am bugged by a nasty problem. The microphone doesn't work, and I've been trying what feels like a million solutions and visit countless threads on this problem - but still nothing. It is primarily for Skype I need it, but nothing seems to work (sound out does work but sound in doesn't) and I think the problem is in Ubuntu and not in the Skype settings.

When I try to run:

**arecord -f cd trysound.wav**

I get the following:

[B]ALSA lib pcm_dmix.c:813: (snd_pcm_dmix_open) The dmix plugin supports only playback stream
arecord: main:546: audio open error: Invalid argument[/B]
	 	
I tested the following proposals for solutions:
- Change the bolts back and forth in Alsamixer.
- Changed **asoundconf** *set-default-card* to the only one listed; "Intel".
- Added options **snd-hda-intel model=auto** in */etc/modprobe.d/alsa-base* according to [https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto") (according to another site it should be **model=ref**, but it doesn't work - and also stops my speakers to work. I've also tried **model=dell-m26** but with the same result as **model=auto**)
- Closed all programs that possibly could block the sound (including Firefox)

I use a laptop from Dell, which has a built-in mic. I am not interested in using that however, for I have a headset I want to use. Right now, neither the built-in mic or my headset works.

Dell Inspiron 1420

Soundcard: HDA Intel
Chip: SigmaTel STAC9228
Product: 82801H (ICH8 Family) HD Audio Controller

Ubuntu 8.04

---

### Post by Sam Lars on 2008-12-17
Not sure if we have the same card, but it's close.  Try adding model=3stack, it got my mic port working.

---

### Post by ulftomas on 2008-12-17
> **Sam Lars said:**
> Try adding model=3stack, it got my mic port working.

Nope, that didn't solve it. Same thing happened as with model=ref, the built-in speakers stopped to work aswell. However some things are clearly happening with the audio when I change the info in alsa-base.

---

### Post by starcannon on 2008-12-17
I'll subscribe to this thread, I have a 1420n coming in on the 24th and I'll be updating it to 8.10. If your not solved by then, I'll let you know the mic solution when I get to that point; if I remember correctly I just had to futz around with the settings in System>Preferences>Sound in order to get the mic working with sky when I loaded 7.10 on it. I have noted that skype(much as I love using it) is a pita and what works today may not work tomorrow.

GL

---

### Post by Sam Lars on 2008-12-17
There's lots of info [here]("http://ubuntuforums.org/showthread.php?t=616845"), if any of it helps.

---

### Post by ulftomas on 2009-01-27
Found the solution. I have following in alsa-base: options snd-hda-intel model=auto

and then followed the instruction on **[this site]("http://davestation.wordpress.com/2008/07/12/how-to-enable-digital-microphone-array-on-dell-inspiron-laptops-in-ubuntu-804/")** to get the Array Microphone to work

and **[this one]("http://neucessor.wordpress.com/2008/07/28/enable-internalexternal-microphone-inspiron-1420-on-ubuntu-804/")** to get the Input Microphone to work.

---

### Post by mikepre on 2009-03-23
This does not seem to work in Ubuntu 8.10 64 bit.
I have tried everything with no luck.
Every time I change an option in Volume Control (enable mic), the changes are not saved...
Do I need to reinstall pulseaudio?

Thank you

---

### Post by Sam Lars on 2009-03-24
When you have things set like you want them try
```
sudo alsactl store 0
```
in a terminal.

---

### Post by atomkind on 2009-06-13
Thank you!!!!

---

