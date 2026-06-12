---
title: "Unable to download upgrades - Need more memory on disk '/'"
date: 2009-09-04
forum: New to Ubuntu
---

### Post by nardthefox on 2009-09-04
I just installed Ubuntu for the first time, and used the first radio button option for install regarding my hard disk. I allowed the computer to sort out the partition approximations. Was this a mistake? Should I have done the fourth advanced option and 50/50'd the memory for each partition on its own? 
Right now I am unable to download any updates, despite that it's only 400MB. The error messages claims I need to empty my trash bin and temporary install files in order to free up disk space. :confused:
So where do I go from here?  Can this problem be fixed 'in system'? How can I check my current memory? Or do I need to reinstall ubuntu from scratch and approximate the memory myself? 
Thanks for any help! It's greatly appreciated!

---

### Post by halitech on 2009-09-04
can you post the output of
```
sudo fdisk -l
```and ```
df -h
```

---

### Post by nardthefox on 2009-09-04
Well, to be entirely honest, I'm really not sure how to even get the point where I can enter in those commands. I'm fresh off the grill, mate. I've spent all my time reading about distros and various installations, as I ran into my own can of worms just on the live cd. 
So how can I get to the command prompt menu (which is where I assume you mean to enter those commands)?

---

### Post by Paqman on 2009-09-04
Applications > Accessories > Terminal

---

### Post by nardthefox on 2009-09-04
So this is what I'm staring at. What does it mean?  Disk /dev/sda: 250.0 GB, 250059350016 bytes 255 heads, 63 sectors/track, 30401 cylinders Units = cylinders of 16065 * 512 = 8225280 bytes Disk identifier: 0x41a641a6     Device Boot      Start         End      Blocks   Id  System /dev/sda1   *           1       30075   241577406    7  HPFS/NTFS /dev/sda2           30076       30401     2618595    5  Extended /dev/sda5           30076       30379     2441848+  83  Linux /dev/sda6           30380       30401      176683+  82  Linux swap / Solaris

---

### Post by Paqman on 2009-09-04
> **nardthefox said:**
> What does it mean?  


It means you have a 250GB disk, but Ubuntu is installed into a wee tiny sliver of it. Hence why you ran out room.

Fear not though, you can steal some space from the Windows partition and give it to Ubuntu. Since that'll mean modifying the Windows partition slightly you should make sure that you've got a recent backup for it (just in case) and run through a defrag.

After that you should boot into a LiveCD and use the Gparted partition editor. Right click on any partitions showing a little key icon and choose "swapoff", then shrink your Windows NTFS partition by at least about 10GB or so, and grow your extended partition and the Linux partition inside it to take up the space you just made. This operation could take some time to complete.

---

### Post by drs305 on 2009-09-04
nardthefox,

Welcome to Ubuntu and the Ubuntu Forums.

You are a victim of a bug in the Ubuntu installation process, as it looks like you have a 2.5GB / partition. That is too small for a normal Ubuntu installation. The devs are working on a fix but it is too late to help you for this installation.

You can either resize your partition, taking space from Windows, or reinstall and change one thing in Step 4. I wrote guides on both:

[HOWTO: 2.5 GB System Partition - What Went Wrong?]("http://ubuntuforums.org/showthread.php?p=7658271")

[Expanding an Ubuntu System Partition ]("http://ubuntuforums.org/showthread.php?t=1219270")

Both will take about the same amount of time, depending on download speeds and partition sizes.

Here is a screenshot of the step that must be changed if you attempt a reinstall:
[http://ubuntuforums.org/attachment.php?attachmentid=121997&d=1248267874]("http://ubuntuforums.org/attachment.php?attachmentid=121997&d=1248267874")

---

