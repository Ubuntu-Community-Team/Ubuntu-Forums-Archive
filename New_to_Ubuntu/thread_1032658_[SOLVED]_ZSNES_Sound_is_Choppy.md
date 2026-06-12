---
title: "[SOLVED] ZSNES Sound is Choppy"
date: 2009-01-06
forum: New to Ubuntu
---

### Post by Drubie on 2009-01-06
I have installed zsnes from src as per the instructions, and it runs fine but with one minor annoyance.
Even at 60fps (full), the sound is still a bit choppy.

I have the settings at 32000Hz sampling rate and have no idea what the other settings mean.  what could be causing choppy sound?

---

### Post by donkyhotay on 2009-01-06
Try this:
```
zsnes -ad sdl
```

---

### Post by Drubie on 2009-01-06
> **donkyhotay said:**
> 
```
zsnes -ad sdl
```

nope, still choppy at 60fps

btw, what does that code do?

---

### Post by Drubie on 2009-01-06
the terminal says I am using the Simple DirectMedia Layer Output driver.
Should I try another?  (and how do I do that?)

---

### Post by donkyhotay on 2009-01-06
I believe it changes the sound library used, sometimes it help. I had this problem myself when I first started using zsnes and if I remember correctly I fixed it by changing the audio output rate. Can't remember exactly and I'm not at my home computer now to look it up. Take a look through the audio options in zsnes for anything relevent to frequency output and try the various options in there, relaunching zsnes between each change, and see what happens.

---

### Post by Drubie on 2009-01-06
> **donkyhotay said:**
> relaunching zsnes between each change

That might be why there seemed to be no change when I was goofing with the settings to try and make it work... I feel silly for not restarting the whole program...

I will try that and get back
Thanks!

---

### Post by donkyhotay on 2009-01-06
Good luck, and don't forget to mark the thread as solved if it works. (c:

---

### Post by Drubie on 2009-01-06
Amazing!  I just maxed out the sound sampling rate (48000Hz I believe), reloaded, and it works like a charm! 
I will try lower rates to see what happens.

Thanks!

---

### Post by donkyhotay on 2009-01-06
Glad that it worked. (c:

---

