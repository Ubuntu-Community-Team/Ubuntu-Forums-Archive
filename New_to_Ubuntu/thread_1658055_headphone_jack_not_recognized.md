---
title: "headphone jack not recognized"
date: 2011-01-02
forum: New to Ubuntu
---

### Post by philipballew on 2011-01-02
i just installed Ubuntu 10.10 32 on my asus laptop and when i plug in headphones nothing happens and the speakers keep producing sound. any help here would be hot?

---

### Post by cariboo on 2011-01-02
Jack sensing is one of the things the devs are working on for the next release as it doesn't work correctly on all systems. For the time being you can right click on the sound icon in the upper panel and select Sound Preferences->Output, and set the output to headphones.

---

### Post by philipballew on 2011-01-02
so is there no way to get alsa to recognize my jack? if not can i create say a script or item in the menu to quickly change from speakers to headphones without having to go into the sound preferences menu every time?

---

### Post by philipballew on 2011-01-03
anyone?

---

### Post by p110011 on 2011-01-03
My laptop headphones worked but speakers would not turn off. I went into the mixer, ```
alsamixer
``` selected my sound card, arrowed to function and arrowed the levels up or down. The "M" means mute and to toggle this press M key. My speakers now turn off with plug insert. Don't know if it will stay with a reboot, but I'm listening to a Hockey game right now:popcorn:

---

### Post by philipballew on 2011-01-04
thats nice, however my problem is that no sound even comes out of my headphones and keep going through the speakers after the headphones are plugged in.

---

