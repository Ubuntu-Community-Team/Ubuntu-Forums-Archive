---
title: "Changing file properties"
date: 2010-03-02
forum: New to Ubuntu
---

### Post by LewRockwellFAN on 2010-03-02
I multiboot several OSs. On my 64 bit installation I can change file properties with right click properties [*NOTE: I was mistaken about that. See below if you are interested. I'm adding this note in edit, rather than correcting the statement, so that the thread will be more comprehensible to anyone researching similar topics who reads it.*] But on my 32 bit installation, when I change anything it immediately changes back. My immediate goal is to change a text file to read only so I can't accidentally mod it.  But I would like to know why the two installations do not work similarly in this regard and if there is an easier way to do this. Perhaps an ap that lets me right click and toggle editable/read only. I do this a lot with text files.

---

### Post by Paddy Landau on 2010-03-02
I presume that you are using Nautilus to right-click and change properties?

It should not change back.

It may be that, for some reason, the file is not owned by you and therefore you don't have permission to change it.

Are you sure that you own the file in question?

---

### Post by LewRockwellFAN on 2010-03-02
TY for your response. Properties indicates owner as fu32 (fu stands for Full Ubuntu, btw). When I open a terminal the prompt is " fu32@fu32-desktop:~$ ". So I suppose I'm the owner. IF my reasoning is unsound, how do I properly check this? I run a single user system that is reasonably physically secure. My frustrations with permissions frequently make me wistful for DOS.

---

### Post by Paddy Landau on 2010-03-02
> **LewRockwellFAN said:**
> My frustrations with permissiohns frequently make me wistful for DOS.
Well, it's thanks to these permissions that we don't get viruses on Linux. I guess you gotta take the rough with the smooth.

Anyway, I'm thinking that perhaps, somehow, the immutable flag has been set accidentally on the file.

Here's how to check and, if set, unset it. I've used [FONT=Courier New]myfile.txt[/FONT] as an example; replace it with the real file name. (If the file name contains spaces, put quotes around the file name, as [FONT=Courier New]'myfile.txt'[/FONT].)You have to run this from a terminal (Accessories > Terminal).
```
lsattr myfile.txt
```You should see your file name preceded by lots of dashes:
[FONT=Courier New]------------------ myfile.txt[/FONT]
On the other hand, if you see the letter i:
[FONT=Courier New]----i------------- myfile.txt[/FONT]
Then the immutable flag is set.

To clear an immutable flag, use this:
```
sudo chattr -i myfile.txt
```Let us know the outcome. If it hasn't worked, then post the results of this:
```
ls -l myfile.txt
```

---

### Post by LewRockwellFAN on 2010-03-02
Thanks, Paddy. I get neither. I get:

fu32@fu32-desktop:/media/Data 1 - 192 on Blue/_copied from red to Blue 1/checked/2/DT - s/misc  docs$ lsattr readme.txt 
lsattr: Function not implemented While reading flags on readme.txt
fu32@fu32-desktop:/media/Data 1 - 192 on Blue/_copied from red to Blue 1/checked/2/DT - s/misc  docs$ 

It's not just this one file. I checked two. They behave the same way. In properties, permissions tab, in either of the 3 dropdowns for Owner, Group, or Others access, if I change "read and write"  to anything else it shows the new setting momentarily and then reverts. If I uncheck "allow executing file as program" it shows clear for a moment and then rechecks itself. The lsattr command yielded the same result on on these two files in that directory also. Several random checks of properties on other files and types of files on other partitions show the same behaviour. I do not see this when I boot from my 64 bit installation of Karmic on another partition of the same drive.

---

### Post by Paddy Landau on 2010-03-02
> **LewRockwellFAN said:**
> /media/Data 1 - 192 on Blue/_copied from red to Blue 1/checked/2/DT - s/misc  docs
Ah ha... It seems to me that the file in question is not on your Linux file system, but on another device or partition.

I'll bet that your "Data 1 - 192 on Blue" is not a Linux file system.

What is it -- an external hard drive? Do you know what type of file system it has (e.g. NTFS, FAT32)?

---

### Post by LewRockwellFAN on 2010-03-02
Correct. It is an NTFS data partition on the same internal hard drive. I don't keep data on system partitions. NTFS cause I keep a few large files on it and I want access from W2k as well.

I just noticed I omitted to follow your second suggestion. So here is the result on another file in the root directory of the same partition:

fu32@fu32-desktop:/media/Data 1 - 192 on Blue$ ls -l "grub-conf on red, uuntu"
-rwxrwxrwx 1 fu32 fu32 3469 2009-12-02 22:54 grub-conf on red, uuntu
fu32@fu32-desktop:/media/Data 1 - 192 on Blue$ 

The last part of the response, the words "grub-conf on red, uuntu", i.e., the file name, is in another color.

I stepped up to the root directory to see if perhaps it was related to path length. With my penchant for long file names and deep nested directory structure that has often created the darndest problems for me in Windows Apparently not the issue though. Tested several files in the root directory and it was the same story.

 You are also correct in the implication that this might not be a problem in the home folder. I checked. It is not.

So what is likely that I did right in my 64 bit installation that I did wrong in the 32?

Thanks for your thoughts and time. I'll try to pass it forward. :)

---

### Post by Paddy Landau on 2010-03-03
> **LewRockwellFAN said:**
> So what is likely that I did right in my 64 bit installation that I did wrong in the 32?
Thanks for the feedback. For future note, it's always important to let us know when something is different from what we might expect -- in this case, the file is not on a Linux file system but on NTFS.

NTFS doesn't support the same types of permissions, though it does support read-only. So, to try to answer your question, I'll ask you some questions first.

[LIST]
[*]How did you mount your NTFS partition? Did you simply go to Places, choose the partition, and let the computer mount it by itself? Or does it mount automatically when you boot? Or do you mount it in a different way?
[*]Did you change the file [FONT=Courier New]/etc/fstab[/FONT] in any way?
[*]Please go to a terminal, enter the command [FONT=Courier New]mount[/FONT], and post the results here.
[/LIST]
I'm not an expert on file systems, so I'll do my best; if someone with more knowledge than I have reads this, perhaps that person could help.

*EDIT* The bit about the immutable flag is a red herring, because NTFS doesn't support it.

---

### Post by LewRockwellFAN on 2010-03-03
*chagrin* mea culpa. My summary of the problem was erroneous. In order to be sure I was answering your questions correctly I rebooted in different OSs several times to check how each mounted the data partitions. In both the 32 and the 64 bit _Ub_untu I get to those partitions by clicking places, clicking the name of the partition on the drop down menu, and, only on the first time I access the partion in a given session,  entering my password. After first mounting it the password step is omitted.

Contrary to what I wrote earlier, the 32 and 64 bit versions ARE behaving exactly the same way. Most likely I went through the motions of setting the files read-only in the 64 bit version and simply didn't realize it it wasn't sucessful. Or possibly I misrembered something I did in Windows or Sabayon as being done in Ubuntu 64. Or maybe I had the 64 working the way I thought and then broke somthing in my obcessive tinkering.

Anyway, I discovered what you probably already suspect, that it is not merely a problem of not being able to reset a read/write file to read-only, but that neither Ubuntu installation recognizes the read-only marker (flag, bit? not sure of the right term here) even when it is properly set from Windows 7 beta.

I don't think I've made any changes in [FONT=Tahoma][B]/etc/fstab. Here is what is in it for the 32:
[/B][SIZE=3]# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda8 during installation
UUID=2231cac5-61e1-457e-8bcc-41326296caa9 /               ext4    errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0[/SIZE][B][SIZE=3]
[/SIZE][/B][/FONT]
Hmmm ... interesting looking stuff there. Maybe I need to learn to edit it if I'm going to tinker with adding and removing drives? 

Here is the response to the command "mount":

[SIZE=2][B]fu32@fu32-desktop:~$ mount
/dev/sda8 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
none on /var/lib/ureadahead/debugfs type debugfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/fu32/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=fu32)
/dev/sda5 on /media/Data 1 - 192 on Blue type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda6 on /media/Data 2 - 193 on Blue type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
fu32@fu32-desktop:~$ 
[/B]
Is it possible the problem here is that the present linux support of NTFS is ALMOST perfect but not quite? And if so, do you think I am more likely to achieve my intent by teaching Windows to work with an extN filesystem (I know this can be done - I don't know how well), by tweaking how Ubuntu works with the present system, by some add-on or work-around, or by living with it until NTFS support is perfected? My intent is to have partitions readable to W2k (which I legitimately own and will go back to after my W7 beta quits working and I get another HD W2k can install to from the CD) and to most linuxes (& BSD perhaps? I like to tinker) which can hold a file the size of an iso of a full DVD. I suppose I could give up on it, split any files I have that big, make ONE special purpose partition for big files and just join the isos if I need to use one, and keep everything else on an FAT32. In truth it probably wouldn't be ALL that inconvenient. It just seems a bit inelegant. Partly I suppose it just appeals to me in a "Can I figure out how to make it do tricks" sort of way.

Thanks for your thoughts.
[/SIZE]

---

### Post by Paddy Landau on 2010-03-04
Well, thanks for all the information.

> **LewRockwellFAN said:**
> Is it possible the problem here is that the present linux support of NTFS is ALMOST perfect but not quite?
I've just tested on another dual-boot computer using both nautilus and chmod, and guess what, I had the same results as you! I suspect that you're right.

I don't know where to find the information definitively; I've been Googling without success.

> **LewRockwellFAN said:**
> ... do you think I am more likely to achieve my intent by teaching Windows to work with an extN filesystem...
I wouldn't know. But, there are drivers for Windows to access ext2 and ext3 partitions (but not yet ext4). The best that I've found is [Ext2FSD]("http://www.ext2fsd.com/").
> **LewRockwellFAN said:**
> ... keep everything else on an FAT32.
I wouldn't use FAT32. I'd use NTFS.

---

### Post by Paddy Landau on 2010-03-04
I've been reading further on this, and it's quite interesting.

It seems that NTFS has a more complicated way of storing permissions, using lists of users and what they're allowed to do. So, read-only in NTFS (as I understand) applies per user.

Linux can only approximate NTFS permissions, because it's used in a very different way, having only three groups: owner, group and 'all'.

On top of all that, the driver that we currently use, namely ntfs-3g, doesn't have full support for NTFS permissions. You mount the partition either with full read-write access or with read-only access.

[ntfs-3g Ownership and Permissions Support]("http://linux.softpedia.com/get/System/Hardware/ntfs-3g-Ownership-and-Permissions-Support-40763.shtml")
[ntfs-3g File Ownership and Permssions]("http://pagesperso-orange.fr/b.andre/permissions.html")
[Communicating With the Other Half: NTFS Support in Linux]("http://www.linux-mag.com/id/5523")

---

### Post by LewRockwellFAN on 2010-03-05
Thank you very much, Paddy, for both the summary and the links. These are very enlightening. Now I understand my options.

I use a UPS and I back up my data anyway so journalling is pretty superfluous. And on a reasonably physically secure single user system I don't need NTFS's fancy security tricks. I keep the plans for revolution and world conquest in a locked file in the wetware. :) I just used NTFS because of the support for >4 GiB files of which I really only have a few anyway. So I'll probably just repartition and segregate them. I think I'll make some test partitions with FAT32, Ext2, and Ext3, install Windows support for ExtN (which I've been meaning to do anyway) and experiment a little.

So with the info you provided I think I'm justified in marking this thread SOLVED but I will report back with the results of my experiments.

Thanks a heap. :)

