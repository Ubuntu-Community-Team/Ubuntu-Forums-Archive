---
title: "How to increase the deb packages cache size in ubuntu?"
date: 2009-04-25
forum: New to Ubuntu
---

### Post by legolas_w on 2009-04-25
Hi
I know that Ubuntu cache deb files which it downloads during apt-get install process. I want to know what is the current cache size, how I can increase this size and whether I can copy the cache content to another computer and expect it to use the cache content instead of downloading the same packages again?

Thanks.

---

### Post by stwschool on 2009-04-25
Can't say much about increasing cache size but I've copied the cache folder to another machine and it's saved a shedload of downloads so that does work.

---

### Post by legolas_w on 2009-04-26
comments are welcome

---

### Post by coffeeaddict22 on 2009-04-26
I use APTonCD.  It's in the repositories.

---

### Post by stwschool on 2009-04-26
Well it seems not to delete any until they become out of date, looking though the settings, so I'd say backing up the /var/cache/apt/archives folder (leave out the lock file and the partial folder though) is fine. I used tar to do the job and it was very effective when transferring to another machine, no downloads necessary.

---

### Post by joshedmonds on 2009-04-26
Ensure that you reload package information before applying any changes in the package manager.

---

### Post by fourscore on 2009-04-26
you can vary the apt-cache size and number of days to be kept in cache by editing the text  file "20archive" in  directory  /etc/apt/apt.conf.d

>sudo gedit  /etc/apt/apt.conf.d/20archive

Change the MaxAge for no of days and MaxSize ( in MB) for required size

---

