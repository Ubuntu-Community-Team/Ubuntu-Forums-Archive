---
title: "Can't Access The Drive I Installed Linux On"
date: 2011-07-27
forum: New to Ubuntu
---

### Post by omar khaled on 2011-07-27
Sorry Am Just New .. I Cant Access The Drive I Installed Ubuntu 10.1 On .. Its Not The C Drive (I Use Windows ) Thanks

---

### Post by khelben1979 on 2011-07-27
Have a look at [this document]("http://www.soluvas.com/read-browse-explore-open-ext2-ext3-ext4-partition-filesystem-from-windows-7/") and read it closely.

I have never been able to read a Linux formatted harddrive myself from any version of Windows up to Windows XP, but it doesn't mean that ain't possible. :) I think to keep it simple, if you want to be able to read and access the Linux harddrive or partition from within the Windows operating system, it would be more simple to create a [EXT2]("http://en.wikipedia.org/wiki/Ext2") filesystem, since an older filesystem would have better support from within the Windows operating system.

What version of Ubuntu and Windows are you using?

---

### Post by Mark Phelps on 2011-07-27
You said "10.1" -- there is no such version.  

I think you mean "10.10" -- in which case the default filesystem (unless you changed it) was Ext4, and I don't think you can read that using MS Windows.

---

### Post by omar khaled on 2011-07-31
ok i know updated it to 11.04 and i have 3 disks C: D: E: the C have Windows in it and D is the Disk I Installed Linux On .. when i open from windows os normally the disks are shown Normally but when i open from ubuntu i can only see the E: folders please help

---

### Post by khelben1979 on 2011-08-05
If you could attach a small picture to this thread it would help, a lot. :) I'm not really sure how it looks like over there.

---

### Post by Muskegman on 2011-08-05
Hi there if you want to see your linux drive from your Windows OS there is a small app that you can download, very simple to install and run from within your Windows OS 

[http://www.howtogeek.com/howto/33387/how-to-browse-your-linux-partition-from-windows/]("http://www.howtogeek.com/howto/33387/how-to-browse-your-linux-partition-from-windows/")

This will read ext2 ext3 or ext4 and will allow you to copy files and folders from your linux OS to your Windows OS

---

### Post by wildmanne39 on 2011-08-05
Hi, did you install using wubi?

---

### Post by omar khaled on 2011-08-06
actually i installed it using the CD Image . Sorry For Being Annoying Am New To This :)

---

### Post by x-D on 2011-08-06
> **omar khaled said:**
> actually i installed it using the CD Image . Sorry For Being Annoying Am New To This :)

It's okay, we're here to help, right. You can see the Drives in Linux but not in Windows, or you can't see the Drives in Linux, but you can in Windows?

I guess it's more likely to be the latter, format the drive to ntfs or ext2 if you can, or download the program Ext2Explore.

:guitar:

---

### Post by wildmanne39 on 2011-08-06
Hi, post #6 has the answer you need.

---

