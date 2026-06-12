---
title: "&quot;Glitchy&quot;, &quot;Jumpy&quot; sound when using speakers"
date: 2009-04-03
forum: New to Ubuntu
---

### Post by Black_Wolf_92 on 2009-04-03
Hey everyone, another new ubuntu user here =) (well not really but this is my first time asking for help)

Basically, since installing ubuntu on my main desktop, the sound, from my memory USED to be fine when using the speakers, however, now everything that comes out of there is "jumpy" or "glitchy" it is difficult to explain. Basically, the correct audio file is playing, but there are gaps, or it is loading to slowly or something

I've never posted for help before, so i'm not sure how to post my symptoms, like what terminal commands you require to help diagnose this, so I placed it in absoloute beginner.

Thanks in advance to anyone who can help =)

---

### Post by mgmiller on 2009-04-03
There is an extensive thread on the forum about fixing sound problems.  Try this:  [http://ubuntuforums.org/showthread.php?t=843012&highlight=sound+problems](http://ubuntuforums.org/showthread.php?t=843012&highlight=sound+problems)

---

### Post by Black_Wolf_92 on 2009-04-03
Thank you for your help. 

I edited the file to changes those fragment options, but i'm not sure if it helped at all, if it did, the issue is not completely gone, but i think there is "less" glitchiness in the playback now.

I forgot to mention that the sound all works PERFECTLY when i plug headphones in, it is ONLY the speakers that have issues

---

### Post by mgmiller on 2009-04-03
Have you tried the speaker plugs themselves where they plug into the motherboard?  Try unplugging and replugging them a few times.  Also try the same for any cables or plugs on the speakers themselves.  

I live in a marine environment with a lot of salt in the air and I find I have to do this from time to time because of slight surface oxidation that builds up on the plugs.  There is a product from Radio Shack called pro-gold that does a good job of preventing (or at least slowing down) this oxidation.

---

### Post by Black_Wolf_92 on 2009-04-03
i thought it could have been connnection, so i booted into windows, but its all working fine there !?

I'll uninstall, reinstall then update alsa and see if i can get it goin. Thanks a lot for your help!

---

### Post by mgmiller on 2009-04-04
Before you reinstall, take a look in System > Preferences > Sound.  

For each of the drop downs for:  Sound Events, Music and Movies and Audio Conferencing, Instead of the default of "Autodetect", try selecting Alsa or one of the other choices available.  They will vary with the sound card you use.  Click the "Test" button and see if the sound is better.  It does not require a reboot, the changes take effect immediately.

---

