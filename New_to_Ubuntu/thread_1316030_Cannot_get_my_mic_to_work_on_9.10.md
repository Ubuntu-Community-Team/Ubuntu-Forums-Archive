---
title: "Cannot get my mic to work on 9.10"
date: 2009-11-05
forum: New to Ubuntu
---

### Post by Lee2eel on 2009-11-05
Hello, I am brand spanking new to Linux and I need help.

I am unable to get my mic to work on my Acer 5810TZ.  My sound chip is intel g45 devctg.  The sound works fine!

My friend told me to try and install linux-backborts-modules-alsa-karmic packages which I did.  But I still cannot get my mic to work.

I've tried to play with different settings in System > Preferences > Sound > Hardware and tried to change the profiles.

I've also tried to play with the settings in skype to try and make it work.  

I have only been using this for 1 day so please try to explain step by step what I should be doing.


Thank you so much for the help

---

### Post by Lee2eel on 2009-11-05
I think i forgot to mention that I have an internal mic built into the laptop.  Also, I was told to change some settings in alsamixer which also did not solve my problem.

---

### Post by Lee2eel on 2009-11-05
It turns out that the issue was not with my mic, but it was with skype 2.1.  Skype would not allow me to select the propper audio and microphone settings.  I uninstalled skype 2.1 completely then I installed skype 2.0.  Then I was able to select the proper audio and microphone settings.

---

### Post by rvitch on 2010-01-19
hi,

I have 5810 tz too with kunbutu 9.10 (x86_64) 
i can't make working my microphone.
I've try a lots of /etc/modprobe.conf/alsabase.conf options :

p, li { white-space: pre-wrap; }  options snd-hda-intel model=dell-m6
 options snd-hda-intel enable_msi=1 ajoute digital
 options snd-hda-intel enable_msi=1 model=dell-m4-1
 options snd_hda_intel model=5stack
 options snd-hda-intel model=hp-m4 
 alias snd-card-0 snd-hda-intel
 

Can you explain how you make it working and can you post your alsabase.conf please.
Have you 64 bit version?

thank's

---

