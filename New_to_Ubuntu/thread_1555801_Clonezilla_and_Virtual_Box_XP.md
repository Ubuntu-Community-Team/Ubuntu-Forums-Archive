---
title: "Clonezilla and Virtual Box XP"
date: 2010-08-18
forum: New to Ubuntu
---

### Post by blues2use on 2010-08-18
Running Ubuntu 10.04,2.6.32-24-generic, Gnome Desktop 2.30.2, GRUB 1.98-1ubuntu7 ...**currently this is a Ubuntu and XP Pro dual-boot system ** and I'd like to change it to a ubuntu system with XP Pro in VirtualBox...

1. I'd like to use Clonezilla to make **-COMPLETE-** separate images of my current ubuntu installation and of my XP Pro installation, reformat the drive and then restore the ubuntu Clonezilla image first. 

2. Then install XP Pro in VirtualBox and restore the XP Pro image to the VirtualBox Xp Pro installation...**presuming this is possible**... 

3. Mostly, I am concerned with what grub will do when I restore the ubuntu image. The partition numbering will change and, of course, the XP Pro OS would be missing from the boot menu.

4. Will I have to run SuperGrub or a Live CD to update grub so that the partitioning will be corrected and the proper boot area is enabled?

Is there a better way to do this?

**[COLOR="blue"]Any/all help is most appreciated... Thanks[/color]**

---

### Post by jonnywombat on 2010-08-18
The converting a XP install on a HDD to vdi file is discussed [here]("http://forums.virtualbox.org/viewtopic.php?t=1404")

hth

---

### Post by blues2use on 2010-08-18
> **jonnywombat said:**
> The converting a XP install on a HDD to vdi file is discussed [here]("http://forums.virtualbox.org/viewtopic.php?t=1404")

hth

I'm reading it now...as I have a SATA system rather than IDE, I presume that I only need to follow the **Step By Step Instructions For Windows XP** and not muck about with the **IDE MERGE** instructions.

I am also looking at these instructions from another site:

1. Boot to the Live CD.

2. Open a terminal window and type:

sudo dd if=/dev/YOUR DEVICE (sda,sdb,etc.) of=A_UNIQUENAME.iso

This takes your OS HDD and creates an ISO from it in FILE format and stores it in your Home directory.

3. Reboot

4. Open VitrualBox and Create a new VM.

5. Right click the VM, select settings, click Mount a CDROM, Select Mount an ISO or Image file.

6. Select ADD.

7. Browse /home and locate the ISO you created with the "sudo dd if=/dev/cdrom of=cd5.iso" command.

8. Select it and double click it (or hit OK).

9. Click OK.

10. Start the VM.

This looks to be an easier method **_-IF-_** it works...

Also, looking at this information on using VMWare's P2V: [http://www.sysprobs.com/physical-virtual-virtualbox-virtualbox-p2v](http://www.sysprobs.com/physical-virtual-virtualbox-virtualbox-p2v)

They both seem to be viable alternatives.

Thanks for the reply

---

### Post by jonnywombat on 2010-08-18
TBH.. when I read through the thread I thought personally I would just do a fresh install of XP into the virtual box, seemed a much simpler and quicker option.

---

### Post by blues2use on 2010-08-18
> **jonnywombat said:**
> TBH.. when I read through the thread I thought personally I would just do a fresh install of XP into the virtual box, seemed a much simpler and quicker option.

Yes, it would be -except- for having to reinstall software...I have XP stripped down and customized and the -ONLY- reason for even using it in a virtual machine is because of software that I have that will only run in Windows XP, Vista or 7. I have my CD's but dread the thought of having to do all of that installation of software and customization of the software and system over again if I can just create a virtual machine image and install that into VirtualBox.

At this point, **I am far more concerned with what grub will do** after I clean install 10.4 and then restore my current 10.4 image via Clonezilla. _I would think that the partitioning identification would change since the NTFS partition would be gone._ I'm hoping it's as simple as booting to the live cd and updating grub and rebooting into my ubuntu system and then on to the VirtualBox install of my XP image.

