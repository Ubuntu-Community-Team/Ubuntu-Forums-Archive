---
title: "ubutnu netbook eee pc 702 - running SLOW"
date: 2009-06-20
forum: New to Ubuntu
---

### Post by ibizatunes on 2009-06-20
Hello
 My G.F has just been given a eee pc 702 8G. So far i have ubuntu netbook remix and its dog slow..... i have tried over clocking to 900 mhz but i cant find any good guides (all the guides are for normal ubuntu) not the netbook remix

1 would i be better installing eeebuntu UNR version is this more efficient?

My CPU is currently running at 635 mhz and i have 1 GB of ram...... I would like my cpu running at 900 mhz but cant seem to get it to work, can some one help please?
Regards

---

### Post by Hospadar on 2009-06-20
I can't say anything specific about overclocking, other than that I would expect it to happen in the bios.  (although it is possible to overclock in software)

As to general speed, you can use some kind of performance monitor to look at what stuff is running, perhaps you will discover certain programs going super slow or eating your resources.

The monitors I like are run from the terminal.  I particularly like htop (you'll need to install it, "sudo apt-get install htop"), and then "htop"

It shows a good overview of clock time usage, memory usage, priority (the "nice" vanlue, from -20 20), etc.  You may be able to isolate the problem, or at least understand what's taking so long.

You might also want to try using something even lighter, like fluxbox or one of the other *box environments, they are extremely lightweight and very snappy.

---

