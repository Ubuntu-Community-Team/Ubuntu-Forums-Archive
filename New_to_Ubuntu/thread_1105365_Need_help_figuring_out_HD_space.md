---
title: "Need help figuring out HD space"
date: 2009-03-24
forum: New to Ubuntu
---

### Post by mvalviar on 2009-03-24
I'm using an old pc with a small hard disk so space is a prized commodity. I was making a copy of my home folder to a windows pc when I noticed this [IMG]http://i225.photobucket.com/albums/dd230/mvalviar/Screenshot.png[/IMG]

How much disk space do I have available really? My system has a total capacity of 17.5GB but I was copying 29.6GB. How could that be?

---

### Post by bruno9779 on 2009-03-24
maybe you copied it twice?

---

### Post by Muhammad Ahmed on 2009-03-24
> **mvalviar said:**
> I'm using an old pc with a small hard disk so space is a prized commodity. I was making a copy of my home folder to a windows pc when I noticed this [IMG]http://i225.photobucket.com/albums/dd230/mvalviar/Screenshot.png[/IMG]

How much disk space do I have available really? My system has a total capacity of 17.5GB but I was copying 29.6GB. How could that be?


I use a 64bit ubuntu and it is awesomly  great.I also have an ubuntu i386 installed on another PC it shows the same.not a problem

---

### Post by jerome1232 on 2009-03-24
> **mvalviar said:**
> I'm using an old pc with a small hard disk so space is a prized commodity. I was making a copy of my home folder to a windows pc when I noticed this [IMG]http://i225.photobucket.com/albums/dd230/mvalviar/Screenshot.png[/IMG]

How much disk space do I have available really? My system has a total capacity of 17.5GB but I was copying 29.6GB. How could that be?

Post the output of df -h, much more readable.

---

### Post by mvalviar on 2009-03-24
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              18G   13G  3.9G  78% /
tmpfs                 505M     0  505M   0% /lib/init/rw
varrun                505M  208K  505M   1% /var/run
varlock               505M     0  505M   0% /var/lock
udev                  505M  2.7M  502M   1% /dev
tmpfs                 505M  296K  505M   1% /dev/shm
lrm                   505M  2.0M  503M   1% /lib/modules/2.6.27-11-generic/volatile

What I'm trying to do is repartition my HD so I can have a separate /, and /home partitions. I believe I have a 20GB HD and I want to have 1GB for swap, 4GB for / and 15 for /home. Any opinion on the is welcome. Is it possible to move or make a root partition in the remaining 4GB of space and  move the /home directory (which makes takes up 90% of HD space) to its partition.

---

### Post by miegiel on 2009-03-24
> **mvalviar said:**
> What I'm trying to do is repartition my HD so I can have a separate /, and /home partitions.

With a disk this small I suggest you don't. You would effectively be cutting your free space in half.

---

### Post by mvalviar on 2009-03-27
Really?! Should I leave my lowly 20GB HD alone?

---

### Post by drs305 on 2009-03-27
If you were copying / and had an external drive mounted on your system (for instance in /media) it's possible you were also copying the contents of the externally mounted folder/device.

To get an idea of how much space each folder is using, you can use the following command. The "max-depth" switch controls how many subfolders it looks at. 4GB is a pretty small partition for /, so look closely at how much you currently have in it and what you would plan to move. You can also use the gui Disk Usage Analyzer from the Applications, Accessories menu.
```

sudo umount -a  # unmounts non-system folders
sudo du / -h --max-depth=1

```


The total space of / and /home would not change significantly if you split them, so you wouldn't really be losing much total free space by doing this.

---

### Post by miegiel on 2009-03-27
It is just a suggestion. You need to make your own evaluation depending on what's most important to you. ;)

Personally I prefer to have a separate home partition. When you reinstall ubuntu you only need to reformat the system partition and can keep the home partition with all your files and settings. But in your case you need to realise that you can run out of free space even sooner if you split your free disk space.

If you do make a separate home partition just look at the size of /home and add about half of your free space. You can always re-size the partitions later using gparted on the ubuntu liveCD or gparted liveCD.

I hope you'll bump into another old pc soon with a salvageable disk in it. :)

---

### Post by cheapie on 2009-03-27
You could also buy another hard drive. [http://www.newegg.com/Product/Product.aspx?Item=N82E16822148231](http://www.newegg.com/Product/Product.aspx?Item=N82E16822148231) would probably be a good one. It's 80GB and $35.

---

### Post by mvalviar on 2009-03-28
> **drs305 said:**
> If you were copying / and had an external drive mounted on your system (for instance in /media) it's possible you were also copying the contents of the externally mounted folder/device.

To get an idea of how much space each folder is using, you can use the following command. The "max-depth" switch controls how many subfolders it looks at. 4GB is a pretty small partition for /, so look closely at how much you currently have in it and what you would plan to move. You can also use the gui Disk Usage Analyzer from the Applications, Accessories menu.
```

sudo umount -a  # unmounts non-system folders
sudo du / -h --max-depth=1

```


The total space of / and /home would not change significantly if you split them, so you wouldn't really be losing much total free space by doing this.

I'd don't have anything attached on the pc when I did this. Besides it was only my home directory that I tried to copy. 

Sorry for being cheap. I still find alot of juice from this battered hd since I don't have alot of media stuff. I just used it to learn some php and the like. 

I don't know which one to believe. When I was with hardy disk usage analyzer told me that I have 35GB of hd cap. In intrepid its 20GB.

---

### Post by drs305 on 2009-03-28
> **mvalviar said:**
> I don't know which one to believe. When I was with hardy disk usage analyzer told me that I have 35GB of hd cap. In intrepid its 20GB.

It is possible that Disk Usage Analyzer was also reporting the .gvfs folder contents in the total, and that the copy statistics somehow also were reporting it. 

.gvfs is a virtual file system used by ubuntu. Reporting it effectively *doubles* the disk space although of course the .gvfs files don't really exist. I believe Disk Usage Analyzer used to include the .gvfs stats by default. You could turn it off via Edit, Preferences - there was a tick box for it. It would explain why the app reported such a large capacity.

---

