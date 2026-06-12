---
title: "screen tearing in Hulu &amp; youtube fullscreen"
date: 2010-12-17
forum: New to Ubuntu
---

### Post by maryalesia on 2010-12-17
YO! I upgraded to 10.10, managed to mess up plymouth & decided to just reinstall 10.04 until a stable release of maverick. Once I reinstalled 10.04, some irritating screen tearing issues that I'd thought I'd fixed resurfaced. 

I've updated my system, activated the accelerated graphics drivers (nvidia geforce 9800M gts), set it to "sync to v blank" in both compiz and nvidia settings & set the refresh rate to 60 in compiz. This dealt with tearing that occured when I moved windows around the screen & used the desktop cube. 

However, I continue to see tearing in videos streamed online. It only happens in fullscreen, and it's bad enough that I don't know what is happening. It occurs in both hulu and youtube,  so I don't think the problem is on their end. Obviously I have the flash plug-in installed. 

I have also installed the medibuntu repositories, which I remember doing when I first encountered this problem. I can't remember if it did anything or not. It didn't do anything this time. 

Please help! This is driving me crazy. I can't remember how I fixed this before.

---

### Post by maryalesia on 2010-12-17
PS - I don't encounter screen tearing when I'm playing video files I've downloaded. There is some issue with those in 720p quality, but other than that it is fine.

---

### Post by maryalesia on 2010-12-17
HA! I remebered the step I forgot! Add nvidia settings to startup applications. It was already there so I thought I could ignore it, but then I checked and it had a different command than what I used before. I left it be and added a new nvidia settings startup app with a command like 'nvidiasettings -l' or something. All fixed.:D

---

### Post by Boksa on 2011-03-31
can you explain what you exactly did ? i have same problem

thanks

---

