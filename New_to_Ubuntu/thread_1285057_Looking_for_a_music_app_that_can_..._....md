---
title: "Looking for a music app that can ... ..."
date: 2009-10-07
forum: New to Ubuntu
---

### Post by techno-mole on 2009-10-07
hello.

im looking for a music app that can perform volume leveling.

basically i (like a lot of people ) have a large mp3 collection, but i have noticed that not all the tracks are the same volume, some are louder, some are quieter, so im looking for an app that i can put the tracks through that will reduce or increase the volume on various tracks so that they all play at the same volume.

when i used windows i had an app called musicmatch which had a feature like this on it, although i think it did it when you ripped from the disc, cant really remember.

ps - with a gui preferably.

cheers in advance for any advice.

---

### Post by orngjce223 on 2009-10-07
When I tried Audacity I found that you could click points on each track to normalize the volume levels, I don't know if you can do that in bulk though.

---

### Post by techno-mole on 2009-10-07
ill have a look, cheers

---

### Post by hashimoto on 2009-10-07
> **techno-mole said:**
> im looking for a music app that can perform volume leveling.

...have a large mp3 collection...

If you only have mp3's, you could also use mp3gain. It's in the repos.

---

### Post by CatKiller on 2009-10-07
> **hashimoto said:**
> If you only have mp3's, you could also use mp3gain. It's in the repos.

+1.

Although you might be interested in [EasyMP3Gain]("http://sourceforge.net/projects/easymp3gain/"), which isn't in the repos but is a .deb file install away (and does FLACs and Ogg Vorbis files too).

You might also be interested in reading about [Replay Gain]("http://en.wikipedia.org/wiki/Replay_Gain"), to find out what you're actually doing.

---

### Post by MrWES on 2009-10-07
> **CatKiller said:**
> +1.

Although you might be interested in [EasyMP3Gain]("http://sourceforge.net/projects/easymp3gain/"), which isn't in the repos but is a .deb file install away (and does FLACs and Ogg Vorbis files too).

You might also be interested in reading about [Replay Gain]("http://en.wikipedia.org/wiki/Replay_Gain"), to find out what you're actually doing.

Banshee is capable of replay gain correction, and it's in the repositories.

Bill

---

### Post by CatKiller on 2009-10-07
> **MrWES said:**
> Banshee is capable of replay gain correction, and it's in the repositories.

Yes, but you need to tag them first, which is what mp3gain/vorbisgain/metaflac/etc do. Most of the media players are capable of applying the Replay Gain tags once they're there.

---

### Post by Chronon on 2009-10-07
The best ReplayGain scanner I have ever used is Foobar2k.  I keep a version of it installed with WINE just for this purpose.

---

### Post by MrWES on 2009-10-08
> **CatKiller said:**
> Yes, but you need to tag them first, which is what mp3gain/vorbisgain/metaflac/etc do. Most of the media players are capable of applying the Replay Gain tags once they're there.


So you have apply the replaygain tags, whether it be --track or --album and then the player will interpret them and apply them accordingly?

Bill

---

### Post by CatKiller on 2009-10-08
> **MrWES said:**
> So you have apply the replaygain tags, whether it be --track or --album and then the player will interpret them and apply them accordingly?

Or both, yes.

---

### Post by Bobulous on 2010-01-03
I'm a little late to this party, but I have written a page on my site which is all about Replay Gain in Linux:

[http://www.bobulous.org.uk/misc/Replay-Gain-in-Linux.html](http://www.bobulous.org.uk/misc/Replay-Gain-in-Linux.html)

It covers soundKonverter, foobar2000, and using a script to run metaflac (or another Replay Gain calculation tool) on every audio file in your digital music collection in one go.

---

