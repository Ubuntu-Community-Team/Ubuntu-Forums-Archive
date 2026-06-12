---
title: "I NEED HARD DISK SPACE.. How to remove programs"
date: 2009-02-24
forum: New to Ubuntu
---

### Post by mal_conductor on 2009-02-24
I need hard disk space.

I am using the Synaptic Package Manager to remove unused applications.
I marked them for complete removal, but I still see some files remain.

How to ensure ALL files are removed when removing an application?!!

---

### Post by taurus on 2009-02-24
Close down synaptic.  Then, open a terminal and run

Applications -> Accessories -> Terminal
```
sudo apt-get clean
sudo apt-get autoremove
df -h
```

Those will empty your cache and remove all the unnecessary dependencies.

---

### Post by lisati on 2009-02-24
Sometimes it's easier to use "Add/Remove Programs" (it's on the "Applications" menu) to remove programs you don't need.

---

### Post by mal_conductor on 2009-02-24
Is there a way to reduce virtual memory?

(This is from my Window days)
I wonder if there is an equivalent in Ubuntu.
Windows assigns a part of the hard drive to complement the RAM. If there is enough RAM then that part of the Hard Drive is wasted.
Does Ubuntu do something similar?
How to reduce the size of the potion assigned?

---

### Post by llamabr on 2009-02-24
You mean swap space?

post the output of df -h

---

### Post by dwasifar on 2009-02-24
Chances are that the amount of space assigned to the swap partition by the installer is not going to be very large, and won't help you much.

For instance, on my laptop, I have a 250GB drive and less than 3GB is swap.  If you're that close to full, you need a bigger drive; stealing a little space from swap is not worth it.

---

### Post by rafac24 on 2009-02-24
> **taurus said:**
> Close down synaptic.  Then, open a terminal and run

Applications -> Accessories -> Terminal
```
sudo apt-get clean
sudo apt-get autoremove
df -h
```

Those will empty your cache and remove all the unnecessary dependencies.

Awesome.

---

### Post by mal_conductor on 2009-02-24
I NEED HARD DISK SPACE.. How to reduce the size Trash
Is there a way to reduce the size of Trash?

(This is from my Window days)
I wonder if there is an equivalent in Ubuntu.
Windows assigns a part of the hard drive to Trash.
Does Ubuntu do something similar?
How to reduce the size of the portion assigned to Trash?

---

### Post by Vantrax on 2009-02-24
Windows does this using a page file called pagefile.sys.

Linux uses a partition called swap.

If you run sudo fdisk -l you can see how big it is, and you can resize it from a live cd with gparted if you really must.

---

### Post by crjackson on 2009-02-24
Trash is just an empty folder. If you have no trash in the bin, then there's nothing to reduce.

---

### Post by bodhi.zazen on 2009-02-24
Threads merged as they all seem to be on the same topic.

---

### Post by mal_conductor on 2009-02-24
I NEED HARD DISK SPACE.. How to clean disk and defragment hard drive?

(From my Windows day)
Does Ubuntu have an equivalent to clean disk to remove unused files and a defragment tool?

---

### Post by MrWES on 2009-02-24
Ext3 file system does not require defraging. However you can try to clean up packages with the following commands from the terminal:

sudo apt-get autoremove

sudo apt-get clean

Bill

---

### Post by mal_conductor on 2009-02-24
> **llamabr said:**
> You mean swap space?

post the output of df -h

me@FUJI:~$ sudo df -h
[sudo] password for ubuntu: 
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             7.7G  3.0G  4.3G  42% /
varrun                501M  108K  501M   1% /var/run
varlock               501M     0  501M   0% /var/lock
udev                  501M   56K  501M   1% /dev
devshm                501M  160K  501M   1% /dev/shm
lrm                   501M   39M  462M   8% /lib/modules/2.6.24-21-generic/volatile
me@FUJI:~$

---

