---
title: "Totem buffering problem with Apple trailers"
date: 2009-10-07
forum: New to Ubuntu
---

### Post by ucoder on 2009-10-07
Hi all,

I'm having trouble watching movie trailers from Apple's site. It seems as if the buffer is too small, causing the movie to stop frequently (playing only a couple of seconds).

I searched through the forums and some posts suggested tweaking the buffer from gconf-editor, but that doesn't seem to change anything. I tried both buffer-size and network-buffer-threshold

Currently movies open in a new Totem window, when I click the link in Firefox.
  
Any suggestions for how to fix this are welcome, also please mention if there is a better way / application for watching quicktime content.

I'm running Ubuntu 9.10

---

### Post by desmane on 2009-10-24
same here, settings in gconf-editor dont seem to do anything. 

It's great that totem opens automatically though, any idea how to fix it?

---

### Post by oboedad55 on 2009-10-24
I just gave it a try and am having no issues here. Could it be your internet connection? Are you running wireless?

---

### Post by desmane on 2009-10-24
good idea. Using eth  is a bit faster. It is the 1080p and 720p trailers not working, the little ones (up to 50mb) run fine --> assuming its the buffer size. Changed values in gconf-editor but that doesnt affect the buffer time, it starts playing after a couple of seconds --> the video interrupts many times that way. Pause doesnt work also.

---

### Post by oboedad55 on 2009-10-24
> **desmane said:**
> good idea. Using eth  is a bit faster. It is the 1080p and 720p trailers not working, the little ones (up to 50mb) run fine --> assuming its the buffer size. Changed values in gconf-editor but that doesnt affect the buffer time, it starts playing after a couple of seconds --> the video interrupts many times that way. Pause doesnt work also.

Ah, okay. I just tested it out using the smallest video. I didn't try the the big ones so that's probably the issue. Is there really that much difference in quality? I found the small file plenty easy to watch.

---

### Post by desmane on 2009-11-01
HD Trailers are quite awesome though ;-)

anyway not very important. 

other stuff: totem takes quite long to start playing and seeking is super slow too!

In addition, it askw to search for suitable plugins, if I click yes it cant find any and if I click cancel, it just plays (with problems mentioned above)! (it looks for teletext plugin...) whats going on, its the default player, thought it would just work :(

---

### Post by Aerodynamic on 2009-11-01
I also have this problem, totem starts to rebuffer all the time

Have tried tweaking the buffer settings with no better results.

It can't be problem with the wireless connection because i have run with the cable also and speed test shows around 10 Mbit/s

Dont' have any problems if i watch 480p Apple Trailers, just 720p and above.

Is this a bug in the Gstreamer plugin?

---

### Post by linuxbeaker on 2009-11-08
Embryonic to linux/ubuntu. I have this issue also - trying to convince the family that ubuntu can replace windows. I haven't seen this in any bug list - any help appreciated.

---

### Post by TBerk on 2009-11-13
Replying with a 'Me Too'; post;

It is not related to how fast your connection is, nor files size. The trouble is the value for buffering doesn't seem to 

A) adapt to the given conditions and/or 
B) isn't manually adjustable.

I can deal with an initial delay to buffer up a sizable percentage prior to playing. What I don't want is intermittent, continuous stopping and starting because a file under 50M is playing faster than I can download it.

How can we get at the settings to adjust the pre-fetch amount and/or the buffer value?


berk
btw- this is fodder for  'Multimedia & Video', rather than the 'Absolute Beginner' forum, isn't it?

---

### Post by TBerk on 2009-11-14
Oh and to purposely add insult to injury I want to add:

Flash (check Youtube for an example) allow for hitting the PAUSE button and caching the whole thing locally before watching it play.

Dem dere be Apples, how ya like em?


berk

---

### Post by finite9 on 2009-11-17
Has anyone logged a bug on launchpad for this issue?  If you have can you post the bug number here?

---

### Post by finite9 on 2009-11-18
[https://bugs.launchpad.net/totem/+bug/108623](https://bugs.launchpad.net/totem/+bug/108623)

Is the relevant bug report on launchpad for the buffering issue.  It has been open since Feisty and is confirmed with status "wont fix".

---

### Post by Mr.Kappa on 2011-01-09
Did anyone come up with a fix?? In 10.10 I still have this problem! It happens with vlc and totem :(

---

