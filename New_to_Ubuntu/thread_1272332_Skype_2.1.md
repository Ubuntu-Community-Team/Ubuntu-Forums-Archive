---
title: "Skype 2.1"
date: 2009-09-22
forum: New to Ubuntu
---

### Post by hifly1231 on 2009-09-22
I can only get Skype 2.1 to give me the option of PulseAudio.  I use my Logitech USB Wireless Headset with Skype, which runs through ALSA.  How to I get Skype 2.1 to give me the option of choosing an ALSA sound device?  HELP!!!

---

### Post by meborc on 2009-09-22
> **hifly1231 said:**
> I can only get Skype 2.1 to give me the option of PulseAudio.  I use my Logitech USB Wireless Headset with Skype, which runs through ALSA.  How to I get Skype 2.1 to give me the option of choosing an ALSA sound device?  HELP!!!

i was also surprised when there was only one option in the microphone section in skype :)

what i did was install pavucontrol package... launch it and unmute the appropriate mic device

skype working BETTER than ever :D

---

### Post by abhiroopb on 2009-09-22
change your sound settings to ALSA and then select "Default device" in skype options.

---

### Post by meborc on 2009-09-22
> **abhiroopb said:**
> change your sound settings to ALSA and then select "Default device" in skype options.

that is also an option... but since pulseaudio is supposed to replace alsa at some point, it is good to try to get it working using it...

but there is always more than one way of doing things

---

### Post by abhiroopb on 2009-09-22
I've tried everything to get it connected using PulseAudio and even with skype 2.1 the CPU usage for skype and pulse was at a steady 100% (see this thread: [http://ubuntuforums.org/showthread.php?t=1127056](http://ubuntuforums.org/showthread.php?t=1127056)).

So, I removed pulse and installed ALSA

---

### Post by gradinaruvasile on 2009-09-22
> **hifly1231 said:**
> I can only get Skype 2.1 to give me the option of PulseAudio.  I use my Logitech USB Wireless Headset with Skype, which runs through ALSA.  How to I get Skype 2.1 to give me the option of choosing an ALSA sound device?  HELP!!!

You have to remove pulseaudio. Kill the pulseaudio process cause it interferes with alsa apps even if u have ur output set to alsa.

---

### Post by dixelpixel on 2009-10-29
> **gradinaruvasile said:**
> You have to remove pulseaudio. Kill the pulseaudio process cause it interferes with alsa apps even if u have ur output set to alsa.

How do I remove pulse audio? I have managed to make the sound (hearing) work by changing the options to 'pulse' in Skype options. I cannot however record my voice trough Skype's test call. If I change microphone or 'sound out' away from 'pulse' to 'Default Device' in Skype options I get an error message in the Skype interface when I try to make a test call.
I have tested voice recording in Terminal which works perfectly however.


Running Jaunty on a Dell Latitude D610. Skype worked perfectly on the Ubnutnu 7 distro I had before.

---

