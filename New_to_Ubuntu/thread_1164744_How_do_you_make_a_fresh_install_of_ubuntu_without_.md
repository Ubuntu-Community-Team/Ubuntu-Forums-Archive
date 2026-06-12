---
title: "How do you make a fresh install of ubuntu without messing with the home partition?"
date: 2009-05-19
forum: New to Ubuntu
---

### Post by jlbr21 on 2009-05-19
OK, so when I installed ubuntu, I partitioned so:

-10gb root
-2 gb swap
-rest as home

So if needed, I could make a fresh install without messing with the home folder. The time has come to make a fresh install, however, Im not sure how to do it.
I thought that when reinstalling, I would just reinstall the OS into the root folder, however, wouldnt that create another home partition and another swap partition?

Sorry for the dumb question, just wanted to make sure I knolw what Im doing before I do it.

Thanks.

---

### Post by BandD on 2009-05-19
It depends on what os you're installing and how you install it.  Ubuntu (and most other linux distros) allow you to choose automatic or custom partitions.  If you choose the custom partitions option you can choose what goes where.  The new Linux OS may create a new home folder, but it won't create a new home partition.

If this is the case then you'll have to link the old home partition to the new home parition folder, or specifiy the user's home as the old home partiton.

Hope that helps!

---

### Post by lindsay7 on 2009-05-20
Choose custom install and make sure that you do not set it to format the old home partition.

---

### Post by nhasian on 2009-05-20
specifically during your new ubuntu installation, you must select Custom option when you get to the partitions screen.  Set the mountpoint of / to your 10 gig partition and mark the format option.  You will need to set the mountpoint of /home for your previous home partition and do NOT tick the format box.  thats all there is to it.

Of course I always recommend backing up first.  I like the tool Simple Backup which can be easily installed with:

```
sudo apt-get install sbackup
```

---

### Post by jlbr21 on 2009-05-20
Thank you all for your valuable help, I got two things straight: back up old home partition just in case, and when installing new ubuntu, do not choose the format home partition.

Thanks again!

---

### Post by Didius Falco on 2009-05-20
To save yourself some time and downloading, you could install **aptoncd** from Synaptic before you reinstall. It will make a CD/DVD or just an iso of all the packages in your apt cache that you can use to reinstall the packages you want.

That way you'd get the best of both worlds - a clean install, a reinstall of the must-have packages and your configuration files all ready and waiting for them. :)

Regards,

Didius

---

