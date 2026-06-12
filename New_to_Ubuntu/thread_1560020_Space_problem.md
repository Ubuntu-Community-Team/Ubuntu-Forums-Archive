---
title: "Space problem"
date: 2010-08-24
forum: New to Ubuntu
---

### Post by Aklyon on 2010-08-24
How could I get ubuntu to use both the tiny amount of hard drive space on my eee pc 900 and the 500GB on my WD My Book external hard drive? the "very low disk space" message is getting annoying. the external hard drive is brand new, nothing on it except what it came with on it.

---

### Post by warfacegod on 2010-08-24
A very basic answer.

Move all your data to it and put some links in your Places menu.

You might run:```
sudo apt-get autoclean
```

Might help make some more space on your internal HDD.

---

### Post by Paqman on 2010-08-24
I've got a 16GB EeePC and find Ubuntu runs well without ever running out of space. Just do a little bit of [housekeeping]("http://ubuntuforums.org/showthread.php?t=140920"). 

I'd also highly recommend uninstalling extra kernels that you aren't using. Open up Synaptic and filter for installed packages called "linux-image". Completely remove all but the most recent one, this will free up about 100MB per kernel, which is golden on a small disk.

---

### Post by Aklyon on 2010-08-24
how would i move it, though? all thats there is ubuntu (and everything that came with it, plus restricted extras), GIMP, VLC player, and TeamSpeak3.

Edit: good liink, Paqman.

---

### Post by Paqman on 2010-08-25
You can't really move the actual installation easily, only your data. Like warfacegod says, empty all your docs, pictures, videos, music, etc out of your home folder and put it on the external drive.

Ubuntu itself only needs about 8GB and can be run on systems with as little as 4GB, so you should have plenty of space if you clear out the junk and your data. How big is your drive, and how much of it are you currently using? Running your drive very full is a bad idea, the filesystem will fragment heavily. This is much less of a problem on an SSD than a hard drive, though.

---

