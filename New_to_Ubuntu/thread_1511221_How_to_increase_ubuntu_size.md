---
title: "How to increase ubuntu size ?"
date: 2010-06-16
forum: New to Ubuntu
---

### Post by cantech on 2010-06-16
hi 
i use xp / ubuntu dualboot ..

at start i just decided to give ubuntu a try and made the size 5GB.. but now its not enough .. how can i increase it easily ? 

thanks

---

### Post by marty1011 on 2010-06-16
You need to use GParted (partition editor). Get the live cd from here: [http://gparted.sourceforge.net/]("http://gparted.sourceforge.net/")

---

### Post by cantech on 2010-06-16
> **marty1011 said:**
> You need to use GParted (partition editor). Get the live cd from here: [http://gparted.sourceforge.net/]("http://gparted.sourceforge.net/")

after i download it what should i do ? 

real newbie here :(

---

### Post by marty1011 on 2010-06-16
After you download it boot it like you did with the live cd. From there use the application gparted. It will show you the primary hd /dev/sda and all the existing partion. Select a partion you want to increase and decrease and edit it (spcify a new size or drag the slider).

More information here [http://www.dedoimedo.com/computers/gparted.html]("http://www.dedoimedo.com/computers/gparted.html")

One caveat: remember to backup your important data. For safety

---

### Post by ajgreeny on 2010-06-16
Make sure you defrag your windows XP a couple of times first, as that way there will be less chance of error messages telling you the partition can not be shrunk any further.

I am assuming that you installed by partitioning in the first place, and did not use WUBI, which installs Ubuntu within windows.  I admit I am not even sure whether you can use WUBI from the usual netbook usb installation system, so this question may be a bit of a red herring.  If so, apologies, and sorry for perhaps confusing you even further.

---

