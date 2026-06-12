---
title: "Areas of Weakness"
date: 2008-08-19
forum: Networking &amp; Wireless
---

### Post by alligoodw on 2008-08-19
I have a HP laptop.  I installed Ubuntu 8.4 as a virtual drive in Vista; the installation was flawless.  My wireless wasn't detected and I almost wanted to commit suicide in order to get it up and running.  My solution was to rid myself of Network Manager and install WICD; it worked flawlessly with absolutely no effort.  Although I can see my other computers on my home network, I can't view their folders (shared) and I can't establish a connection with a shared printer.  I'm just looking for simplicity and as of yet, I haven't found it.  Those computers CAN NOT see my Ubuntu system as well.

The world of Nvidia is an entirely different story of its own.  The system defaulted to 800x600 resolution; I wanted to bang my head in the center of my desk.  After trying several suggestions, I eventually ended up with Nvidia-Settings.  It works!  Seeing this is so, why isn't it the default?  Why do I need to look near and far to find it?  After that, I rebooted the system and discovered that Nvidia-Settings didn't save the settings I selected; further reading revealed that I needed to run the program as administrator (sudo). I did so, saved the information and I'll know if it worked this evening when I boot up the system; I'm currently dual booting my laptop.  Would have been better if it just worked.  

I decided to insert a movie.  I knew this would work without a problem.  Wrong!  I was told that I needed to download and install certain codecs.  I did so and it still didn't work.  Would have been better if it just worked.  

Overall, I love Ubuntu.  It would be better, however, if it just worked.  This way, I'll have more time experiencing the system without the hangup of this hardware madness.

---

### Post by tuxxy on 2008-08-19
How did you install the driver and what card are you using?

To view movies you do need codecs for video playbac, one package contains these and a lot of other proprietery extras, search for ubuntu-restricted-extras in synaptic or type in terminal

```
sudo apt-get install ubuntu-restricted-extras
```

---

