---
title: "Not sure how to transcode Mkv files to a more &quot;playable&quot; format"
date: 2010-02-07
forum: New to Ubuntu
---

### Post by Salamancero on 2010-02-07
A friend of mine gave me a bunch of .mkv files for some light entertainment but I'm encountering a lot of stuttering on playback. I've optimized Mplayer as best as I could but I think its really my old laptop's hardware that's limiting proper playback (Celeron M 1.6 ghz,2 gig ram, Ati Express 200m vid card).  I'm thinking of transcoding (is that the proper term?) the files to something that my laptop can run better but I'm not sure what software to use.  Can anyone give me some pointers?  I'll try to figure things out on my own from there. :) 

Thanks!

---

### Post by hemimaniac on 2010-02-07
Go and get your self [Handbrake]("http://handbrake.fr/downloads.php") it is imo the ultimate for video converting, or if you want to use something more native, there is avidemux, or devede in the repos, avidemux is a good tool and the latter is perfect for converting to dvd. devede is one of the few convert to dvd tools that will handle ,mkv files, but if you want to go with an .avi format, Handbrake would be the option for you

---

### Post by Salamancero on 2010-02-07
Thanks for the info!  I'll give Handbrake a go. :)

---

### Post by nhasian on 2010-02-07
mkv is used usually for high definition videos.  if your hardware is not capable of smooth playback [hint celeron] then you probably want to downsample them to a lower resolution with handbrake.

---

### Post by solitaire on 2010-02-07
try playing then using cvlc it's installed with the vlc player.
it's a basic player and I can use it to play 720p with my Laptop 2Ghz Celeron with a intel mobile graphics. (cpu stays at around 75% when on fullscreen)

also best to stop all other programs and apps before playing..

---

### Post by Salamancero on 2010-02-13
Thanks for the tips guys.  I'll give cvlc a try too.  I just found out that handbrake doesnt transcode to avi anymore.  I was hoping I could lower the resolution to something more playable but I haven't had the chance to go over the manual yet.  :)

---

### Post by goldshirt9 on 2010-02-13
meGUI is a great tool but i'm not sure if it runs in ubuntu 
[http://forum.doom9.org/archive/index.php/t-112931.html](http://forum.doom9.org/archive/index.php/t-112931.html)

---

### Post by samantha_ on 2010-02-13
try avidemux.
Dont expect any filesplitting or editing from it yet, because of [https://bugs.launchpad.net/ubuntu/+source/avidemux/+bug/496739](https://bugs.launchpad.net/ubuntu/+source/avidemux/+bug/496739)

---

### Post by Salamancero on 2010-02-16
> **goldshirt9 said:**
> meGUI is a great tool but i'm not sure if it runs in ubuntu 
[http://forum.doom9.org/archive/index.php/t-112931.html](http://forum.doom9.org/archive/index.php/t-112931.html)

I've never heard of that but I'll give it a shot sometime soon. Thanks!

---

### Post by Salamancero on 2010-02-16
> **samantha_ said:**
> try avidemux.
Dont expect any filesplitting or editing from it yet, because of [https://bugs.launchpad.net/ubuntu/+source/avidemux/+bug/496739](https://bugs.launchpad.net/ubuntu/+source/avidemux/+bug/496739)

I just downloaded avidemux and I'll probably start tinkering around with it in a few days time.  Thanks for the all the info you've been providing.  :)

---

