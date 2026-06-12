---
title: "new to ubuntu and my screen wont turn on"
date: 2011-06-13
forum: New to Ubuntu
---

### Post by hellcatt on 2011-06-13
ive tried using both wubi.exe and a burned cd and when i try to boot into ubuntu my laptop runs but my screen is not just blank but doesnt even seem to turn on.

---

### Post by parkerskouson on 2011-06-13
What did you use to burn the instalation cd?

---

### Post by hellcatt on 2011-06-13
windows image disk burner. but even with wubi i get the same action and i tried that before any cd

---

### Post by parkerskouson on 2011-06-13
I would try and download Imgburn, as it specializes in .ISO burning. Then just using it to burn the .ISO.

---

### Post by hellcatt on 2011-06-13
ok i have that anyway ill try that

---

### Post by parkerskouson on 2011-06-13
Let me know if that helps. Also, ubuntu uses a different format type. so that might be the problem.

---

### Post by hellcatt on 2011-06-13
> **parkerskouson said:**
> Let me know if that helps. Also, ubuntu uses a different format type. so that might be the problem.

can you elaborate? and is there a way to fix my problem in wubi?

---

### Post by nzjethro on 2011-06-13
If you have a USB stick lying around, download unetbootin ([http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)) and you can make a Live "CD" on your USB. It'll load faster, and it may help with these issues if it didn't burn properly.

---

### Post by parkerskouson on 2011-06-13
The drive format is just how to OS reads the HDD. Windows( which is what i am assuming that you are using) uses drive format Ntfs. Ubuntu uses drive format ext3. A format of the HDD is nesicary for a install.

---

### Post by hellcatt on 2011-06-13
> **parkerskouson said:**
> The drive format is just how to OS reads the HDD. Windows( which is what i am assuming that you are using) uses drive format Ntfs. Ubuntu uses drive format ext3. A format of the HDD is nesicary for a install.

so im wasting my time trying to run it off of a cd without a partition?

btw second cd using imgburn didnt change anything

---

### Post by nzjethro on 2011-06-13
> **hellcatt said:**
> so im wasting my time trying to run it off of a cd without a partition?

btw second cd using imgburn didnt change anything

No, not wasting your time. When you get the live CD to boot, you can run GParted to alter (create, format, etc.) your partitions. Did you try unetbootin? Is it possible that your download was wrong? I don't know the size of the install .iso, but maybe check out the Ubuntu homepage and see if your file is the right size. Else it may have downloaded wrong.

---

### Post by hellcatt on 2011-06-13
im downloading unetbootin right now so ill try that next, its going incredibly slow. which version should i get anyway?

---

### Post by nzjethro on 2011-06-13
> **hellcatt said:**
> im downloading unetbootin right now so ill try that next, its going incredibly slow. which version should i get anyway?

Um, up to you. I'm using 10.10, as you can see, and have had absolutely no issues with it. But I've heard that 10.04LTS is rock solid, and there are a lot of very smart people on here running LTS, so heaps of support. Maybe give that a try? I'd stay away from 11.04. What were you looking at?

---

### Post by fabricator4 on 2011-06-13
> **hellcatt said:**
> im downloading unetbootin right now so ill try that next, its going incredibly slow. which version should i get anyway?

Which version of Ubuntu?  I'd really recommend 10.04 LTS for newcomers.  LTS means "long term support" - it's supported until April 2013 is relatively problem free at installation.

You problem may be related to your graphics card.  Ubuntu 11.04 has a whole lot of new code relating to graphics and the desktop and problems with this are causing people installation problems.  As I said, I'd recommend 10.04 to the newcomer.

If you can't boot the machine off the LiveCD and try it out successfully, then it's most likely that an install won't work either.

Chris

---

### Post by hellcatt on 2011-06-13
ok well that helps alot because i was trying 11.04. i dont see LTS in unetbootin tho. if it matters any im doing this purely for android purposes even tho ive been curious about linux for a long time

im downloading LTS from the ubuntu site now

---

### Post by parkerskouson on 2011-06-13
Sad to say but basicly.

---

### Post by nzjethro on 2011-06-13
> **hellcatt said:**
> ok well that helps alot because i was trying 11.04. i dont see LTS in unetbootin tho. if it matters any im doing this purely for android purposes even tho ive been curious about linux for a long time

im downloading LTS from the ubuntu site now

Smart choice. LTS will be a good move, and it's similar enough to 10.10 that there is a hell of a lot of support here for it. If LTS doesn't boot properly, post back. :)

---

### Post by hellcatt on 2011-06-14
got it going guys, thanks for all the help

---

### Post by dFlyer on 2011-06-14
Burn a live cd and see if you can get to the desktop, off the cd.

---

### Post by wildmanne39 on 2011-06-14
Hi, are you still trying to do a wubi install? if you are you install it through windows and you do not format the partition as told to do in a previous post. This is for a wubi install if you are still trying to use wubi.
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)
[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Differences+between+Wubi+vs+dual-booting&as_qdr=all&sa=Google+Search&lang=en#911](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Differences+between+Wubi+vs+dual-booting&as_qdr=all&sa=Google+Search&lang=en#911)
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by fabricator4 on 2011-06-14
> **hellcatt said:**
> got it going guys, thanks for all the help

Excellent!  Chalk another one up for LTS :-)

If you have any more questions, come back and see us ;-)  and welcome to the forums.

Chris.

---

### Post by nzjethro on 2011-06-14
> **hellcatt said:**
> got it going guys, thanks for all the help

Cool, good to hear. Want to mark this thread as solved so others with the same problem know this is a solution?

---

