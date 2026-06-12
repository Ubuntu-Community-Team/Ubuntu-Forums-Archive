---
title: "Perfect partioning..."
date: 2010-06-17
forum: New to Ubuntu
---

### Post by Procrat on 2010-06-17
Hi everyone! :)

I'm reinstalling Ubuntu, and I was wondering what might be the best partioning for my computer.
I have two 'devices' (as GParted calls them), sda has 20GB and sdb has 160GB.
Now, I have three questions:
1. How much swap do I need? I know the rule is two times the amount of RAM, but I only have 256MB RAM (:oops:), so is 512MB enough? :-?
As you can see, I don't mind giving up a lot of disk space for swap. Is there a disadvantage on using too much swap?
2. What basic filesystem should I use? Ext3?
3. What should I use the 20GB device for? (Previously, I used it /only/ for swap.)

So, what is the perfect partitioning? :)

---

### Post by Bucky Ball on 2010-06-17
Stick OS  on the 20Gb partition;  

/
/home
/swap (2Gb)

... and partition the 160Gb however is convenient for data storage. Smaller disk is faster OS and OS on fastest part of the drive if you install first.

Or ... You might like to stick:

/
/swap

... on the twenty and put /home on the 160Gb. If the 20Gb dies, that will only be the OS. Your /home data will be on the other drive. But we always back up, don't we??? ;)

---

### Post by Penguin Guy on 2010-06-17
> **Procrat said:**
> 1. How much swap do I need? I know the rule is two times the amount of RAM, but I only have 256MB RAM (:oops:), so is 512MB enough? :-?
As you can see, I don't mind giving up a lot of disk space for swap. Is there a disadvantage on using too much swap?
There is no disadvantage to using too much swap apart from the obvious fact that you'll have less space for other things. If you can spare the space, make a good chunk of swap. On a side note, I completely disagree with the [FONT="Courier New"]swap = 2 x ram[/FONT] rule - the more ram you have, the less swap you need (unless you're planning on using hibernation).
> **Procrat said:**
> 2. What basic filesystem should I use? Ext3?
Since it can be a complicated process to change the filesystem after installation, I'd go for the new ext4 filesystem - I've been using it for half a year and haven't had any problems.
> **Procrat said:**
> 3. What should I use the 20GB device for? (Previously, I used it /only/ for swap.)
Partition your drive however you want, although it would make sense to put Ubuntu and swap on the 20GB drive and leave the 160GB drive for data. You could also look into RAID which you could use to speed up your computer.

---

### Post by Procrat on 2010-06-17
What a quick response! Thank you! :)

But I'm not planning on using it for a lot of data storage of any kind. So I'm getting the feeling that 160 GB will remain unused...
Anyhow, I think I'll go for that second option.

My other rest however unanswered. Why shouldn't I use more swap when I can, and why can't it be spread over both HDs?
And should I use ext3 or another filesystem?

By the way, no, I actually do not back up... I always found it useless, seeing that all important data is uploaded on Ubuntu One. :)

---

### Post by Procrat on 2010-06-17
Appearantly I was to quick to react. :razz:

So on sda (20GB):
/ using ext4 (18-19GB)
swap (1-2GB)

And on sdb (160GB):
/home using ext4 (159GB)
((Is another swap partition usefull? If so: another 1GB of swap))

Alrighty! Thank you very much! :grin:

---

### Post by Penguin Guy on 2010-06-17
> **Procrat said:**
> Is another swap partition usefull?
Swap is mainly used as a backup if you run out of RAM, so I think one swap partition will suffice.

Glad you got your question resolved quickly, it might help others, though, if you marked it as solved ([COLOR="Green"]Thread Tools -> Mark this thread as solved[/COLOR]). :) Thanks.

---

### Post by philinux on 2010-06-17
[How much swap do I need?]("https://help.ubuntu.com/community/SwapFaq#How%20much%20swap%20do%20I%20need?")

---

### Post by MichealH on 2010-06-17
I could go for:
/ (25-40% of the Disk)
/swap (512Mb-1GB)
/home (The rest)

I put home in a different one because If I reinstall it keeps all my files and settings all I do then is reinstall the apps.

Or if you like you can Install without swap but it will be unresponsive when it is under overload because no more space to dunk temp files= crash!

---

### Post by srs5694 on 2010-06-17
> **Procrat said:**
> Appearantly I was to quick to react. :razz:

So on sda (20GB):
/ using ext4 (18-19GB)
swap (1-2GB)

And on sdb (160GB):
/home using ext4 (159GB)
((Is another swap partition usefull? If so: another 1GB of swap))

I'd say this is pretty reasonable. Since /home is where your user files go, it makes sense for it to more-or-less fill your 160GB drive. 20GB is on the large side for a Linux root (/) partition, but not ridiculously so, so this is a good way to split everything up. IMHO, there's no point to having /home on the 20GB drive and then a separate data partition on the 160GB drive, as Bucky Ball suggested. Such a configuration is often beneficial in a dual-boot configuration, but it appears this is a Linux-only system.

One consideration, though, is that older and smaller drives are generally slower than newer and bigger drives. Thus, it's conceivable you'd get better performance by putting swap on the 160GB drive. OTOH, disk access patterns might favor the 20GB drive, if you access user files on /home more than system files outside of /home. It's a bit of a gamble either way.

You could certainly create two separate swap partitions, and doing so might spread the disk load a bit, but probably not in a significant way. Again, it's hard to say what's best without running tests on *your* hardware.

One other point: You might consider using the GUID Partition Table (GPT) partitioning system rather than the older Master Boot Record (MBR) partitioning system. Although MBR is the default, GPT offers a number of minor advantages, including elimination of the confusing and occasionally trouble-prone distinction between primary, extended, and logical partitions; backups of all important partition definitions; CRC checksums of partition definitions to help spot problems; and names for partitions (vs. names for the filesystems they contain, which are present for both MBR and GPT). GPT also supports disks bigger than 2 TiB, which MBR doesn't. That's obviously not a concern for you with these disks, but it does mean that you'll probably be using GPT within a few years, so you might want to familiarize yourself with it before it's forced upon you. Linux is happy to install to and boot from GPT disks, although Windows isn't so flexible. If you go with GPT, be sure to create a [BIOS Boot Partition](http://grub.enbug.org/BIOS_Boot_Partition) of between 50KiB (yes KiB) and 1 MiB. GRUB will install part of itself there. In GParted or similar tools, you must select an option to create a new partition table, then select "gpt" as the type from an "advanced" menu in the dialog box.

---

