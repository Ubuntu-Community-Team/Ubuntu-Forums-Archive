---
title: "Install alongside other operating system not available"
date: 2011-03-09
forum: New to Ubuntu
---

### Post by Aldoux on 2011-03-09
I'm trying to install Ubuntu 10.10 on my netbook, which already has Win 7 on it. but the option for install alongside other OS isn't available. Only erase and manually select partitions.

Here is the screen shot of my what I've got:  [http://i.imgur.com/ypawA.png](http://i.imgur.com/ypawA.png)

I want to use the 36gb Partition for Ubuntu. Which boot loader device would I select, and how would I partition the partition? ext4 an which mount point?
Thanks

---

### Post by deeZee on 2011-03-09
Your drive seems to be partitioned in an unusual way.  Have you tried to install another OS before?

---

### Post by Don1500 on 2011-03-09
> **Aldoux said:**
> I'm trying to install Ubuntu 10.10 on my netbook, which already has Win 7 on it. but the option for install alongside other OS isn't available. Only erase and manually select partitions.

Here is the screen shot of my what I've got:  [http://i.imgur.com/ypawA.png](http://i.imgur.com/ypawA.png)

I want to use the 36gb Partition for Ubuntu. Which boot loader device would I select, and how would I partition the partition? ext4 an which mount point?
Thanks

THAT IS ABSOLUTELY PERFECT. I'm not kidding, it's exactly what I would expect to see on a new set up.
From the live disk (or  usb drive, whatever you're using), go to the try out so you have ubuntu working.
Go to "system -=> Administration -=> Gparted (I believe it's still there)

You need to divide the largest partition you have into three. The first will be your Windows partition. JUST RESIZE THIS, DO NOT FORMAT!!!
Make that a size you are OK with but remember you need at least 10 gig for Ubuntu.) 
With the area you freed up make the next partition the same size as your RAM (normally 2 gig) This is your SWAP

Next format what is left into an ext4 partition, this is where Ubuntu will go.
Now hit APPLY and everything you just did will become true.

REBOOT and load WINDOWS, it will take some time because it will do a chkdsk to affirm it's new structure.

Now install Ubuntu. when you get to the page you showed. select the small partition and label it as SWAP.
Select the Ubuntu partition and say yes to format and the mount point is -=> / <=- (Only the "/" nothing else.)

It should not be a problem from there on.

---

### Post by Aldoux on 2011-03-09
> **deeZee said:**
> Your drive seems to be partitioned in an unusual way.  Have you tried to install another OS before?


No, just that when I installed Windows, I partition the drive so that it would be 100ish gig for win 7, 35ish for Linux, 100ish for storage, and 4ish for a swap.

Besides that, they're all raw/unformatted partitions.

---

### Post by Don1500 on 2011-03-09
Sounds like you didn't hit "APPLY"

---

### Post by Aldoux on 2011-03-09
> **Don1500 said:**
> THAT IS ABSOLUTELY PERFECT. I'm not kidding, it's exactly what I would expect to see on a new set up.
From the live disk (or  usb drive, whatever you're using), go to the try out so you have ubuntu working.
Go to "system -=> Administration -=> Gparted (I believe it's still there)

You need to divide the largest partition you have into three. The first will be your Windows partition. JUST RESIZE THIS, DO NOT FORMAT!!!
Make that a size you are OK with but remember you need at least 10 gig for Ubuntu.) 
With the area you freed up make the next partition the same size as your RAM (normally 2 gig) This is your SWAP

Next format what is left into an ext4 partition, this is where Ubuntu will go.
Now hit APPLY and everything you just did will become true.

REBOOT and load WINDOWS, it will take some time because it will do a chkdsk to affirm it's new structure.

Now install Ubuntu. when you get to the page you showed. select the small partition and label it as SWAP.
Select the Ubuntu partition and say yes to format and the mount point is -=> / <=- (Only the "/" nothing else.)

It should not be a problem from there on.

Thanks, but I'm running into an error with Gparted, it crashes when I open it.

Also, the largest partition already has windows 7 installed on it, and is about 80% full. 

Sorry if I read this wrong

---

### Post by Aldoux on 2011-03-09
> **Don1500 said:**
> Sounds like you didn't hit "APPLY"

Ah :(. Well can I do anything with them now? or will I need to go through your previous post?

---

### Post by Don1500 on 2011-03-09
You need to format the other partitions.
I couldn't see your complete partition map on that screen shot. But I think you said that now you have that one partition (104 gig) with windows (already there, and good)
one partition of 35 gig, unformated for Ubuntu and one partition of 4 gig for SWAP. 
SO your notebook came with a 150gig drive, correct?
All you need to do is fire up some type of partitioning program (like Gparted, but you said that crashes) and format those two partitions.

One other thing, you can only have 4 primary partitions on a drive, so some of what I said may not work if you are trying to make more than 4 partitions.

---

### Post by Aldoux on 2011-03-09
> **Don1500 said:**
> You need to format the other partitions.
I couldn't see your complete partition map on that screen shot. But I think you said that now you have that one partition (104 gig) with windows (already there, and good)
one partition of 35 gig, unformated for Ubuntu and one partition of 4 gig for SWAP. 
SO your notebook came with a 150gig drive, correct?
All you need to do is fire up some type of partitioning program (like Gparted, but you said that crashes) and format those two partitions.


The netbook has a 250gb Hdd.

Roughly it looks like:
100gb : Windows 7
100gb: raw/unformatted - use for storage later
36gb: raw/unformatted - want to use for Linux
4gb: raw/unformatted - want to use for the Swap

Can I just use the partition program that is built into the installer?

---

### Post by Don1500 on 2011-03-09
Yes you can, I have never used it (I like gparted) but the functionality is there.
Format the ubuntu partition to ext4 and your storage partition to ntfs. If you make the storage partition ext4 windows won't see it.

---

### Post by Aldoux on 2011-03-09
> **Don1500 said:**
> Yes you can, I have never used it (I like gparted) but the functionality is there.
Format the ubuntu partition to ext4 and your storage partition to ntfs. If you make the storage partition ext4 windows won't see it.

Thanks, which mount point should I use for the ext4? (/, /usr, etc) and which boot loader should I use?

/dev/sda/ ATA #### (250.1gb) - the harddisk
/dev/sda1
/dev/sda2
/dev/sda3
/dev/sda4 Windows 7 (Loader)

---

### Post by deeZee on 2011-03-09
> **Aldoux said:**
> I want to use the 36gb Partition for Ubuntu. Which boot loader device would I select, and how would I partition the partition? ext4 an which mount point?
Thanks

Your 36 gig partition is on /dev/sda2 and your mount point would be "/".

You could try selecting it to see if it will let you install, but I'm a little concerned that it's saying /dev/sda is unusable, and that your other partitions are "unknown."

---

### Post by Aldoux on 2011-03-09
> **deeZee said:**
> Your 36 gig partition is on /dev/sda2 and your mount point would be "/".

You could try selecting it to see if it will let you install, but I'm a little concerned that it's saying /dev/sda is unusable, and that your other partitions are "unknown."


Alright thanks, I've set it to that, now all I need is which /dev/sda for the boot loader.

---

### Post by deeZee on 2011-03-09
install the bootloader to /dev/sda

---

