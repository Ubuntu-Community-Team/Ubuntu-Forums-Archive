---
title: "How to automount a partition on startup??"
date: 2010-12-11
forum: New to Ubuntu
---

### Post by arjunlalb on 2010-12-11
Hi :-)

I would like to know how can I set up a ntfs partition to be mounted automatically on startup...
Is there is command for that or any application to set it up?? other than pysdm..because pysdm had made my system crash last time

Operating System : Ubuntu 10.10 Maverick Meerkat

---

### Post by Wtower on 2010-12-11
You need to edit /etc/fstab. In console:

```
gksudo gedit /etc/fstab
```

And then add a line in the end as:

```

/dev/sdb1    /media/ntfs    ntfs    defaults    0    0

```

Replace sdb1 with the appropriate disk partition. You can see all disk partitions in the system administration menu, disk tool.

Regards

---

### Post by supererki on 2010-12-11
yes, easiest way is to add line to /etc/fstab

If you are uncertain what to write there, then you should :

```
cat /etc/mtab 
```

while the disk in question is mounted, and the copy the corresponding line to fstab.

---

### Post by karthick87 on 2010-12-11
Install pysdm

```
sudo apt-get install pysdm
```After installation it will be found under [B]System>>Administration>>Storage Device Manager
[/B][IMG]http://imgur.com/d1kiZ.png[/IMG]
In the left side you can find all your partitons,select your partition and then click **Mount** and [B]Apply.

ALTERNATE METHOD:
[/B]Install ntfs-config
```
sudo apt-get install ntfs-config
```It will be found under **System>>Administration>>NTFS Configuration Tool      **
[IMG]http://imgur.com/dsKi5.png[/IMG]

---

### Post by Verbeck on 2010-12-11
its better to use the uuid of the partition in fstab
_1._ to find it and the filesystem type, run the following in a terminal
```
sudo blkid -c /dev/null
```it should give something like 
/dev/sdb3: LABEL="Extras" UUID="**0C2A39615EAFB871**" TYPE="**ntfs**" 

_2._ create the mount point 
```
sudo mkdir **/media/Extras**
```_3._ then edit fstab
```
sudo gedit /etc/fstab
```add a new line 
```

UUID=**0C2A39615EAFB871  /media/Extras  ****ntfs  **defaults  0  0

```more help : _[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)_

---

### Post by Wtower on 2010-12-13
Numerous possibilities :) choose whichever you prefer, karthick87 suggestion is the most user friendly I would rather say

---

### Post by arjunlalb on 2010-12-13
thanks to all.. :-) I've learned how to do that :-)

---

### Post by tajiknomi on 2010-12-13
> **Wtower said:**
> Numerous possibilities :) choose whichever you prefer, karthick87 suggestion is the most user friendly I would rather say

[SIZE=2]+1 for that, but unfortunately One has to Go ***back*** to FSTAB in order to add trash-option + Read-write-Exec Accesses, 

i had used NTFS-config last time, but it then doesn't allow me to ***move-items-**to-Trash***, then i move to my FSTAB and ***Manually*** add that line...

I think the Best way to add the lines manually to fstab..
[/SIZE]

---

