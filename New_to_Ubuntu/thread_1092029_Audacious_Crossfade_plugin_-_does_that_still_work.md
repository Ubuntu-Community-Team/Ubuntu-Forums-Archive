---
title: "Audacious Crossfade plugin - does that still work?"
date: 2009-03-09
forum: New to Ubuntu
---

### Post by The Bright Side on 2009-03-09
Hi!

Another noob question... I just started using Ubuntu 2 days ago, and for my music playback, I found that Audacious is the best program to use. It does everything I want, except one thing:

GAPLESS OUTPUT.

It's a bit annoying when listening to Pink Floyd or a live recording to have those breaks between tracks. I heard about the Crossfase plugin that will enable gapless output for Audacious, but for the life of me, I haven't been able to get that to run. I spent hours on it, I actually even got it installed (or so I think), but it won't appear as an option in the Audacious preferences.

Does this plugin even still work with the current Audacious version? And if so, could you give me some advice on installing it?

Thanks guys!

---

### Post by The Bright Side on 2009-03-10
...nobody? :-( Here's some additional info: I'm using Ubuntu intrepid 8.10 64 bit, and my Audacious version is 1.5.1. 

Come on guys, some of you must be using this program, right? Or if not, which music player do you have for gapless output? There must be a decent one out there that's lightweight, plays all formats (incl. FLAC, MPC...) and does so without gaps between the files.

Thanks for your help and suggestions!

---

### Post by yaztromo on 2009-04-11
Look here for the audacious crossfade plugin. Download the .deb, double click it.

[https://launchpad.net/ubuntu/intrepid/i386/audacious-crossfade/0.3.14-1](https://launchpad.net/ubuntu/intrepid/i386/audacious-crossfade/0.3.14-1)

64bit version: [https://launchpad.net/ubuntu/intrepid/amd64/audacious-crossfade/0.3.14-1](https://launchpad.net/ubuntu/intrepid/amd64/audacious-crossfade/0.3.14-1)

Good luck getting it to work though, you may get crashes, see here for more details: [http://www.linux-archive.org/debian-user/240350-audacious-crossfade.html](http://www.linux-archive.org/debian-user/240350-audacious-crossfade.html)

---

### Post by vanadium on 2009-04-11
Audacious crossfade plugin works for me using the default software from the repository (Hardy). For gapless playback, it is the next best thing to mpd, which I normally use.
To avoid any issues with gapless playback, use ogg rather than mp3 where possible. ogg vorbis supports gapless by design, contrary to mp3. More software can gaplessly playback ogg than can do that with lame mp3.

---

### Post by yaztromo on 2009-04-11
It no longer works on Jaunty unfortunately. Segfaults audacious.

---

### Post by vanadium on 2009-04-11
Is the software not anymore in the repositories???

---

### Post by yaztromo on 2009-04-11
It's no longer in the repos for jaunty, in fact I believe they have set the audacious package to conflict with audacious-crossfade now. My entire collection is in mp3, so audacious is no longer an option. I noticed rythymbox has crossfade plugin, so looking at that.

---

### Post by obi-nine on 2009-04-25
I compiled it from source for Jaunty on my netbook as per Kallium's instructions at [http://ubuntuforums.org/showthread.php?t=697041&page=2](http://ubuntuforums.org/showthread.php?t=697041&page=2) and it's working well for me. 

Here is a link to the two files it made which were put in */usr/lib/audacious/Output/* (owned by root) if you want to try just copying mine: [http://virishi.net/sites/default/files/audacious-crossfade.tar](http://virishi.net/sites/default/files/audacious-crossfade.tar)

Good luck!

---

### Post by yaztromo on 2009-04-25
Thank you Obi!

Your provided binaries work great so far.

---

### Post by n838901 on 2009-05-02
There is also a rebuilt audacious-crossfade package on this thread:

[https://bugs.launchpad.net/ubuntu/+source/xmms-crossfade/+bug/208666/comments/32](https://bugs.launchpad.net/ubuntu/+source/xmms-crossfade/+bug/208666/comments/32)

I use Audacious with the crossfade plugin as well as the LADSPA host plugin for a compressor and limiter for live DJing.

---

### Post by The Bright Side on 2009-05-04
Hey, these don't seem to work on 64-bit versions, do they? I tried putting yours in the Output folder, Obi (thanks!), but they don't appear as an option in Audacious.

Quod Libet sounds like a nice program, I hear there's a version in the making with gapless output. I'll keep my eyes open for that.

---

### Post by nenolod on 2009-05-11
Audacious 2.x features a rewritten version of the crossfade plugin. However, it probably has bugs that need to be tended to. We intend to release 2.0 this weekend.

---

### Post by logos34 on 2009-05-11
Crossfade plugin in Audacious works for me on 8.04 Heron.

I love [MOC (Music-on-console)]("http://moc.daper.net/") player (CLI).  It's the only one that does gapless flawlessly.  And it's super lightweight.

---

### Post by The Bright Side on 2009-05-12
Hey Nenolod, that's amazing news!! Do you have a change log or news site somewhere? I think Audacious is a great program and I'd love to see what else you've been doing with it.

Keep up the good work--

---

### Post by nenolod on 2009-05-13
> **The Bright Side said:**
> Hey Nenolod, that's amazing news!! Do you have a change log or news site somewhere? I think Audacious is a great program and I'd love to see what else you've been doing with it.

Keep up the good work--

audacious: [http://redmine.atheme.org/projects/activity/audacious](http://redmine.atheme.org/projects/activity/audacious)
audacious-plugins: [http://redmine.atheme.org/projects/activity/audacious-plugins](http://redmine.atheme.org/projects/activity/audacious-plugins)

---

### Post by krippa on 2010-05-15
Does anyone know what happened to the crossfade plugin? Im using Audacious 2.3 on Lucid Lynx and I still cant see it in the default plugins..

---