---

### Post by Paddy Landau on 2010-03-05
> **LewRockwellFAN said:**
> ... I'll make some test partitions with FAT32, Ext2, and Ext3, install Windows support for ExtN...
I formatted my external hard drive as ext3 a year ago, and I've had no problems whatsoever. Admittedly, I hardly ever access it from Windows any more, but when I used to do so regularly, [Ext2Fsd]("http://www.ext2fsd.com/") worked absolutely fine with it.

It's unfortunate that we don't have an ext4 driver for Windows.

---

### Post by G3lrod on 2013-03-25
>  ```
lsattr myfile.txt
```You should see your file name preceded by lots of dashes:
[FONT=Courier New]------------------ myfile.txt[/FONT]
On the other hand, if you see the letter i:
[FONT=Courier New]----i------------- myfile.txt[/FONT]
Then the immutable flag is set.


I have a similar problem, and when I run the command, I get this:
[FONT=courier new]----------------e- myfile.txt

[SIZE=3][FONT=times new roman]What does that mean?[/FONT][/SIZE]
[/FONT]

---

### Post by Paddy Landau on 2013-03-25
> **G3lrod said:**
> I have a similar problem[SIZE=3]…[/SIZE]
@G3lrod — this is a very old thread. The details in this thread may no longer apply.

Please start a new thread and explain your situation and your problem clearly.

---

### Post by oldos2er on 2013-03-25
Old thread closed.

---

