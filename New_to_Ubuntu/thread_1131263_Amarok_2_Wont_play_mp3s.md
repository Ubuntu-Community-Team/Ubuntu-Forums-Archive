---
title: "Amarok 2 Wont play mp3s"
date: 2009-04-20
forum: New to Ubuntu
---

### Post by betterthanjordan79 on 2009-04-20
hi i installed 9.04 beta a few days ago and have been havin problems wit amarok 2.it opens and seems to operate fine but it will not play mp3s(and possible no other music-i havent tried). anyone able to help me with this problem r anyone else having this problem???

Thanks in advance 
Daniel

---

### Post by inobe on 2009-04-20
are you getting any errors Daniel ?

have you checked the obvious like sound/mixer levels, also did you install restricted extras .....

is this an up grade to 9.04 ?

---

### Post by betterthanjordan79 on 2009-04-20
yes i have done both-rythembox is workin fine so i assume there using the same thing...no this was a clean install.

---

### Post by inobe on 2009-04-20
so you assume that your choice of music is playing except you hear nothing ?

edit: i see it's not kubuntu, my bad

seems that amarok may be missing a requirement, did you follow a guide similar to this 

[http://monespaceperso.org/blog-en/2009/03/15/how-to-install-amarok-2-on-ubuntu-810/](http://monespaceperso.org/blog-en/2009/03/15/how-to-install-amarok-2-on-ubuntu-810/)

---

### Post by betterthanjordan79 on 2009-04-20
no im runnin ubuntu 9.04 as shown in my screen shot,also im runnin amarok 2 as also shown.what happens is that it tries to play a track but just jumps past it till playlist is completed...

[IMG]http://g.imagehost.org/0816/Screenshot.png[/IMG]

---

### Post by fooman on 2009-04-20
do you have the ubuntu-restricted-extras package installed (probably need [FONT=monospace]libxine1-ffmpeg as well)[/FONT]?

if not, try opening a terminal (applications > accessories > terminal) and type or copy/paste the following command:

```
sudo apt-get install libxine1-ffmpeg ubuntu-restricted-extras
```

after they install,  close amarok if it was open....then restart it.

hope that helps

---

### Post by inobe on 2009-04-20
> **inobe said:**
> so you assume that your choice of music is playing except you hear nothing ?

edit: i see it's not kubuntu, my bad

seems that amarok may be missing a requirement, did you follow a guide similar to this 

[http://monespaceperso.org/blog-en/2009/03/15/how-to-install-amarok-2-on-ubuntu-810/](http://monespaceperso.org/blog-en/2009/03/15/how-to-install-amarok-2-on-ubuntu-810/)

:)

---

### Post by betterthanjordan79 on 2009-04-20
> **fooman said:**
> do you have the ubuntu-restricted-extras package installed (probably need [FONT=monospace]libxine1-ffmpeg as well)[/FONT]?

if not, try opening a terminal (applications > accessories > terminal) and type or copy/paste the following command:

```
sudo apt-get install libxine1-ffmpeg ubuntu-restricted-extras
```

after they install,  close amarok if it was open....then restart it.

hope that helps

that was actually my problem...i though i had installed them already...now i feel like a fool...anyways thanks for your help inobe and also for ur help fooman!!!

---

### Post by john stiles on 2009-04-20
I recall I installed the lame package to get Banshee to play nicely with jaunty. I'm sure the actual release will iron out the usual non-free issues.

---

### Post by smokeslikeapoet on 2009-04-21
I got mp3 support and playback working with Amarok 2 on Jaunty (not Kubuntu) by installing these packages:
```

sudo aptitude install libxine1-ffmpeg kubuntu-restricted-extras phonon-backend-xine
```

---

### Post by mrbinitie on 2009-04-23
Yes that does work.

---

### Post by fr0gg on 2009-04-30
Hey guys, I'm having difficulty getting Amarok to play my music files..It's loaded all of the contents of my Ipod, but when I try and play, i get a message that reads "Audio Output Unavailable: the Device is Busy xine parameters:" I'm fairly certain it's something strange with my X-fi, just downloaded the drivers creative released, and audio works otherwise, just not in Amarok.
Any suggestions?
Thank you.

It seems the x-fi drivers are a bit dodgy, but they're working now, still no luck with amarok though

---

### Post by Nightreaver1986 on 2009-08-13
Yeah, the command here is what worked for me too. Depends on what kind of iPod you're using, but iPods are touchy things on Linux anyway. Maybe try reading one of the iPod support threads, see if this is a problem discussed somewhere in there?


sudo aptitude install libxine1-ffmpeg kubuntu-restricted-extras phonon-backend-xine

---

