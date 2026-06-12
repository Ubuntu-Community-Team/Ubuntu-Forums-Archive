---
title: "Need Partitioner. . ."
date: 2009-06-28
forum: New to Ubuntu
---

### Post by P13808 on 2009-06-28
I need a partitioner for Ubuntu and it seems I don't have one.  Which should I use?
I also have no direct Internet connection(only the library and a thumb drive),  How can I get it?

---

### Post by WRDN on 2009-06-28
Assuming you have a Ubuntu LiveCD, you can use GParted, which can be found at System > Administration > GParted.
GParted can also be downloaded seperately.

It can also be installed on Ubuntu, and used to alter partitions on disks. Note that, you cannot change the partitions on the current drive (i.e. the one Ubuntu is running on at the time).

You can download it here: [http://packages.ubuntu.com/karmic/gparted](http://packages.ubuntu.com/karmic/gparted)

---

### Post by Captain_tux on 2009-06-28
Your partitioner is located at **System > Administration > Partition Editor **.

For your Internet connection... are you using Wireless?

---

### Post by &#1082;&#1086;&#1084;&#1084;&#1091;&#1085;&#1080;&#1089;&#1090;&#1080;&#1095;&#1077;&#1089;&#1082; on 2009-06-28
You can use GParted (partition editor) from the Administration menu. What is your internet connection?

---

### Post by -kg- on 2009-06-28
Hardy comes with no GPartEd installed by default.  If you want to have one in the installation you will have to install it from the Repositories.

If you want a standalone Live CD version, the [GPartEd Live CD]("http://gparted.sourceforge.net/") works very well.

Not having an internet connection is a problem.  If you want to install GPartEd from the Repos, you will need to find one (perhaps a friend?) so that you can hook your computer to it.  The GPartEd Live CD is around a 95 MB download, so it's not too onerous...not like a Live CD, which is 650-700 MB.

<Edit> WRDN is right...I never thought of that.  While GPartEd is not installed in Hardy by default, the Live CD does have this program in the indicated menu.

---

### Post by P13808 on 2009-06-28
Is there an easy way to download all the dependencies at once?
I have no Internet connection at home whatsoever.  AQll I can do is download at the public library.

---

### Post by Cresho on 2009-06-28
ya but from what i read, the whole ubuntu repository is over 40 gigs and you can create a local repository on your pc with repositories.  ALso, you wont benefit from updates.

[http://ubuntuforums.org/showthread.php?t=20217](http://ubuntuforums.org/showthread.php?t=20217)

ill get you started on this thread.  There are many good threads but this one will get you started.

---

### Post by Sef on 2009-06-28
> Is there an easy way to download all the dependencies at once?
I have no Internet connection at home whatsoever.  AQll I can do is download at the public library.

Order a Live CD from [Ship-it]("https://shipit.ubuntu.com/").

---

### Post by SuperSonic4 on 2009-06-28
Why not use the one on the live cd? Alternatively there is the gparted live CD too which does the same thing.

The dependencies of gparted are **parted** and **gtkmm** both of which are probably on a standard ubuntu install

---

