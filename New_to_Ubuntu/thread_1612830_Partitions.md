---
title: "Partitions"
date: 2010-11-03
forum: New to Ubuntu
---

### Post by sneaker12345 on 2010-11-03
I want to remove my current Ubuntu partitions and restore my hard drive to the way it was when I just had Windows 7 installed on it. My reason for this is simply that I want a fresh Ubuntu install. The hard drive is a bit messy due to playing around with it for learning purposes. Currently my partitions look like this:

sda1 ntfs Windows7(loader)
sda2 ntfs Windows7
sda3 (extended):
  sda6 ext4 Ubuntu 10.10
  sda5 swap linux-swap

My question is which of these are safe to remove which will result in my computer just booting into Windows 7 like it use to? I would assume that removing all except sda1 and sda2 would accomplish my goal, but I want to ask before I go and make a mistake! Thanks in advance.

---

### Post by Foxheadz on 2010-11-03
You could just install Ubuntu from a live Cd and then just install it to the Ubuntu partition and format it.

---

### Post by sneaker12345 on 2010-11-03
I want to get to the point where windows 7 is the only thing on the computer first. Would what I originally said work?

---

### Post by Quackers on 2010-11-03
You would probably need to repair the Windows mbr (overwrite grub) with a Windows repair disc as grub won't find any of the Ubuntu partitions and will panic and boot nothing at all.
Also the Ubuntu partitions should be deleted whilst the system is unmounted. You may be able to use the Gparted in the Ubuntu Live CD for this. I personally use the GParted Live CD.

---

### Post by coffeecat on 2010-11-03
> **sneaker12345 said:**
> I would assume that removing all except sda1 and sda2 would accomplish my goal, but I want to ask before I go and make a mistake! Thanks in advance.

If you do that you will (temporarily) make the system unbootable. This is because grub stage 1 is in the mbr, but stage 2 and the configuration files are in the root partition of Ubuntu - in your case sda6.

If you don't have a Windows repair or install disk to run fixmbr, you can restore the Windows mbr with an Ubuntu live CD (rather counter-intuitively). Post back if you want to know how.

---

### Post by Rex Bouwense on 2010-11-03
Quackers is correct.  When you installed Ubuntu, GRUB took over the booting duties.

---

### Post by BlueLionCostas on 2010-11-03
Why would you want that? If you really want to restore it, you should indeed just delete sda3 and resize sda2 back to full size and additionally restore the windows mbr. But what good would this do to you, if you're just going to install Ubuntu again? Because if you're just going to install Ubuntu again, I strongly advise against this :) Considering the Ubuntu installation has the ability to use the existing Ubuntu partition, formatting it, effectively removing everything from it.

Edit: I see I should learn to write posts faster, since when I'm done writing there are already posts saying what I'm saying...

---

### Post by sneaker12345 on 2010-11-03
> **coffeecat said:**
> If you don't have a Windows repair or install disk to run fixmbr, you can restore the Windows mbr with an Ubuntu live CD (rather counter-intuitively). Post back if you want to know how.

I'd like to know how, please. I have my Ubuntu disc here,  my windows disc isn't available.

---

### Post by coffeecat on 2010-11-03
> **sneaker12345 said:**
> I'd like to know how, please. I have my Ubuntu disc here,  my windows disc isn't available.

You have two options. Since you can still boot into Windows 7, type 'repair' in the search box in the start menu. Go to create a repair disk (or words to that effect) and follow the prompts. You will then have a bootable W7 repair disc which you can repair the mbr with and do other rescue operations if needed. **Do it now** - seriously - while Windows 7 is still bootable. You may regret it later if you don't.

Once you've made the repair disc, you may need to drop to a command prompt to run bootrec (see the link in my post below).

The other option is also in this link, which is to install and run lilo in the live CD Ubuntu session. Here's the post with both:

[http://ubuntuforums.org/showpost.php?p=10056077&postcount=5](http://ubuntuforums.org/showpost.php?p=10056077&postcount=5)

If you choose to use lilo, before you close down from the live Ubuntu session, open System > Administration > Gparted and delete the Linux partitions as well as the extended partition sda3. You will need to right-click on sda5 and choose swapoff before you can do this.

IMPORTANT. **Do not resize the Windows 7 C: partition with Gparted**. Once you've removed the Linux partitions with Gparted, power down the machine, remove the Ubuntu CD and reboot into Windows and use Windows 7 to resize your C: partition or create other partitions as you may need.

---

### Post by BlueLionCostas on 2010-11-03
> IMPORTANT. **Do not resize the Windows 7 C: partition with Gparted**. Once you've removed the Linux partitions with Gparted, power down the machine, remove the Ubuntu CD and reboot into Windows and use Windows 7 to resize your C: partition or create other partitions as you may need.
I'm curious, why exactly is this? I remember doing this on a few occasions through PartedMagic.

Also, I'll repeat what I said before, if you're after a clean install of Ubuntu this is all unnecessary. There's always some risk involved with partitioning and this amount of trouble doesn't really sound like something you'd want to do just to make that installation an extra bit cleaner, which it probably won't even be.

---

### Post by coffeecat on 2010-11-03
> **BlueLionCostas said:**
> I'm curious, why exactly is this? I remember doing this on a few occasions through PartedMagic.

When Vista first launched there were many nasty instances of Gparted making Vista unbootable after the C: partition was resized. This has also happened with W7. It's well-documented on this forum and all over the intertubes. The newer versions of Gparted may not do this, but it's best to be safe.

I have resized a Vista partition myself with Gparted and got away with it, but I wouldn't recommend it because so many people have come to grief.

> **BlueLionCostas said:**
> Also, I'll repeat what I said before, if you're after a clean install of Ubuntu this is all unnecessary. There's always some risk involved with partitioning and this amount of trouble doesn't really sound like something you'd want to do just to make that installation an extra bit cleaner, which it probably won't even be.

The OP seems to be clear that they only want Windows on the machine. At least that's the way I read their posts.

---

### Post by BlueLionCostas on 2010-11-03
> **coffeecat said:**
> When Vista first launched there were many nasty instances of Gparted making Vista unbootable after the C: partition was resized. This has also happened with W7. It's well-documented on this forum and all over the intertubes. The newer versions of Gparted may not do this, but it's best to be safe.That seems like a good reason :P

> 
The OP seems to be clear that they only want Windows on the machine. At least that's the way I read their posts.
Well, he did say his ultimate reason was a clean install of Ubuntu, but I guess I said my piece, so I'll just keep my peace.

---

### Post by coffeecat on 2010-11-03
> **BlueLionCostas said:**
> Well, he did say his ultimate reason was a clean install of Ubuntu, 

You're quite right - I missed that. In which case I 100% agree with you that a fresh install of Ubuntu would be the simplest and cleanest option. However, it may be that the OP wants the experience of restoring the machine to its original state before re-installing. In which case I would respect that. Between us we've given plenty of options to try. :)

I want to correct/amend something else I said:

> **coffeecat said:**
> I have resized a Vista partition myself with Gparted and got away with it, but I wouldn't recommend it because so many people have come to grief.

The only reason I got away with it was because I had the retail Vista install DVD which most (all?) people with machines with pre-installed Windows do not have. I did indeed make Vista unbootable by resizing it with Gparted, but it was quickly and easily repaired with the recovery options in the DVD. But without a Vista install DVD you are effectively snookered. Or a repair DVD in the case of W7, which the OP may or may not have prepared already. Hence my comments.

---

