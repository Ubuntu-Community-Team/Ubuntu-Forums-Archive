---
title: "defrag after changing from windows to ubuntu?"
date: 2011-06-12
forum: New to Ubuntu
---

### Post by Rosscopico on 2011-06-12
Hi everyone,
My netbook came with windows xp, which I used for nearly 2 years, before making the change to ubuntu. I have read that linux based systems dont need to be defragged, but because I didnt format my hard drive before installing ubuntu ( as I wanted to keep my files), would I need to defrag as my computer was originally a windows system?

---

### Post by oldos2er on 2011-06-12
Did you use a Wubi install? That's the only way I know of to create an Ubuntu installation without partitioning and formatting, and I'm unsure how defragging would affect a Wubi install, if at all.

---

### Post by el_koraco on 2011-06-12
No, defragmenting is a matter of the filesystem, which is different in Linux and Windows. fi you installed Ubuntu, and have only Ubuntu on your computer, there's no need to defrag.

---

### Post by audiomick on 2011-06-12
> **oldos2er said:**
> Did you use a Wubi install?

I think this is a very pertinent question. A bit more detail about how you did the Ubuntu install might help people give you useful advice.

In short: if you still have an NTFS partition that has been used by windows for two years, it may well be useful to de-frag it. Any partitions that are using Linux file systems should not need de-fragmenting.

This is a good read:
[http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting](http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting)

---

### Post by cgroza on 2011-06-12
Your ext3, ext4 partitions do not need a defrag. Your FAT and NTFS do.

---

### Post by Rosscopico on 2011-06-12
Im not sure if it was a wubi install. I did the bootable thumb drive thing, then decided to abandon windows completely.8-[

---

### Post by psusi on 2011-06-12
Did you run the installer from inside windows, or did you boot from the cd when you installed?  Open the disk utility and see what kind of partition(s) you have on the disk.  If it is NTFS, then you did a WUBI install and should reinstall without WUBI.  If not, then you did format when you installed.

---

### Post by Mark Phelps on 2011-06-13
To check your partitioning scheme, open a terminal in Ubuntu and enter "sudo fdisk -lu" (that's a lowercase L, not a one).

If all you see is NTFS or FAT partitions, then you did a Wubi install and defragging will not accomplish anything for Ubuntu.

---

### Post by psusi on 2011-06-13
> **Mark Phelps said:**
> 
If all you see is NTFS or FAT partitions, then you did a Wubi install and defragging will not accomplish anything for Ubuntu.

Actually it very well could if the Ubuntu partition image file is fragmented, but the only way to defrag NTFS is with Windows.

---

### Post by Frogs Hair on 2011-06-13
When I used a Wubi installation , Ubuntu was hidden from Windows . The disk defrag tool I  used could recognize Ububtu was there  , but could not defag  that portion of the disk . It would give a hidden files message and bypass.

---

