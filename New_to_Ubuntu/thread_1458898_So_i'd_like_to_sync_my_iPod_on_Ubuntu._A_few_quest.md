---
title: "So i'd like to sync my iPod on Ubuntu. A few questions..."
date: 2010-04-20
forum: New to Ubuntu
---

### Post by chrisxuk on 2010-04-20
Good evening.

I'd like to start syncing my iPod video 80GB on Ubuntu, but I just have a few questions.

1. The majority of the content on my iPod would be video. Rhythmbox doesn't seem to be able to play video files, so is there an alternative player that can sync my ipod with music and video?

2. Next, I like my podcasts. In particular TWiT (This Week In Tech). Is it possible to subscribe to podcasts from the iTunes store, so I don't have to manually download the audio files each time a new episode is released?

3. Lastly, for now, is about where my music and video is stored on my PC. I have 1 x 500GB split into 2 partitions. 1 x 365 with my Windows XP installation, and 1 x 125GB. What i'd like to do, is use the music and video that are on my Windows partition, and just import them into the music player. I presume this will be possible?

So to summarise, I'd like a media player that can; sync my iPod, be able to sync video files onto my iPod; subscribe to podcasts, especially TWiT(!); and import my content from another partition, without putting them onto my Ubuntu partition.

I hope this all makes sense, and I look forward to your suggestions.

Chris

---

### Post by Paddy Landau on 2010-04-20
If you have Windows, then do it all from Windows.

Unfortunately, the iPod is *not* supported on Linux (complain to Apple about it; that's one reason that I avoid Apple's products).

Apparently, 10.04 (due out later this month) does support iPod sync, but I don't know how well.

You can get an older version of iTunes (version 7) to run on Linux. Use [PlayOnLinux]("http://www.playonlinux.com/") to make its installation dead easy. But that's the best you'll get on Linux, and I don't know how buggy iTunes will be.

---

### Post by chrisxuk on 2010-04-20
Thanks for the quick reply! A friend of mine IRL has just suggested iFuse. Is this something you recommend?

---

### Post by nothingspecial on 2010-04-20
```
sudo apt-get install gtkpod-aac
```

Open gtkpod from you sound and video menu.

It should recognise your ipod.

Click on your ipod in the left hand tab and choose add files.

Navigate to your video files on your windows partition and select the ones for transfer.

Click save changes.

Eject ipod.

Happy viewing.

---

