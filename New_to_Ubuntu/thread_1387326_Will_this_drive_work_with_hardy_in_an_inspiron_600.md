---
title: "Will this drive work with hardy in an inspiron 6000?"
date: 2010-01-21
forum: New to Ubuntu
---

### Post by hortstu on 2010-01-21
Western Digital Scorpio 160GB Internal EIDE Hard Drive for Laptops
Model: WD1600VERTL
SKU: 8692373

---

### Post by tgalati4 on 2010-01-21
It should work fine.  They are fast drives.  Quiet too.  I have the 320 GB version, which is the largest EIDE drive that they make.

---

### Post by hortstu on 2010-01-21
> **tgalati4 said:**
> It should work fine.  They are fast drives.  Quiet too.  I have the 320 GB version, which is the largest EIDE drive that they make.

Thanks unfortunately for me this computer won't recognize anything larger than 137gb.

---

### Post by tgalati4 on 2010-01-21
You could try a BIOS update.  Dell is pretty good about keeping their old hardware going.  Try the Ubuntu LiveCD, if it boots (and it should) then it should be able to deal with larger drives.

If you can't upgrade the BIOS, or if the BIOS just won't recognize a larger drive, then just partition the drive into 2 x 80 GB partitions.  You can do this with a $6 notebook EIDE to desktop EIDE connector.  Then plug the drive into an open connector on the drive ribbon cable.

You could also use a notebook drive USB adapter and partition it in another machine.

---

### Post by hortstu on 2010-01-21
> **tgalati4 said:**
> You could try a BIOS update.  Dell is pretty good about keeping their old hardware going.  Try the Ubuntu LiveCD, if it boots (and it should) then it should be able to deal with larger drives.

Yep it has the most current bios update and I ran it on the live CD before partitioning it and installing hardy
> 
If you can't upgrade the BIOS, or if the BIOS just won't recognize a larger drive, then just partition the drive into 2 x 80 GB partitions.  You can do this with a $6 notebook EIDE to desktop EIDE connector.  Then plug the drive into an open connector on the drive ribbon cable.

So you're saying I just have to do this on another computer then install it in the laptop and it will recognize the drive as 2 80GB drives.  That's a great idea.  I was told I couldnt do that because the BIOS wouldn't recognize it but if I do it on a computer that does... thanks. 

> You could also use a notebook drive USB adapter and partition it in another machine.

I might be misunderstanding your last statement.  Can you elaborate a little?

---

### Post by tgalati4 on 2010-01-22
If you can't find the notebook IDE ribbon adapter (Fry's electronics or online) then you can search for a USB notebook drive enclosure (Best Buy, Staples, etc).  They are more expensive, but easier to find.  You put your new drive into the USB enclosure and plug it into another machine, boot the liveCD.

Discover the device name--what the drive is called--in a terminal:

sudo fdisk -l

Probably /dev/sde

sudo gparted /dev/sde

Then make your partitions:

160 GB drive will probably give you 154 GB of space:

/      76 GB ext4
/home  76 GB ext4
/swap   2 GB swap

Or (if you need windows)

ntfs 76 GB
/    76 GB
/swap  2 GB

Once the partitioning is done, install windows first, then ubuntu.

If you are an advanced linux user (which means you already know this)

/  38 GB ext4 Ubuntu Karmic Koala
/home  76 GB ext4 (where your user data resides)
/New_Distro_1 38 GB (where Lucid Linxs will go)
/swap  2 GB

That way in a year or so, you can test out a new distribution (SUSE 12, Fedora 13, Ubuntu LL, Slackware, whatever) and keep your existing distro until you have thoroughly worked with it.

When you install the second distro, you will have a dual-boot system: your current, working Ubuntu, and a newer, untested distro--that you may like better.

Your /home data resides in the same partition, which makes backup easier.  Both distros can use /home, but be sure to back it up regularly.

---

### Post by hortstu on 2010-02-12
Thanks for the help tgalati

I'm still using the Hardy heron live cd... maybe that's why ext 4 isn't available to me in gparted?

Since lucid lynx will be my next install should I use ext 2 or ext3 for my home folder?

---

