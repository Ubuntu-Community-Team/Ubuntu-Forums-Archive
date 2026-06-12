---
title: "Is there a way to make Ubuntu act as a Media Server for a Playstation 3?"
date: 2010-04-29
forum: New to Ubuntu
---

### Post by diablo75 on 2010-04-29
My girlfriend just got me a Playstation 3 (her way of saying thanks for remodeling the bathroom/I love you/Happy Early Birthday).

I've never really messed with one of these things before in depth but someone told me about how they were able to setup some sort of Media Server in Windows for the PS3 to access (for playing music or videos or whatever).  But I don't use Windows...

Anyone have some suggestions?

---

### Post by tarps87 on 2010-04-29
I am currently using [Media tomb]("http://mediatomb.cc/") which works fairly well, I have had issues with some video formats, then again the version I am using is about a year old.
There is this one in the community documentation:
[https://help.ubuntu.com/community/Ps3MediaServer](https://help.ubuntu.com/community/Ps3MediaServer)
I have not tried it, but it is worth a try

---

### Post by Hignar on 2010-04-29
PS3MediaServer works very well.  You need to make sure you have mplayer, mencoder and ffmpeg installed if you want it to transcode on the fly.

---

### Post by buntunoob on 2010-04-29
Here's the how-to I've used [http://wiki.flexion.org/InstallingMediaTomb012.html](http://wiki.flexion.org/InstallingMediaTomb012.html) There are a few things missing from it if you have a new install. Like build-essential,

---

### Post by diablo75 on 2010-05-22
Well I followed the steps for PS3MediaServer from this link:

[https://help.ubuntu.com/community/Ps3MediaServer](https://help.ubuntu.com/community/Ps3MediaServer)

And I have to say IT WORKS GREAT!

There was one little catch I had to work out for myself.

My server has Firestarter installed, so I had to watch the events viewer when I told the PS3 to scan for media servers.  I had to create two new rules for my firewall and unblock ports 5001 and 1900.  Then the PS3 hooked right up and was able to play back my files immediately, transcoding on a mere Pentium 4.  It works great!!!

---

