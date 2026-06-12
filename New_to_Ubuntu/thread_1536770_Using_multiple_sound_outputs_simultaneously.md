---
title: "Using multiple sound outputs simultaneously?"
date: 2010-07-22
forum: New to Ubuntu
---

### Post by Ozymandias_117 on 2010-07-22
Hi, If I go into sound preferences, it offers Juniper HDMI Audio Out and On-board Audio Out. I want the HDMI, but then my headphone port doesn't work anymore, unless I change it back to on-board. Is there any way I can make it send sound to both outputs simultaneously?

---

### Post by lidex on 2010-07-22
Beneath that you should see 'Profile'. Try selecting a different one. Also check 'Connector' on 'Output' tab.

---

### Post by Ozymandias_117 on 2010-07-22
> **lidex said:**
> Beneath that you should see 'Profile'. Try selecting a different one. Also check 'Connector' on 'Output' tab.

I'm not having problems getting sound from one or the other, but I can't find a way to make BOTH play sound at the same time. Like, being able to select both connector options under output.

---

### Post by lidex on 2010-07-22
> **Ozymandias_117 said:**
> I'm not having problems getting sound from one or the other, but I can't find a way to make BOTH play sound at the same time. Like, being able to select both connector options under output.

Don't know how to do that. My thinking is that with hdmi chosen, using a different profile might get you headphone output also.
OK I understand what you're saying. There was a thread somewhere - I'll see if I can find it.

---

### Post by Ozymandias_117 on 2010-07-22
> **lidex said:**
> Don't know how to do that. My thinking is that with hdmi chosen, using a different profile might get you headphone output also.

Unfortunately, there is only one profile under HDMI. :(

---

### Post by lidex on 2010-07-22
So the quest here is for simultaneous output to two soundcards? paprefs may do that for you (pulseaudio preferences). Do you have it installed? If not:
```
sudo apt-get install paprefs
```

More info here:
[http://ohioloco.ubuntuforums.org/showthread.php?t=843012](http://ohioloco.ubuntuforums.org/showthread.php?t=843012)

---

### Post by Ozymandias_117 on 2010-07-22
Thanks! With that program it was super easy! I just couldn't seem to find something like that on my own this time :(

---

