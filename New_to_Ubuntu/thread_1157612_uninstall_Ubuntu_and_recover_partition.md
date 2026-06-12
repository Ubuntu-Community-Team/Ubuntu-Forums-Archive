---
title: "uninstall Ubuntu and recover partition"
date: 2009-05-12
forum: New to Ubuntu
---

### Post by robertron76 on 2009-05-12
Following is the config of my HDD and have dual-boot menu set.


[LIST]
[*]Vista     -- C:\ (120GB)
[*]Ubuntu  -- 40 GB (E:\) -- hidden, meaning I can't see this in Vista.
[*]Data      -- F:\ 70GB
[/LIST]
I'd like to uninstall Ubuntu and recover partition to merge it with Vista.

I'd like to do this to familiarize install/uninstall  Ubuntu and create/recover partition procedures.

I know from other threads that I need to fix MBR and GRUB when uninstalling Ubuntu.

Can you suggest a cleanest approach on doing this?

TIA

---

### Post by robertron76 on 2009-05-12
> **robertron76 said:**
> 
Skol,

Is your PC booting directly into Windows now, without getting the Grub boot loader?

If so, it probably wiped all the partitions except the one where your Windows restore is and set the rest of the HDD back to one Windows partition.

To make sure, simply boot up using the Ubuntu cd (make sure the Bios is set to boot from CD first) and choose the "try without making any changes to my PC" option.

Once it loads up, go to  System > Administration > Partition Editor to launch GParted.

Load Gparted and and take a look at the partitions. If you see any that are listed as Ext2, Ext3 or Linux Swap, delete them. You can then resize the Windows partition to reclaim all the free space.

I found a post, wehre Didius Falco provided a solution to delete Linux partition and recover it, which answers my second-half of the Q.

But prior to this, How do I fix MBR/GRUB? I have Vista recovery CDs, but I dont want to use Vista Recovery CDs to reset Vista to factory settings as it has data in it.

What's the usual procedure to remove dual-boot menu option and have Vista as default?

BTW, I've attached the partition screenshot, where I need to remove sda5 and recover it back to sda2--Vista.

---

### Post by robertron76 on 2009-05-12
> 1.
restore a Windows MBR to your HDD while you are in Ubuntu by doing:
     Code:
     sudo apt-get install lilo
sudo lilo -M /dev/[COLOR=red]sda[/COLOR] mbr 
And change "sda" if the drive in question is different
> 2.
With the Vista install disc, navigate to system repair and command prompt.  type

     Code:
     bootrec.exe/FixMbr 
Reboot.  Good luck.
> 3.

You'll need to restore Vista's mbr. If you have no disc you can get one here:

[http://neosmart.net/blog/2008/window...disc-download/]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/")

Instructions here:

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

You want to "fix boot" and "fix mbr"!

Which one of the above options is better to restore MBR?

---

### Post by sir_nasty on 2009-05-12
I'd personally do it off the vista disc...  With microsoft stuff I've found it MUCH easier to use the install cd's to do repairs with rather than mess with outside stuff....

---

### Post by Mark Phelps on 2009-05-13
Your "recovery" CDs probably will not let you do anything other than completely reinstall Vista -- which is not what you want to do.

Personally, I would go for option #3 -- because you will have a Vista "Repair" CD that will come in handy later.

---

### Post by robertron76 on 2009-05-13
> **Mark Phelps said:**
> Your "recovery" CDs probably will not let you do anything other than completely reinstall Vista -- which is not what you want to do.

Personally, I would go for option #3 -- because you will have a Vista "Repair" CD that will come in handy later.

Thanks Mark.That's what I was thinking of.

---

