---
title: "Can I Save This?"
date: 2009-06-19
forum: New to Ubuntu
---

### Post by P13808 on 2009-06-19
I was running PartionMagic 8.0 on Windows XP to resize a 150gb partition to 55.  Upon activatating the process, I got an error 1518.  Now whenever I boot onto that hard drive I get a BSOD.
Luckily my other internal hard drive is running Ubuntu.  Is there a way to save my other drive without a clean format?  Losing the unbackedup files would be bad. Also, I have no Internet connection on that computer....

---

### Post by Hospadar on 2009-06-19
Just to clarify, the files of interest are on the windows partition?

A couple questions:
Can you boot with a windows cd and chdisk the windows partition?

Otherwise, you can try mounting the windows partition, I think you can just click on it in the file browser, otherwise you can try on the command line.  You'll probably need to use "sudo fdisk -l" to figure out the drive name (probably like /dev/sda1 or something similar) and then something like "sudo mount -o ntfs-3g /dev/sda1 /media/windows"

You can search these forums, google, and the community docs in my sig for more info on mounting and whatnot.

---

### Post by P13808 on 2009-06-20
Yes, the files are on the Windows partition.  It seems the entire drive is messed up as the HP Recovery system won't work, either.  I have managed to save the files through Ubuntu.
Can I save Windows?  I have no install CD, only the HP Recovery CDs.  Can I redownload the needed files for the recovery partition?

---

### Post by philinux on 2009-06-20
Quite a few hits.

[http://www.google.co.uk/search?q=chkdsk+from+linux&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.co.uk/search?q=chkdsk+from+linux&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

---

### Post by LewRockwell on 2009-06-20
[http://www.partedmagic.com/](http://www.partedmagic.com/) has testdisk and photorec on it

---

