---
title: "No sound in flash 64bit"
date: 2011-06-07
forum: New to Ubuntu
---

### Post by faint545 on 2011-06-07
I just recently installed Kubuntu 11.04 (64 bit) and I really like it. Only problem is that I cant seem to get the audio in adobe flash to work. I downloaded the 64 bit version of adobe flash from the Adobe website and moved it to my **.mozilla/plugins** folder in my home directory.

I have searched Google for people who have the same issues but none of the solutions seem to work. Can someone help? Also, sound card I am using is Creative X-Fi if that is of any relevance.

---

### Post by wolfen69 on 2011-06-07
There's no sounds issues other than that?

---

### Post by faint545 on 2011-06-07
Correct. There is no sound when I try to play videos from YouTube on Firefox and Chrome.

---

### Post by wolfen69 on 2011-06-07
See this. [http://ubuntuforums.org/showthread.php?t=1777188](http://ubuntuforums.org/showthread.php?t=1777188)

---

### Post by faint545 on 2011-06-07
That flash-aid add on did not help my situation. Also, I am starting to think this issue is related to my configuration. I have Kubuntu 11.04 64 bit installed on my laptop and the audio works fine with flash. My desktop however has multiple audio cards installed so maybe somewhere the audio is being sent to the wrong device?

My desktop has 1 embedded audio card, 1 PCI-e audio card and a USB headset (Logitech G35) which has it's own audio card built in (i believe).


**EDIT**: 

My suspicions were spot on. I plugged my speakers into my embedded audio card and audio was now working when playing flash videos.. So now my question is how do I fix this? I want audio from flash videos to be sent to my Creative X-Fi card.

---

### Post by el_koraco on 2011-06-07
> **faint545 said:**
> 
My suspicions were spot on. I plugged my speakers into my embedded audio card and audio was now working when playing flash videos.. So now my question is how do I fix this? I want audio from flash videos to be sent to my Creative X-Fi card.

Yup, that's a problem with some devices and pulseaudio in Kubuntu. I couldn't get flash audio to play through my USB speakers either. You can try to go to System Settings - Multimedia - Phonon, and mess around with the configuration, or you can install padevchooser and Gnome Alsamixer and see if you'll get any results there (padevchooser should help, I think).

---

### Post by superpbeck on 2011-06-07
I had a similar issue with mine.  I installed padevchooser and tinkered around with it and got it to work... partially.  I have a logitech 5.1 speaker system and it's hooked up optically to my monitor, which is then HDMI to my laptop.  Anyway, got it work, but will only play out of two of my speakers.  It wasn't until I downloaded flash 64 bit that I was having problems with sound on the internet.

---

