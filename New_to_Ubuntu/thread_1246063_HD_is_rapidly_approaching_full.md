---
title: "HD is rapidly approaching full"
date: 2009-08-21
forum: New to Ubuntu
---

### Post by jcats on 2009-08-21
I recently checked gparted, and it says my Ubuntu partition is 95% full.
I have a 150 GB HD, dual booted w/ XP. 30 GB is for XP, the rest is for Ubuntu (8.10). 

df -h shows:
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2             115G  104G  4.8G  96% /
tmpfs                 759M     0  759M   0% /lib/init/rw
varrun                759M  324K  759M   1% /var/run
varlock               759M     0  759M   0% /var/lock
udev                  759M  2.8M  756M   1% /dev
tmpfs                 759M  356K  759M   1% /dev/shm
lrm                   759M  2.2M  757M   1% /lib/modules/2.6.27-14-generic/volatile

I have run apt-get clean and emptied the trash.
I have run/checked Disc Usage Analyzer and Filelight. My / is 13GB and that is the biggest file.
I can't figure out what is filling up the HD

Any help or directions would be most appreciated.
Thanks;
jcats

---

### Post by bumanie on 2009-08-21
Suggest you try > sudo apt-get autoclean

---

### Post by quanumphaze on 2009-08-21
Run the Disk Usage Analyser program in Accesories to get a nice pie chart of what is eating all your space. (or use file size view in Konqueror if you use KDE)

---

### Post by mapes12 on 2009-08-21
I had a similar problem. This sorted me out: [http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)

---

### Post by jcats on 2009-08-21
Thank you,mapes12, . That was the problem. Thanks again

In a slightly different note-wasn't there a way to post a thanks, if you felt somebody helped?
How do I mark this post as solved?

---

### Post by mapes12 on 2009-08-21
> How do I mark this post as solved?There used to be an option in Thread Tools but it's gone. So to do this click on edit of your first post. Then Go Advanced then add [SOLVED] at the begining of your Title to the thread.

Yeh, I was gksu nautilus and deleting stuff not knowing that all I was doing was filling up roots trash bin.

Glad to be of assistance.

Land of the free...........:guitar:

---

