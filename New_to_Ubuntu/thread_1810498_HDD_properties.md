---
title: "HDD properties"
date: 2011-07-23
forum: New to Ubuntu
---

### Post by naomibrown on 2011-07-23
Hi,

I think I'm a bit confused :(

I have an external hard drive that I want to copy some files onto, but when I look at the properties of the drive it looks like it only has 83.6 GB of data on it, but the pie chart shows that there is only 11.7 GB free on a 500 GB drive?

I'm using Ubuntu 10.04. 

Thanks :)

---

### Post by lmarmisa on 2011-07-23
Open a terminal (Applications -> Accessories -> Terminal) and type this command:

```

df -h

```

Check if the information of the output related to your HDD is congruent.

---

### Post by naomibrown on 2011-07-23
This is what I get:

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             222G  151G   61G  72% /
none                  493M  308K  493M   1% /dev
none                  497M  6.1M  491M   2% /dev/shm
none                  497M  192K  497M   1% /var/run
none                  497M     0  497M   0% /var/lock
none                  497M     0  497M   0% /lib/init/rw
none                  222G  151G   61G  72% /var/lib/ureadahead/debugfs
/dev/sdb1             466G  454G   12G  98% /media/FREECOM HDD

Does that mean that I don't have any spare space? 

Thanks,
Naomi

---

### Post by lmarmisa on 2011-07-23
> **naomibrown said:**
> This is what I get:

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             222G  151G   61G  72% /
none                  493M  308K  493M   1% /dev
none                  497M  6.1M  491M   2% /dev/shm
none                  497M  192K  497M   1% /var/run
none                  497M     0  497M   0% /var/lock
none                  497M     0  497M   0% /lib/init/rw
none                  222G  151G   61G  72% /var/lib/ureadahead/debugfs
[COLOR="Blue"]/dev/sdb1             466G  454G   12G  98% /media/FREECOM HDD[/COLOR]

Does that mean that I don't have any spare space? 

Thanks,
Naomi

You have about 12 GB of free space.

---

### Post by philinux on 2011-07-23
> **naomibrown said:**
> Hi,

I think I'm a bit confused :(

I have an external hard drive that I want to copy some files onto, but when I look at the properties of the drive it looks like it only has 83.6 GB of data on it, but the pie chart shows that there is only 11.7 GB free on a 500 GB drive?

Browse the drive. Press ctrl h to show hidden files and check that Trash is not hogging the space.

I'm using Ubuntu 10.04. 

Thanks :)
Browse the drive. Press ctrl h to show hidden files and check that Trash is not hogging the space.

---

### Post by naomibrown on 2011-09-08
Yep - that was it! :)

Thanks,
Naomi

---

