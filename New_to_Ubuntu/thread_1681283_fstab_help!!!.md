---
title: "fstab help!!!"
date: 2011-02-03
forum: New to Ubuntu
---

### Post by john_r on 2011-02-03
I am using Ubuntu 10.10

I was trying to get my Mac OS X drive to auto mount on startup. And must have messed up somewhere. Now I am unable to even open that volume. I get an error message that says: 

Error mounting: mount exited with exit code 1: helper failed with:
[mntent]: line 1 in /etc/fstab is bad
[mntent]: line 2 in /etc/fstab is bad
mount: can't find /dev/sda2 in /etc/fstab or /etc/mtab

What should I do?

---

### Post by sandyd on 2011-02-03
> **john_r said:**
> I am using Ubuntu 10.10

I was trying to get my Mac OS X drive to auto mount on startup. And must have messed up somewhere. Now I am unable to even open that volume. I get an error message that says: 

Error mounting: mount exited with exit code 1: helper failed with:
[mntent]: line 1 in /etc/fstab is bad
[mntent]: line 2 in /etc/fstab is bad
mount: can't find /dev/sda2 in /etc/fstab or /etc/mtab

What should I do?
make sure theirs a space in between the pound sign (#) and the comment.
top couple of lines should look like
```

# /etc/fstab: static file system information.
#
# noatime turns off atimes for increased performance (atimes normally aren't
# needed; notail increases performance of ReiserFS (at the expense of storage
# efficiency).  It's safe to drop the noatime options if you want and to
# switch between notail / tail freely.
#
# The root filesystem should have a pass number of either 0 or 1.
# All other filesystems should have a pass number of 0 or greater than 1.
#
# See the manpage fstab(5) for more information.
#

```

---

### Post by john_r on 2011-02-03
I am not sure what you want me to do.

---

### Post by b0b138 on 2011-02-03
post what is in /etc/fstab

---

### Post by presence1960 on 2011-02-03
> **b0b138 said:**
> post what is in /etc/fstab

In case you do not know how to do that: open a terminal and run ```
gksu gedit /etc/fstab
```

Copy the contents of the file and paste back here.

---

### Post by john_r on 2011-02-03
Here is what is in /etc/fstab


UUID=d095faf2-219d-3cdd-a200-b70d8f1b2e7d /media/My Computer hfsplus defaults 0 0
UUID=d095faf2-219d-3cdd-a200-b70d8f1b2e7d /media/My Computer hfsplus defaults 0 0
UUID=6eb79430-5ee2-421d-a480-2bf7ec3005c2 / ext4 defaults 0 1



--I REALLY appreciate everyone helping me!---

---

### Post by b0b138 on 2011-02-04
Really need the whole file. But from that, theres a duplicate entry. Its trying to mount the same thing twice.

---

### Post by john_r on 2011-02-04
That is the entire file. Is it missing some stuff? Or should I just try to delete one of those repetitive lines?

---

### Post by Elfy on 2011-02-04
You'll not want duplicates.

```
gksudo gedit /etc/fstab
```

put a # at the beginning of one of the duplicates,s ave and close then

```
sudo mount -a
```

IF after the last command the prompt returns and shows nothing all should be well.

Check it's mounted with 

```
df -h
```

If that is your entire fstab then I would think you've edited it previously.

---

### Post by john_r on 2011-02-04
That didn't work. After the"sudo mount -a" command terminal returned " [mntent] : line 1 in /etc/fstab is bad"

Could you paste what should be in my fstab file? Could I just copy and paste the missing stuff back in there?

---

### Post by Elfy on 2011-02-04
Is your fstab really just those 3 lines?

Can you open a terminal and run these commands and paste the outputs here please - use code tags for each output - if you use the New REply button there is a # radio button in the text area - highlight the ouput and hit the button. IF quick reply put [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

```
sudo fdisk -l
sudo blkid
cat /etc/fstab
mount
```

---

### Post by sandyd on 2011-02-04
> **john_r said:**
> That didn't work. After the"sudo mount -a" command terminal returned " [mntent] : line 1 in /etc/fstab is bad"

Could you paste what should be in my fstab file? Could I just copy and paste the missing stuff back in there?
```

# /etc/fstab: static file system information.
#
# noatime turns off atimes for increased performance (atimes normally aren't 
# needed; notail increases performance of ReiserFS (at the expense of storage 
# efficiency).  It's safe to drop the noatime options if you want and to 
# switch between notail / tail freely.
#
# The root filesystem should have a pass number of either 0 or 1.
# All other filesystems should have a pass number of 0 or greater than 1.
#
# See the manpage fstab(5) for more information.
#

# <fs>                  <mountpoint>    <type>          <opts>          <dump/pass>

# NOTE: If your BOOT partition is ReiserFS, add the notail option to opts.
UUID=d095faf2-219d-3cdd-a200-b70d8f1b2e7d /media/My\040Computer hfsplus defaults 0 0
UUID=6eb79430-5ee2-421d-a480-2bf7ec3005c2 / ext4 defaults 0 1

```Also, the likely reason why you cant mount the partition is because theirs a space in the filepath.

---

### Post by Morbius1 on 2011-02-04
Why are we torturing this guy:

>  UUID=d095faf2-219d-3cdd-a200-b70d8f1b2e7d /media/My Computer hfsplus defaults 0 0"My Computer" has a space in it and fstab gets all discombobulated with spaces. So insert a "\040" ( thats a zero - 4 - zero without the quotes ) where the space is:
```
 UUID=d095faf2-219d-3cdd-a200-b70d8f1b2e7d /media/My\040Computer hfsplus defaults 0 0
```Save the file and run the following command to check for errors and mount the partition:
```
 sudo mount -a
```

---

### Post by john_r on 2011-02-04
bump

---

### Post by sandyd on 2011-02-04
> **john_r said:**
> bump
fixed my above post to include Morbius1's answer....
just use the fstab there.

---

### Post by john_r on 2011-02-04
that worked!! thanks guys! and sorry for my lack of knowledge.

---

