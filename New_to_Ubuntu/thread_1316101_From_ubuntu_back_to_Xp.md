---
title: "From ubuntu back to Xp"
date: 2009-11-05
forum: New to Ubuntu
---

### Post by herbertg on 2009-11-05
For work I need to go back to XP. I dedicated my whole harddrive to ubuntu x2 file system. Now I need to go back to ntfs. When I put the xp disc in it tells me my hardrive might have a virus but I know that it doesn't. What do I do now? After I put XP back on I'm going to dual boot. I'm not giving up ubuntu I like it too much.

---

### Post by goldshirt9 on 2009-11-05
cant you run xp in vmware or similare

---

### Post by herbertg on 2009-11-05
It would be nice to dual boot if possible.

---

### Post by mikewhatever on 2009-11-05
Boot from the Ubuntu live cd and use System->Admin->Partition manager to repartition. Alternatively, you can also install Windows in virtual box and use both Ubuntu and Windows at the same time.

---

### Post by Zoot7 on 2009-11-05
Here's a nice guide to dual boot Ubuntu and XP with Ubuntu installed first, it's a little old, but still good:
[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

I agree with goldshirt9, before you dual boot, consider running XP in a virtual machine; For all my windows apps (with the odd exception) I've XP virtualized in Virtualbox which IMO is a lovely simple tool to use, and it works like a charm.

---

### Post by oboedad55 on 2009-11-05
> **herbertg said:**
> For work I need to go back to XP. I dedicated my whole harddrive to ubuntu x2 file system. Now I need to go back to ntfs. When I put the xp disc in it tells me my hardrive might have a virus but I know that it doesn't. What do I do now? After I put XP back on I'm going to dual boot. I'm not giving up ubuntu I like it too much.

I'm usually a little dense so bear with me. Is there a question you had with how to do something? Are you having trouble with your windows install? You can download Parted Magic, just google it, and re-partition your hard drive and make it all one partition with ntfs file system. Otherwise, if you want Ubuntu on there as well then make two partitions, one for each, and a swap partition.

---

### Post by goldshirt9 on 2009-11-05
> **Zoot7 said:**
> Here's a nice guide to dual boot Ubuntu and XP with Ubuntu installed first, it's a little old, but still good:
[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

I agree with goldshirt9, before you dual boot, consider running XP in a virtual machine; For all my windows apps (with the odd exception) I've XP virtualized in Virtualbox which IMO is a lovely simple tool to use, and it works like a charm.

the link may be old but i used it to dual boot xp and ubuntu :D:D:D:D

---

### Post by arrow.69 on 2009-11-05
I'm pretty sure the XP install disc can delete a ubuntu partition.  If you're cool with doing that.  Just wipe your hard drive completely, make a smallish NTFS partition, install XP on there.  Then you can reinstall Ubuntu on the remaining hard drive space, and Ubuntu should take care of setting up GRUB so you can boot into XP.  To me that's the easiest way of going about this.

Otherwise you have to shrink your partition with Gparted, install XP on there, then figure out how to set GRUB to list XP as a boot option.  And then you run the risk of breaking your bootloader and having to start over from scratch.

Both options are definitely viable though.

Also.  I find it hilarious that XP would warn users that linux is a virus on their hard drives.  Such a Microsoft thing to do.

---

### Post by Merk42 on 2009-11-05
> **herbertg said:**
> It would be nice to dual boot if possible.

Unless you need something like 3D acceleration, a VM would be a lot easier.
Though dual booting is possible.

What in particular is reason for needing XP?

---

### Post by cariboo on 2009-11-05
XP will usually see any partition but ntfs of vfat as unknown, just delete all the partitions and create new ones. If you are going to dual boot leave enough free space at the end of the drive to install Ubuntu, that way you don't have to resize any partitions.

---

### Post by oboedad55 on 2009-11-05
If you're going to partition ahead of installing XP, which is what I'd do, then you can use this bootable disk to create your partitions. It's called Parted Magic and it can be found here; [http://partedmagic.com/](http://partedmagic.com/)

---

### Post by goldshirt9 on 2009-11-06
as stated above.
if you are going to reload xp you can partition your hdd before you install xp.
follow the instructions. trouble is you may delete linux (xp is aggressive )

a tip though.
partition one    xp operating system
partition two   for vids / music / pictures
partition three  for vids / music / picture.

so on as required.


when you have xp / linux installed afresh both systems will see the partitions and you can use all the info for both systems.
saves having to copy to both systems music / pics / vids

---

### Post by lkraemer on 2009-11-07
One thing to keep in mind is that for any Physical Hard Drive there is a 
Maximum of Four Primary Partitions.  XP will be on one, and that leaves
three remaining.  If you install Linux, you will either use two or three
depending on what your needs are.  Now you can select one Partition
and make it extended where you can have many additional partitions, but
I choose not to go that route.  Instead I make three Linux partitions.
~15 Gig for Ubuntu (/), Linux-swap partition that is Two times the Available
RAM for (swap), and the remainder for (/home).  That uses all four.  The
advantage of doing it this way is all your data and files are on /home
so you can wipe the / partition and install a new version easily without
much worry.  Just my two cents worth.

lk

---

### Post by ivanvajar on 2009-11-07
1. Create NTFS partition with your Ubuntu LiveCD
2. Install Windows
3. Reinstall grub using Ubuntu LiveCD (search forum on how to do that)
4. Edit /boot/grub/menu.lst by adding WinXP lines to make it bootable (search forum on how to do that)

---

### Post by Shpongle on 2009-11-07
> **zoot7 said:**
>  for all my windows apps (with the odd exception) i've xp virtualized in virtualbox which imo is a lovely simple tool to use, and it works like a charm.

+1

---

