---
title: "window 7 on ubuntu"
date: 2009-08-23
forum: New to Ubuntu
---

### Post by r.v.the.evil on 2009-08-23
how to install windows 7 on ubuntu 9.04... by making dual operating system

---

### Post by Roadbloc on 2009-08-23
just shove in the windows 7 install disk and start your computer i think. windows 7 install is actually ok with handling other os's and partitions.

---

### Post by AZinOH on 2009-08-23
[http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm](http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm)


It's amazing what you can learn by using Google.

---

### Post by 3rdalbum on 2009-08-23
Yes, but what sort of "dual operating system"?

You could resize your Ubuntu partition downwards, make a new partition in the free space formatted to NTFS, and then install Windows 7 into that new partition, and then reinstall GRUB so you have access to Ubuntu again.

Or, you could install Windows 7 inside a virtual machine, so that Windows 7 appears in a window on your Ubuntu desktop. This is, realistically, going to be the easiest way forward for you, because repartitioning for Windows is dangerous to your data.

If you want to look at virtual machine software, take a look at Virtualbox (it's in the repositories) and install Windows 7 onto the virtual hard disk.

---

### Post by 3rdalbum on 2009-08-23
> **Roadbloc said:**
> just shove in the windows 7 install disk and start your computer i think. windows 7 install is actually ok with handling other os's and partitions.

I'd be amazed if it can resize Ext3 partitions.

---

### Post by Roadbloc on 2009-08-23
> **3rdalbum said:**
> I'd be amazed if it can resize Ext3 partitions.

On second thoughts, yeah.... ignore me, im talking outa my ****.

You may have to install windows 7 first and then let the ubuntu install do the work.

Or use partition logic. [http://partitionlogic.org.uk/](http://partitionlogic.org.uk/)

---

### Post by r.v.the.evil on 2009-08-23
is this the sme procedure for vista

---

### Post by r.v.the.evil on 2009-08-23
actually i have four partition 
out of one is for ubuntu 
2nd one free
and 3rd and 4th r for storing data
i want 2 install 7 in 2nd partition

---

### Post by r.v.the.evil on 2009-08-23
so r there any steps

---

### Post by MrWES on 2009-08-23
> **r.v.the.evil said:**
> how to install windows 7 on ubuntu 9.04... by making dual operating system


I have Win7 RC installed in a Virtualbox. Simple enough.

Bill

---

### Post by Torgas Prim on 2009-08-23
Agreed with above comment. For ease of installation, Windows should be installed first, then ubuntu. I never have issues when doing a dual-boot this way.

---

### Post by daes_coconut on 2009-08-23
I had issues when I installed Ubuntu then Windows 7 as Windows 7 then proceded to erase/destroy Ubuntu which was on an entirely seperate harddrive.

So my advice would be Ubuntu -> Windows

---

