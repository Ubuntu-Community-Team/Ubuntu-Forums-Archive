---
title: "Deleting Files from Boot Folder"
date: 2010-04-02
forum: New to Ubuntu
---

### Post by pearsonb on 2010-04-02
Let me begin by apologizing for my rudimentary (at best) understanding of what I'm doing.  I noticed my filesystem space in my ubuntu partition is getting a little tight (93%).  The Disk Usage Analyzer indicates that the boot folder (in the partition with Ubuntu) accounts for 16.7 GB.  Can I delete any of the files in this folder to free up space or is that a terrible idea?  If I can delete some, how do I know which are ok to delete and which are necessary?  The folder contains 6 files that begin vmcoreinfo (e.g., vmcoreinfo-2.6.31-14-generic), 6 files that begin with config (e.g., config-2.6.31-14-generic), as well as 6 that begin System-map, vmlinuz, and 6 packages.  Without really understanding what I'm looking at, I'm guessing that these are hierarchical derivations of something really important, but that's about as far as I can get.  I'm working on a low-end laptop, that doesn't have a great deal more space I can use (in terms of changing the partitions), so I'm hoping there is some way to reduce the size of the space through reduction rather than construction.  Thanks for any help you can provide.

---

### Post by oldos2er on 2010-04-02
Are you sure the /boot folder is using 16.7GB? That seems extraordinarily excessive. Could you please run **du -h /boot** in a terminal and post the output here?

---

### Post by undecim on 2010-04-02
Sounds like you have a lot of old kernels left on your computer.

Open up synaptic package manager and search for "linux-image-2"

You should get many results, of which several will be installed. It is safe to remove any package that is not for the kernel version you are running.

To check which kernel version you are running, open a terminal and type "uname -a"

Press enter and you will see something like this (this is my output):
```
Linux caffeine **2.6.31-20-generic** #58-Ubuntu SMP Fri Mar 12 04:38:19 UTC 2010 x86_64 GNU/Linux
```

The part I highlighted in bold is the kernel version I am running right now. So if I were doing this, I would remove all "linux-image-2.*" packages except for "linux-image-2.6.31-20-generic"

---

### Post by undecim on 2010-04-02
> **oldos2er said:**
> Are you sure the /boot folder is using 16.7GB? That seems extraordinarily excessive. Could you please run **du -h /boot** in a terminal and post the output here?

Woah... I thought I was reading MB...

Yes, that is definitely wrong. The boot folder should never be that large.

---

### Post by pearsonb on 2010-04-02
Hmm.  Here's the output, which confirms what you said:

ben@ubuntu:~$ du -h /boot
25K    /boot/grub
82M    /boot

and here's the output showing the available space:

Filesystem            Size  Used Avail Use% Mounted on
/dev/loop0             17G   15G  1.3G  92% /
udev                  880M  264K  880M   1% /dev
none                  880M  452K  880M   1% /dev/shm
none                  880M  212K  880M   1% /var/run
none                  880M     0  880M   0% /var/lock
none                  880M     0  880M   0% /lib/init/rw
/dev/sda2              70G   51G   19G  73% /host
/dev/sr0              699M  699M     0 100% /media/cdrom0

Here's where the 16.7GB comes in: when I look at the Disk Usage Analyzer, it shows the directories and sub directories as: 
Host- Ubuntu- Disks, and at the Disks line it shows "usage 96.1%" and a size of of 16.7GB.  When I open the folder Host- Ubuntu- Disks and check the properties it lists 45 items with a total size of 18.9GB.  
It looks like the size is mainly driven by the six packages (cute little boxes) that are titled beginning with initrd.img (i.e., initrd.img-2.6.31-15-generic, initrd.img-2.6.31-17-generic, and so forth).  The largest of these is 7.6MB.  Again, I'm not sure what these are, and admittedly I'm not the brightest guy on the block.  Can I delete these packages or move them to an external hard drive?  Thanks for your help.

---

### Post by oldos2er on 2010-04-02
Is this a Wubi install?

You can use Synaptic Package Manager to uninstall any kernel(s) you don't need. Search for "linux-image" and right-click to choose 'Removal'. I like to leave at least two kernels installed, just for safety reasons. But, removing them isn't going to save you much space.

See [http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670) for more ideas on regaining hard disk space.

---

### Post by pearsonb on 2010-04-02
It's not an Wubi install (I had to look that up, but nope, not Wubi).  But I am booting from a disk (I'm not sure if that's part of my problem or not).  I looked up "linux-image" in the Synaptic Package Manager and there are 28 packages.  Six have a green box filled in on the left.  So I'm guessing somewhere along the line I'm generating a lot of extra packages.  Can I delete most of these?  Should I just keep the ones with the green boxes?  Can I prevent this sort of build-up in the future?

---

### Post by Arand on 2010-04-02
> **pearsonb said:**
> (...)
 
It looks like the size is mainly driven by the six packages (cute little boxes) that are titled beginning with initrd.img (i.e., initrd.img-2.6.31-15-generic, initrd.img-2.6.31-17-generic, and so forth).  The largest of these is 7.6MB.  Again, I'm not sure what these are, and admittedly I'm not the brightest guy on the block.  Can I delete these packages or move them to an external hard drive?  Thanks for your help.Do NOT remove those files manually, period.


> **pearsonb said:**
> It's not an Wubi install (I had to look that up, but nope, not Wubi).  But I am booting from a disk (I'm not sure if that's part of my problem or not).  I looked up "linux-image" in the Synaptic Package Manager and there are 28 packages.  Six have a green box filled in on the left.  So I'm guessing somewhere along the line I'm generating a lot of extra packages.  Can I delete most of these?  Should I just keep the ones with the green boxes?  Can I prevent this sort of build-up in the future?

So you have currently six kernels installed, which would equal 100MB * 6 ~ 0.6GB
The kernels do take up space, but is most likely not your main problem.
Recommended is to keep the current and one older kernel as a backup, looking in synaptic, the kernels marked as green are the one's that are installed, you can probably safely remove the 4 with the lowest version number, unless you know specifically that you use them, also removable would be the equivalent linux-headers-«versionnumber»-generic package


What I would guess is that you either have installed a lot of applications and thus filled up the system in general, or your home folder is filled with downloaded items or similar.

To find out if your home folder is large use```
du -shc ~/*
```This listing as summary (s) for all items (*) in your home directory (~/) by means of size in MB and GB (h) and a total (c) at the end.
Most items here would have been created manually by you and should be safe to remove.

Never delete files outside your home directory unless you know exactly what you are doing, and let the package manager handle as much as possible

To find out what installed packages are taking up the most space you can use:```
dpkg-query -Wf '${Installed-Size}\t${Package}\n' | sort -n
```Once again, look for things that you have manually installed, make sure not to remove packages which are important to the system.
If it is a game or a proper application it will most likely be listed under the "installed" section in the Ubuntu Software Centre, and this is probably the easiest way to remove them.

- Arand

---

### Post by pearsonb on 2010-04-02
Excellent, Arand. Thanks for those lines of code, it looks like the biggest files are indeed stuff I can move (iso files I created to back up DVDs and forgot about, big pdf files in my docs).  I'll move those to an external hard drive.  That should open up around 9GB.  Thanks for your help.

---

