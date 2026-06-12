---
title: "Digital audio, system-wide"
date: 2009-11-10
forum: New to Ubuntu
---

### Post by LeDechaine on 2009-11-10
Well, after creating a simple ".asoundrc" file in my home directory, containing this:
```
pcm.!default {
    type plug
        slave {
        rate 48000
        pcm "spdif"
    }
}
```

I've rebooted my computer, and, surprise, i've got sound in digital!
I was expecting absolutely nothing from this simple script, i'm impressed.

But the problem is... the sound is coming **only** from the digital source... and **only** from xmms.

So, apart from xmms, (and, weirdly, the "sound preferences" tests, which sends sound **only** in analog to my headphones) nothing else produces sound.

With this little script, isn't alsa supposed to re-route *everything* system-wide to the digital outputs? **If it's not the case, well, it's sad, because that's *exactly* what I want!**

Everything is set to Alsa in the sound preferences.
Everything is to the max in the volume controls for every possible (heh, and non-possible) outputs of my sound card, which is an **Audigy 2 ZS Platinum Pro**.

A little ".asoundrc" that re-routes everything, system-wide, to the digital **and** analog outputs would be perfect. ;)

---

### Post by LeDechaine on 2009-11-10
Well, after killing PulseAudio, the sound is back to analog (!) and restarting it with pulseaudio -D doesn't re-enables the digital sound output!
And now, without doing anything, the sound is back to digital, looks like i've got my system-wide digital audio!!!
xmms, firefox (flash), vlc, and even frozen bubble (haha) outputs sound in digital!

Madness.. But at least, now, it works!

So, i'll cross my fingers, and i'll search for help about modifying the ".asoundrc" file to get the sound in analog, too!

---

### Post by LeDechaine on 2009-11-10
Heh, you know what? Problem solved. How? My digital audio goes through RCA to my speakers, and also through an optical cable, to my other stand-alone soundcard, which allows me to plug my earphones in. ;)

I call this *temporarily* solved, even if I get decent sound quality. :popcorn:

---

### Post by LeDechaine on 2009-11-13
Well, there's another problem: Looks like this can only play one sound at a time!

Playing xmms (even a paused mp3) + a youtube video = the youtube video will play, but without sound. Stopping xmms, and restarting/continuing the video = firefox just replays the last 250ms or so of the xmms song played indefinitely until I kill firefox and restart it.

Playing a youtube video, or having a youtube video paused = trying to listen to a song in xmms fails, (error telling the sound card is busy).

Everything in the sound system preferences is set to alsa, and the only thing in my .asoundrc file is mentioned in my first post (except the "rate 48000" line, which took 20% of more cpu usage only to play an mp3 file on my poor Pentium 3! - But the same thing happens with or without this line).

---

