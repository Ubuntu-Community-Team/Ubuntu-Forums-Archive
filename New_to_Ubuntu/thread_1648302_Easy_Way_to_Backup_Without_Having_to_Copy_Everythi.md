---
title: "Easy Way to Backup Without Having to Copy Everything?"
date: 2010-12-18
forum: New to Ubuntu
---

### Post by teejay17 on 2010-12-18
Is there an easy way to backup up specific files and folders? More specifically, I have a picture folder with about 15 gigs of photos on that I periodically backup on an external hard drive. The problem is that this takes so darn long! Is there a way that Ubuntu can look, and then backup only the photos and/or folders that have been added since the last backup? This would save time by not having to copy over everything...
I'm not sure what to call such a process, or where to look, but it is something that I greatly would like to accomplish.
Thanks in advance.

---

### Post by Ocxic on 2010-12-18
check out rsync

---

### Post by CharlesA on 2010-12-18
> **Ocxic said:**
> check out rsync

+1.

Also Check out RLB:

[http://ubuntuforums.org/showthread.php?t=912460](http://ubuntuforums.org/showthread.php?t=912460)

---

### Post by oldfred on 2010-12-18
More on rsync for backup.

Originally Posted by MountainX View Post #20 also other backup apps
[http://ubuntuforums.org/showthread.php?t=868244&highlight=backup](http://ubuntuforums.org/showthread.php?t=868244&highlight=backup)

one of my lines from my version of above which I use:
rsync -aruvP /mnt/data_DT/Documents /usr/local/fred/data/

Note that a rsync backup is not an archive. If you delete or change something that will be in the copy. You need to also copy to an external hardcopy - DVD, Tape drive or other device to have historical copies.

---

### Post by earthpigg on 2010-12-18
[http://www.psychocats.net/ubuntu/backup](http://www.psychocats.net/ubuntu/backup)

---

### Post by sgosnell on 2010-12-18
Install grsync, if it isn't already.  It's a GUI interface for rsync, and it makes backing up your system easy.  Rsync is fine, but it's a command-line app, and you have to do some research to get the results you want.  Grsync simplifies it, and saves multiple configurations, so you can back up different folders or drives at different times with a couple of mouse clicks.  It doesn't do anything rsync itself doesn't do, it just makes it easier for those who have shorter memories and less command-line experience.

---

### Post by teejay17 on 2010-12-19
Thanks everyone for your responses. I now have a few different options to try out when backing up files. Also some good leads to research further--at least I now know program names and all that good stuff.

---

### Post by Joeb454 on 2010-12-19
If you're looking for a DIY solution, ignore the rest of this post :)

If you're looking to simply backup important documents, it may be worth checking out [Dropbox]("http://www.dropbox.com"). It backs things up to their servers, while also syncing the files between your computers (provided dropbox is installed).

There's naturally a limit on the size with this method, if you wanted to backup your 16GB music library, for example, rsync would be my choice too :)

---

### Post by teejay17 on 2010-12-19
Thanks everyone. Grsync was exactly what I was looking for. Pretty easy to figure out, and I now have backed up my folders and it only transfered new files and folders that didn't already exist. A great time-saver.

---

