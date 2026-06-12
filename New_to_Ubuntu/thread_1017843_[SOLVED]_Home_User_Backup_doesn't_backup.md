---
title: "[SOLVED] Home User Backup doesn't backup"
date: 2008-12-21
forum: New to Ubuntu
---

### Post by Charlie Chick on 2008-12-21
Hello Everybody,

I've just tried to backup my entire Home folder using Home User Backup. I want to backup onto my external USB 2 hard drive formatted as NTFS. The program sees the drive all right, but when I click 'backup' it says that it has finished in 3 seconds flat! Needless to say, nothing was backed up. What am I doing wrong?

Thanks,

Charlie

---

### Post by jerome1232 on 2008-12-21
Personally I use rsync to make backups of my home folder. I'm downloading hubackup right now (I'm assuming that's the program your using) to give it a spin and see what works.

Rsync is simple to use and makes the backups go quick (it only updates what has changed since the last backup)

```
rsync -av ~/ /path/to/destination
```

edit: I'm not sure why hubackup isn't working for you it seems very straight forward and is working as expected for me.

---

### Post by Charlie Chick on 2008-12-22
I think that it must have something to do with the fact that the external USB drive is formatted in NTFS. I tried using Home User Backup again, but this time selecting the desktop as an experiment. It worked. Looks like I'm going to have to re-format the drive as EXT 3.

---

### Post by nhasian on 2008-12-22
i use sbackup to backup my home folder.

```
sudo apt-get install sbackup
```

---

### Post by Charlie Chick on 2008-12-29
I gather that a new Ubuntu Home User Backup program (like Apple's Time Machine) is in the pipeline. I think that I'll wait for that.

---

