---
title: "how to resize ubuntu partition?"
date: 2010-09-12
forum: New to Ubuntu
---

### Post by abs_kkk on 2010-09-12
like in the title i would like to know how to resize the linux partitions i.e the home and the root partitions.
thanks for the replys in advance ;)

---

### Post by Elfy on 2010-09-12
Use either a standalone partition editor such as gparted or use the partition editor in the system admin menu of the buntu livecd.

You will possibly need to turn of swap if it is in an extended partition with / and /home.

---

### Post by Lateralis on 2010-09-12
It is possible, but a few notes and words of caution:

1) Ensure that all data which is important to you is properly backed up out of harms way on external media, e.g. CD/DVD discs, external USB key/external HDD.  I'm sure you know that resizing a partition can be a dangerous affair and thus I'm sure this warning is redundant, but I somehow feel compelled to say it anyway. :P  

2) The partition(s) you want to resize must be unmounted before you can do this.  You should therefore use an Ubuntu LiveCD to make these changes. 

3) I don't know if this will happen as I've never done it before, but for all I know the UUIDs of /home, /root and other partitions might change.  If you refer to these partitions using UUIDs in /etc/fstab or /boot/grub/menu.lst or any other configuration file then these might need to be updated.  I say again though I'm not sure if that will happen - just conjecture and something you might want to look out for.  I'm sure someone else will be able to clarify this point for me?

---

### Post by abs_kkk on 2010-09-12
what is a UUID??

---

### Post by Elfy on 2010-09-12
```
sudo blkid
```

Universally unique identifier.

fstab uses uuid's

You can see here - 
```

/dev/sda1: UUID="9E04AD3804AD1475" TYPE="ntfs" 
/dev/sda5: UUID="66f8bf6a-aaac-471e-894b-cdb498691e64" TYPE="swap" 
/dev/sda6: UUID="43f9cd41-c238-4798-8435-5d19a839e4db" TYPE="ext4" 
/dev/sda7: UUID="3549d0ba-dc4d-4ef0-b3ed-417e53a71e1d" TYPE="ext4" 
/dev/sdb1: UUID="14ee47cc-54cb-4887-8773-fd53121efe10" TYPE="ext4" 

# / was on /dev/sda6 during installation
UUID=43f9cd41-c238-4798-8435-5d19a839e4db /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=66f8bf6a-aaac-471e-894b-cdb498691e64 none            swap    sw              0       0

#Media drive

UUID=14ee47cc-54cb-4887-8773-fd53121efe10 /mnt/sysmedia ext4 defaults 0 2

#Spare Drive
UUID=3549d0ba-dc4d-4ef0-b3ed-417e53a71e1d /mnt/spare ext4 defaults 0 2
```

Check you uuid's with the blkid command and make sure they match fstab - before you reboot.

You can mount and edit the /'s fstab from within the livecd.

---

### Post by egalvan on 2010-09-12
> **Lateralis said:**
> It is possible, but a few notes and words of caution:

1) Ensure that all data which is important to you is properly backed up ...
 I somehow feel compelled to say it anyway. :P

I also feel compelled to say it... BACK IT UP!


> 2) The partition(s) you want to resize must be unmounted before you can do this. 
 You should therefore use an Ubuntu LiveCD to make these changes. 

One problem is that most LiveCD's will search for (and mount) a valid 'swap' partition. You need to check for this.
There is a 'swapoff' cli command... hopefully other gurus will chime in.

> 3) ... the **UUIDs of /home, /root and other partitions might change.**
  If you refer to these partitions using UUIDs ...these might need to be updated.  ... 
 I'm sure someone else will be able to clarify this point for me?

Under PartedMagic (which is what I use for all my partition work) the UUID's indeed change, because the partitions are (technically) changing.

I solve this problem by **storing the original UUID's in a text file** and backed up on a USB device so I can access it easily from any OS/LivdCD etc..

After changing the partitions, **change the UUID's back to the original ones**. 
No need to update anything else.

---

