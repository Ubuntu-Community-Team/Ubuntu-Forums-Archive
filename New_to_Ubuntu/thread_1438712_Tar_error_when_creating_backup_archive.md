---
title: "Tar error when creating backup archive"
date: 2010-03-25
forum: New to Ubuntu
---

### Post by seawolf167 on 2010-03-25
I'm trying to create a backup file of my system using tar, but I am getting an error when the file is being created which exits the process.

Here is what I'm doing:

```

cd /
sudo su
tar cvpzf backup.tar.gz --exclude=/backup.tar.gz --exclude=/proc --exclude=/lost+found --exclude=/sys --exclude=/mnt --exclude=/media --exclude=/home /

```Which (to my understanding), puts everything from / into /backup.tar.gz (with the above exclusions left out)

I am getting the following error though:

```

...
/var/games/gnobots2.robots2-safe.scores
/initrd.img
tar: /: file changed as we read it

```So it is getting through everything (alphabetical from bin -> var), just erroring out on that file in /

Any help or suggestions would be appreciated!

BTW I'm using Ubuntu Linux 2.6.31-20-generic x86_64

---

### Post by baddnady23 on 2010-03-25
Check out this link:

[http://ubuntuforums.org/showthread.php?t=35087]("http://ubuntuforums.org/showthread.php?t=35087")

It worked perfectly several times for me and should fix your problem.

---

### Post by seawolf167 on 2010-03-25
It looks like I'm doing the same thing he has listed there - in the link you provided he does make this note:

"At the end of the process you might get a message along the lines of 'tar: Error exit delayed from previous errors' or something, but in most cases you can just ignore that."

Do you think the error I'm receiving one of the ones that is ignorable?

I googled initrd.img and its a RAM disk image used when booting the kernel, so I'm assuming this is because of my dual boot setup, so it should be ok to exclude it?

The file is 1.9 GB when it exits, so it sure looks like just about everything is included.

---

### Post by seawolf167 on 2010-03-25
After reading some more I think I should be ok ignoring the files that were skipped. I checked the created archive vs. the files that were supposed to be archived and everything is there but the ones listed below:

initrd.img (7.5 MB)
initrd.img.old (7.5 MB)
vmlinuz (3.8 MB)
vmlinuz.old (3.8 MB)

If, however, I need to include these files somehow, please let me know! 

Thanks!

---

### Post by Paddy Landau on 2010-03-25
May I strongly recommend a different way to back up your system?

Using tar is fine, but it's terribly slow.

[CloneZilla]("http://clonezilla.org/") is especially designed to back up or restore an entire partition (it can also back up or restore an entire disk). Like tar, it backs up only used space, and compresses the backup.

Try it.

---

### Post by seawolf167 on 2010-03-25
That actually looks pretty good Landau - I'll give it a try, thanks!

---

### Post by Paddy Landau on 2010-03-25
> **seawolf167 said:**
> That actually looks pretty good Landau - I'll give it a try, thanks!
I've used CloneZilla to back up the Windows partition that my children occasionally use. Whenever they manage to break the antivirus and get a virus, I simply restore that partition. (I've warned the children not to keep any important data on the Windows partition.)

I also back up the Ubuntu partitions with CloneZilla.

It's a little confusing to use, at first, but once you've got the hang of it, it's easy.

---

### Post by dirtyhabanero on 2010-08-21
seawolf,

did you end up just excluding those files in your tar backup? my backup finished when it is interrupted by one of those files, in my case the vmlinuz.old file. Is it safe to assume that this was the only file not copied and everything else has been?

i have been reading through another similar HowTo
[http://ubuntuforums.org/showthread.php?t=81311&page=1](http://ubuntuforums.org/showthread.php?t=81311&page=1)

---

