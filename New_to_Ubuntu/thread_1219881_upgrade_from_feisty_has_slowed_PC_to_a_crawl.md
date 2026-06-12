---
title: "upgrade from feisty has slowed PC to a crawl"
date: 2009-07-22
forum: New to Ubuntu
---

### Post by ginestre on 2009-07-22
I upgraded from Feisty to 8.10, the next LTS and have found that everything is SO slow, particularly if the net is involved. CPU usage goes up to 70% when using Firefox, for instance.

Any ideas on what to do?


TIA

---

### Post by s.fox on 2009-07-22
Hi :) ,

Can you tell us the specifications of your computer?   It  may be time for a hardware update.

-Silver Fox

---

### Post by mjstelly on 2009-07-24
> **ginestre said:**
> I upgraded from Feisty to 8.10, the next LTS and have found that everything is SO slow, particularly if the net is involved. CPU usage goes up to 70% when using Firefox, for instance.

Any ideas on what to do?


TIA
It's not Linux. The problem is with Firefox and Flash. I installed 9.04 and would regularly max the cpu doing even the most simple of tasks, like scrolling the mouse wheel. I performed the tweaks from two reference sites that now have my cpu rarely peaking above 60%

**      [Firefox optimization and troubleshooting thread  ]("http://ubuntuforums.org/showthread.php?t=1193567&highlight=favorite+web+browser")**
[Speed Up Firefox web browser]("http://www.ubuntugeek.com/speed-up-firefox-web-browser.html")

                         I'm not sure exactly which piece of advice actually resolved the issue. But I did them all and now Firefox runs twice as fast. 

Also note that there is a known Linux bug in Adobe Flash that causes most of the problems you are experiencing with your web browsing because so many sites use Flash as their UI.

Hope that helps.

---

### Post by LowSky on 2009-07-24
just so you know 8.10 isn't a LTS, 8.04 is the LTS.
also sounds like a flash issue

---

### Post by QIII on 2009-07-24
If Flash is indeed your "problem" -- that is if you installed the flash-installer and went to a Flash site where it was installed -- you may actually be having conflict problems with swfdec or gnash.

I would remove swfdec and gnash and see if your performance improves.

---