### Post by abs_kkk on 2010-09-12
oh ok i think i won't be partitioning anmore :D there is alot of unsaved data i don't wanna lose :(

---

### Post by drs305 on 2010-09-12
Here are some tips I wrote for changing the size of an Ubuntu partition:
[Expanding an Ubuntu System Partition]("http://ubuntuforums.org/showthread.php?t=1219270")

It was written about a Jaunty bug, so the part you are interested in starts at the "Some basic rules for expanding your / system partition:" section. 

Also, the first link in the "Related Links" at the end is very good at describing partition changes and includes a few graphics.

---

### Post by srs5694 on 2010-09-12
I wrote [an article on this topic]("http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html") for IBM developerWorks recently. I see that [Part 2](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-2/index.html) is also now available, although that's for more advanced configurations and troubleshooting.

I've seen the claim that UUIDs change when resizing partitions once or twice before, but I've never encountered it myself. Here's an example:

```

$ sudo blkid /dev/sdc1
/dev/sdc1: UUID="3a50e92c-ae7f-4af0-be8d-fe19a7d5be4e" SEC_TYPE="ext2" TYPE="ext3" 
$ sudo gparted /dev/sdc
======================
libparted : 2.3
======================
$ sudo blkid /dev/sdc1
/dev/sdc1: UUID="3a50e92c-ae7f-4af0-be8d-fe19a7d5be4e" SEC_TYPE="ext2" TYPE="ext3"

```I shrank my test partition in GParted, so those two blkid calls were separated by a resize operation. The preceding test was done on a Gentoo system, but I just checked with PartedMagic 4.11, which egalvan claims changes UUIDs, and got the same (null) results. Perhaps there's such a bug in specific versions of GParted that produces changes in UUIDs, or maybe such a bug affects some filesystems but not others (I used ext3 in this test), but if so I don't know what versions or filesystems are affected. If egalvan can verify his claim of changing UUIDs, I suggest that he post details, such as the exact version of PartedMagic and/or GParted/libparted he's using, and what filesystem(s) are affected, so that others can verify the problem and people can avoid the buggy version(s) of the software.

---

### Post by Elfy on 2010-09-12
I've had UUID's change on me with gparted - though it was some time ago and I have no idea at all what version it was.

Regardless of that - checking the UUIDs and fstab is a minute job, easily achieved. Much quicker than waiting fro the mount to fail during boot.

Edit - as an aside here 

> Our apologies&#8230;

The page you requested cannot be displayedis the result of trying to read [http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-2/index.htmlPart 2](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-2/index.htmlPart 2) might be worth changing that

---

### Post by srs5694 on 2010-09-12
I've fixed the typo in the URL to Part 2 of the series on partition resizing.

---

### Post by Elfy on 2010-09-12
> **srs5694 said:**
> I've fixed the typo in the URL to Part 2 of the series on partition resizing.

Thanks - I have bookmarked it and part1 as well - I'll have a look a bit later - but they look well written :)

---

### Post by drs305 on 2010-09-12
*srs5694*'s work is a good read and is the link I indirectly cite as the "first link" in my post.

---

### Post by egalvan on 2010-09-13
> **srs5694 said:**
> I wrote [an article on this topic]("http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html") for IBM developerWorks recently. I see that [Part 2](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-2/index.html) is also now available, although that's for more advanced configurations and troubleshooting.

Excellent articles... and a big **THANK YOU** for making this available off-line, specifically a pdf...
it's so nice to be able to carry these around on a Palm Pilot (anybody else remember those?) to read anytime!

> I've seen the claim that UUIDs change when resizing partitions once or twice before, but I've never encountered it myself. Here's an example:

```

$ sudo blkid /dev/sdc1
/dev/sdc1: UUID="3a50e92c-ae7f-4af0-be8d-fe19a7d5be4e" SEC_TYPE="ext2" TYPE="ext3" 
$ sudo gparted /dev/sdc
======================
libparted : 2.3
======================
$ sudo blkid /dev/sdc1
/dev/sdc1: UUID="3a50e92c-ae7f-4af0-be8d-fe19a7d5be4e" SEC_TYPE="ext2" TYPE="ext3"

```I shrank my test partition in GParted, so **those two blkid calls were separated by a resize operation.** The preceding test was done on a Gentoo system, but I just checked with **PartedMagic 4.11,** which egalvan claims changes UUIDs, and got the same (null) results.** Perhaps there's such a [COLOR="Red"]bug[/COLOR]** in specific versions of GParted that produces changes in UUIDs, or maybe such a bug affects some filesystems but not others (I used ext3 in this test), but if so I don't know what versions or filesystems are affected. If egalvan can verify his claim of changing UUIDs, I suggest that he post details, such as the exact version of PartedMagic and/or GParted/libparted he's using, and what filesystem(s) are affected, so that others can verify the problem and people can avoid the buggy version(s) of the software.

I didn't specifically mention 4.11, but since I've been using PartedMagic since v1.8, and it's now up to v5.4, yeah, I most likely used 4.11 at one time :)
(an aside... PartedMagic is such a great "partition/format/recover" tool, that I donate (monthly subscription) to the authors... who BTW are VERY responsive to user comments/feedback/bug-reports.)

Changing UUID's plagued installs back in the 7.x days..
when I got serious about consulting in the 8.x days, I started keeping notes... especially about the swap partition.

this is a snippet of one note file related to UUID's, initramfs & blkid...
the url at the top is the cite.

> [http://ubuntuforums.org/showthread.php?t=857565](http://ubuntuforums.org/showthread.php?t=857565)


1 - Run 
code:
   sudo blkid -c /dev/null

 [b]Include the -c /dev/null bit.
 If you run blkid without options it reads from its cache file.
 If you've run it before and any partition has changed you'll get erroneous results.[/B]

2 - Check that the UUID for swap in /etc/initramfs-tools/conf.d/resume
 is the same as the UUID you got from blkid.
 Edit the file if necessary.

3 - Run
code:
    sudo update-initramfs -u

4 - Reboot

I have to admit I did not test the highlighted statement concerning blkid and it's cache...
I merely incorporated this info into my "bag-o-trix"

I will run a series of tests on this, using PartedMagic from v1.x to v5.x.
Work loads won't let me start for a couple of weeks.


An aside... I DO remember that the older gparted tools, roughly Hardy era,
 did erase the contents of a partition when a LABEL was applied. Not sure when this was "fixed".
The command-line 'label' tools, IIRC, did not have this problem.

And a further aside... 
My Opinion Only, but I don't think that changing the UUID on a partition that is **changed** in size is a "[COLOR="Red"]bug[/COLOR]"...
the theory of UUID is that it is UNIQUE to that UNIQUE partition.
Make it bigger, or make it smaller, and it is no longer the "IDENTICALLY UNIQUE" partition; hence the new Unique Identifier.

And if you don't agree, then hand me a $100 bill, I'll remove half of the bill (re-sizing it ;) ), and hand the remaining half back to you.
You still have your "original" $100 bill, it's just half-size :)

You're probablly thinking... "it;s not the same situation"

You are probably right, since partitions are more analogous to "containers";
so let's do this...

hand me a five-gallon pail, I'll cut the top half off, and then you can explain how your "re-sized"  2.5 gallon container is still "identical" to the "original" five-gallon container :)

Or build a 10x10 shed that you use to store gentoo penguins in.
Re-size it to 5x10, and see how many penguins still fit!

Enough of this humor, I should keep my day-job, I agree... :)
(rim-shot)
which reminds me, go to to get going to my day-job...

