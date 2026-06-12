---
title: "Using GPARTED from LiveCD"
date: 2010-08-29
forum: New to Ubuntu
---

### Post by donescamillo on 2010-08-29
Hi,

Can I insert a LiveCD, go to Synaptic, install GPARTED and repartition a hard drive?
I am not worried about the data on the hard drive.

---

### Post by gandaran on 2010-08-29
yes, but theres no need to install it, the live cd already has it.
system » administration » gparted

---

### Post by albandy on 2010-08-29
yes, but you don't need to to this, in ubuntu 10.04 it's installed in the live cd.
System --> Administration-->gparted

Edit:
As gandaran said before.

---

### Post by nair on 2010-08-29
I am trying to use GParted from the LiveCD to erase an existing Ubuntu installation on my harddrive, but I cannot quite figure it out.  I do not want to format the entire drive harddrive, just the partition with Ubuntu on it.  I ultimately want to do a fresh install of Ubuntu on the partition I am already using for Ubuntu.

I see one partition, "/dev/sda3", with a little key icon next to it, which is an extended file system.  Using Gparted, I can see within "/dev/sda3" three different partitions:

"/dev/sda5" with ext4 file system,
"unallocated" with unallocated file system, and
"/dev/sda6" with linux-swap file system

The "/dev/sda6" linux-swap partition has a little key icon next to it as well.  How can I blow the whole /dev/sda3 partition away, and all of the partitions contained within?  If I click on any partition with a key icon next to it, I am not able to do anything except click on "manage flags" and "information".  None of the formatting, resizing, or deleting options are available ... they stay greyed out.

Also, note that I could not figure out how to only format the existing Ubuntu partition through the initial Live CD install screen.  If I could do it that way, it would be sufficient.

I am using Gparted 0.5.1 on the Ubuntu 10.04 x64 Live CD.

---

### Post by Elfy on 2010-08-29
> **nair said:**
> ....
"/dev/sda5" with ext4 file system,
"unallocated" with unallocated file system, and
"/dev/sda6" with linux-swap file system...

Also, note that I could not figure out how to only format the existing Ubuntu partition through the initial Live CD install screen.  If I could do it that way, it would be sufficient...

Run the installer - when you reach the partition stage - choose manual.

Select sda5 - Edit - in the new window - Use as ext4 - mountpoint set as / - exit then make sure to set it to format the partition.

Carry on - this will install over the existing install.

If you want to work on the partitions in the livecd you will need to right click the swap partition and swap off first.

---

