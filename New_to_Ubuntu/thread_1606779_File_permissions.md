---
title: "File permissions"
date: 2010-10-26
forum: New to Ubuntu
---

### Post by wightghost on 2010-10-26
Just installed 10.10.  Pretty impressed overall but I'm having problems getting required access to my files on a separate partition.

I have been using 'gksu nautilus' to change permissions on folders but the files within those folders are still locked out - I can open them but can't make any changes, delete or move them.  Rhythmbox won't import my music files even though the folders are unlocked because the files within are still locked out.

Short of unlocking each file individually (a very tedious process) how do I unlock these files?

The partition is /dev/sda2 and named 'Files'.  Looking forward to some help.
Thanks

---

### Post by DooM55 on 2010-10-26
```
chmod -c 777 <file name>
```

try this code may help u 
:guitar:

---

### Post by papibe on 2010-10-26
It is very uncommon that the the files on a local partition files are "blocked". Is it a NTFS partition (windows)? Could you post the result of these commands:
```
$ mount -l
```
```
$ cd /files
$ ls -l
```
Regards.

---

### Post by wightghost on 2010-10-27
Sorry,
it's an **ext4** partition

> brad@EAST:~$ ls -l
total 176
drwxr-xr-x 2 brad brad  4096 2010-10-22 11:35 Desktop
drwxr-xr-x 2 brad brad  4096 2010-10-22 11:35 Documents
drwxr-xr-x 2 brad brad  4096 2010-10-22 14:24 Downloads
-rw-r--r-- 1 brad brad   179 2010-10-22 11:09 examples.desktop
drwxr-xr-x 2 brad brad  4096 2010-10-22 11:35 Music
drwxr-xr-x 2 brad brad  4096 2010-10-22 11:35 Pictures
drwxr-xr-x 2 brad brad  4096 2010-10-22 11:35 Public
drwxr-xr-x 2 brad brad  4096 2010-10-22 11:35 Templates
drwxr-xr-x 2 brad brad  4096 2010-10-22 11:35 Videos

---

### Post by SeijiSensei on 2010-10-27
> **wightghost said:**
> Short of unlocking each file individually (a very tedious process) how do I unlock these files?

Use the -R switch to recurse down the directory tree.

```

chown brad.brad -R .
chmod u+rw,go+r -R .

```

should change the ownership of all files below the current directory to user and group brad and will change the permissions so user brad has read/write privileges and everyone else has read privileges.

---

### Post by papibe on 2010-10-27
SeijiSensei's solution is what I was going to replay, but if after a reboot you have the same problem, then you need to change the mount options. I hope not.

Regards.

---

### Post by wightghost on 2010-10-28
> **SeijiSensei said:**
> 

```

chown brad.brad -R .
chmod u+rw,go+r -R .

```

should change the ownership of all files below the current directory to user and group brad and will change the permissions so user brad has read/write privileges and everyone else has read privileges.

It worked!! Thanks so much SejiSensei and to everyone else who took the time to reply.:)

I should spend more time learning about the terminal. It has a lot of power.

Brad

---

### Post by quirkification on 2010-10-28
Sweet deal, after a reformat of my whole drive. windows virus... i was had. i felt like an idiot. it was a really good way of making me think i have threats and i installed the "anti-virus" JERKS.

but yea, thanks i now have access to every file since I finally did a fully opened install.

[PHP]chmod u+rw,go+r -R /[/PHP]FTW!!!

---

### Post by JKyleOKC on 2010-10-28
Of course you also made it possible for any intruder to totally demolish your system, or to turn it into a botnet member and even deny you access...

But everyone has the right to choose their own preferences!

---

### Post by georgetom on 2010-10-28
> **DooM55 said:**
> ```
chmod -c 777 <file name>
```

try this code may help u 
:guitar:
I'm glad you could chown and fix it.
777 is deadlier than 666!! :p

---

