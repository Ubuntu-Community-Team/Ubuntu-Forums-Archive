---
title: "Playing two sounds at once in Ubuntu 9.04 (Jaunty)"
date: 2009-11-21
forum: New to Ubuntu
---

### Post by LeDechaine on 2009-11-21
Yes, you've read that right. I can't play two sounds at the same time in Jaunty since i've put this *.asoundrc* file in my home directory to have digital audio.

```
pcm.!default {
    type plug
        slave {
        pcm "spdif"
    }
}
```
Playing an mp3 in xmms (even a paused mp3) + a youtube video = the youtube video will play, but without sound. Stopping xmms, and restarting/continuing the video = firefox just replays the last 250ms or so of the xmms song played indefinitely until I kill firefox and restart it.

A youtube video will play with sound, but having a youtube video playing or paused = trying to listen to a song in xmms fails, (error telling the sound card is busy). And opening a video with VLC won't output sound when xmms or youtube is playing or paused, etc.

Everything in the sound system preferences is set to alsa.
Oh, and there's no analog output since i've created this *.asoundrc* file. Is it possible to fix this, too?

---

### Post by LeDechaine on 2010-04-30
Well, just tried the Ubuntu 10.04 CD and saw there was a way to set it in the sound preferences so every program outputs to the optical out, and there's no bullsh** about "I can't play this sound because xmms/a youtube video/whatever is paused instead of stopped!"

So i'm guessing there must be a way to do something that was standard 10 years ago in Ubuntu 9.04?

Also, a more-or-less off-topic rant:
There's one thing Ubuntu has never been able to do in like 10 years: Output sound to the DAMN SOUND BLASTER HEADPHONE OUT!!!

Whatever. Somebody tell me how to fix **at least** the optical two-sounds-at-once problem,

Or should I just stop messing around for hours with standard-working-10-years-ago-things and just install XP...

Anyway, thanks in advance.

---

### Post by Chronon on 2010-04-30
It's your time, so the decision about whether XP or a certain version of Ubuntu is best for you is entirely up to you.

Have you tried PulseAudio?  I have been using it for several releases now and it seems to work as advertised -- though strangely, some of the tools that help to configure it are not included by default.

---

### Post by LeDechaine on 2010-04-30
Well, PulseAudio or not nothing ever worked the way I wanted to. I ended up uninstalling PulseAudio one week ago thinking it was useless for me. Nothing changed, still the same problem. Just less CPU use... I guess.

I'm guessing I can reinstall it and reinstall the config tools...

---

### Post by Chronon on 2010-05-01
I removed PulseAudio once when I was having problems with it and found that ALSA wouldn't let me mix audio from two different sources.  You need some sort of mixer installed to allow that, as apparently ALSA doesn't provide this inherently.  

I have found PulseAudio fairly reasonable to deal with if you install all of the associated utilities.

---

