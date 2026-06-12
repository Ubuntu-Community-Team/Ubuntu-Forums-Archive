---
title: "PC freezing"
date: 2011-02-11
forum: New to Ubuntu
---

### Post by ryansanchez88 on 2011-02-11
It's true, I am an absolute beginner with linux. I switched over from windows 7, which was having a blue screen problem, with an ubuntu 8.10 cd and have been getting used to the linux world, and I like it.

I get a freeze almost every session, usually during video play through mozilla. I looked at var/log dmesg but I don't know exactly what i'm looking for so I figured it was time to register an account and start learning what the heck I'm doing.

When the freeze happens I lose all keyboard and mouse ability, the video stops playing, but the audio almost always continues playing through the video being watched and I have to do a hard reboot.

I don't want to post the whole dmesg log unless I have to so if I need a certain section just let me know.

-I know this post is probably not sufficient to diagnose the problem but if I could get some guidance on what information to provide i'll do it quickly.

Thanks!
 
Glad I registered!

---

### Post by davidmohammed on 2011-02-11
hi there and welcome to the forums.

There could be many reasons for "freezing" - either software or hardware.  For your windows blue screen, were there any error messages reported?  May be they could indicate a hardware issue.

if you post your hardware specifications as per the forum sticky, we can help further.

---

### Post by desnaike on 2011-02-11
If u are indeed running 8.10 my suggestion is to install 10.04 or 10.10 then see if u still have problems.

---

### Post by 3rdalbum on 2011-02-11
> **desnaike said:**
> If u are indeed running 8.10 my suggestion is to install 10.04 or 10.10 then see if u still have problems.

I would agree with this. Ubuntu 8.10 is ancient - it's like trying to surf the web on Firefox 1.5.

However: Crashes on Windows, crashes on Linux. Sounds like a hardware problem. Most hardware problems that cause crashes are either graphics cards or bad RAM. If you can, take out some of your RAM and see if that helps; if it doesn't, then put it back in and take out the rest of it. If you can't do that, then try running Phoronix Test Suite's memory benchmark; it will reliably crash a computer with bad RAM, and then you'll know that this is the problem.

For your graphics card, check that you've got enough airflow going into your computer case and that the card's fan is running and is not clogged with dust. The final test you can do, if you haven't already found the problem, is to take some load off the power supply to check if the graphics card is getting enough power.

---

