---
title: "Brand new user 10.04 microphone issue"
date: 2010-05-07
forum: New to Ubuntu
---

### Post by Toews91 on 2010-05-07
Hey all,

I am brand new to ubuntu, i put it on my desktop and my netbook this week and love it!!  I am having a problem on my netbook though (Gateway LT20 series), I cannot get the built in microphone to work.  I hear static on programs like skype or the sound recorder.  I know the microphone works b/c it works on the system tests, just not in any applications.  I have searched for solutions but I don't understand what most of them are telling me to do.  

I would appreciate any real detailed help for a green Ubuntu user anyone could give!

Thanks!

---

### Post by Arla on 2010-05-07
So, personally I'd start with enabling backports and installing the Alsa backport (under synaptic package manager, select settings > software sources, click the updates tab, and select "Unsupported Updates" reload the available packages, then select the one called "linux-backports-modules-alsa-lucid-generic" and install it, assuming you are running 10.04, otherwise it would be karmic-generic, or something else depending on what version you are running).

That fixed it for my Y450 when I had issues.

---

### Post by Toews91 on 2010-05-07
> **Arla said:**
> So, personally I'd start with enabling backports and installing the Alsa backport (under synaptic package manager, select settings > software sources, click the updates tab, and select "Unsupported Updates" reload the available packages, then select the one called "linux-backports-modules-alsa-lucid-generic" and install it, assuming you are running 10.04, otherwise it would be karmic-generic, or something else depending on what version you are running).

That fixed it for my Y450 when I had issues.

I tried that, and it still didn't work... thank you for the response though... any other suggestions?

---

### Post by Toews91 on 2010-05-08
I got it guys, I needed to uncouple the left and right microphone channels and just use one... after i did that it worked like a charm!

---

