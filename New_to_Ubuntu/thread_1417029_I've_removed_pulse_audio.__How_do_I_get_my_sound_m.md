---
title: "I've removed pulse audio.  How do I get my sound mixer icon back on the upper panel?"
date: 2010-02-26
forum: New to Ubuntu
---

### Post by diablo75 on 2010-02-26
I recently swapped out sound cards (disabled the on-board sound and installed a Creative Labs Sound Blaster Audigy 2) and after doing so had a problem with PulseAudio thinking the sound card was only capable of 2 channel sound output when it's actually capable of 5.1 analog surround sound output.  I tried a lot of different things to try and get it to work (detailed in [this thread]("http://ubuntuforums.org/showthread.php?t=1416248")) but nothing worked.

So I decided to remove PulseAudio with:

```
sudo apt-get purge pulseaudio
```

And restarted the computer.

After rebooting, I found that my soundcard still worked and *worked even better* when it came to surround sound output.  VLC now allows me to select 5.1 channel output when playing media that has surround sound, which PulseAudio didn't.

But now the mixer panel which used to be present in the olds days of ALSA is missing, and I was wondering if anyone knows how to get that back.  It's probably just a simple package I need to installed.  I tried "alsamixergui" but it's not quite the same as the one they used to have that looked like this:

[IMG]http://michaeleberhart.net/linux/ubuntu/8_04/alsa_mixer.png[/IMG]

Anyone know how to get that particular mixer app back up at the top?

---

### Post by Enigmapond on 2010-02-26
The way I worked around this problem is install gnome-alsamixer and alltray. Alltray will put any application on the upper panel. But...it IS  a problem after uninstalling pulseaudio also the inability to set the system sounds.

---

### Post by Chris Edgell on 2010-02-26
[http://ubuntuforums.org/showthread.php?t=1348822](http://ubuntuforums.org/showthread.php?t=1348822)
[http://ubuntuforums.org/showpost.php?p=8462183&postcount=19](http://ubuntuforums.org/showpost.php?p=8462183&postcount=19)

I don't see too much action on your querry, so I've looked up my one post of this problem...and the second is the response and the person who got me right.  I'll keep an eye on this thread or you can PM him, he's a very agreeable guy...may not be around for a week at a time though, you may know him.

After all, I missed the one that looked like a terminal and instead got the gui.  (It wasn't the alsamixer terminal, it was a terminal that popped up like a window when I went to Multimedia>Mixer.  Know what I mean??!!)

Oh, now I see, I was looking at the other responder...and I mistakenly thought you were running Jaunty, but I'm thinking it's Karmic.  (Is there a reason why you don't have that there on your profile area, or whatever it's called?)

Best wishes

---

### Post by diablo75 on 2010-02-26
Oops, never noticed that I didn't have my version in my little profile thing.  Got it put on there now.

Anyway, I've had good luck using the alsa mixer app mentioned above.  And best of all, my microphone works in both Skype and Audacity.

GOOD RIDDANCE, PULSEAUDIO!

---

### Post by diablo75 on 2010-02-26
Alright, slight update/question:

I've noticed that the default movie player (totem) is failing to play audio out with any video I throw at it.  Although it's not a big deal, I was wondering why.  I can't seem to find an audio setting in it to change to get it to point at ALSA (perhaps it's trying to use Pulse audio which isn't there).

Likewise, I noticed the neat feature Ubuntu used to have, where you hover your mouse over an audio file and it plays a preview of it automatically without you having to open it no longer seems to work.  So perhaps certain aspects of the system are still pointing at something other than ALSA...

---

