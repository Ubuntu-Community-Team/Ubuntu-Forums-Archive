---
title: "Youtube streams very slowly..."
date: 2010-01-11
forum: New to Ubuntu
---

### Post by cozski on 2010-01-11
Hello

I have a recurring problem with Youtube... the videos never seem to stream quickly enough, resulting in lots of pauses. My connection is so fookin fast you could be here in miuntes! But not via youtube.... any thoughts?

Thanks :)

---

### Post by philinux on 2010-01-11
> **cozski said:**
> Hello

I have a recurring problem with Youtube... the videos never seem to stream quickly enough, resulting in lots of pauses. My connection is so fookin fast you could be here in miuntes! But not via youtube.... any thoughts?

Thanks :)

It's most likely there bandwidth that is the problem. Hit the pause button and let the vid download then hit play.

I'm not seeing any delay here. Which vid streams bad for you. Post a link

---

### Post by frenchn00b on 2010-01-11
[COLOR="Red"][B]It is due to LINUX and the youtube player : adobe flash player 10 known to be x2 faster under WINDOWS XP than under any LINUX[/COLOR]

tell and manifest your interest to the community to having a GNU version free and much better to see flash !!!! 

my install:
```

$ dpkg -l | grep flash
ii  flashplugin-nonfree                  1:2.5~bpo50+1                  Adobe Flash Player - browser plugin
ii  kwordquiz                            4:3.5.9-2                      flashcard and vocabulary learning program fo
```[/B]

---

### Post by The Secret on 2010-01-11
Have had this problem for a while now, even when on Windows. Not sure who's fault is it but it seems that it's time for YouTube to upgrade their servers and/or connection :p

---

### Post by stoogiebuncho on 2010-01-11
I've also noticed this on Windows as well as Ubuntu.  My theory is that youtube doesn't want to pay the bandwidth to send you the entire video if you're only going to watch 30 seconds of it, so it streams the first part at a high speed, and then streams the rest in little bursts as you continue to watch the movie.  If you look at your network activity while you watch the video you can see this happening.  A lot of video sites do this, actually.

So my guess is that this is on youtube's end.  They're not properly determining how fast they need to send you the information to keep your video from pausing.

The fact that this doesn't happen on other video sites suggests that it's not a flash or Ubuntu problem.  

But I'm with you.  It's as annoying as heck to wait for a video to load when you pay for a fast connection.

---

### Post by cozski on 2010-01-13
Well it's odd alright... in some cases when I pause the stream to alow it to buffer on many occasions it's not even buffering either... so cant get around it that way. Now in fairness, on some occasions, it does stream without any problems - but not often enough) I've tried a few other streaming sites (vimeo, johnlocker, freedocs) and there doesn't appear to be a problem... gonna keep tinkering anyway ;) Thanks for advice... appreciated.

---

### Post by stoogiebuncho on 2010-01-13
Good luck. :)  If you come up with any solutions, let us know.

---

### Post by J V on 2010-01-13
cheap n dirty hack, but saves you lots of time:

set the yt player to mute, play the vids, and have a shortcut leading to a script that cps all the Flash* files to your desktop, wait till its done with the video, hit the button, watch on desktop, easy :P

---

