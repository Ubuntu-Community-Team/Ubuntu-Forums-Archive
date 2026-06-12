---
title: "Mount Partition on Boot"
date: 2010-09-27
forum: New to Ubuntu
---

### Post by jediken21 on 2010-09-27
I'm using Ubuntu 10.10 beta and was wondering how I go about getting my Windows 7 partition (that has my music) to mount automatically when I boot. Basically I just need it to be mounted every time i start my computer so it doesn't have to research for my music every time I turn on my computer. Thanks.

---

### Post by jtarin on 2010-09-27
[Using blkid and editing your /etc/fstab (as sudo).]("http://www.cyberciti.biz/faq/linux-finding-using-uuids-to-update-fstab/")

---

### Post by julio_cortez on 2010-09-27
I never used UUID to do that (*and I wasn't aware of that way, honestly*)..

I just take track of the dev I want to "automount" (say it's /dev/sda2 and it's NTFS) then I do this:

[LIST=1]
[*]sudo mkdir /media/Data *(or whatever you want as long ias it's  /media/whatever)*
[*]gksudo gedit /etc/fstab
 then I add the proper line in fstab, that in my case will look like```

 /dev/sda2   /media/Data   NTFS   defaults   0   0
``` and save the file (*NOTE: I use defaults but you're free to add any option you see fit*)
[*]sudo mount -a
[/LIST]
and I'm usually fine :)

---

### Post by Mark Phelps on 2010-09-27
If your music is in a data partition, automounting is OK.  But, if it's in your Win7 OS partition, automounting is asking for trouble.  One unclean shutdown and Win7 is rendered unbootable, and since you then won't be able to boot into it to run chkdsk, potentially unfixable.

Better approach is to store your media in a separate NTFS partition that you don't use to boot.  That way, if there is a problem, you can boot into Win7, run CHKDSK, and fix it easily.

---

### Post by julio_cortez on 2010-09-27
> **Mark Phelps said:**
> But, if it's in your Win7 OS partition, automounting is asking for trouble.This.

I forgot to add this very suggestion in my post, I took the Win7 partition to make an example but really shouldn't (mine is not automounted, only the /Data one is) :D

---

