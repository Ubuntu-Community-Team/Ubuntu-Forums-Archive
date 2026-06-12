---
title: "copy entire drive using dd if=/dev/sda of=/dev/sdb"
date: 2010-01-15
forum: New to Ubuntu
---

### Post by tom.swartz07 on 2010-01-15
Hi all,

Im trying to clone my entire drive, including the MBR. 

Would the command 
```
dd if=/dev/sda of=/dev/sdb
```
work?


I have the internal drive (sda) that I want to copy to a brand new-unformatted drive of the same size.

I have several OS's on the source drive, and the data is relatively important.


Any help would be greatly appreciated!

---

### Post by falconindy on 2010-01-15
Since the drives are the same size, you'll be fine.

---

### Post by tom.swartz07 on 2010-01-15
> **falconindy said:**
> Since the drives are the same size, you'll be fine.

great. Just to verify, the command is 
```
dd if=/dev/sda of=/dev/sdb
```

Do I need any other flags on the command, like blocksize, etc?
Should i boot to LiveCD to run it, or can i do it booted regularly?

---

### Post by ptn107 on 2010-01-15
You should try Partimage[1] to backup/clone partitions.  It works just like Norton Ghost.

[1]_[http://www.partimage.org/Main_Page]("http://www.partimage.org/Main_Page")_

---

### Post by tom.swartz07 on 2010-01-15
> **ptn107 said:**
> You should try Partimage[1] to backup/clone partitions.  It works just like Norton Ghost.

[1]_[http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page)_


Partimage doesnt support ext4, unfortunately.

Thanks for the offer. 
Ill see if i could get clonezilla to work

---

### Post by tgalati4 on 2010-01-15
Even simpler:

sudo cp /dev/sda /dev/sdb

As long as the second drive is the same size or bigger.  You can use gparted to allocate any unused space if the second drive is bigger.

---

### Post by Ocxic on 2010-01-15
go with dd, you can always expand the partition later and you'll get a byte for byte copy.

---

### Post by baddog144 on 2010-01-16
Yup, should work fine :)

Not so sure about `cp` though...

---

### Post by HermanAB on 2010-01-16
Howdy,

TIMTOWTDI...

# dd if=/dev/sda of=/dev/sdb
long wait...


# dd if=/dev/sda of=/dev/sdb bs=1M
slightly shorter wait...


Here kitty, here kitty kitty!!!
# cat /dev/sda > /dev/sdb
Even the good old kitty can do it.


Or you can do it over a network to another machine using netcat the networked kitty:

Save image on a server:
# nc -l -p 50000 | dd bs=1M of=pc.img

On the PC:
# dd bs=1M if=/dev/hda | gzip --fast | nc servername 50000

Restore image on the PC:
# nc -l -p 50000 | gunzip |  dd bs=1M of=/dev/hda

On the server:
# dd bs=1M if=pc.img | nc pc.ip.addr.ess 50000

---

### Post by Paqman on 2010-01-16
One major drawback of using dd is that it will copy across your whole drive, including the empty part. So if your drive isn't really full it takes a lot longer than other methods.

---

### Post by tom.swartz07 on 2010-01-16
Thanks for all the replies, I tried 

dd if=/dev/sda of=/dev/sdb bs=5M

but for some reason the copy fails just as it transfers the last partition.

Running fdisk -l on the two drives shows that the partitions on SDA are there (theres 9) and on SDB its missing sdb9.

Opening the drive in gParted to investigate further, the ENTIRE sdb drive is shown as unformatted?


Whats going on? did i get a faulty replacement drive?

---

### Post by john_spiral on 2010-01-16
**ddrescue** might be an option:

[http://www.linux.com/learn/tutorials/8225-clone-your-ubuntu-installation-onto-a-new-hard-disk](http://www.linux.com/learn/tutorials/8225-clone-your-ubuntu-installation-onto-a-new-hard-disk)

---

### Post by tom.swartz07 on 2010-01-19
Alrighty everyone,

Thanks for the help, but as it turns out- it was easier to to a reinstall of 9.10.

I managed to pull my home folder and all of the needed files from the old drive. That made the transfer 1000x easier than I imagined.
I just copied and pasted my Home folder, and after a restart, all of my settings were auto-magically loaded!


Thanks for the help

---

### Post by mikechant on 2010-01-20
Just to note that one reason the dd could fail on the last partition is that the new drive actually has very slightly less space than the old one due to a few more bad sectors (which I believe you can still get a few of even on a new drive).

---

### Post by spiderbatdad on 2010-01-20
dd is also subject to failures when copying mounted partitions...where parts of the filesystem are in use. Best to run dd from a live environment on unmounted filesystems.

---

### Post by tom.swartz07 on 2010-01-20
> **spiderbatdad said:**
> dd is also subject to failures when copying mounted partitions...where parts of the filesystem are in use. Best to run dd from a live environment on unmounted filesystems.

I definitely made sure that I was running from a LiveCD. 
As far as the extra badblocks, Im not too sure- my old drive had 101 bad blocks.

Its entirely possible that the badblocks on the old drive were preventing the transfer?

---