Gparted screenshot attached

Thanks for the reply

---

### Post by bodhi.zazen on 2010-08-18
As much time as it takes, I advise a different approach.

You can manage your partitions with gparted on a live CD and I see no reason to clone / restore Ubuntu.

As far as windows goes, I suggest you perform a fresh install in VBox, you will get much better performance. Install as much as possible without an internet connection.

Then install only the windows apps you need.

Then perform all updates.

At that point take a snapshot.

The gain in performance and the fact that you will have a snapshot of a fresh known good install are well worth the effort.

---

### Post by blues2use on 2010-08-18
> **bodhi.zazen said:**
> As much time as it takes, I advise a different approach.

You can manage your partitions with gparted on a live CD and I see no reason to clone / restore Ubuntu.

As far as windows goes, I suggest you perform a fresh install in VBox, you will get much better performance. Install as much as possible without an internet connection.

Then install only the windows apps you need.

Then perform all updates.

At that point take a snapshot.

The gain in performance and the fact that you will have a snapshot of a fresh known good install are well worth the effort.

I've been using ubuntu for almost 18 months but have a long way to go insofar as knowing the most expeditious routes to take to perform certain functions. I understand how Gparted can manage partitions, format, copy, paste, move etc. but **if I copy/paste and then remove the NTFS partition, what step(s) do I need to take to make sure that grub is aware of that and will allow me to boot back into my working ubuntu installation?** 

To reiterate, I would like to preserve my current physical XP install, image it in one form or another and then install that image into VirtualBox. Since I have plenty of disk space in my ubuntu installation, I think I'll try that first and, depending on success or failure, consider the other suggestions made so far and I will certainly take your suggestions into account as well.

Thanks for the reply

**This forum is a wonderful resource for folks like me and I sincerely appreciate everyone taking the time to offer their help...**

---

### Post by bodhi.zazen on 2010-08-18
Once you are ready, you can simply delete (reformat) your windows partition (assuming you are not running wubi).

You then update grub from Ubuntu.

If you wish, you can use the old windows space as a data partition or install another OS.

Converting your windows install to a vdi should be easy.

FYI: If you keep your windows partition you can potentially boot it directly either with virtualbox or if you have the hardware KVM.

---

### Post by blues2use on 2010-08-19
> **bodhi.zazen said:**
> Once you are ready, you can simply delete (reformat) your windows partition (assuming you are not running wubi).

You then update grub from Ubuntu.

If you wish, you can use the old windows space as a data partition or install another OS.

Converting your windows install to a vdi should be easy.

FYI: If you keep your windows partition you can potentially boot it directly either with virtualbox or if you have the hardware KVM.

No, I'm not running Wubi...So, with the Live CD, I can delete the partition and reformat to ext3 after it's imaged and then run **sudo update-grub to insure that ubuntu will boot properly** and that the former XP (partition and operating system) will not be on the boot menu?

Thanks for the reply

---

### Post by bodhi.zazen on 2010-08-19
> **blues2use said:**
> No, I'm not running Wubi...So, with the Live CD, I can delete the partition and reformat to ext3 after it's imaged and then run **sudo update-grub to insure that ubuntu will boot properly** and that the former XP (partition and operating system) will not be on the boot menu?

Thanks for the reply

That plan should work. Consider ext2 or ext4, both will, in general, perform better then ext3.

---

### Post by blues2use on 2010-08-20
> **bodhi.zazen said:**
> That plan should work. Consider ext2 or ext4, both will, in general, perform better then ext3.

I am still concerned about using the Live CD to delete the /dev/sda1 XP partition, reformat the former XP partition and extend that new partition to my existing ubuntu installation and then run sudo update-grub so that the proper changes are made to the partitioning schema and boot area.

I've never used a Live CD to perform these particular tasks and I'm a little apprehensive about it. I certainly **DO NOT** want to mess up my _"runs great"_ ubuntu installation.

Thanks

---

