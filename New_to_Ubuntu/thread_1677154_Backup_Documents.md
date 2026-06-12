---
title: "Backup Documents"
date: 2011-01-28
forum: New to Ubuntu
---

### Post by jrev on 2011-01-28
Hi all,

What are you using in order to backup your files (Documents) ?

there are 2 different alternatives :

1) Scripts in command line
2) Dedicated applications

tell us which do you prefer and why 

Thanks

---

### Post by sikander3786 on 2011-01-28
Sorry you were focusing on Documents and I don't backup my documents individually.

I prefer Clonezilla. It is capable of cloning disks, making backup images, is available as a Live CD and can backup over the networks.

[http://clonezilla.org](http://clonezilla.org)

---

### Post by mharrison on 2011-01-28
I use rsync myself.  I have an external drive and just backup my entire /home/user directory to the external drive.

---

### Post by jrev on 2011-01-28
> **mharrison said:**
> I use rsync myself.  I have an external drive and just backup my entire /home/user directory to the external drive.

Can you give us the script doing it ?

---

### Post by mharrison on 2011-01-28
> **jrev said:**
> Can you give us the script doing it ?

Sure

```
rsync -zvra /home/user /media/drivename/user
```

---

### Post by bizz101 on 2011-01-28
Deja dup!

Perfect for me. Set it & forget it. :popcorn:

---

### Post by vanadium on 2011-01-28
rsync certainly is most suited for having very quick (hence with a much better chance regular and up to date) backups of your personal data, and it is the way for you to go.

You may also use the graphical backuptool "Back in time". This relies on rsync, but is configured to create "snapshots" of your backups. It does that without using a lot of extra space, because not changed files are only hard linked, and thus occupy their disk space only once for all snapshots.

For your purpose, "Backup Documents" (what everybody should do), taking an image certainly is a very bad idea. This would involve that you have to copy your entire system each time you have worked on a few files. Where an rsync backup will take 10 seconds, a disk image might take 30 minutes or more (I really do not know: could be even more).

> **mharrison said:**
> Sure
```
rsync -zvra /home/user /media/drivename/user
```

Why do you use the -z option? It does not make sense when the copy is not over the network. As your processor needs more work, it probably will slow things down.

Whay do you use the -r option? This is already implied in the -a ("archive) option.

Hint: take a look at the man pages when you try a command.

An adequate command is:
```
rsync -av /home/user /media/drivename/user
```

If you want your backup to be a "mirror", you can add the --delete option: files that you deleted will also be deleted in the backup. Otherwise, they will be accumulating there. Obviously, be careful with that option, and do not exchange source and destination. In case the destination is still empty, the result would be catastrophical ...

---

### Post by mharrison on 2011-01-28
> **vanadium said:**
> 
Why do you use the -z option? It does not make sense when the copy is not over the network. As your processor needs more work, it probably will slow things down.

Whay do you use the -r option? This is already implied in the -a ("archive) option.

Hint: take a look at the man pages when you try a command.

An adequate command is:
```
rsync -av /home/user /media/drivename/user
```

If you want your backup to be a "mirror", you can add the --delete option: files that you deleted will also be deleted in the backup. Otherwise, they will be accumulating there. Obviously, be careful with that option, and do not exchange source and destination. In case the destination is still empty, the result would be catastrophical ...

Actually, the command line I got was given to me by someone and it worked so I never questioned it.  I added the A because I was reading and saw that it kept the date and time stamp info and I liked that.  It didn't say anything about not need R so I kept R in there.  I'll try removing the Z and R though, especially if this speed things up a bit.

---

### Post by vanadium on 2011-01-28
Removing z will (theoretically) speed up, removing r will not make a difference (it is implied in a).

---

