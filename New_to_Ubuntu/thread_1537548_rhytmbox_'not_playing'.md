---
title: "rhytmbox 'not playing'"
date: 2010-07-23
forum: New to Ubuntu
---

### Post by dulce on 2010-07-23
i launched it and poked 'play'. why does it still say say 'not playing'-- and indeed remains silent?

while i'm at it-- how do i hook up to shoutcast?

---

### Post by jtarin on 2010-07-23
Don't poke as in Windows, but click.
Did you indicate a file for it to play or choose something from your playlist?
[Shoutcast]("http://code.google.com/p/rhythmbox-shoutcast/wiki/HOWTO_Install")

---

### Post by puca mor on 2010-07-25
I am having rhythmbox troubles too. 

Like Dulce, when i clicked 'play' nothing happened. I installed 'ubuntu-restricted-extras'. After restarting rhythmbox did indeed play.. 

You could give that a go, if you haven't already.

However, now it seems when i play anything from youtube, it stops rhythmbox playing, and returns it to the broken state it was in before... pretty strange. And i haven't found a fix for it yet.:(

---

### Post by bsharp on 2010-07-25
Disclaimer: I'm 98% sure on this, so if I'm wrong someone please educate me.

The reason Rhythmbox stops playing when Firefox is open (or flash is playing, more specifically) is because FF/Flash is configured to use the PulseAudio sound server while Rhythmbox uses ALSA, which only allows one program to use its devices at a time.

Technically, there's nothing wrong, as the software is doing exactly what it's told to do, so I don't know how to "fix" it. There is probably a way to configure Rhythmbox to use Pulse.

---

### Post by puca mor on 2010-07-25
Thanks bsharp - that does indeed seem to be the cause. 

I'm using Chrome, but the effect seems to be the same. I just closed all my chrome windows.. and rhythmbox worked again. 

Thanks for the tip bsharp! :)

---

