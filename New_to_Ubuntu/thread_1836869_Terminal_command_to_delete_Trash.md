---
title: "Terminal command to delete Trash?"
date: 2011-08-31
forum: New to Ubuntu
---

### Post by greenelf on 2011-08-31
How do I delete my trash via terminal commandline? I have several thousand files in my trash, and it takes to long "preparing"

This is for 11.04.

---

### Post by aura7 on 2011-08-31
rm -rf ~/.Trash/*

---

### Post by Rex Bouwense on 2011-08-31
Try
```
rm -rf ~/.Trash/*
```

---

### Post by HunterDX77M on 2011-08-31
Here is the code that I think will work for you (please have someone double check):

```

cd ~/.local/share/Trash/files
rm -rf *

```

The first line will get you into the Trash's directory. The second removes **everything** in the directory. Check to make sure there is nothing important in there first! I hope this helps.

---

### Post by greenelf on 2011-08-31
> **Rex Bouwense said:**
> Try
```
rm -rf ~/.Trash/*
```

> **aura7 said:**
> rm -rf ~/.Trash/*

That worked, thanks!

---

### Post by Rex Bouwense on 2011-08-31
You are welcome.:popcorn:

---

### Post by AvengerX9 on 2012-09-18
I have the latest Ubuntu desktop now, but I cant make any of these commands work when I wanna delete my trash. So what changed ?

---

### Post by hypnot0ad on 2012-09-18
This is the only code working for me.

> **HunterDX77M said:**
> Here is the code that I think will work for you (please have someone double check):

```

cd ~/.local/share/Trash/files
rm -rf *

```


However this did not.

```
rm -rf ~/.Trash/*

```

---

### Post by AvengerX9 on 2012-09-18
nothing happens when I type that, just gets a new line :) And the first command gives me no such file or directory

---

### Post by jrog on 2012-09-18
> **AvengerX9 said:**
> nothing happens when I type that, just gets a new line :) And the first command gives me no such file or directory
In Linux, a new line (with no output) often means success. Are you sure it didn't successfully empty your trash?

---

### Post by AvengerX9 on 2012-09-18
Maybe, I dont know :), but I still have a problem with a very large disk use just for Ubuntu. How large is Ubuntu supposed to be? Its also serving as a webserver

---

### Post by jrog on 2012-09-18
> **AvengerX9 said:**
> Maybe, I dont know :), but I still have a problem with a very large disk use just for Ubuntu. How large is Ubuntu supposed to be? Its also serving as a webserver
How much disk space? Assuming your hard drive is /dev/sda (which it may not be), what is the output of:

```
sudo df -h /dev/sda
```

Ack, I also just noticed that you posted your questions here in a thread started in August of 2011. You shouldn't do that, and a moderator may end up closing this thread or modifying it in some way because you've bumped such an old thread.

---

### Post by AvengerX9 on 2012-09-18
it says:


filesystem: udev
size: 2,0g
used: 4,0k
avail: 2,0g
use%: 1%
mounted on: /dev

---

### Post by jrog on 2012-09-18
> **AvengerX9 said:**
> it says:


filesystem: udev
size: 2,0g
used: 4,0k
avail: 2,0g
use%: 1%
mounted on: /dev

Sorry, don't know why I included "/dev/sda" in there. I meant to ask for the output of just "sudo df -h".

---

### Post by AvengerX9 on 2012-09-18
Here it is

Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1        33G  4.0G   28G  13% /
udev            2.0G  4.0K  2.0G   1% /dev
tmpfs           806M  1.1M  805M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            2.0G  152K  2.0G   1% /run/shm
/dev/sdb1       100M   25M   76M  25% /media/Reservert av systemet
/dev/sdb2       233G  657M  233G   1% /media/D604DC4E04DC32EB

---

### Post by jrog on 2012-09-18
> **AvengerX9 said:**
> Here it is

Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1        33G  4.0G   28G  13% /
udev            2.0G  4.0K  2.0G   1% /dev
tmpfs           806M  1.1M  805M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            2.0G  152K  2.0G   1% /run/shm
/dev/sdb1       100M   25M   76M  25% /media/Reservert av systemet
/dev/sdb2       233G  657M  233G   1% /media/D604DC4E04DC32EB
That doesn't look bad. You've got a ton of free space on /dev/sdb2 and a decent amount of free space on /dev/sda1.

If you want to try to free up more space (I saw in another thread that you deleted trash and some log files), you might also try:

```
sudo apt-get autoclean
```

If you want to try to free up even more space, and you don't care about keeping a cache of files you have installed using apt-get, you can also try:

```
sudo apt-get clean
```

---

### Post by AvengerX9 on 2012-09-18
Thanks, I tried both of these now and I think it worked :) Do you know anything about moving the apache www dir to another disk by any chance ? :)

---

### Post by jrog on 2012-09-18
> **AvengerX9 said:**
> Thanks, I tried both of these now and I think it worked :) Do you know anything about moving the apache www dir to another disk by any chance ? :)
I do, but see your other thread about that (I replied there). Let's not mix the threads together.

---

