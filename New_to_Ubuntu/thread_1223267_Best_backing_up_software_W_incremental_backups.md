---
title: "Best backing up software? W/ incremental backups?"
date: 2009-07-26
forum: New to Ubuntu
---

### Post by spacesearcher on 2009-07-26
Hello, I'm getting tired of manually copying my files to an external drive. I was wondering if anyone could recomend a good program that can easily be setup to look for changes on my computer and store it to an external hard drive. And then have a setup so I can restore files how they were at a given backup? I have found Flyback and Timevault but it doesn't look like they have any recent releases.

---

### Post by presence1960 on 2009-07-26
> **spacesearcher said:**
> Hello, I'm getting tired of manually copying my files to an external drive. I was wondering if anyone could recomend a good program that can easily be setup to look for changes on my computer and store it to an external hard drive. And then have a setup so I can restore files how they were at a given backup? I have found Flyback and Timevault but it doesn't look like they have any recent releases.

rsync, if you want a GUI frontend grsync. Find them in the repositories thru synaptic package manager or run in terminal ```
sudo apt-get install grsync
```replace grsync with rsync in the above command for the CLI only version.

---

### Post by spacesearcher on 2009-07-26
> **presence1960 said:**
> rsync, if you want a GUI frontend grsync. Find them in the repositories thru synaptic package manager or run in terminal ```
sudo apt-get install grsync
```replace grsync with rsync in the above command for the CLI only version.

Is it possible to do incremental backups with this?

---

### Post by binbash on 2009-07-26
[http://blogs.techrepublic.com.com/10things/?p=895](http://blogs.techrepublic.com.com/10things/?p=895)

---

### Post by presence1960 on 2009-07-26
> **spacesearcher said:**
> Is it possible to do incremental backups with this?

yes. here is a link to a page describing setting up a backup scheme with grsync. it is from a pclinux user but is basically the same process on ubuntu. [http://ubuntuforums.org/showthread.php?t=1223267&goto=newpost](http://ubuntuforums.org/showthread.php?t=1223267&goto=newpost)

---

### Post by expatCM on 2009-07-26
I think that presence1960 really has his finger on the pulse.  grsync will be able to help you out here with minimal effort.  Whilst grsync is a gui for rsync the full functionality of rsync is not found though the grsync interface.  rsync has rather more flexibility if you need to be more precise about what you include and exclude but making the settings can be a total pain.

---

### Post by spacesearcher on 2009-07-26
> **presence1960 said:**
> yes. here is a link to a page describing setting up a backup scheme with grsync. it is from a pclinux user but is basically the same process on ubuntu. [http://ubuntuforums.org/showthread.php?t=1223267&goto=newpost](http://ubuntuforums.org/showthread.php?t=1223267&goto=newpost)

this just links to this page I think you may have made a copy/paste error.

and thanks binbash that looks like a good recent article.

---

### Post by presence1960 on 2009-07-26
> **spacesearcher said:**
> this just links to this page I think you may have made a copy/paste error.

and thanks binbash that looks like a good recent article.

sorry here it is: [http://mag.mypclinuxos.com/html/Issues/200708/page04.html](http://mag.mypclinuxos.com/html/Issues/200708/page04.html)

---

### Post by amac777 on 2009-07-26
For keeping incremental backups, I highly recommend rsnapshot. It is based on rsync and also uses a trick with hard links so it looks like it has taken a full backup each time, but the extra disk storage used is only for the files that changed.

```
sudo apt-get install rsnapshot
man rsnapshot

```

Also, lots of information about it here:

[http://rsnapshot.org/](http://rsnapshot.org/)

---

### Post by cybergalvez on 2009-07-26
get Back-in-time, its super easy to use, and makes incimental backups and 
[http://backintime.le-web.org/](http://backintime.le-web.org/)

---

