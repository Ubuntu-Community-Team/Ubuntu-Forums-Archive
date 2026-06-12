---
title: "Brasero stuck at &quot;creating image checksum&quot;"
date: 2010-10-14
forum: New to Ubuntu
---

### Post by furiousjason on 2010-10-14
When I try to burn an iso, audio cd, dvd, anything brasero sits at creating image checksum. Tried changing speeds, uninstalling and reinstalling. Any ideas?

---

### Post by Sealbhach on 2010-10-14
Can you do md5sum from the command line?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

.

---

### Post by furiousjason on 2010-10-14
Followed the instructions on [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM). 
I have verified the md5 hash and when I go to burn the iso again still sitting at creating image checksum.

---

### Post by thomas_d_j on 2010-10-15
I had the same problem.  You can run:
brasero -g
from a command prompt and you will get some debug messages pointing to the problem.  Mine kept saying device not ready.  A reboot fixed it however.

---

### Post by neednewlaptop on 2010-10-15
If I understand correctly you have already verified the md5, so the iso is unchanged and now you just want to burn that iso to cd/dvd and then Brasero hangs-up on you. I think switching-off the md5 plug-in in Brasero preferences might solve this.

---

### Post by OzzyFrank on 2010-11-14
As above, turning off the plugin will do the trick. I just did a blog post on it, for any who don't know how to do it:

[http://ubuntugenius.wordpress.com/2010/11/15/disable-annoying-creating-image-checksum-in-brasero-after-ubuntu-10-10-upgrade/](http://ubuntugenius.wordpress.com/2010/11/15/disable-annoying-creating-image-checksum-in-brasero-after-ubuntu-10-10-upgrade/)

Cheers. OzzyFrank

---

### Post by dubrict on 2011-01-24
Installing the cdrdao package fixed this problem for me.  No idea why it was left out of the dependencies.

```
sudo apt-get install cdrdao
```

---

### Post by rockerZ71 on 2011-02-22
> **dubrict said:**
> Installing the cdrdao package fixed this problem for me.  No idea why it was left out of the dependencies.

```
sudo apt-get install cdrdao
```

Thanks, looks like its working for me now

---

### Post by ehron on 2011-03-09
Ran brasero using the -g option.  Saw that the device was not ready.

Looked at output of mount.  In my case a cd that was no longer in the drive was still mounted.  Unmounted phantom cd from /media, and Brasero functioned as expected generating checksums in a timely manner and burning the disk.

---

### Post by JungleFish on 2011-04-15
> **thomas_d_j said:**
> I had the same problem.  You can run:
brasero -g
from a command prompt and you will get some debug messages pointing to the problem.  Mine kept saying device not ready.  A reboot fixed it however.

Same problem, same solution. ty

---

### Post by jtpoole99 on 2011-05-26
I have the same issue with Brasero being stuck at "creating image checksum", but this happens after the iso file has been burned and finalized.  

When the burning is done, it displays the "creating image checksum" message again and the drive light stays on for about 20-30 minutes in what seems like a stuck session and then after a few minutes it stops and tells me to insert a writable disc for burning.  This happens after every iso file I burn to cd/dvd/   

Maybe I'm putting this in the wrong section, but Brasero does this after the iso file has been burned and finalized.  I'm sure this isn't normal.  Would appreciate any help in solving this problem.

---

### Post by OzzyFrank on 2011-05-26
Did you disable the plugin as suggested? You shouldn't have that happening again after that.

---

### Post by digitaleagle on 2011-07-27
I had two computers, both with Ubuntu 11.04, that did the same thing.  I tried installing cdrdao on one of them, but it didn't seem to make a difference.  I checked the mount command, and I didn't see anything mounted in the media directory or anything like that.

My solution was to install k3b and use it.  It solved the immediate problem.

---

