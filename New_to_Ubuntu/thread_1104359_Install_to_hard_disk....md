---
title: "Install to hard disk..."
date: 2009-03-23
forum: New to Ubuntu
---

### Post by georgew77 on 2009-03-23
Ok, I took the step and started installing Ubuntu from a live CD, on a TX1100 series laptop - I had it all working on an external hard disk, but now I have tried to dual boot with XP it seems to have gone awry.

I got as far as the resizing the partition which claims it might take 'some time' however over an hour in it hasn't moved off 0% - is this normal?

[[IMG]http://img256.imageshack.us/img256/6085/screenshotr.th.png[/IMG]](http://img256.imageshack.us/my.php?image=screenshotr.png)

Now its started, I'm rather reluctant to stop it, just in case it ballses something up :o

G.

---

### Post by ptn107 on 2009-03-23
I've once increased my root partition by 10 GB and that took 5 hours alone.  Just give it some more time.  Though, I have never had it take more than a minute at most 'during' an install.

---

### Post by georgew77 on 2009-03-23
Oh, OK its just come up with a resize operation failure message, the resize has been aborted!

There didn't seem to be any way to change the size of the partition it wanted, but I'll have play.

G.

---

### Post by kestrel1 on 2009-03-23
No that isn't normal. You should be OK to turn off & start again.

---

### Post by georgew77 on 2009-03-23
Ok there seems to be something wrong with gparted, or my partition...

[[IMG]http://img244.imageshack.us/img244/6395/screener.th.png[/IMG]](http://img244.imageshack.us/my.php?image=screener.png)

Do I need to do a chkdsk and defrag in windows and try again?

G.

---

### Post by kestrel1 on 2009-03-23
Looks like the drive more than gparted. I would do what you suggest & then try agian.

---

### Post by avtolle on 2009-03-23
> **georgew77 said:**
> Ok there seems to be something wrong with gparted, or my partition...

[[IMG]http://img244.imageshack.us/img244/6395/screener.th.png[/IMG]]("http://img244.imageshack.us/my.php?image=screener.png")

Do I need to do a chkdsk and defrag in windows and try again?

G.
Yes, you should do both. I presume from the screenshot that you are trying to resize the extended partition within which your XP partition is found, and install Ubuntu within said extended partition. Is this what you are trying to accomplish?

---

### Post by lisati on 2009-03-23
I concur with the chkdsk and defrag suggestions. Running defrag two or three times probably won't hurt. Deleting temporary files is probably a good idea too.

It can take a while to resize a partition. I recently resized the Vista partition on one of my laptops using gparted (the "shrink" option of Vista didn't want to touch it). It took over an hour for gparted to simulate the action (presumably the simulation is a precaution against errors) and another 4 hours or so to do the actual resize.

---

### Post by georgew77 on 2009-03-24
Chkdsk and defrag has sorted the situation out, now need to sort the wifi - as its currently showing as eth1 rather than wlan....

G.

---

### Post by kestrel1 on 2009-03-24
eth1 would be correct for a wifi adaptor.

---

