---
title: "No sound on youtube"
date: 2010-04-18
forum: New to Ubuntu
---

### Post by jonpon on 2010-04-18
Hi Im having bizarre problem with flash files. They dont play in the browser but they play on my desktop. I'm using Firefox 3.0.19 and Epithany (geko) as browsers but they both play videos silent. if I pull a flv file out of my 'tmp' folder onto the desktop it plays fine. Anyone got any idea?

---

### Post by 1991sudarshan on 2010-04-18
> **jonpon said:**
> Hi Im having bizarre problem with flash files. They dont play in the browser but they play on my desktop. I'm using Firefox 3.0.19 and Epithany (geko) as browsers but they both play videos silent. if I pull a flv file out of my 'tmp' folder onto the desktop it plays fine. Anyone got any idea?

may be you should use pulse audio which is there in the audio settings. i faced the problem when i was using the HDA intel audio sound after i switched to the pulse audio everything came back to normal

---

### Post by lidex on 2010-04-18
Reference this post:
[http://ubuntuforums.org/showpost.php?p=9124143&postcount=12]("http://ubuntuforums.org/showpost.php?p=9124143&postcount=12")

---

### Post by lovinglinux on 2010-04-18
I'm not using Gnome right now, but going to "System >> Preferences >> Sound" and changing the video option to ALSA always worked for me.

Also make sure all volume controls are at maximum.

---

### Post by jonpon on 2010-04-18
Thanks a lot guys for the suggestions, I've tried them all, but unfortunately still nothing. I've tried every possible combination of ALSA,OSS and Pulse, some I loose the sound all together and others only in the browser the link suggersted by Lidex made not a peep either sadly.
Funny thing is that Once-upon-a-Time it worked fine.
Hmmmmmm..........
I'm using Ubuntu 8.10 Intrepid (I know, bit old, when I get a faster internet connection I'll upgrade)
Is it possible that the last Firefox update has changed something?

---

### Post by lidex on 2010-04-18
Maybe....purging and removing any traces of flash and then re-installing. Conflicts are fairly frequent. Link:
[http://ubuntuforums.org/showthread.php?t=1414595]("http://ubuntuforums.org/showthread.php?t=1414595")
And have you tried starting firefox with a clean profile?
Alt+F2
```
firefox -P
```

---

### Post by lidex on 2010-04-18
BTW, what do you see in "Tools>Add Ons> Plugins"?

---

### Post by jonpon on 2010-04-19
[SIZE="1"]> **lidex said:**
> Maybe....purging and removing any traces of flash and then re-installing. Conflicts are fairly frequent. Link:
[http://ubuntuforums.org/showthread.php?t=1414595]("http://ubuntuforums.org/showthread.php?t=1414595")
And have you tried starting firefox with a clean profile?
Alt+F2
```
firefox -P
```
[/SIZE]
[SIZE="4"][B]That It!!! The answer was to remove any trace and then re-install. Its working again.
Thank you so much Lidex for your persistence!!![/B]
:D[/SIZE]

---

