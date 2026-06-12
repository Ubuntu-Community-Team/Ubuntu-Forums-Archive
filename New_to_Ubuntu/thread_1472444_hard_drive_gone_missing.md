---
title: "hard drive gone missing"
date: 2010-05-04
forum: New to Ubuntu
---

### Post by vnpifhf on 2010-05-04
I installed ubuntu some time ago and I never used windows again :P But I wanted to sell the computer, so I went into windows and disk management to delete the partition which caused me serious problems. I had to use the windows vista repair cd to use the command fixmbr.exe and it worked, so when I logged back into windows and half my hard drive was gone = 160GB into 79GB, so i went into disk management and it says you have 79GB free disk space, so i tried to get the partition back and try to reformat and revolume it into NTFS but every time I try to it says there is not enough disk space to complete this operation, the computer says its free space, why wont it work!!

Thanks for all your help on this as I need to sell this computer to buy my new ubuntu netbook :P:P

---

### Post by nitstorm on 2010-05-04
If you want to just make a separate partition, Try using the [GParted Live Disc]("http://gparted.sourceforge.net/download.php") and format the free space to NTFS. I think GParted allows us to make NTFS partitions too...

---

### Post by vnpifhf on 2010-05-04
nope that thing never worked , thanks anyway ^^

---

### Post by vnpifhf on 2010-05-04
bump

---

### Post by Grenage on 2010-05-04
> **jahangir99 said:**
> nope that thing never worked , thanks anyway ^^

You're going to have to give more details if you want meaningful help.  The advice was sound, what happened when you tried?

---

### Post by vnpifhf on 2010-05-04
i dont have a spare cd so the iso was outta question 

and also i tried downloading the other files, opened em with winrar and didnt find an application;.

---

### Post by Grenage on 2010-05-04
So rather than that thing never worked, you never tried that thing. ;)

Ok, basically the drive can't be resized or repartitioned while mounted, se you're either going to want to boot from a CD, or a USB.  Do you have an Ubuntu CD?  You can boot from that, run Gparted and resize.  Failing that, you can wipe the partition table with the Windows CD.

---

### Post by vnpifhf on 2010-05-04
hmm how do i do that because its empty and i just want it back again

---

### Post by Grenage on 2010-05-04
Do you... have an Ubuntu CD?

To double check, this is one hard drive in a computer, not a secondary drive with nothing on it?

---

### Post by vnpifhf on 2010-05-04
yep , 1 hard drive, but i split it in two for a windows ubuntu double boot.

Dont have any cd's including ubuntu and windows ones.

---

### Post by vnpifhf on 2010-05-04
b to the u to the m to the p

---

### Post by Grenage on 2010-05-04
Alas, without a bootable USB drive or CD/DVD, I have nothing to suggest.

---

### Post by jetsam on 2010-05-04
Would it work to install wubi and use gparted from there?  Does gparted work from cygwin...  Just throwing out some ideas.  

Vmware install will run gparted, but it won't have access to native hardware, but the other two above might.

Also, buy partition magic is an option...

or buy an external cd player or a live usb key with some kinda linux on there...

Your millage will vary.  Take care before committing to any hard drive modifications at the partition level.   

There's probably net based distros that still boot from floppy drive.  Do you have a floppy drive?  If you have a floppy and a non-bootable cd player, you can use smart boot manager to boot from the cd usually.

---

### Post by thirdspace on 2010-05-04
> **jahangir99 said:**
> yep , 1 hard drive, but i split it in two for a windows ubuntu double boot.

Dont have any cd's including ubuntu and windows ones.

Generally speaking the reasonable "free" solutions start with downloading a CD image from the Internet and burning it to a CD-R or CD-RW disc. If you can't do that (or obtain the burned CD-R some other way), no advice is going to get you far.

---

### Post by jetsam on 2010-05-04
> **jahangir99 said:**
> I installed ubuntu some time ago and I never used windows again :P But I wanted to sell the computer, so I went into windows and disk management to delete the partition which caused me serious problems. I had to use the windows vista repair cd to use the command fixmbr.exe and it worked, so when I logged back into windows and half my hard drive was gone = 160GB into 79GB, so i went into disk management and it says you have 79GB free disk space, so i tried to get the partition back and try to reformat and revolume it into NTFS but every time I try to it says there is not enough disk space to complete this operation, the computer says its free space, why wont it work!!

Thanks for all your help on this as I need to sell this computer to buy my new ubuntu netbook :P:P

So you really just wanna wipe the hard drive clean?  I'd try this... [DBAN aka Darik's Boot And Nuke]("http://www.dban.org/").  If that fails, then back to figuring out how to get gparted started.  And if that doesn't work, to heck with it.  Tell the new owner if they install Ubuntu, they get to see the secret ext3 partition!

Just to be perfectly clear, DBAN stands for Darik's Boot And Nuke and it does one thing... wipe out the contents of hard drives.  Use with extreme caution, but judging by your sig, op...

... It shouldn't be much of an issue, really, now should it?

---

