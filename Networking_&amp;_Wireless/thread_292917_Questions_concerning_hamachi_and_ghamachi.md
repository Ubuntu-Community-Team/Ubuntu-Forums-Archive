---
title: "Questions concerning hamachi and ghamachi"
date: 2006-11-04
forum: Networking &amp; Wireless
---

### Post by genekrupa on 2006-11-04
Using the HowTo written by KingofNowhere (thanx!) I have installed Hamachi on my Linux-box. When I started Hamachi from my powerbook and logged onto the same network, I could see the nick of my Linus-box. So I know it is running. 


However, I understand that I have to change the firewall-settings in my router to be able to run a remote VNC viewer. The question I have is: Do I have to give access to the full range of Hamachi-adresses (5.x.x...) or is it enough if I specify the precise adress that Hamachi assigns to my powerbook?

Also, I try to run ghamachi, the grafical interface for hamachi, but the furthest I get, is the following error:

*** glibc detected *** free(): invalid next size (fast): 0x081fe070 ***
Avbrutt (SIGABRT)

(avbrutt = aborted)

To me, this looks either like a bug or some kind of RAM-conflict in my machine, which would mean that I cannot run ghamachi. Is that so?


Let me just add that I am really pleased with Ubuntu that I installed only a couple of weeks ago, and likewise with all the friendly HowTo's and advice in the community! So far, it was a lot easier to find my way around in the Linux world than I expected.

---

### Post by genekrupa on 2006-11-05
I found a solution to the ghamachi-thing  in this thread in hamachi forum: [http://forums.hamachi.cc/viewtopic.php?t=2488&postdays=0&postorder=asc&start=90&sid=334c2c0335b9a26e88b50b3c93f7c1fc](http://forums.hamachi.cc/viewtopic.php?t=2488&postdays=0&postorder=asc&start=90&sid=334c2c0335b9a26e88b50b3c93f7c1fc)

"It is possible you have a ".lock" file that was not deleted from a previous session. You can remove the file like so:
Code:
$ rm ~/.hamachi/.lock"

Worked for me.

---

