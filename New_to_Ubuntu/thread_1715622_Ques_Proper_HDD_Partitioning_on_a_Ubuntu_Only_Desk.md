---
title: "Ques: Proper HDD Partitioning on a Ubuntu Only Desktop"
date: 2011-03-27
forum: New to Ubuntu
---

### Post by paulmr1968 on 2011-03-27
Hi all,

New to Ubuntu.  I'm taking up the project on the advice/counsel of a friend who is an expert.  I'm not.  I'm a moderately capable computer user from the Windows/Mac world.

I'm having installation issues.  I have an old Windows XP/Amd Athalon chip box from HP circa 2002.  HDD is 80GB, Nvidia 5700 card - AGP x1.

I've installed Ubuntu three times and it hasn't been working properly.  Before I started, I create the CD-ISO by burning and verifying.  I then did a full offload of all data from the PC.  I then used WipeDrive to get a clean hard drive.  I'm looking to do a clean, Ubuntu only installation.

What should the proper partitioning of a 80 GB hard drive be?  (I believe this to be the/a problem because after 3 installs, on the 4th I choose manual.  When I didn't try to change anything from the default, and move forward, I got an error message about how it was setup.  Don't remember the details of the message.)

Please include the full table of info.  Device, Type, Mount point, Format?, Size, Used info that will appear.

Thank you very much!

---

### Post by fela on 2011-03-27
Well, the automatic partitioner should do it for you the 'proper' way if you select 'Use whole disk' (or however it's phrased).

If you want to do it manually, here is the "way I'd do it":

EDIT: You asked about what device name to use. Well to find this out, open a terminal (apps > accessories > terminal). Now run ```
sudo fdisk -l
``` and the drive you want will be the one that says it's 80GB in size. It's almost certainly /dev/hda, or /dev/sda if it's a SATA (which I highly doubt as it's a machine from 2002) or SCSI (which I also highly doubt).

(end edit)

The first partition will be about 150MB, mount point /boot, format to ext4. The second partition will be about double your RAM size, and this will be the swap partition (format to swap, no mount point). If you're looking to upgrade your RAM in the near future, make sure this partition will be bigger than the size of your RAM, or you won't be able to hibernate.

The third partition will be ext4, mount point /, and will fill the rest of the disk.

But really, I think you're better off with the auto partitioner.

---

### Post by Cheesehead on 2011-03-27
The installer recommendations should be fine. Listen to the installer.

Manual partitioning has a risk tradeoff: On one hand, you can separate your data from apps-and-os, so a bad upgrade won't corrupt your data. But on the other hand, if a partition fills up faster than expected a resize is much riskier than a bad upgrade.

For 80 GB, you can get better data protection by simply backing up regularly.

---

### Post by Hedgehog1 on 2011-03-27
> **paulmr1968 said:**
> ...***I've installed Ubuntu three times and it hasn't been working properly***.  Before I started, I create the CD-ISO by burning and verifying.  I then did a full offload of all data from the PC.  I then used WipeDrive to get a clean hard drive.  I'm looking to do a clean, Ubuntu only installation....

paulmr1968,

Can you describe what isn't working properly?  Ar you having issues with the OS after the install, or are you only unhappy with the partitioning the install defaults to.

Also, I am going to respectfully disagree with fela's partitioning suggestion.

Assuming your hard drive shows up as /dev/sda (if yours shows up as /dev/hda, swao hda for sda), here is a workable partitoning layout:

/dev/sda1 10 gig ext4 mount point: '/' (said as "root")
/dev/sda2 2.2 gig Linux Swap (this assumes 2 gig RAM - take your RAM amount and make this partition 1.1 x RAM)
/dev/sda3 67 gigs ext4 mount point: '/home' (uses whatever is left of the drive)


***The Hedge***

:KS

---

### Post by vanadium on 2011-03-27
I used to have a simple single / partition and a swap on my 80 GB drive. Now, I also have as setup similar to Hedgehog1: a 10 GB root partition, then an extended partition that includes 1) the /home partition and 2) the swap.

---

### Post by paulmr1968 on 2011-03-28
Thank you all for the replies.

My techie friend concluded that I had too many bad sectors on my hard drive.  Thus, why the default installer wasn't working.

When I did manual partioning, it worked a little.  Until the I/O errors that went off the screen.

So, instead of converting an old machine to a Linux-only box, I'm using my newer PC and have installed VMWare Workstation.  I've setup a VM running the Desktop LTS.

So far it seems to be working, but I think I'll have different issues from this point forward.

I'm looking to get to a LAMP type setup and build a database/website.

Thank you all for your help.  Without it, I wouldn't have tried enough things to eventually conclude what I did and move on.

---

### Post by fela on 2011-03-28
> **paulmr1968 said:**
> I'm looking to get to a LAMP type setup and build a database/website.

Awesome :D

---

