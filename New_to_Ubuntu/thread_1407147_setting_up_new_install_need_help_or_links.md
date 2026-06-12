---
title: "setting up new install need help or links"
date: 2010-02-14
forum: New to Ubuntu
---

### Post by hortstu on 2010-02-14
Basically my questions revolve around partitioning... I've read a lot about it the last few days so I'm fine with the making of them the size etc.

Here's the plan.  I'd happily take any criticism on this and I need to know the best mount point for a data partition that I'd like to be able to access from either OS install.

15gb....................hardy..................ext3.........../boot mount point?
3gb.....................hardy_home.............ext3.........../home mount point?
-----------------extended starts here------------------
15gb....................lucid..................ext3.........../boot mount point? or leave these unallocated for now
3gb.....................lucid_home.............ext3.........../home mount point? or leave these unallocated for now

(remainder of drive)....data...................ext3.........../? not sure what mount point to select for this

4gb.....................swap..................................?
-----------------extended ends here---------------------

Now if I do a manual install using the live cd and set up all these partitions will everything boot properly and automatically go to the right places or is there something I need to do to make that happen?

Thanks,
Mike

---

### Post by cariboo on 2010-02-14
I would suggest:

[list]
[*] 10Gb for / both versions
[*] 10Gb for /home both versions
[*] shared swap maximum size twice the amount of ram
[*] the rest /media/data
[/list]

Install Hardy first, and make sure Grub-legacy is on the first partition of the first hard drive, then install Lucid and install Grub2 over top of Grub-legacy. Grub is smart enough to point to the correct partition for which ever version you want to boot.

I should warn you that Lucid is just at alpha2 and is suffering from a few what might be considered show stopper bugs, depending on your skill level. I would suggest you have a look at the [Lucid Lynx Testing & Discussion]("http:///ubuntuforums.org/forumdisplay.php?f=377") sub-forum before jumping in.

---

### Post by uRock on 2010-02-14
I agree 10 gigs each would work great. I haven't used more than 8 gigs in the / partition, but I prefer it has room for expansions during upgrades. I also have 7.5 gigs of swap and I have filled it up while running Wireshark and downloading. That is with having all of the Ubuntu Studio stuff installed along with lots of network mapping and other penetration programs.

Good luck!

---

### Post by jken146 on 2010-02-14
> **hortstu said:**
> 
15gb....................hardy..................ext3...........**/boot** mount point?
15gb....................lucid..................ext3...........**/boot** mount point? or leave these unallocated for now


You don't want a 15 gig /boot !!!  I think you really mean that you want these partitions to be mounted at **/** (a.k.a. root, the top level of the filesystem hierarchy).

Apart from that, you've pretty much got it sussed. You're right, you would just choose the 'manual' option at the partitioning screen of the installer wizard, and create each partition there (it's simplest to make one big extended partition over the whole disk and put the others inside that). So, assuming you have one hard disk (/dev/sda), which is 300 GB in size here's what your partition table would look like:

```

partition    size      partition type    label         filesystem    mount point
/dev/sda1    300 GB    extended          --            --            --
/dev/sda2    15 GB     logical           hardy_root    ext3         /
/dev/sda3    3 GB      logical           hardy_home    ext3         /home
/dev/sda4    15 GB     logical           lucid_root    ext3         /mnt/lucid_root
/dev/sda5    3 GB      logical           lucid_home    ext3         /mnt/lucid_home
/dev/sda6    260 GB    logical           data          ext3         /mnt/data
/dev/sda7    4 GB      logical           --            swap         --

```

---

### Post by hortstu on 2010-02-14
> **cariboo907 said:**
> I would suggest:

[list]
[*] 10Gb for / both versions
[*] 10Gb for /home both versions
[*] shared swap maximum size twice the amount of ram
[*] the rest /media/data
[/list]

Install Hardy first, and make sure Grub-legacy is on the first partition of the first hard drive, then install Lucid and install Grub2 over top of Grub-legacy. Grub is smart enough to point to the correct partition for which ever version you want to boot.

I should warn you that Lucid is just at alpha2 and is suffering from a few what might be considered show stopper bugs, depending on your skill level. I would suggest you have a look at the [Lucid Lynx Testing & Discussion]("http:///ubuntuforums.org/forumdisplay.php?f=377") sub-forum before jumping in.

Thanks for the input caribou... I'm going to wait til april to install Lucid I just wanted to set aside some space for it.

I'm in the manual partitioner now during the install and don't know what to pick for a "mount point" on the data partition... or why it matters.

my choices are...
/
/boot
/home
/tmp
/usr
/var
/srv
/opt
/usr/local

How do I make sure swap is shared?  I imagine if I only make one it will be.

---

### Post by hortstu on 2010-02-14
> Apart from that, you've pretty much got it sussed. You're right, you would just choose the 'manual' option at the partitioning screen of the installer wizard, and create each partition there (it's simplest to make one big extended partition over the whole disk and put the others inside that). So, assuming you have one hard disk (/dev/sda), which is 300 GB in size here's what it would look like:

OK thanks for the corrections...

The partitioner doesn't give me the option of making an extended partition.  Just primary and logical so I assume anything that select logical for will automatically be in some extended partition?

---

### Post by hortstu on 2010-02-14
Also /mnt isn't an option... I imagine I should selecting something else and then make changes later via terminal?

---

### Post by jken146 on 2010-02-14
> **hortstu said:**
> Also /mnt isn't an option... I imagine I should selecting something else and then make changes later via terminal?

Just type it in yourself.

---

### Post by jken146 on 2010-02-14
> **hortstu said:**
> OK thanks for the corrections...

The partitioner doesn't give me the option of making an extended partition.  Just primary and logical so I assume anything that select logical for will automatically be in some extended partition?

A bit of googling revealed [this]("https://lists.ubuntu.com/archives/ubuntu-users/2009-June/187142.html"), which seems to say that you don't need to worry about the extended partition, just carry on creating them.

---

### Post by jken146 on 2010-02-14
> **hortstu said:**
> How do I make sure swap is shared?  I imagine if I only make one it will be.

It will be shared as long as you tell the installer about it when you install lucid. You'll have to choose 'manual' again then and tell it which you want to be /, /home, /mnt/data, /mnt/_harady_root, /mnt/hardy_home and swap.  But that's for April.

---

### Post by hortstu on 2010-02-14
Thanks everyone and especially Jken for the very specific help here.

I know it must seem rudimentary to all of you but I feel like I've learned quite a bit over the last 72 hours.

Thanks.

---

### Post by jken146 on 2010-02-14
You're welcome :-)

---

