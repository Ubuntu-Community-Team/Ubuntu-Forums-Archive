---
title: "getting ready to install 10.10 - fstab"
date: 2010-08-26
forum: New to Ubuntu
---

### Post by DouglasAdams on 2010-08-26
i am trying to get all my ducks in a row so i can install 10.10 as soon as it's released. i'm planning to do a clean install, from the live cd, formatting my root and /boot partitions in the process, my /home is on a different partition. however, it has taken me some time to get my fstab how i like it and i really don't want to start again. i am not planning on changing the location of any of my file systems.
questions:
what is the best way to preserve my current fstab?
is it possible / a good idea to place the /etc file system on a different partition that is not destroyed during a clean install?
or would doing that cause possible problems during a "clean install"?
thanks

---

### Post by Miljet on 2010-08-26
One of the better ideas that I have heard is to create a directory somewhere in your /home. Then every time you make changes to any configuration file, save a copy of it to that directory. That way you have copies of all changes you have made and can choose which ones to use again.

---

### Post by DouglasAdams on 2010-08-26
well {beep} me! i must be doing something right as i've already got a /backup directory in my /home that i use to save all sorts of stuff to, including my router config; browser bookmarks (a bit of a throwback to my affair with firefox).

i guess the only difference is that i don't know which config files i should save, or when they are changed, or even where they are located. 

just thought, ideally i'd love to save all my current cron jobs too ... where-ever they are located  :)

---

### Post by DouglasAdams on 2010-09-03
i am allowed to say, i love you ...
Ubuntu 10.10 Beta (Maverick Meerkat) Released

is locating the /etc fs on a partition that is not erased during a full install, keeping same /home, a good idea? ... or possible?

are there other fs's that could / should / might / possible / or certainly not / whatever ... during an install?

please?

---

