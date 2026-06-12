---
title: "No Sound Issue"
date: 2009-01-15
forum: New to Ubuntu
---

### Post by sharondenscabbia on 2009-01-15
Hello

Still learning my way around Ubuntu 8.10 on my Toshiba Equium p200-1ed, and I've just come up against a problem and don't know what to do.

Yesterday, my sound was working fine. Now, its not. When I turned it on, there was a crackling sound instead of the start up music. This then happened whenever I tried to do anything with audio, nothing played, just a crackling sound. 

I went into system-preferences-sound and messed around with the options there. It seemed that switching from "autodetect" to "Oss" worked, and the audio was fine, but it keeps going back to that crackling sound, then I go back to sound, mess some more, its fine for a few mins then goes back to crackling.

Theres also something which comes up frequently when I try to test the audio. 

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=music: Could not open audio device for playback. Device is being used by another application.

I know of no reason why it would do this sometimes, and properly test it others. 

Has anybody come across something like this spontaneously occuring before? How could I stop it? 

Thanks,
Sharon

---

### Post by HermanAB on 2009-01-15
You have to go to the OSS project web site and read their forum:
[http://www.opensound.com/](http://www.opensound.com/)

Someone else is bound to have the same problem.

Cheers,

Herman

---

### Post by sharondenscabbia on 2009-01-16
Its not a problem with OSS, 'autodetect' used alsa it seems, and theres something wrong with that...

Sharon

---

### Post by Dumbestcrayon on 2009-01-17
I'm having the same problem. No audio but there is some crackling. I tried with the web browser and with banshee. I restarted and tried again. No change. Even the start up sound is just crackling.

---

### Post by seagullplayer77 on 2009-01-17
> **sharondenscabbia said:**
> Hello

Still learning my way around Ubuntu 8.10 on my Toshiba Equium p200-1ed, and I've just come up against a problem and don't know what to do.

Yesterday, my sound was working fine. Now, its not. When I turned it on, there was a crackling sound instead of the start up music. This then happened whenever I tried to do anything with audio, nothing played, just a crackling sound. 

I went into system-preferences-sound and messed around with the options there. It seemed that switching from "autodetect" to "Oss" worked, and the audio was fine, but it keeps going back to that crackling sound, then I go back to sound, mess some more, its fine for a few mins then goes back to crackling.

Theres also something which comes up frequently when I try to test the audio. 

**audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=music: Could not open audio device for playback. Device is being used by another application.**

I know of no reason why it would do this sometimes, and properly test it others. 

Has anybody come across something like this spontaneously occuring before? How could I stop it? 

Thanks,
Sharon

I've seen the bolded message quite a few times...usually happens when I have Opera open when I'm trying to test audio :P. For whatever reason, having a Web browser open qualifies as having an audio application open, so the test won't work. You might try closing every single program except for the sound configuration utility and see what that gets you.

---

### Post by 00arthuryu on 2009-01-26
Same problem here :(
just crackling
It was working just fine yesterday

---

### Post by mister_p_1998 on 2009-01-26
Kernel update killed sound?
Try pressing escape in the grub menu, & choose an earlier Kernel, I bet the sound suddenly comes vack!

Steve

---

