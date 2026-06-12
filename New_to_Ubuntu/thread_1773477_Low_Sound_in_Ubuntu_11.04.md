---
title: "Low Sound in Ubuntu 11.04"
date: 2011-06-02
forum: New to Ubuntu
---

### Post by computerandu on 2011-06-02
The sound in Ubuntu 11.04 is almost half of what i get in Windows7.....any idea to get more out of it...

---

### Post by jtarin on 2011-06-02
You should tell us what you have tried.

---

### Post by computerandu on 2011-06-02
> **jtarin said:**
> You should tell us what you have tried.

Honestly I haven't tried anything other than going in to the sound preference and increasing the output volume to max...(is it good for speakers' sound quality?)

---

### Post by pwicken on 2011-07-03
You are not very generous regarding information on your hardware.

However, if sound is about half of that with Windows 7, and your machine does have an integrated microphone I will suspect your Sound Settings-> Hardware-> Profile says Analog Stereo Duplex rather than Analog Stereo Output. Try switching those. 

I thought this should be handled through which application is running. I.e. if Skype or SIP-phone is running it should choose the first and if Totem or Banshee it would choose the latter. That is not happening, at least not for me.

---

### Post by computerandu on 2011-07-04
> **pwicken said:**
> You are not very generous regarding information on your hardware.

However, if sound is about half of that with Windows 7, and your machine does have an integrated microphone I will suspect your Sound Settings-> Hardware-> Profile says Analog Stereo Duplex rather than Analog Stereo Output. Try switching those. 

I thought this should be handled through which application is running. I.e. if Skype or SIP-phone is running it should choose the first and if Totem or Banshee it would choose the latter. That is not happening, at least not for me.

Is it not painful to choose different profiles for different applications? I use both Skype and Banshee...will be a pain to keep changing the profile...

---

### Post by pwicken on 2011-07-04
It is inconvenient. 

Did this work for you? Do you get louder sound when switching these settings?

---

### Post by computerandu on 2011-07-04
> **pwicken said:**
> It is inconvenient. 

Did this work for you? Do you get louder sound when switching these settings?

I am at work..will check it once I'm home...:P

---

### Post by pwicken on 2011-07-05
Just changed my settings back to "Analog Duplex Stereo" so the internal microphone is now activated. 
Fired up Terminal, entered:
```
alsamixer
```
increased Master output and everything seems to be OK. 

Hope you "suffer" the same faith!

---

