---
title: "Problem with my /etc/fstab file."
date: 2010-02-04
forum: New to Ubuntu
---

### Post by igriego on 2010-02-04
I was recently trying to format a flash drive and I changed a line in the /etc/fstab file and forgot to go back and undo my changes, now when I boot up it hangs and says that it is waiting on /dev/sdc which is the line I added to that file. I need to change that back but when I try using strictly the terminal it says that it is read-only.

---

### Post by oldfred on 2010-02-04
Possible explanation:
[http://xkcd.com/149/](http://xkcd.com/149/)




OK I was trying --- did you use sudo?

---

### Post by Gone fishing on 2010-02-04
Boot up on a live disk and the remove the offending line from you fstab.

---

### Post by SuperSonic4 on 2010-02-04
> **Gone fishing said:**
> Boot up on a live disk and the remove the offending line from you fstab.

Or comment it out by preceding the line with a #

---

### Post by thameera on 2010-02-04
sudo gedit /etc/fstab

Replace 'gedit' with whatever text editor you're using

---

### Post by howefield on 2010-02-04
> **thameera said:**
> sudo gedit /etc/fstab

You mean gksudo gedit /etc/fstab

---

### Post by igriego on 2010-02-04
I can't sudo into the file because it is recognizing everything as a read-only filesystem, but I'll try the other ideas as well once I get home. Thanks all for the suggestions.

---

### Post by nikhilbhardwaj on 2010-02-04
you need to remount the root filesystem in read-write mode
and then edit your fstab with a command line editor like nano or vim
i'll look up the command that'll mount the / filesystem in rw mode and let you know

---

### Post by SecretCode on 2010-02-04
> **igriego said:**
> I can't sudo into the file because it is recognizing everything as a read-only filesystem

Did you try from a **live CD**? (If the live CD mounts your hard disk read-only then you probably have filesystem errors and need to run fsck.)

---

### Post by nikhilbhardwaj on 2010-02-04
[B]```

mount -n -o remount,rw /

```
[/B]you can refer to [http://www.itworld.com/nlsunix070424](http://www.itworld.com/nlsunix070424) for an in depth guide
but the above code should do the trick for you

also i didn't understand why you'd need an fstab line to format a flash drive
you could use gparted or cfdisk even without that

---

### Post by falconindy on 2010-02-04
Since no one's mentioned it yet, you declared an entire drive to be mounted, not just a single partition. /dev/sdc**1** is probably what you meant to add to /etc/fstab. Also, since its a USB drive and may not always connected, add 'noauto' to the list of mount options in fstab as well.

---

### Post by igriego on 2010-02-04
Well to answer the question as to why I added the line in the first place, ubuntu wasn't seeing the drive because I had unmounted it I tried adding that line so it would be recognized, not having a clue to what that file was actually for, then I found out that I had to mount the drive forgot about that file and there it sits without my access stopping me from booting. just so you know why it is there but I'm still in class so I might have future questions.

---

### Post by igriego on 2010-02-05
Ok, so the mounting of the drive as read-writable fixed that perfectly thank you all so much.

---

