---
title: "need help with /HOME partition"
date: 2011-04-06
forum: New to Ubuntu
---

### Post by steninj on 2011-04-06
hi i'am using ubuntu 10.10..
i heard that creating a seperate /home partion is good so that i won't lose any data while reinstalling...
i've a separate /home partition,but it contains many hidden foldrs..
its due to the applications i installed,i know that..

bt what i need is:
get a home folder which contains only my datas and no other system files or hidden folders in it..&i dont want to lose it while reinstalling..

its like if u install windows in "C" drive,,all d pgrm files will b in "c" drive,,so dat we can get a pure "D"."E" drives...
i need the same thing here also.. 

currently device:/dev/sda5  mounted at:/home

my system specs:
160GB HD
1GB RAM

thnk u :)

---

### Post by mikewhatever on 2011-04-06
A home folder always contains user settings, there is no way around that. What you want is a separate data partition, in which case, you might not need a separate home at all.

---

### Post by Fire_Chief on 2011-04-06
Those folders contain the settings for your applications but not the applications themselves. The idea is that when you reinstall Ubuntu and put those apps back on the system, you don't have to reconfigure the application again. It starts up and "remembers" how you had it setup before.
Generally, these hidden folders don't consume a large amount of space and if it does, then it probably has some of your relevant data (email stores, etc) that you would want to keep anyway.

Cheers!

---

### Post by The Cog on 2011-04-06
As they say, those hidden folders contain all your personal application settings and preferences, not the applications themselves.

I would expect that you would want to retain those preferences when you reinstall the OS, to save hours of setting up each application's preferences again. 

However, if you really do want to have all the settings erased when you reinstall the OS, then I would suggest that you don't really want a sepatate /home partition at all. Instead, you probably want your home folders stored on the / partition, and to have a separate partition mounted elsewhere, perhaps create a mount-point /data in which you create a folder for each user with data, like /mnt/data/user1, /mnt/data/user2 etc. You can create a symlink in each user's home folder pointing to their data folder if you want to make things easier for them. Come back here and ask if you need help setting up an arrangement like this.

---

### Post by steninj on 2011-04-06
@mikewhatever,Fire_Chief,The Cog::

thank you so much for ur information guys..

i am new to ubuntu&i don't know much,but i really like ubuntu..

now wat i need actually is a separate data partition..
how to set it up?..
when i reinstall,,can i hv an option like,if i want i can keep the program data settings also along with my personal stuffs..
otherwise i cn avoid it.

anyways i don't want to lose my songs &movies etc...
last time i set up /boot,swap,/home and "/"
only /home was logical and other 3 were primary

i need ur help :)

---

### Post by seawolf167 on 2011-04-07
[Here ]("https://help.ubuntu.com/community/Partitioning/Home/Moving")is the official how-to for moving /home to a separate partition

---

