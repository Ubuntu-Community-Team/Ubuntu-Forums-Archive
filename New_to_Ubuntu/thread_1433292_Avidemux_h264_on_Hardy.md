---
title: "Avidemux h264 on Hardy"
date: 2010-03-18
forum: New to Ubuntu
---

### Post by stoppage on 2010-03-18
Hi, I need a version of Avidemux..preferably .deb. that can properly handle .mp4/h264/aac audio without sync issues. I have version 2.4.1 on Hardy.. Anyone please?

---

### Post by sandyd on 2010-03-18
> **stoppage said:**
> Hi, I need a version of Avidemux..preferably .deb. that can properly handle .mp4/h264/aac audio without sync issues. I have version 2.4.1 on Hardy.. Anyone please?
see attached link.
[https://bugs.launchpad.net/ubuntu/+source/avidemux/+bug/496739](https://bugs.launchpad.net/ubuntu/+source/avidemux/+bug/496739)

they say it should be fixed by 2.6

---

### Post by stoppage on 2010-03-19
This isn't an .mkv file, it's an .mp4...same bug apply?

---

### Post by coffeecat on 2010-03-19
I find that avidemux is quite incapable of maintaining audio/video sync in **any** format except AVI. I've wasted days with this. It's good at AVIs though. Trouble is, the AVI container is a dying standard. It's been dropped from Handbrake, for example.

And, last I tried, avidemux was quite hopeless with h264.

> **carlee said:**
> they say it should be fixed by 2.6

Oh, I hope so. I really hope so. [-o<

---

### Post by sandyd on 2010-03-19
> **stoppage said:**
> This isn't an .mkv file, it's an .mp4...same bug apply?
its a general h264 problem

h264 support is severely broken on the current version, so they have to use "safe mode" which sucks at syncing.

btw, the mkv that was submitted was encoded in h264 (I know this cause I was the one who submitted it)

---

### Post by stoppage on 2010-03-19
Sounds dismal for a file-format that everyone's raving about. All I need to do with this file is save a portion, it can stay in same format. Does anybody know of another app?

---

### Post by anewguy on 2010-03-19
I've had problems with every release of avidemux not syncing video and sound correctly, didn't matter what format I was using.  I just gave up and have been trying to find something else to use, but so far haven't done the best there either.

Dave ;)

---

### Post by sandyd on 2010-03-19
kdenlive? openshot?

---

### Post by coffeecat on 2010-03-19
@stoppage and @anewguy,

I hate to have to post this on an Ubuntu forum, but the shortcomings of what could be a good video editor - avidemux - force me to. There is a free app, but its only available for MacOS and Windows. MPEG Streamclip here:

[http://www.squared5.com/](http://www.squared5.com/)

Advantages - it doesn't get things out of sync unless you give it a very broken ts-mpeg. It's as simple to use as avidemux.

Disadvantages: 

- There's no Linux version and I can't get it to run in Wine, despite what it says on that website. If someone can, I'd be glad to hear.

- If you want the Mac version, you have to pay Apple £15 for the QuickTime mpeg playback component otherwise it can't handle mpeg files.

- If you want to encode a video file into AVI or MP4, you're offered some weird and wonderful (mostly Apple) codecs.

What it's good at is taking a ts-mpeg file recorded from a dvb-t and repairing all the transmission breaks and hiccups - things that tend to cause loss of sync anyway and which avidemux completely fails at.

---

### Post by gordintoronto on 2010-03-19
> **stoppage said:**
> Sounds dismal for a file-format that everyone's raving about. All I need to do with this file is save a portion, it can stay in same format. Does anybody know of another app?

I am delighted with Cinelerra.  Some people don't like the user interface, but it doesn't bother me at all.  It has some learning curve, but this web site is very helpful: [http://www.g-raffa.eu/Cinelerra/HOWTO/index.html](http://www.g-raffa.eu/Cinelerra/HOWTO/index.html) 

There are also numerous tutorials on youtube.

I have an AMD Phenom II X2 CPU, and rendering a minute of video in Cinelerra takes less than a minute.

---

### Post by anewguy on 2010-03-19
> **carlee said:**
> kdenlive? openshot?

I remember trying kdenlive a few times, but it's been quite a while and I really don't remember what I was trying to do or what the results were. ;) 

[QUOTE=coffeecat] Re: Avidemux h264 on Hardy

@stoppage and @anewguy,

I hate to have to post this on an Ubuntu forum, but the shortcomings of what could be a good video editor - avidemux - force me to. There is a free app, but its only available for MacOS and Windows. [/QUOTE] 

Lots of Windows apps available, including things like Kate's Video Converter, which I've always liked.  As you noted, the trick is in finding a way to run them while booted in Linux - I haven't had much success with any of them in Wine.

As the world knows (at least anyone who has watched these forums at all), a strong easy-to-use open-source video app is strongly needed, and has been for a long time.  There has been progress, and outside of what to me at least is a very tough learning curve, cinelerra appears the most promising.  If there was a way to "dumb it down" for some of us without loosing functionality it would be very good.

The challenge of writing such an app intrigues me, but I have absolutely no knowledge of video formats, so while I might be able to program I lack the knowledge needed to build such an app.  It would be a challenge, though.

Best of luck!

Dave ;)

---

### Post by coffeecat on 2010-03-20
The OP was asking about a problem with avidemux which describes itself as:

> a free video editor designed for simple cutting, filtering and encoding tasks.Apps like kdenlive and cinelerra are more complex, really for those wanting to create movies. They're somewhat different animals - horses for courses - which is why I mentioned MPEGStreamclip whose level of functionality is similar to avidemux (except that it keeps most things in sync :rolleyes:). 

I've just remembered something that was announced a couple of months ago. [The VLC team is working on a video editor]("http://lifehacker.com/5432946/vlc-team-working-on-a-cross+platform-video-editor"). Now that is good news. VLC already does a good job of converting/re-encoding videos. I look forward to the editor becoming available.

---

### Post by anewguy on 2010-03-24
> **carlee said:**
> kdenlive? openshot?

Thanks for the shout out on openshot!  While I still have to play with it to see what it can/can't do, it does look promising for what I needed!

Thanks again!

Dave ;)

---

