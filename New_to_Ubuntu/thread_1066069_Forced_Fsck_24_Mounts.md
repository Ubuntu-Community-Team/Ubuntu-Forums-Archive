---
title: "Forced Fsck 24 Mounts"
date: 2009-02-10
forum: New to Ubuntu
---

### Post by Iwanthelp on 2009-02-10
Ok, well, I figure just like in the FG forums if I post my problem here I'll get more help than general help, so, here it is, we've also now got the exact error message:

```
checking root file system...                              [OK]
1005
fsck 1.41.3 (12-oct-2008)
/lib/init/rw/rootdev contains a file system with errors, check forced
/lib/init/rw/rootdev: Unattached inode 411743

/lib/init/rw/rootdev: UNEXPECTED; RUN fsck MANUALLY
		(i.e., without -a or -p options)
fsck exit status 4


							[fail]
	*an automatic file system check (fsck) of the root filesystem failed.
a manual fsck must be preformed, then the system restarted.
the fsck should be preformed in maintenance mode with the
root filesystem mounted in read-only mode.
	*the root filesystem is currently mounted in read-only mode.
a maintenance shell will now be started.
after performing system maintenance, press CONTROL-D
to terminate the maintenance shell and restart the system.
bash: no job control in this shell
root@ubuntu~#
```

I installed with Wubi and didn't partition. Sorry if that's the same thing, I'm not a nerd or geek or whatever you want to call it, especially not Ubuntu guru yet, only used it a couple months, me and my brother both don't know how to run the fsck. Help is much appreciated as I'd like to not reinstall everything again and theme it etc.

---

### Post by Drate on 2009-02-10
just do what it says basically, run fsck.

at that prompt there with th "#" sign type "fsck" and hit enter and I think that should get it running, hopefully will fix whatever errors it has.

---

### Post by Iwanthelp on 2009-02-11
You're absolutely sure it's that simple?

---

### Post by Iwanthelp on 2009-02-11
Nevermind, I just reinstalled.

---

### Post by Iwanthelp on 2009-02-12
How do I increase the forced fsck mount number? My brother says "'Cause then we won't have the 24 mount problem, will have the 50,000 mount problem. And no Linux distro ever lasts that long."

---

### Post by jerome1232 on 2009-02-12
> **Iwanthelp said:**
> Nevermind, I just reinstalled.

Are you serious... 

Would you reinstall Windows because it's asking you to run chkdsk after a bad restart?

That's what  fsck is, it's a **f**ile-**s**ytem **c**hec**k**. You just needed to do as the error prompted you to do and run fsck on the root paritition.

So since that maintenance shell said the file system was mounted read only you could've run this and checked the system.
```
fsck /
```

> **Iwanthelp said:**
> How do I increase the forced fsck mount number? My brother says "'Cause then we won't have the 24 mount problem, will have the 50,000 mount problem. And no Linux distro ever lasts that long.

Is this just an attempt to troll?

---

### Post by Iwanthelp on 2009-02-12
No, it's not an attempt to troll, he said to post it here.

> Are you serious...

Would you reinstall Windows because it's asking you to run chkdsk after a bad restart?

That's what fsck is, it's a file-sytem check. You just needed to do as the error prompted you to do and run fsck on the root paritition.

So since that maintenance shell said the file system was mounted read only you could've run this and checked the system.

My brother, who's the nerd of the family, said it wouldn't do anything since we used Wubi. But would it? We reinstalled again today when the last install was yesterday because it wanted an fsck and did a weird thing where it would log me out, and restart. I then couldn't google or use the address bar in Firefox so I logged out and it couldn't load the gdm and brought us to a recovery like screen and we tried moving the highlight and it made a beep every time and brought up fragments of... Terminal like text where it said a forced fsck was needed... Yeah, sorry for the long story. Anyways, would it work?

---

### Post by Iwanthelp on 2009-02-15
Bump?

---

### Post by jerome1232 on 2009-02-15
Oh yeah to change the frequency of forced file system checking, use tune2fs.

For example by default they are set to be checked every 24 mounts or 180 days which ever comes first. If I wanted to change it to every 10 mounts or 30 days I would do this

```
sudo tune2fs -c 10 /dev/sdxx
sudo tune2fs -i 30d /dev/sdxx
```

or (and I wouldn't do this routine checking is there for a reason) set it to never force fsck's

```
sudo tune2fs -c 0 /dev/sdxx
sudo tune2fs -i 0 /dev/sdxx
```

Check out the man page of tune2fs for more  detail's, here's the two options I was talking about

```
       -i  interval-between-checks[d|m|w]
              Adjust the maximal time between two filesystem checks.  No post&#8208;
              fix or d result in days, m in months, and w in weeks.   A  value
              of zero will disable the time-dependent checking.

              It  is  strongly  recommended that either -c (mount-count-depen&#8208;
              dent) or -i (time-dependent) checking be enabled to force  peri&#8208;
              odic  full  e2fsck(8) checking of the filesystem.  Failure to do
              so may lead to filesystem corruption (due to bad disks,  cables,
              memory, or kernel bugs) going unnoticed, ultimately resulting in
              data loss or corruption.

```

```
       -c max-mount-counts
              Adjust  the  number of mounts after which the filesystem will be
              checked by e2fsck(8).  If max-mount-counts is 0 or -1, the  num&#8208;
              ber  of  times  the filesystem is mounted will be disregarded by
              e2fsck(8) and the kernel.

              Staggering the mount-counts at which  filesystems  are  forcibly
              checked  will  avoid  all  filesystems being checked at one time
              when using journaled filesystems.

              You should  strongly  consider  the  consequences  of  disabling
              mount-count-dependent   checking  entirely.   Bad  disk  drives,
              cables, memory, and kernel bugs could all corrupt  a  filesystem
              without  marking  the  filesystem dirty or in error.  If you are
              using journaling on your filesystem, your filesystem will  never
              be marked dirty, so it will not normally be checked.  A filesys&#8208;
              tem error detected by the kernel will still force an fsck on the
              next reboot, but it may already be too late to prevent data loss
              at that point.

              See also the -i option for time-dependent checking.


```

---

### Post by Iwanthelp on 2009-02-18
Ooh, even better, none! Although, I have figured out how(Well, my brother, found a post here.) and I set mine to 999. I guess I'll now do never.(Something my brother read says it doesn't do anything in Wubi.)

EDIT: Ok, I tried but it says 

```
tune2fs 1.41.3 (12-Oct-2008)
tune2fs: Bad magic number in super-block while trying to open /dev/sda2
Couldn't find valid filesystem superblock.
```

It's weird, it worked before.

---

