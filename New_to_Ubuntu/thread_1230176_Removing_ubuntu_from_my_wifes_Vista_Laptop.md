---
title: "Removing ubuntu from my wifes Vista Laptop"
date: 2009-08-03
forum: New to Ubuntu
---

### Post by Johnecash on 2009-08-03
now that I have a dedicated ubuntu machine working I would like to remove ubuntu completely from my wifes laptop (she is quite delicate about having the dual boot options list come up)
 
do you guy know how to do this?

---

### Post by zeroseven0183 on 2009-08-03
How did you install Ubuntu? If it's inside Windows then it would be easy to remove it from the programs list.

If it has a separate partition, you can just delete the partition and correct your boot sequence (MBR).

In order for us to help you, we need to know how Ubuntu got there.

---

### Post by mikechant on 2009-08-03
Just a thought, but if you actually would quite like to leave Ubuntu in place for emergencies but just hide it during the boot sequence, you can do this easily (and there's a small chance of screwing up Vista when you actually remove Ubuntu, so this is also the safer option).

You can either:
1/ Edit the grub menu.lst file to hide the grub menu and set the timeout to zero - so grub will boot straight in Windows.
See [http://www.debianadmin.com/show-and-hide-the-grub-menu-on-ubuntu.html](http://www.debianadmin.com/show-and-hide-the-grub-menu-on-ubuntu.html) 
(but I'd suggest using 'gksudo gedit' instead of 'sudo vi' unless you're familiar with the 'vi' editor).

or
2/ Install the startup-manager package which gives you a gui front end to make the same changes.


If you do this you'll be able to use the LiveCD to reverse the change if you subsequently need Ubuntu to be visible again.

---

### Post by slakkie on 2009-08-03
Why would you need a live CD to edit grub to make an old version of Ubuntu visible again? Just use a livecd then.. ;)

I don't know how you installed Ubuntu, but you could remove it completely by removing the partition (believe you can do this from within Windows) and creating a new NTFS disk. Make sure you have a Windows boot disk so you can fix the mbr though.

---

### Post by Regenweald on 2009-08-03
> **Johnecash said:**
> now that I have a dedicated ubuntu machine working I would like to remove ubuntu completely from my wifes laptop (she is quite delicate about having the dual boot options list come up)
 
do you guy know how to do this?

Just boot into vista and go to disk management. In there the Ubuntu partition/drive will be laballed something like unknown/unrecognized file system. Frag it :) in other words format it NTFS. You're done.

NB. **MAKE SURE** everything you need is no longer on that drive. _there is no going back_.

As slakkie said. A win boot disk is vital.

---

### Post by LewRockwell on 2009-08-03
I think a SuperGrubDisk will fix MBR also

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

.

---

### Post by egalvan on 2009-08-03
> **Regenweald said:**
> Just boot into vista and go to disk management.
 the Ubuntu partition/drive will be labelled something like unknown/unrecognized file system.
 Frag it :) in other words format it NTFS. You're done.

Nope, GRUB is still installed on the MBR,
and will now complain about "missing files"


> NB. **MAKE SURE** everything you need is no longer on that drive. _there is no going back_.


Again, nope... most MS-Windows "formats" are non-destructive to the actual data.

but still, I agree, **[COLOR="Red"]MAKING BACKUPS IS AN EXCELLENT IDEA[/COLOR]**.

A customer had her husband accidentally reinstall XP on her school-work machine, and I recovered almost 100% of her files.

> As slakkie said. A win boot disk is vital.

Yep, using this to repair the MBR will eliminate the initial GRUB boot,
THEN you can eliminate the Linux partitions...

SuperGRUB is also excellent, +1, as LewRockwell stated...
but I have no personal experience with Vista MBR.
I know it works with MS-XP MBR and all previous Windows products.

---

### Post by tgalati4 on 2009-08-03
With the constant reboots that windows requires, it must be irksome to see the foreign-looking GRUB screen.  Might as well be a foreign language.  I would leave Ubuntu as an emergency boot partition and just make windows the default boot.  Set a really short delay (say 1 second).  Rename the Ubuntu title to "Emergency Windows Repair"

---

### Post by LewRockwell on 2009-08-03
> **tgalati4 said:**
> With the constant reboots that windows requires, it must be irksome to see the foreign-looking GRUB screen.  Might as well be a foreign language.  I would leave Ubuntu as an emergency boot partition and just make windows the default boot.  Set a really short delay (say 1 second).  Rename the Ubuntu title to "Emergency Windows Repair"

I'd be very inclined to do this also(and make sure you take a little time once in awhile to keep Ubuntu updated...you never know when you might want to use it)

.

---

### Post by philinux on 2009-08-03
Girlfriends vista lappy is used by her kids. I put ubuntu on it for me.
Under advanced install I put grub on the ubuntu partition.
Then I used easybcd to modify the vista bootloader. 2 secs timeout with vista the default OS. 

Kids are unaware that ubuntu is on there. Result everyone happy.

---

### Post by zvacet on 2009-08-03
@ **Johnecash**

If you really want to remove Ubuntu then first do [this.]("http://members.iinet.net.au/~herman546/p18.html#MbrFix.exe") After that insert live CD to delete Ubuntu partition.You can also use [Gparted live Cd]("http://gparted.sourceforge.net/") for that.

---

