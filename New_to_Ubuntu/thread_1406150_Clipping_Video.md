---
title: "Clipping Video"
date: 2010-02-13
forum: New to Ubuntu
---

### Post by Stigmata13 on 2010-02-13
Does anyone know any good programs for clipping video? I would like to take a large video file (700 mb) and clip it into several smaller ones. I would prefer something where you could move frame to frame and then hit a button to clip the video at that point... and then maybe export each individual clip. It seems like every program I use has a "razor tool" but I would prefer to stop the video playback at a certain point, move frame to frame to the exact point I would like to clip, and then use a button to clip it, like you can in windows movie maker.
Any suggestions?

---

### Post by NightwishFan on 2010-02-13
I use Pitivi to do editing operatings. The only bug I really found was my sound rendering is a bit odd unless I use 48000hz. It can use any format supported by Gstreamer, and is written in python.
[http://en.wikipedia.org/wiki/PiTiVi](http://en.wikipedia.org/wiki/PiTiVi)

You can install with this link: [apt://pitivi]("apt://pitivi")

Or type:
```
sudo aptitude install pitivi
```

---

### Post by Stigmata13 on 2010-02-13
I've tried Pitivi and it works pretty well... the only thing I don't like is that there is no way to get it to cut the video at the exact frame of playback... instead you have to use the razor tool and click somewhere on the timeline... is there any way you can get pitivi to cut the video at the exact point in playback?

---

### Post by NightwishFan on 2010-02-13
Now that you think about it I am unsure. There are other video editors, such as Kdenlive, Avidemux, and Lives.

---

### Post by Stigmata13 on 2010-02-13
Avidemux never worked for me, it would just crash. Live's looked OK but it couldn't support larger files so that took away any reason to use it. kdenlive is nice though, aside from the fact that the audio gets choppy (even after looking up the problem, I still can't figure that one out.)
Well anyway I'm trying to make an AMV... my goal is to try to clip certain scenes, rearrange them to music and add video effects. The whole effects and music part is easy to do I'm just having some trouble splitting up that 700+ mb file into clips of the scenes I want :P

---

### Post by NightwishFan on 2010-02-13
Linux video editors are getting some attention lately, though the ones I like are a bit limited. I think if you can work it out Kdenlive may be your best option. I heard of a really good one called Cinelerra, but I have no idea how to install it.
[http://en.wikipedia.org/wiki/Cinelerra](http://en.wikipedia.org/wiki/Cinelerra)

---

### Post by philip5 on 2010-02-17
> **Stigmata13 said:**
> Avidemux never worked for me, it would just crash. Live's looked OK but it couldn't support larger files so that took away any reason to use it. kdenlive is nice though, aside from the fact that the audio gets choppy (even after looking up the problem, I still can't figure that one out.)
Well anyway I'm trying to make an AMV... my goal is to try to clip certain scenes, rearrange them to music and add video effects. The whole effects and music part is easy to do I'm just having some trouble splitting up that 700+ mb file into clips of the scenes I want :P
If you wish to try the latest (and greatest?!?!) version of kdenlive which right now is 0.7.7 and also its mediaframework mlt 0.5.0 you'll find packages for Karmic on my PPA on Launchpad. (See more info in my signature.)

The Kdenlive team have work alot to make the app more stable so as new version as possible is a goot bet to make it work more smoothly. The MLT framework have also got some attention and among them the cache handling. Maybe that will help with the sound problems you have?

Give it a try and have fun!

---

