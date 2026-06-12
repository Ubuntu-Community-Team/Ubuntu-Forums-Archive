---
title: "ext3 to ext2"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by chrisblack on 2009-01-28
is there a quick and easy way to convert from ext3 to ext2 - without needing ubuntu cd or similar...?

i've got gparted if that is going to help me?

thanks

chris

---

### Post by Simian Man on 2009-01-28
You could use gparted to do the conversion, but you realize this will erase all of your data right?

---

### Post by chrisblack on 2009-01-28
i'd like to do it without losing data...  it's for my ssd drive on acer aspire 

chris

---

### Post by iBoniek on 2009-01-28
You could try this:
-mount your partition as ext2
-delete journal file

reference:
[http://speech.braille.uwo.ca/pipermail/speakup/2003-November/021868.html](http://speech.braille.uwo.ca/pipermail/speakup/2003-November/021868.html)

---

### Post by handydan918 on 2009-01-28
My [friend]("http://www.google.com") found [this...]("http://www.redhat.com/archives/ext3-users/2002-September/msg00138.html")

---

### Post by chrisblack on 2009-01-28
iBoniek... that sounds simple, but how do I mount it as ext2 ?

chris

---

### Post by iBoniek on 2009-01-28
you could try 

gksudo gedit /etc/fstab

and change ext3 to ext2

---

### Post by chrisblack on 2009-01-28
tried that

gparted still shows it as ext3 as does the screen on boot up.

chris

---

### Post by jamesrl on 2009-01-28
I'm pretty sure its quite simple utility like tune2fs can change between the two.

[http://www.cyberciti.biz/faq/how-to-convert-back-linux-ext3-file-system-to-ext2-file-system/](http://www.cyberciti.biz/faq/how-to-convert-back-linux-ext3-file-system-to-ext2-file-system/)

---

### Post by sanderj on 2009-01-28
> **chrisblack said:**
> is there a quick and easy way to convert from ext3 to ext2?


Why do you want to do that?

Anyway:

Wikipedia says "Since ext3 aims to be backwards compatible with the earlier ext2, many of the on-disk structures are similar to those of ext2. "

So you can handle an ext3 partition/FS as ext2.

HTH

---

### Post by chrisblack on 2009-01-28
straightforward ... but how do I determine the original mount point for the last command?

chris

---

### Post by chrisblack on 2009-01-28
in answer to a previous post...

I want to do it to prolong the life of the ssd..

can anyone answer my question on how to determine the original mount point?

thanks

chris

---

### Post by iBoniek on 2009-01-29
just

```
sudo mkdir /mnt/mynewext
```
and
```
mount -t ext2 /dev/hda5 /mnt/mynewext
```
You have to change /dev/hda5 to your device name

You can also mount on ```
/
``` if it's Ubuntu partition

---

### Post by jrusso2 on 2009-01-29
> **chrisblack said:**
> in answer to a previous post...

I want to do it to prolong the life of the ssd..

can anyone answer my question on how to determine the original mount point?

thanks

chris

I am just curious has how to prolong the life of an SSD but using
ext2 over ext3?  If you have never used ext2 before when you lose
power it can be a real mess.

---

### Post by novafluxx on 2009-01-29
I believe he wants ext2 because it is not a Journaling file system. Am I right?

Try formatting it as FAT32 or ZFS ;-)

---

### Post by jrusso2 on 2009-01-29
There is really on a couple of reasons I know to run ext2.  One is a small partition like /boot and another would be pure speed.  I have never heard it prolongs the life of an ssd driver or any drive.  If this is true I would like to know why.

---

### Post by igknighted on 2009-01-29
> **jrusso2 said:**
> There is really on a couple of reasons I know to run ext2.  One is a small partition like /boot and another would be pure speed.  I have never heard it prolongs the life of an ssd driver or any drive.  If this is true I would like to know why.

I think his theory is that journaled file systems write to disk more, and since SSDs are very expensive investments with limited write cycles, you would want to protect that investment.

I would recommend NOT running a swap partition on a SSD, but I would not worry about ext2 vs. 3.  You will risk more in data through corruption over the life of the drive than you could ever save with the few fewer write cycles.

---

### Post by jerome1232 on 2009-01-29
As I understand it the problem is with repeated writes to the same physical area on the disc shortens the life of the disk substantially. This applies to Solid State Disk Drives only. I don't know how susbtantial it is, but have seen it recommended in quite a few places that you don't want to use a journaled file-system on a SSD drive..

Btw I'm not sure if this was answered clearly so here it is. If you mount the ext3 partition as ext2 it will not use the journal. You can remove the journal as well but it's not required.

If the file system has a journal this will remove it, if there is no journal this will add one.
```
sudo tune2fs -o ^has_journal /dev/sdxx
```

You can get more details here [http://batleth.sapienti-sat.org/projects/FAQs/ext3-faq.html](http://batleth.sapienti-sat.org/projects/FAQs/ext3-faq.html)

and by checking the tune2fs man page

---

### Post by jrusso2 on 2009-01-29
> **jerome1232 said:**
> As I understand it the problem is with repeated writes to the same physical area on the disc shortens the life of the disk substantially. This applies to Solid State Disk Drives only. I don't know how susbtantial it is, but have seen it recommended in quite a few places that you don't want to use a journaled file-system on a SSD drive..

Btw I'm not sure if this was answered clearly so here it is. If you mount the ext3 partition as ext2 it will not use the journal. You can remove the journal as well but it's not required.

If the file system has a journal this will remove it, if there is no journal this will add one.
```
sudo tune2fs -o ^has_journal /dev/sdxx
```

You can get more details here [http://batleth.sapienti-sat.org/projects/FAQs/ext3-faq.html](http://batleth.sapienti-sat.org/projects/FAQs/ext3-faq.html)

and by checking the tune2fs man page

I think that might be a bit over rated.  I was able to find some articles that refuted this as being a minor issue.  Probably easier to lose your drive using ext 2.

For example

    * Lets take the benchmark values from eeepc.it which makes it to a max of 50 MByte/sec. But this is a sequential write, which is not the write profile of our atime, swap, journaling… stuff. That are typically 4k Blocks which leads to 2 MByte/sec. (Side node: The EeePC 901go mount the same disk of SSD ‘EeePC S101, to be precise model ASUS SATA JM-chip Samsung S41.)
    * We stay also with the 2 million cycles and assume a 16GB SSD
    * With 50 MByte/sec we get 20 years!
    * With 2 MByte/sec we get 519 years!
    * And even if we reduce the write cycles to 100.000 and write with 2 MByte/sec all the time we’re at 26 years!!

And all this is with writing all the time, even ext3 does write the journal only every 30 secs if no data needs to be written. So the recommendation to safeguard SSDs, as the can not write that often is bull.

Changed last word due to forum rules.

---

### Post by jerome1232 on 2009-01-29
I would say your are making a fair amount of sense to me. :)

---

### Post by egalvan on 2009-01-29
There is also the fact that these types of memory have "write-balancing" algorithms built into the controller, to try level out the write cycles.

Further prolonging their life.

---

### Post by egalvan on 2009-01-29
> **chrisblack said:**
> 

in answer to a previous post...

I want to do it to prolong the life of the ssd..

Found this article, has some useful tweaks..

[http://tombuntu.com/index.php/2008/09/04/four-tweaks-for-using-linux-with-solid-state-drives/](http://tombuntu.com/index.php/2008/09/04/four-tweaks-for-using-linux-with-solid-state-drives/)

---

