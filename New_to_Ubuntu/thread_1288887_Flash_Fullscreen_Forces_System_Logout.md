---
title: "Flash Fullscreen Forces System Logout???"
date: 2009-10-11
forum: New to Ubuntu
---

### Post by 11010110 on 2009-10-11
Good evening all, 

I have no idea where to go or where to even begin a troubleshoot on this one... No mater which flash player is used on what site (youtube, facebook et cetera...), about 50% of the time that fullscreen is used, the system freezes and returns to the system log in screen. Once logged in again, all programs have exited and need to be restarted. Any assistance would be greatly appreciated.

Thank you all very much in advance.

---

### Post by coldReactive on 2009-10-11
All flash players? gnash, swfdec and the official flashplugin-nonfree? (You have to have one or the other installed, you can't have any combination of them.)

If flashplugin-nonfree is giving you that kind of issue, what is your graphics card (including video ram amount), RAM, processor speed, etc? (hardinfo might help)

---

### Post by stoogiebuncho on 2009-10-11
If you have an intel graphics card, you might be affected by a bug that hasn't been fixed yet.  Please open a terminal and post the output from this command:

```
cat /proc/mtrr
```

---

### Post by Orographic on 2009-10-12
Yes, it could be the known bug with flash full screen and related issues, try here:

[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

---

### Post by 11010110 on 2009-10-12
the output from cat /proc/mtrr is as follows:

reg00: base=0x000000000 (    0MB), size= 2048MB, count=1: write-back
reg01: base=0x07f700000 ( 2039MB), size=    1MB, count=1: uncachable
reg02: base=0x07f800000 ( 2040MB), size=    8MB, count=1: uncachable
reg03: base=0x0d0000000 ( 3328MB), size=  256MB, count=1: write-combining

And yes I do have an intel chipset (all information is included in my sig). I have done a lot of work on flash problems in the past including stuttering and freezing of the video itself. the logging out problems have just started recently. In order to fix those problems I had in the past I simply had to revert the Intel drivers back to 2.4 from intrepid and voila, all was well for about 3 months (give or take), and video itself is still relatively stable when not in fullscreen (limited staggering from time to time). The problem is only in browser based flash. When extracted and viewed through VLC then everything is gravy. It is a hassle to extract all flash videos to be viewed though. I also have the official plugin as downloaded from Adobe's site (the actual nonfree plugin from synaptic did not work for me as well in the past). And Orographic, the use of that tutorial, if you will, was what lead me to the fix that I used in the past. But thank you for the link I appreciate all of the help so far everyone!

---

### Post by CatKiller on 2009-10-12
To clarify, it's not that the system is arbitrarily logging you out. Something that the Flash plugin is doing is crashing X. So X restarts. When X starts, it automatically takes you to the login screen.

---

### Post by 11010110 on 2009-10-12
Right. Yeah sorry for the confusion I should have been more clear on that lol... Any ideas how I could restore stability? I had it working fine before so it puzzles me that it would start this mess again. Does anyone know why support for Intel graphics is so poor?

---

### Post by 11010110 on 2009-10-13
Bump

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2013-01-24
Strangely enough, this problem has occured on my Acer laptop with Precise 12.04. Just wandering if anyone has found a solution yet?

---

### Post by overdrank on 2013-01-24
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

