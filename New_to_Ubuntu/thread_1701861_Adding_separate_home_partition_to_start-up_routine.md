---
title: "Adding separate home partition to start-up routine in 10.04"
date: 2011-03-07
forum: New to Ubuntu
---

### Post by TeeSquare on 2011-03-07
I was using Ubuntu 8.04 and had a separate home partition from the time of installation. I recently installed Ubuntu 10.04 which has its own home folder in the root partition. I wish to delete it and make the existing home directly accessible whenever I start up. Now I have to mount it separately each time, which was not the case with Ubuntu 8.04.
This may be a general question on how to add or remove programs from the start-up sequence. I would like to know what programs are being loaded each time, and possibly remove those which I will never use, such as games.
I request readers who respond to the above query to please have patience with my inability to respond quickly to forum posts. I am not computer/internet-savvy, and generally access the web only briefly once daily, mainly to check e-mail. I often find it difficult to understand the jargon in computer forums, and am also slow to formulate my questions in a way I think the geeks might understand. Please try to provide detailed instructions and possible options or pitfalls, especially the exact syntax for any command line entries. Thank you, =TeeSquare=

---

### Post by Ben Page on 2011-03-07
You can automount your partition fairly easily by following this relatively simple guide: [http://enli.co.cc/tutorials/automount-partitions-in-ubuntu-at-startup/](http://enli.co.cc/tutorials/automount-partitions-in-ubuntu-at-startup/)

You basically need to edit your fstab file

```
sudo gedit /etc/fstab
```

This will mount your partition where you set it to mount i.e. /media/My Home, but the partition won't act as a default home partition. To use your old Home partition, you need to install Ubuntu again and set it up at installation to use your Home partition as a default home partition. When you're setting the root "/" partition and SWAP partition.

---

### Post by wizard10000 on 2011-03-07
> **Ben Page said:**
> ...To use your old Home partition, you need to install Ubuntu again and set it up at installation to use your Home partition as a default home partition. When you're setting the root "/" partition and SWAP partition.

You can change the location of /home without reinstalling.  Here's how to do it -

```
ls -l /dev/disk/by-uuid/ 
```

Write down the UUID of your old home partition then edit (as root) /etc/fstab like this - your fstab will be different but you'll get the general idea -

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=9d90f659-a0e6-4ab6-adec-15580d30a331 /               ext4    errors=remount-ro 0       1
[COLOR="Green"]UUID=6379ed50-507d-4eb0-a11a-f345fcd46d42 /home           ext4    defaults        0       2[/COLOR]
# swap was on /dev/sda5 during installation
UUID=924b6430-5580-4991-9088-32bd5c605b61 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

Add the line in green, substituting the UUID of your old home partition.  Save the file as /etc/fstab.new and don't overwrite the old one yet.

Okay.  Now boot into recovery mode into a root terminal.  You'll need to provide the superuser password.  Once you get to the terminal, do this -

```
mv /home /home.old
```

then

```
mv /etc/fstab /etc/fstab.old
```

then

```
mv /etc/fstab.new /etc/fstab
```

Reboot and everything should work just fine.

cheers -

---

### Post by TeeSquare on 2011-03-07
Thank you, Ben Page and wizard10000
It will take me a couple of days or more to try out the instructions 'very cautiously'. Will report the outcome in due course. I don't remember any option for specifying a separate home folder during installation of Ubuntu 10.04. But I could have missed it, as I managed only after several failed attempts! =TeeSquare=

---

### Post by TeeSquare on 2011-03-14
Hello wizard1000. Operation successful! I was able to follow your instructions and get my home folder as default in Ubuntu 10.04. The "ls -l /dev/disk/by-uuid/" command gave an error : ...no such file or directory, but I was able to note the uuid from partitions/properties in the GParted screen. I have earlier used GParted to shrink the WinXP C: drive which occupied all the space when I got my new Dell laptop.
I have a lot of other issues in coping with Ubuntu, but will have to find the time to formulate the questions properly and post them in the appropriate forum threads. Thanks again, =TeeSquare=

---

