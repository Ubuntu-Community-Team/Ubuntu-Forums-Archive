---
title: "Skype Microphone Problem"
date: 2010-12-12
forum: New to Ubuntu
---

### Post by QuentinK on 2010-12-12
I'm not sure if this is where this needs to be, but being an absolute beginner I figured this is the best place.

I recently tried to have a Skype call with someone, and when I called them, my video worked perfectly, but they couldn't hear me.
So I went into settings and went to the Audio Device tab to see what they had as the Mic, and it was Pulseaudio Server (Local), which isn't my mic. So I tried to change it, but it wouldn't show any other options than Pulseaudio. So to see if my mic worked at all, I went into Audacity, which registered it fine and it recorded perfectly. So I'm wondering what I can do to get Skype to register my correct mic (which is integrated into my webcam)

Thanks
~Quentin

---

### Post by cariboo on 2010-12-12
Your microphone is probably there, I had to use alsamixer to turn up the microphone volume on my netbook to use skype. To check alsamixer, open an Applications->Accessories-> Terminal and type:

```
alsamixer
```

use the tab key for navigation and the arrow keys to change the levels. Once you have the settings to where everything works the way it should, press the esc key to exit, then type:

```
sudo alsactl store 
```

To save the changes you have made.

---

### Post by OldBoy44 on 2010-12-25
Hi all,

I too have a similar problem - have just loaded Skype and have a Logitech webcam C200 which works fine in Video mode but sound test fails! I adjusted alsamixer.

Does anybody have any further thoughts?

Cheers,  :)

---

### Post by OldBoy44 on 2010-12-25
Fixed my Microphone problem with the aid of -
[https://help.ubuntu.com/community/SkypeTroubleshooting](https://help.ubuntu.com/community/SkypeTroubleshooting)

I'm happy!  :)

I guess it is up to QuentinK to mark as Solved unless somebody advises otherwise.

---

