---
title: "partitioning"
date: 2009-06-10
forum: New to Ubuntu
---

### Post by trypanon on 2009-06-10
Hi all,
i'd like to ask in advance regarding following "issue":
i have installed fresh ubuntu station, where defined 3 partitions during the installation - 1st for root (/), 2nd for files (/home), & 3rd for swap.
the question is how can i check all partitions i physically have, cause in fact i'm using only "/" partition at the moment. should i mout what was predefined in installation? i thought that there's posibility to use multiple partitions exatly like in windows - for system & for data separately. am i wrong? where?

---

### Post by kwacka on 2009-06-10
Your / partition is where all system files are stored, /home is where data & user's settings are stored.

You could, for example, further divide your / partition (e.g. /bin, /usr) whilst your /home partition is already subdivided into /home/userA, /home/userB, etc.

---

### Post by trypanon on 2009-06-10
i paid attention that /home folder's weight approximatelly as i defined. but it sits altogether with another system folders. is it ok? i expected to get additional drive icon

---

### Post by gwoodruff on 2009-06-10
The OS mounts the file systems at boot. Your partitioning scheme is the simplest way to keep your home data secure from the system files. If you had to reformat your boot partition your home partition would stay intact. You could use synaptics to install gparted to look at your partitions and keep track of free space on each partition.

Gary

---

### Post by Cheesemill on 2009-06-10
You're thinking with a Windows mindset.

With Linux all of your partitions are mounted under / no matter how many you have, there is no such thing as 'drive letters'.

To check what partitions you have mounted just open a terminal and type
```
df -h
```

Cheesemill

---

### Post by trypanon on 2009-06-10
ok, got it,thanx a lot!
but the last question still remains opened : is there possibility visually split the icons of home from "/"? the one who made the step to linux was me, but not my wife. it is still hard to her :)

---

### Post by Cheesemill on 2009-06-10
If you just want an icon for the home directory on the desktop you can just create a symbolic link:
```
ln -s /home/rob /home/rob/Desktop/
```
Obviously replacing rob with your username.

Cheesemill

PS - This can be used to create links anywhere, the syntax is just
```
ln -s [TARGET] [LINK_NAME]
```

---

### Post by trypanon on 2009-06-11
than-q all!

---

