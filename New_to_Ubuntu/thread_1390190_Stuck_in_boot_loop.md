---
title: "Stuck in boot loop"
date: 2010-01-25
forum: New to Ubuntu
---

### Post by lzd on 2010-01-25
I was getting no sound in YouTube while watching a movie in VLC so I read that pulseaudio was the problem so I did the instructions in a thread about safely removing it and didn't notice much a difference. So I went into synaptic and removed libpulse0 and a long list of other with it since I couldn't access sound in preferences and read to remove pulseaudio in synaptic. Still no difference. So I just searched for sound and removed I think libjack0 because it said it allowed multiple applications to use the sound card at once so I thought that there was a small chance it would help and still nothing. 
 
Then I tried to restart using the upper right menu and it didn't do anything so I had to push the power button and select restart from the menu that popped up. It restarts and the screen flashes then it prompts me to log in and I enter the correct password and it goes to the bootup screen again then back to the login prompt and it's stuck in this endless loop. After messing around in recovery mode then trying to login again instead of a login prompt it gives me the option to start in low graphics mode then it says dev/fb0 not found and back to the loop. What do I do?

---

### Post by beauty. proletariat on 2010-01-25
That happened to me once, though I was messing with graphics drivers. Stuck in login loop.

I did a keyboard bash (no, not the command XD) and it got fixed o.o

>.> i suck, nothing to contribute really >.<

---

### Post by lzd on 2010-01-25
I think it might have somehow messed with the graphics drivers when I uninstalled libpulse0.

---

### Post by lzd on 2010-01-25
Any help?

---

### Post by gnack on 2010-01-25
Check the xorg log to see if reports anything useful:

/var/log/Xorg.0.log

> So I went into synaptic and removed libpulse0 and a long list of > other...

Do you remember what the "long list of other" included?

---

### Post by lzd on 2010-01-25
I have no idea how but it suddenly just boot up fine again. Only difference was it told it didn't detect any devices and to boot in low graphics mode but everything else is the exact same. My YouTube problem is even fixed somehow.

---

### Post by mikebp on 2010-01-27
So, lzd, what did you actually do to get it out of the infinite login loop?
 
...I'm still stuck.    ](*,)

---

### Post by jacklinux on 2010-01-27
i had the infinte loop, but mine was a GRUB issue, i booted liveCD and then restored my sytem worked a treat.

---

