---
title: "Using parted to display Free Space and Unallocated Space on a Harddisk"
date: 2010-06-18
forum: New to Ubuntu
---

### Post by austinium on 2010-06-18
I am trying to teach myself the GNU Parted.

parted -l doesn't display the Free Space & Unallocated space on a Harddisk. Is there option of parted that would display these? 

I using ubuntu 10.04.

---

### Post by jtarin on 2010-06-18
> **austinium said:**
> I am trying to teach myself the GNU Parted.

parted -l doesn't display the Free Space & Unallocated space on a Harddisk. Is there option of parted that would display these? 

I using ubuntu 10.04.

[[COLOR="Blue"]_These are the session commands for GParted_[/COLOR] ]("http://www.gnu.org/software/parted/manual/parted.html#Invoking-Parted")
[[COLOR="Blue"]_You want to use the "df" command instead for free space info_[/COLOR]]("http://en.wikipedia.org/wiki/Df_%28Unix%29")

---

### Post by austinium on 2010-06-18
> **jtarin said:**
> [[COLOR="Blue"]_These are the session commands for GParted_[/COLOR] ]("http://www.gnu.org/software/parted/manual/parted.html#Invoking-Parted")
[[COLOR="Blue"]_You want to use the "df" command instead for free space info_[/COLOR]]("http://en.wikipedia.org/wiki/Df_%28Unix%29")

None of those options show unallocated space on a Disk. 

When you use GParted it shows you the entire disk with all the partitions and unallocated space. Whereas "parted -l" only lists the partitions which have been formatted. There must be an option in parted which displays unallocated and free space on a disk? :confused:

---

### Post by jtarin on 2010-06-18
> **austinium said:**
> None of those options show unallocated space on a Disk. 

When you use GParted it shows you the entire disk with all the partitions and unallocated space. Whereas "parted -l" only lists the partitions which have been formatted. There must be an option in parted which displays unallocated and free space on a disk? :confused:

I mis-read your post.The link I gave was to show you the commands that GParted used.For "parted" information and commands just type in your terminal```
sudo man parted
```I don't think you will find what you want.The "df" command will show you your unallocated space.

---

### Post by austinium on 2010-06-18
from what i know df shows free space on all mounted partitions, so it won't show me unallocated or free space on the Disk :(

---

### Post by warfacegod on 2010-06-18
Use the Gparted GUI in: System> Admin.> Gparted.

---

### Post by austinium on 2010-06-18
warfacegod: iam looking to do this from the command line.
There has to be a command line option somewhere to list all partitioned and unpartitioned space in a Harddisk :-k

---

### Post by jtarin on 2010-06-18
> **austinium said:**
> from what i know df shows free space on all mounted partitions, so it won't show me unallocated or free space on the Disk :(

The command df -h will show you in human terms the free space you have on each mounted partition. Free space=unallocated.Do themath. Too much work? Then apt-get Baobab (disk usage analyzer).

---

### Post by austinium on 2010-06-20
> **jtarin said:**
> The command df -h will show you in human terms the free space you have on each mounted partition. Free space=unallocated.Do themath. Too much work? Then apt-get Baobab (disk usage analyzer).

thanks for helping out jtarin. I am looking for a *command* to list out the *Unpartitioned* space on a Hard Disk.

---

### Post by jtarin on 2010-06-21
Try this
```
as root, use the cfdisk command

ex:$ cfdisk /dev/xxx

"x" being the drive letter, which is probably "a" if you have only one hard drive.

or you can try:
1) lspv will show all physical disks in your system
2) lspv -L /dev/xxx
will show you which partitions used and how many free.
```

Have a look and then just quit the program. 
Now can I ask why you need to know it this way?

---

### Post by austinium on 2010-06-22
iam trying to make a front end to GNU Parted...i can't seem to find any option in it to display complete information about a Hard disk...

lspv doesn't work : command not found

---

### Post by jtarin on 2010-06-22
When it says command not found it can mean at least two things.(1.There is no such command. (2.You do not have the tools installed to be able to run this command.

---

### Post by austinium on 2010-06-23
my bad. i was posting in a hurry. i did try searching for lspv on both the Ubuntu & Debian repos, nothing came up.

---

### Post by austinium on 2010-08-27
parted -ms /dev/hda unit s print free
hda->the device you are looking for info on
s-> sectors, other options include B for Bytes, MB , GB and so on, ref. to man parted for more.

Thanks to the GNU Parted Mailing List for this.

---

### Post by rabinnh on 2012-01-03
Old thread, but the easy way is:

cat /proc/partitions

Which will show all devices and partitions, even empty ones.

---

