---
title: "Ubuntu 9.10: Microphone Crackling"
date: 2009-12-19
forum: New to Ubuntu
---

### Post by kestal on 2009-12-19
Hi! I need help.

In Jaunty, My microphone was fine for the most part, but decided to install Ubuntu 9.10 (Fresh Install). I am up to date as of right now and I am hearing crackling when I try recording from my microphone in any program. Please help.

I set the settings in alsamixer to max. My motherboard is the M3A78-CM and the sound card is built in. Its  "onboard 8-channel HD audio (High Definition Audio, previously codenamed Azalia)".

Is there anything I can do about this? any commands to test to see if something is not working properly?

---

### Post by mikewhatever on 2009-12-19
I used to have the same issue on a netbook, but with Jaunty. Having read through this howto ->[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578), I changed the settings is /etc/pulse/daemon.conf to the following, and voila, no more crackling.
```
default-fragments = 6
default-fragment-size-msec = 20
```

---

### Post by MADcat1990 on 2009-12-31
Sorry to be reviving an old thread, but I have the same problem, I tried your solution, and I still have the problem... I can record a sample if it helps.

---

### Post by supermario641996 on 2010-08-16
Hi I have the same issue.  Did you ever fix it?

---

