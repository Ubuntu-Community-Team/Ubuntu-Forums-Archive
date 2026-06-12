---
title: "Firefox is taking up 50-80% of my cpu. Is this normal?"
date: 2009-08-09
forum: New to Ubuntu
---

### Post by jalehtor on 2009-08-09
My desktop's been slowing lately, and when I get on a page with too many gifs, or when I have a number of pages open, it starts to sound like it's working hard--this could take up nearly 20-30 seconds--and slows down, or, rarely, freezes altogether. The noise goes down after a while, and then it speeds up.

Looked at top, and when the computer slows down, Firefox is usually taking up 60-80% of my CPU.

I'm wondering if this is normal?

I'm going to be dual booting with xp soon for games, but I want to make sure that Ubuntu is OK before I do that. 

Thank you!

---

### Post by SoftwareExplorer on 2009-08-09
It shouldn't take that much unless you have an ancient computer.

---

### Post by jerrrys on 2009-08-09
here are a couple of guides

[http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT004](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT004)

[http://kb.mozillazine.org/Firefox_hangs](http://kb.mozillazine.org/Firefox_hangs)

---

### Post by jalehtor on 2009-08-09
> **SoftwareExplorer said:**
> It shouldn't take that much unless you have an ancient computer.

It's not THAT ancient: HP Compaq D530 2.6GHz 3800GB 40GB

---

### Post by SoftwareExplorer on 2009-08-09
> **jalehtor said:**
> It's not THAT ancient: HP Compaq D530 2.6GHz 3800GB 40GB
Yeah, I kind of doubted that was the case. I was talking the Mhz processor range.

---

### Post by binbash on 2009-08-09
I have same problem on Ubuntu Jaunty , Ubuntu Karmic, Ubuntu Intrepid. I have tried over 15 versions of Firefox in 2-3 years. 

I installed debian and PClinuxOS on same computer and i never see %2 Cpu usage even. There is something wrong with Ubuntu packages or compile flags.

---

### Post by SoftwareExplorer on 2009-08-09
Not to say you don't have a problem, just to say that its not on every computer. My FF uses ~5% on a single core, no HT 2.4 GHZ CPU.

---

### Post by JoeNZ on 2009-08-09
Just to come from left-field. I recently tried Opera and that kept locking up on me so I turned to Epiphany. It seems sweet as so far.

---

### Post by jerrrys on 2009-08-09
it is strange how ff works for some and not others.  right now i have 4 ff windows open with tabs and running at 6% cpu usage.  and its just been that way from the start, no magic involved.

i did manage to slow it way down once.  did this by adding live radar to my google home page.  just like you, it would take 15 to 20 seconds to load a tab.

---

### Post by gradinaruvasile on 2009-08-09
If u load pages that have Flash content, it will eat CPU power and thats because of the Flash plugin - not the browser itself. 
There are pages that dont have much eyecandy but they use CPU like crazy Example [www.intend.ro](www.intend.ro)

It depends what kind of pages are you visiting. Opening Flash sites will eat your CPU no matter what (there are differences between browsers though - it seems Opera and Chromium uses less CPU than FF).

---

### Post by JoeNZ on 2009-08-09
For some reason when I used Opera, it chewed up my cpu & ram. I ran Firefox at the same time and it used far less. I ran the 'top' command in a terminal to compare the two.

---

### Post by gradinaruvasile on 2009-08-09
Which version of Opera?
 I use 10.00 Beta 2 Qt4.5

---

### Post by jalehtor on 2009-08-09
Is there a solution? Btw, this was not an issue earlier on; it's been going on for only a few months, and I've been using ff all along. Is there a different version of ff that might not do this?

---

### Post by JoeNZ on 2009-08-09
9.64

---

### Post by arky on 2009-08-09
While testing Karmic I found that firefox would end up consuming lot of CPU and hit the roof.

The problem was gone when I cleanup all firefox-3.0.x packages and used firefox-3.5

---

### Post by gradinaruvasile on 2009-08-09
Well i see that u have a P4@1500 mhz. That isnt strong processor anyways. I have a Dell C640 Laptop with P4M@1800 - If i use firefox, it heats up like crazy, the fan is on all the time. U should try the new 3.5 firefox or midori.

---

### Post by jerrrys on 2009-08-09
what about "firefox lite", will that run any better on a P4?  have not tried it myself...and [jalehtor]("http://ubuntuforums.org/member.php?u=727193"), post #3, there are a couple of good tips there about keeping ff cleaned out...

---

### Post by jalehtor on 2009-08-09
> **gradinaruvasile said:**
> Well i see that u have a P4@1500 mhz. That isnt strong processor anyways. I have a Dell C640 Laptop with P4M@1800 - If i use firefox, it heats up like crazy, the fan is on all the time. U should try the new 3.5 firefox or midori.

> **jerrrys said:**
> what about "firefox lite", will that run any better on a P4?  have not tried it myself...and [jalehtor]("http://ubuntuforums.org/member.php?u=727193"), post #3, there are a couple of good tips there about keeping ff cleaned out...

I will download 3.5. Jerrrys, yes, there are good tips there. 

THANK YOU.

---

