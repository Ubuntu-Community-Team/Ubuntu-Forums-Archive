---
title: "Firefox - Choppy Video Playback"
date: 2009-04-21
forum: New to Ubuntu
---

### Post by LesterPalooza on 2009-04-21
Hardware specs:
[LIST]
[*]amd athlon dual core 64
[*]NVidia GeForce 8200M G
[*]1 ghz
[*]3GB RAM

[*]NVidia Prop drivers enabled (updated to 180)
[*]**_Desktop effects set to None_**
[*]_**Compiz not running**_
[*]Videos on hard drive play superbly. :)
[*]Laptop running on Ubuntu 8.10 32-bit.
[*]Gnash not installed
[/LIST]

I go to youtube.com and select a random video to watch, and videos are choppy and appears to be out of sync, has cuts horizontally and occasionally makes firefox irresponsive. I am not playing the video on fullscreen and _the video is in normal quality_. I am running firefox 3.0.8 for intrepid ibex and just installed flash plugins using the terminal:

```
sudo apt-get install flashplugin-nonfree
```

It was downloading flash player 10 (the latest one I believe) and rebooted the PC and restarted firefox. Video is still choppy..

Question: Any ideas why this is happening?

EDIT: Switched to 64-bit Ubuntu. Made programs run faster for me. Including flash.

---

### Post by inobe on 2009-04-21
one question' what happens with youtube quality when you disable desktop affects ?

---

### Post by LesterPalooza on 2009-04-21
> **inobe said:**
> one question' what happens with youtube quality when you disable desktop affects ?

Still choppy. :(

---

### Post by inobe on 2009-04-21
are these 720p HD videos ?

how  do video's on your hard drive workout ?

---

### Post by LesterPalooza on 2009-04-21
> **inobe said:**
> are these 720p HD videos ?

how  do video's on your hard drive workout ?

Nope. Normal quality videos in youtube. avi videos mounted from drive from Windows play absolutely fine.

---

### Post by inobe on 2009-04-21
then it's strange because it's not leading towards nvidia !

i could only assume it's an isolated flash issue...
have you restarted since the flash update ?

i am not understanding why you are experiencing this if you did restart.

some suggestions

you did

```
sudo apt-get install flashplugin-nonfree
```

why not ?

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by LesterPalooza on 2009-04-21
> **inobe said:**
> then it's strange because it's not leading towards nvidia !

i could only assume it's an isolated flash issue...
have you restarted since the flash update ?

i am not understanding why you are experiencing this if you did restart.

some suggestions

you did

```
sudo apt-get install flashplugin-nonfree
```

why not ?

```
sudo apt-get install ubuntu-restricted-extras
```

Okay I typed:

```
sudo apt-get install ubuntu-restricted-extras
```

in the terminal and restarted. Some problems occured including being unable to mount my drives and missing Desktop icons. I tried watching YouTube videos and well.. nothing changed. Still choppy and videos still cut horizontally. :(

How I can revert back? I removed restricted extras and did not bring back my desktop icons and still cannot mount my drives. :( Man.... I'm not liking this...

---

### Post by Jazzy_Jeff on 2009-04-21
I don't know what could be causing the problem. One thing I would suggest is to install Opera browser through the package manager and see if you have the same problems. Maybe something is weird through Firefox.

---

### Post by LesterPalooza on 2009-04-21
> **Jazzy_Jeff said:**
> I don't know what could be causing the problem. One thing I would suggest is to install Opera browser through the package manager and see if you have the same problems. Maybe something is weird through Firefox.

I found this article:

[http://www.phoronix.com/scan.php?page=article&item=616&num=1](http://www.phoronix.com/scan.php?page=article&item=616&num=1)

says something about firefox having problems with flash plugins.

btw, I AM RUNNING 32-bit Ubuntu 8.10

---

### Post by Jazzy_Jeff on 2009-04-21
> **LesterPalooza said:**
> I found this article:

[http://www.phoronix.com/scan.php?page=article&item=616&num=1](http://www.phoronix.com/scan.php?page=article&item=616&num=1)

says something about firefox having problems with flash plugins.

btw, I AM RUNNING 32-bit Ubuntu 8.10


I am running 32-bit Ubuntu 8.10 as well and all videos play fine. Your system is faster than mine also. Like I said in my other post, try using Opera. It is a great browser and see if you have the same problems with it. Then you will know if it is a browser issue or something else.

---

### Post by inobe on 2009-04-21
> **LesterPalooza said:**
> Okay I typed:

```
sudo apt-get install ubuntu-restricted-extras
```

in the terminal and restarted. Some problems occured including being unable to mount my drives and missing Desktop icons. I tried watching YouTube videos and well.. nothing changed. Still choppy and videos still cut horizontally. :(

How I can revert back? I removed restricted extras and did not bring back my desktop icons and still cannot mount my drives. :( Man.... I'm not liking this...

i seriously doubt those extras causing such behavior.

could you tell us what you did or the steps you followed prior to getting flash installed ?

did you follow any guides before launching 

```
sudo apt-get install flashplugin-nonfree
```

---

### Post by laluz on 2009-04-22
I understand you have already downloaded flash10 from Adobe. Have you installed it? Basically you have to run the adobe binary from the command line and answer to a few questons.

---

### Post by bobbo85 on 2009-04-24
I have been searching for a solution to this for about a year and have not found one.  It seems to be a flash issue, not a linux one, so I found a bug report at adobe.com and voted for it to be fixed.  

Please vote for the issue to be addressed here (I did):
[http://bugs.adobe.com/jira/browse/FP-1692](http://bugs.adobe.com/jira/browse/FP-1692)

---

### Post by afonteijn on 2009-05-15
I have had this problem ever since I started using linux (early 2007). In the mean time I have installed a variety of linux distos (32 and 64 bit) on several computers using nvidia and linux video chips. It is more visible on slower computers (p4 and such), but even on my new 3ghz dual core machine the videos in HD are a bit choppy. (you need to look carefully, but it is there). I think that adobe's flash is just not programmed very efficiently. The same videos run fine using movie player or vlc.

---

### Post by NHArticleTen on 2009-05-15
> **afonteijn said:**
> I have had this problem ever since I started using linux (early 2007). In the mean time I have installed a variety of linux distos (32 and 64 bit) on several computers using nvidia and linux video chips. It is more visible on slower computers (p4 and such), but even on my new 3ghz dual core machine the videos in HD are a bit choppy. (you need to look carefully, but it is there). I think that adobe's flash is just not programmed very efficiently. The same videos run fine using movie player or vlc.

I second this commentary

---

