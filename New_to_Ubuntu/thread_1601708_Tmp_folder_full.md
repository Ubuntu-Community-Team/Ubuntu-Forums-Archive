---
title: "Tmp folder full"
date: 2010-10-20
forum: New to Ubuntu
---

### Post by Messyhair42 on 2010-10-20
I am getting warnings that my Tmp folder is almost full, it's on its own partition ~300MB. what can i safely clear out of /tmp and is there an automatic way to keep it clean?

---

### Post by NightwishFan on 2010-10-20
300mb imo is a bit small for /tmp as a lot of apps like CD burners put stuff in there.

---

### Post by Kaperww on 2010-10-20
You can resize the partition with gparted, because you're properly going to need more than 300mb for your /tmp partition.

---

### Post by ezsit on 2010-10-20
Many programs will rely on /tmp being bigger than 300MB. I would suggest not making /tmp its own partition, but if you need to for other reasons, give it at least 6GB, more if you ever want to burn or copy DVDs.

---

### Post by Old *ix Geek on 2010-10-20
> **Messyhair42 said:**
> I am getting warnings that my Tmp folder is almost full, it's on its own partition ~300MB. what can i safely clear out of /tmp and is there an automatic way to keep it clean?The /tmp directory is just what its name implies, temporary. You can safely delete everything, although that would likely affect programs/processes that you're currently running! :eek: The point is, /tmp in UNIX was designed for temporary storage only, and would have its contents deleted upon a reboot. You can set up a cron job to periodically clean it out, or you can manually delete everything that isn't currently in use (i.e., based on date/time).

---

### Post by Messyhair42 on 2010-10-21
I emptied /tmp, a few things had to be done through terminal (sudo nautilus). and then after i had cleared the trash and closed terminal i couldn't open nautilus or anything. on a reboot something was wrong with GNOME, it was very basic and i couldn't log in. ran dpkg in recovery mode and things are working again. i know i didn't change anything but the contents of /tmp. like i said things are working now but i thought it might be important to mention.
i got the 300 MB from the reccomended partition scheme in the ubuntu documentation. what are the steps to resize a partition in gparted?

---

### Post by AngusH on 2010-10-21
To resize a partition with gparted you will need to boot a live cd (because the partitions cannot be mounted at the time), you can either use a regular ubuntu live cd or a gparted live cd.
Fire up the gparted program.
Right click on any partitions you want to resize and select resize/move.
Tweak the options until they are just to your liking.
You will have to shrink some adjacent partitions before you can enlarge tmp.
Then apply changes.

I'll try and find a link to someone who explains it in more detail.
Regards
Angus


PS As a general rule, don't run sudo rm or gksudo nautilus unless you know exactly what your doing and exactly what programs are relying on the files your about to clear.


EDIT: [http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted) here's a good link. It assumes your using the gparted live cd rather than a linux live cd but the principle is the same, just select gparted in the ubuntu meun if your using a ubuntu live cd.

---

