---
title: "Getting video to stream in ubuntu"
date: 2010-04-13
forum: New to Ubuntu
---

### Post by ZJ88 on 2010-04-13
Hey,
 
I am trying to stream some videos on my website but they don't seem to want to load outside my network. I have apache2 installed. It's just a simple html website, nothing fancy. Do I need to change some apache config files to allow it to stream video? my website is at [www.hirekriskringle.com]("http://www.hirekriskringle.com")
 
Thank you, Zachary Larsen
 
P.S. I know the website name and actual site don't match but I am on a tight budget and I want to get the kinks out before I buy a new domain name.
 
P.P.S. I just checked my site at a friends and noticed that 2/3 videos work in internet explorer but only 1/3 work in fire fox.

New update: I've heard from some people that sometimes none of the videos will load and other times that all of them work.  Wondering why this may be...

---

### Post by Doctor Mike on 2010-04-14
> **ZJ88 said:**
> Hey,
 
I am trying to stream some videos on my website but they don't seem to want to load outside my network. I have apache2 installed. It's just a simple html website, nothing fancy. Do I need to change some apache config files to allow it to stream video? my website is at [www.hirekriskringle.com]("http://www.hirekriskringle.com")
 
Thank you, Zachary Larsen
 
P.S. I know the website name and actual site don't match but I am on a tight budget and I want to get the kinks out before I buy a new domain name.
 
P.P.S. I just checked my site at a friends and noticed that 2/3 videos work in internet explorer but only 1/3 work in fire fox.

New update: I've heard from some people that sometimes none of the videos will load and other times that all of them work.  Wondering why this may be...When I try to open the "not working" video in movie player (Ubuntu) it says file location not found. Could be you need to provide an absolute address for the video file your trying to embed.

---

### Post by philinux on 2010-04-14
It says the video link to the first one is this videos/life.wmv/videos/life.wmv

---

### Post by ZJ88 on 2010-04-14
Hmm strange.  I'll have to check it again, it seems some of my links keep adding stuff or changing.  Not sure why, I might be accidentally adding something.  I'll try the absolute link.  Thanks for the help.  I've also noticed that when you do click on a video link or something, it will just stay at connecting to media.

Also, I have noticed that sometimes not adding the www in front for some reason doesn't load the videos correctly. Not sure if that has something to do with it.  I also found that the videos would work for a time then i'd reload the page or go back to one of the videos and it would no longer load.

---

### Post by Doctor Mike on 2010-04-14
> **ZJ88 said:**
> Hmm strange.  I'll have to check it again, it seems some of my links keep adding stuff or changing.  Not sure why, I might be accidentally adding something.  I'll try the absolute link.  Thanks for the help.  I've also noticed that when you do click on a video link or something, it will just stay at connecting to media.

Also, I have noticed that sometimes not adding the www in front for some reason doesn't load the videos correctly. Not sure if that has something to do with it.  I also found that the videos would work for a time then i'd reload the page or go back to one of the videos and it would no longer load.Are you hosting your own server or is it hosted?

---

### Post by ZJ88 on 2010-04-14
I'm hosting my own.  It's not a very big or fast server but it should be able to get the job done.

---

