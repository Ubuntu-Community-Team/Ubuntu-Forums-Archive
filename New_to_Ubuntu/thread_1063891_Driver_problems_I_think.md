---
title: "Driver problems I think"
date: 2009-02-08
forum: New to Ubuntu
---

### Post by Fox McCloud on 2009-02-08
I'm having an issue with the sound on my laptop. The drums that play at the login screen reverberate, a little at a time to the point where it quite but continous. Even now a hour after I logged in I hear the very last bit of the drums.

No other sounds come through the speakers, and connecting audio through the headphone jack does nothing. The sound continues through the laptop speakers. I can however mute it with the volume control...

What could be causing this?

---

### Post by Temposs on 2009-02-08
I'm not sure, but I'll throw something out there. Let's see if it's pulseaudio screwing up. In a terminal type:

```
killall pulseaudio
```

---

### Post by Fox McCloud on 2009-02-08
Nope, that did not help. :(

---

### Post by Fox McCloud on 2009-02-08
Thanks to taurus reply to another thread about getting system info, I was finally able to find out more about my sound card and Googled it. Sure enough someone has had the exact same problems:
[https://bugs.launchpad.net/ubuntu/+bug/269586](https://bugs.launchpad.net/ubuntu/+bug/269586)

Now my issue is, what is my default su password? or how do I change it? I need to know so I can apply the fix.

---