---

### Post by srs5694 on 2010-09-13
> **egalvan said:**
> Excellent articles... and a big **THANK YOU** for making this available off-line, specifically a pdf...
it's so nice to be able to carry these around on a Palm Pilot (anybody else remember those?) to read anytime!

Thanks for the PDF option are owed to IBM, not to me. I just wrote the content for their site; they designed the layout and format options.

That said, it's usually pretty easy to create a PDF from any Web page, although the details depend on your browser. In Firefox, select File > Print, then click "Print to File" as the printer. This will enable you to create a PostScript or PDF file of the printed form of the Web site. Of course, the results aren't always as neatly formatted as you'd like, but it's a quick and easy way to get a PDF if you need one. There are also a bunch of Web sites that do HTML-to-PDF conversion. I don't believe I've ever used any of them, but Googling "HTML to PDF" turns up a bunch of promising-looking hits.

> My Opinion Only, but I don't think that changing the UUID on a partition that is **changed** in size is a "[COLOR=Red]bug[/COLOR]"...
the theory of UUID is that it is UNIQUE to that UNIQUE partition.
Make it bigger, or make it smaller, and it is no longer the "IDENTICALLY UNIQUE" partition; hence the new Unique Identifier.
...
hand me a five-gallon pail, I'll cut the top half off, and then you can explain how your "re-sized" 2.5 gallon container is still "identical" to the "original" five-gallon container

By the same logic, the UUID should change every time you add, delete, or alter any file in the filesystem, since then the filesystem has changed. Or to take something more akin to your pail analogy, the names we apply to children shouldn't be used to identify them as adults, since they've obviously grown quite a bit. Reasoning by analogy can be dangerous. So can too much focus on one word in an acronym.

IMHO, it's better to look at it this way: For what is the filesystem UUID used, and based on that use, when does it make sense to change the UUID? The main use, at least in Linux, is to identify the filesystem for mounting purposes in /etc/fstab. If you resize or move a filesystem, chances are you still want to mount it in the same way you did before, so the UUID shouldn't change when you've resized or moved the filesystem. Hence, I stick by my use of the word "bug" in reference to any such change by a resizing utility.

---

### Post by QLee on 2010-09-13
[QUOTE=srs5694]...
IMHO, it's better to look at it this way: For what is the filesystem UUID used, and based on that use, when does it make sense to change the UUID? The main use, at least in Linux, is to identify the filesystem for mounting purposes in /etc/fstab. If you resize or move a filesystem, chances are you still want to mount it in the same way you did before, so the UUID shouldn't change when you've resized or moved the filesystem. Hence, I stick by my use of the word "bug" in reference to any such change by a resizing utility.[/QUOTE]
FWIW, I agree with you srs5694, I don't think the partition manager changes UUID, it seems to me that there might be a semantic difference at work here. The UUID is set when the volume is formatted and used as you have described. However, when a lower numbered partition is deleted, there is a renumbering of the partitions and thus the device node does change and is a different device node than what the partition previously had, and, in certain situations it will "appear" that the UUID has "shifted" (or changed) to a different device although is just a different node in the filesystem.

---

