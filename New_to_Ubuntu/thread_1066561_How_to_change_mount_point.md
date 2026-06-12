---
title: "How to change mount point?"
date: 2009-02-11
forum: New to Ubuntu
---

### Post by Hutom on 2009-02-11
I think I have made a mistake. :D I installed Kubuntu in my desktop and other than the SWAP I made 2 partitions. In partition 1 I put the mount point as /. In partition 2 (this is the bigger partition) I put the mount point as /boot ](*,) (don't laugh). Now I can not access that partition. How can I change that mount point?

---

### Post by JohnLM_the_Ghost on 2009-02-11
You may do that in /etc/fstab

However beware... there must be system files in /boot
So you have to move those to partition 1
hmm

I could create a little scriptie to do it for ya... if ya want.

Anyway solution is
[LIST=1]
[*]Move /boot/* (whatever is in boot folder) to somewhere on root partition
[*]Unmount /boot partition
[*]Move boot files back (to now empty) /boot folder
[*]edit /etc/fstab for new mountpoint
[*]Reboot! (Warning! If you do it wrong... you might not boot up it again)
[/LIST]

Keep a LiveCD in reach :)

---

### Post by sleepyjon on 2009-02-11
moving /boot might make it so you can't boot, just be aware of that.

---

### Post by JohnLM_the_Ghost on 2009-02-11
Also on other hand... you could make you own folder in /boot partition (chown if necessary), leave mountpoint as is.

Then symlink the folder somewhere you feel it should be.

This would be safer, but it is not what you asked for...

---

### Post by Hutom on 2009-02-11
> **JohnLM_the_Ghost said:**
> Also on other hand... you could make you own folder in /boot partition (chown if necessary), leave mountpoint as is.

Then symlink the folder somewhere you feel it should be.

This would be safer, but it is not what you asked for...

Well, That would also do for the time being (at least until i understand this mount point business completely). But how can I do that? Give me a little detail instruction or I'll mess it up again. :confused:

How can I access that partition? How to mount it? Where shall I find it? I can't even see it right now. And then what to do?

---

### Post by Hutom on 2009-02-11
Ok. Suppose I try to make a directory in /boot. Two questions:

1) Is it possible to make a dir. in /boot by this mkdir command?

2) To reach that dir. every time do I need to use the terminal?

---

### Post by JohnLM_the_Ghost on 2009-02-11
hmm... I quite dunno way around KDE... but no, there should be a way where you can access the whole root tree. i.e. /

anyway now you can
```
cd /boot
sudo mkdir -v something
sudo chown -R hutom:hutom ./something
ln -sv /boot/something ~/
```

these commands will make a folder (replace "something" with what you fancy best), make owner of it you (assuming your username is hutom - replace if it is not) and make a symlink to your home folder.

You can move symlink whereever you like from there

EDIT: btw check then for free space in the new folder... to make sure it is on partition 2 (aka the /boot partition) (if it is not, then /boot is not mounted and ther is no use for this discussion :) ).
Also by typing ```
mount
``` into terminal will return any current mounts and their mountpoints

---

