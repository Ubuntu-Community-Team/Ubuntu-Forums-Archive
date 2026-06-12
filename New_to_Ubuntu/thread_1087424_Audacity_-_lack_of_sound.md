---
title: "Audacity - lack of sound"
date: 2009-03-05
forum: New to Ubuntu
---

### Post by hmich176 on 2009-03-05
I'm having a sound problem with Audacity.  I just installed it, and when I played a song, it played, but without sound.  What should I do to fix this?

---

### Post by gackt on 2009-03-05
Are others player working? like amarok or vlc?

---

### Post by hmich176 on 2009-03-05
> **gackt said:**
> Are others player working? like amarok or vlc?

Yes, everything else is working.  It's only Audacity.

---

### Post by zaarin on 2009-03-11
I'm having the same problem.  I noticed that when I first opened Audacity the audio output device was OSS, and it worked.  Now, for some reason, even though I haven't changed any settings, (though I downloaded some Ubuntu updates) the output device is ALSA and I have no sound in Audacity.  Still have sound everywhere else.

---

### Post by linuxuser21 on 2009-03-11
> **zaarin said:**
>  the output device is ALSA and I have no sound in Audacity.

It seems ALSA has a lot of problems on a lot of things including Firefox.  This probably is your problem.

---

### Post by hmich176 on 2009-03-11
> **zaarin said:**
> I'm having the same problem.  I noticed that when I first opened Audacity the audio output device was OSS, and it worked.  Now, for some reason, even though I haven't changed any settings, (though I downloaded some Ubuntu updates) the output device is ALSA and I have no sound in Audacity.  Still have sound everywhere else.

Well, I'm glad to know I'm not the only one!

---

### Post by drz4007 on 2009-03-13
i have the same problem. i tried all the choises for the default playback devise but in vain. so what do can we do?

---

### Post by hmich176 on 2009-03-13
Yeah, I'd really like some help on this.  I posted this question a week ago, and there isn't any response for help.  I don't know what to do, nor if there is an appropriate solution.

---

### Post by Old Jimma on 2009-03-18
Ubuntu Dudes:

Here is what worked for me:

1. Start audacity.
2. open the file you wanna play, but don't mash on the green arrow.
3. edit > preferences > playback Then, in the Device box, choose your output device driver. Mine is ALSA. 

Great sound now!

Gimme the beans!!!

Phil Smith
Duluth, GA

---

