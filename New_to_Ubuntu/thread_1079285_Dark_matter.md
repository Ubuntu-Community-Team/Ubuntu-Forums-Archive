---
title: "Dark matter"
date: 2009-02-24
forum: New to Ubuntu
---

### Post by gorade on 2009-02-24
There is something filling out my HDD, that I can't see. According to Baobab 2.24.1 Total capacity of hdd is 219,9 GB, Linux including home and all seems to be 9,2 GB, but used is 159 GB which leaves some 60 GB free. I can't find out what those near 150 GB is.
Running 
parted -l
df

gives: 
Filesystem 1K-block Used Avail Used% Mounted at
/dev/sdb1 230582768 166271036 52598744 76% /
tmpfs 1994764 0 1994764 0% /lib/init/rw
varrun 1994764 304 1994460 1% /var/run
varlock 1994764 0 1994764 0% /var/lock
udev 1994764 2892 1991872 1% /dev
tmpfs 1994764 12 1994752 1% /dev/shm

I am sure the "black matter" is some junk and want to remove it.
Does anyone know what this is?

---

### Post by llamabr on 2009-02-24
What's the ouput of df -h

Also, look in your /tmp dir.  Is there anything huge in there?

---

### Post by gorade on 2009-02-24
48 objects, totally  62,2 KB. That wasn't the corps.

---

### Post by laithbsoul on 2009-02-24
all I can come up with is try a fresh install of ubuntu 8.10

---

### Post by gorade on 2009-02-24
> **laithbsoul said:**
> all I can come up with is try a fresh install of ubuntu 8.10
Yes, as a last resort, but then I never will know what happened

---

### Post by llamabr on 2009-02-24
A fresh install to clean out a directory reminds me of a story about a sledgehammer and a fly.

What was the output of df -h

---

### Post by stumbleUpon on 2009-02-24
Also use du -hs in your home directory to find the usage of all the folders.
Sometime configuration directories (those whose names begin with a .) take up a lot of space. Check them as well.

---

### Post by llamabr on 2009-02-24
I'd guess a very large log file, filling up quickly.  do you notice that it's getting bigger, though you do nothing in particular?

look in /var/log for something giant.

if it's one large file, you can find it by looking for big files.  cd to / and run:

sudo find . -size +5000 -print | more

To then list dir's by size:

sudo du -sk * | sort -nk 1 | pg

---

### Post by gorade on 2009-02-24
> **llamabr said:**
> A fresh install to clean out a directory reminds me of a story about a sledgehammer and a fly.

What was the output of df -h

Filsystem            Storlek Anvnt Tillg Anv% Monterat på
/dev/sdb1             220G  173G   37G  83% /
tmpfs                 2,0G     0  2,0G   0% /lib/init/rw
varrun                2,0G  304K  2,0G   1% /var/run
varlock               2,0G     0  2,0G   0% /var/lock
udev                  2,0G  2,8M  1,9G   1% /dev
tmpfs                 2,0G   12K  2,0G   1% /dev/shm

---

### Post by newbee70 on 2009-02-24
Have you looked at your disk with gparted, or "disk usage in the apps acc"

they may give you a hint.

---

### Post by gorade on 2009-02-24
> **llamabr said:**
> I'd guess a very large log file, filling up quickly.  do you notice that it's getting bigger, though you do nothing in particular?

look in /var/log for something giant.

if it's one large file, you can find it by looking for big files.  cd to / and run:

sudo find . -size +5000 -print | more

To then list dir's by size:

sudo du -sk * | sort -nk 1 | pg

/var/log contains about 20 MB 
A disturbing thing is that the dark matter seems to have increased during the day. Now only about 36 GB remains. Something weird is going on.

---

### Post by gorade on 2009-02-24
> **llamabr said:**
> I'd guess a very large log file, filling up quickly.  do you notice that it's getting bigger, though you do nothing in particular?

look in /var/log for something giant.

if it's one large file, you can find it by looking for big files.  cd to / and run:

sudo find . -size +5000 -print | more

To then list dir's by size:

sudo du -sk * | sort -nk 1 | pg

/var/log contains about 20 MB 
A disturbing thing is that the dark matter seems to have increased during the day. Now only about 36 GB remains. Something weird is going on.

---

### Post by yther on 2009-02-24
Can you run "baobab" as root, using gksu?  That might give you a different perspective, in case the files are not readable by a normal user.

---

### Post by gorade on 2009-02-24
> **newbee70 said:**
> Have you looked at your disk with gparted, or "disk usage in the apps acc"

they may give you a hint.

both give about the same picture. gparted shows that 175 GB out of 223 are used. 

Disk usage shows my program and home directories If I add them I get around 20 GB there still is a mysterious 150 GB left.

---

### Post by newbee70 on 2009-02-24
> **gorade said:**
> both give about the same picture. gparted shows that 175 GB out of 223 are used. 

Disk usage shows my program and home directories If I add them I get around 20 GB there still is a mysterious 150 GB left.

When you use disk usage; does it show what is using the hidden unused space when you mouse over the areas? where is the heavy usage showing up?

Are you using trucrypt or another disk encryption program which will not show up ?

---

### Post by gorade on 2009-02-24
> **yther said:**
> Can you run "baobab" as root, using gksu?  That might give you a different perspective, in case the files are not readable by a normal user.
Hmm.. this one looks more like the culprit than the last one I shot down..
[IMG]/home/gorade/Skrivbord/Skärmbild-Diskanvändningsanalysator-1.png[/IMG]
There is a big chunk 175 GB called /media/ It seems like the program hdd contains a copy of two external discs that I use as backup. 
It seems to have the name Dokbackup_ 

That explains why free space is shrinking after I make a backup. Let's see how I get rid of it. Any hint?

---

### Post by yther on 2009-02-24
> **gorade said:**
> There is a big chunk 175 GB called /media/ It seems like the program hdd contains a copy of two external discs that I use as backup. 
It seems to have the name Dokbackup_ 

That explains why free space is shrinking after I make a backup. Let's see how I get rid of it. Any hint?

I suspect you are doing your backup in reverse.  :)

Instead of "copy /here to /there" you may have "copy /there to /here"... fix your backup task and that should solve your problem.

---

### Post by gorade on 2009-02-24
> **yther said:**
> I suspect you are doing your backup in reverse.  :)

Instead of "copy /here to /there" you may have "copy /there to /here"... fix your backup task and that should solve your problem.

Anyway the copies appear on the backup disks too. It seems like the program makes me an extra backup of my backup. 

My ordinary method of making a backup is a tar file in the root, then I copy this to the backup disk. Or so I thought I did. 

I thank you all for your help. Still I hesitate to label it solved since I still don't understand why this happens.

---

