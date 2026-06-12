---
title: "sound skipping forward on multiple sound cards"
date: 2010-03-02
forum: New to Ubuntu
---

### Post by abben on 2010-03-02
_The problem:_
Basically, whenever I fire up xmms or vlc, and play any audio, it will occasionally skip forward a small amount of time, like 0.5 seconds. Throughout any particular song, this is like to happen perhaps 1-10 times, at irregular intervals. If I replay the same song, it will not skip at the same point it did previously.

_My sound device(s):_
The *first* sound device I used is super old: it is a Crystal CS4235 which I believe was made in 1998. It is part of the Delphi-III mainboard on an old etower 333k. After having some sound quality problems with that card, I plugged in a sound blaster card.

Both cards have this skipping issue.

_How I got sound working_:
 I did a minimal, bare-bones installation. I originally had **no** sound related programs or drivers of any kind.

To set up my sound, I did this:

```
sudo apt-get install **alsa-oss alsa-utils oss-compat**
```

I used my newly installed modprobe tool:

```
sudo modprobe **snd-cs4236**
```

I went to my newly installed **alsamixer**, and unmuted everything and turned up the volume on everything. I installed vlc, since vlc plays everything. Lastly added snd-cs4236 to the bottom of /etc/modules.

Then, I replaced snd-cs4236 with snd-sb16 in /etc/modules. I did this because I only plan on using one card or the other and don't want to hassle with switching sound devices.

xmms lets me switch between alsa 1.2.11 output plugin and oss 1.2.11 output plugin (or leads me to believe I'm switching), but either option produces the same skipping behavior.

And now I'm here, with working, but skippy sound. It's not just that I'm using an old soundcard/old computer is it?

---

