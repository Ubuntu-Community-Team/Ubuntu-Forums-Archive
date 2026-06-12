---
title: "A couple more questions"
date: 2009-05-04
forum: New to Ubuntu
---

### Post by tmos22 on 2009-05-04
A couple more questions, what type of antivirus can i use with Ubuntu? And how do i expand the partition i have Ubuntu in?

---

### Post by qwertyuiop96 on 2009-05-04
Go to add/remove, search partition, and choose (Gnome Partition Manager) Run that program- It's fairly obvious how it works once you are in it.  Ubuntu doesn't need an antivirus, as far as I know people don't even bother to write viruses for it.  If you still want one, use the almighty GOOGLE!!

---

### Post by kansasnoob on 2009-05-04
> **tmos22 said:**
> A couple more questions, what type of antivirus can i use with Ubuntu? And how do i expand the partition i have Ubuntu in?

Well look here:

[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

Personally I just use an email like yahoo, gmail, etc. that has a scan so I protect my friends from viruses that will never bother me.

As far as resizing your Ubuntu partition I'd want to know what other operating system(s) you're using:confused:

If you're dual booting with Vista I strongly recommend changing Vista's partition size only with Vista's own tools and then using Gparted to "grow" the Ubuntu partition.

---

### Post by tmos22 on 2009-05-04
I am dual booting with Vista, but i just want some more memory for ubuntu. I plan to only use Vista for a couple of programs from now on

---

### Post by Mortus Pryde on 2009-05-04
Antivirus is far from a necessity in Linux, I have Avast 4 Workstation installed on my laptop just so I can scan files while I am on the road, and scan my e-mails before I pick them up at home for the time being as I primarily use my ISP account that does not scan my e-mails for viruses or does a piss poor job of it.

I do not get much spam, but at least 1 in 50 seems to have some form of malicious payload that Avast on Windows picks up. As it is spam it does usually get deleted right away, but knowing an e-mail is potentially malicious up front is not a bad thing in my book even if it is destine for the the trash bin.

---

### Post by MontelEdwards on 2009-05-04
> **tmos22 said:**
> I am dual booting with Vista, but i just want some more memory for ubuntu. I plan to only use Vista for a couple of programs from now on
Did you know that you can run Vista or virtually any other operating system in Ubuntu?
have a look here [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

---

### Post by kansasnoob on 2009-05-04
> **tmos22 said:**
> I am dual booting with Vista, but i just want some more memory for ubuntu. I plan to only use Vista for a couple of programs from now on

Saying you want more "memory" scares me. I hope you mean you want to give Ubuntu more disc space.

While running Ubuntu would you please post the output from terminal of:

```
sudo fdisk -l
```

BTW that's a lower case L.

If you have a true dual boot between Vista and Ubuntu and you want to shrink Vista and enlarge Ubuntu look here first:

[http://www.ehow.com/how_2262528_extend-ntfs-partitions-windows-vista.html?ref=fuel&utm_source=yahoo&utm_medium=ssp&utm_campaign=yssp_art](http://www.ehow.com/how_2262528_extend-ntfs-partitions-windows-vista.html?ref=fuel&utm_source=yahoo&utm_medium=ssp&utm_campaign=yssp_art)

Or here:

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=2](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=2)

The second link is only included for graphics! Don't reinstall anything.

Then you can use Gparted (aka: parition editor) from you Ubuntu live CD to expand the size of your Ubuntu partition(s).

NOTE: If you move or resize the SWAP partition you'll have to do some UUID reparation!

---

### Post by tmos22 on 2009-05-04
Yeah i think i might try that out soon, you know when i download something like Virtualbox or Gnome Partition Manager, how do i run it afterwards, i cant seem to find them

---

### Post by Tyke91 on 2009-05-04
do one of the following:

GUI:
Applications>Accessories> Virtual Box

CLI:
open a terminal
type
```
virtualbox
```Your GPartEd advise was a bit misleading.

Here's the trick, you can't actually use GPartEd from within a mounted filesystem, or... you can't use GPartEd to change the mounted file system that it is in. In order to change a filesystem, you must unmount it, and if you unmount your / filesystem, then you will not be able to access GPartEd!

to get around this, use the GPartEd that came on your Ubuntu live CD, or if you want a really powerful version, download the GPartEd live CD here.

[http://sourceforge.net/project/downloading.php?group_id=115843&filename=gparted-live-0.4.4-1.iso&a=74655513](http://sourceforge.net/project/downloading.php?group_id=115843&filename=gparted-live-0.4.4-1.iso&a=74655513)

---

### Post by presence1960 on 2009-05-05
for anti-virus and other security this a must read : [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by tmos22 on 2009-05-05
Thanks for all the help guys

---

