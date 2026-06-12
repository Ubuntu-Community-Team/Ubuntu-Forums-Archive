---
title: "Data Storage"
date: 2010-10-02
forum: New to Ubuntu
---

### Post by thebarisaxkid on 2010-10-02
I have an 80g drive that has Ubuntu+Programs on it.  I have a second 120g drive with nothing on it. How can i make the 120g drive hold all my folders.

I have GParted+disk utility.  If u want, you can reccomend different ways.

---

### Post by Hippytaff on 2010-10-02
what do you man by all your folders?

---

### Post by thebarisaxkid on 2010-10-02
Music, Pictures, Word documents, etc.

---

### Post by Hippytaff on 2010-10-02
found this -You can format the external as ext3 and install fs-driver so windows can write to it.

here - [http://ubuntuforums.org/showthread.php?t=524257](http://ubuntuforums.org/showthread.php?t=524257)

any good?

---

### Post by Joeb454 on 2010-10-02
Do you dual boot? If so, obviously you'll want to make the drive readable by multiple OS's.

If not, you can simply format the drive, then edit fstab to mount it on startup as a certain directory. I'm not 100% sure on how to do that part though :p

---

### Post by raymondh on 2010-10-02
following Joeb's suggestion ...

If you don't dual boot, you can also move your whole /home into the second drive ...effectively moving your 'stuff' separate from the OS or root.

---

### Post by thebarisaxkid on 2010-10-02
The both hard drives are internal, but I doubt this makes a difference.

I only have Ubuntu, And I want to move the /home folder content to the second drive.

So I have to format it as ext3, right?

---

### Post by raymondh on 2010-10-02
Yes ....usually ext3 (my preference is ext4)

[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

I personally have tried psychocats' tutorial.  I have not done it in a while as since then, I have installed with a separate /home.

Back-up your data first to an external storage.  That way, if anything borks, you can re-install and set-up with a separate /home .... without the fear of losing any data permanently.

Regards.

---

### Post by thebarisaxkid on 2010-10-02
> **raymondh said:**
> Yes ....usually ext3 (my preference is ext4)

[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

I personally have tried psychocats' tutorial.  I have not done it in a while as since then, I have installed with a separate /home.

Back-up your data first to an external storage.  That way, if anything borks, you can re-install and set-up with a separate /home .... without the fear of losing any data permanently.

Regards.
I used the link that raymondh provided (1st one), followed the steps, and I got it.  Just one small problem though.  I for some reason cannot delete the old_home folder.  How do i do this?

---

