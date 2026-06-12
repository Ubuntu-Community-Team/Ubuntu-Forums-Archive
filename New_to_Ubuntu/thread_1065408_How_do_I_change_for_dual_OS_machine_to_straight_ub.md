---
title: "How do I change for dual OS machine to straight ubuntu?"
date: 2009-02-09
forum: New to Ubuntu
---

### Post by sooperspook on 2009-02-09
Hi! I've been using Ubuntu for a year or two although I still consider myself a newb at it. 

At first I dual booted with XP but now I want to switch completely over to ubuntu.

How can I do this without having to reinstall from scratch? 

Any help will be appreciated.

Thanks in advance. :)

---

### Post by RealG187 on 2009-02-09
Delete the XP Partition, remove XP from grub and resize the Ubuntu partition to take this space.

---

### Post by beno1990 on 2009-02-09
Download gparted

```

sudo apt-get install gparted

```

And use that to repartition your drives and delete the Windows OS partitions, and set them up as a Linux partition(s).

Then you'll want to remove the Windows XP boot entry from your GRUB menu.

```

sudo gedit /boot/grub/menu.lst

```

Scroll down to where you can see the Windows entry and delete it. Don't touch anything else in that file other than the Windows boot entry though, you could break your OS.

---

### Post by lapubell on 2009-02-09
you're going to have to resize your main partition from a live cd or something that isn't your main hdd.  you can't resize it if you are using it.  :)

if you don't want to do that, you could just delete the XP partition and make a new partition that ubuntu can read (etx, fat32, reiser, etc.) and just store your stuff there...

---

### Post by sooperspook on 2009-02-09
Whoa! That was a fast reply time!

See, this is why this community rocks hard. :D

Thanks guys!

I'll let you know how I do, assuming I don't blow up my machine or something. :)

---

### Post by kansasnoob on 2009-02-09
Well, first of all, why bother? I'm thinking you'd be better off just resizing partitions if you need space.

It can get complicated. For instance if Win is the only primary partition you may find the Ubuntu partition NOT bootable without creating a new primary boot partition.

---

### Post by unplugged23 on 2009-02-09
> **kansasnoob said:**
> Well, first of all, why bother? I'm thinking you'd be better off just resizing partitions if you need space.

It can get complicated. For instance if Win is the only primary partition you may find the Ubuntu partition NOT bootable without creating a new primary boot partition.

Very true and very important. Keep a close eye on your boot flag partition!

---

### Post by RealG187 on 2009-02-09
If you get a grub menu, then I think the Linux Partition is the one that had the boot record...

---

### Post by sooperspook on 2009-02-09
Bit late for that warning. I just deleted the Win partition but everything seems to be ok. It rebooted no problem.

Before I do anything else tho, what should I allocate the space as? Primary Partition,? Logical? Extended? 

And what is the difference? (Told you I'm still pretty much a newb at this.)

---

### Post by sooperspook on 2009-02-10
Ok I've allocated the space as a Primary Partition. I have no idea if that affects anything.

I have run into a little problem though, I can't write to it. I wanted to copy my music over to it but it tells me I don't have permission to do so.
Any ideas?


Another thing, kansasnoob mentioned resizing the partitions. How? I tried resizing the partition I normally use to take up the extra space but I don't even get the option to do so in Gparted. It's greyed out.

Thanks in advance.

---

### Post by whoop on 2009-02-10
I would just ditch the partition you just created and resize your existing linux partition. You just have to boot ubuntu from the livecd, run gparted, make sure that your drive is unmounted, delete your new partition and resize your old partition.

---

### Post by theozzlives on 2009-02-10
Boot off the live CD, you should be able to resize then.

---

### Post by sooperspook on 2009-02-10
I tried using the live cd but i only have the old one (5 dot something) and there is no gparted on it.

---

### Post by RealG187 on 2009-02-12
> **sooperspook said:**
> I tried using the live cd but i only have the old one (5 dot something) and there is no gparted on it.

You probably have 5.10 and You probably should update.

---

### Post by sooperspook on 2009-02-15
Yeah :) 

I have updated though. I just haven't updated the CD. :D

Anyway, I tried using a Live USB to start up (so I can use gparted from that) but for some reason I don't get the option to boot from USB in the BIOS. ANy idea what might be the reason?

thanks.

---

