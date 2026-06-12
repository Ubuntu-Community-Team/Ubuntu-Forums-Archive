---
title: "Installing on an Pre-Defined Partition"
date: 2011-02-05
forum: New to Ubuntu
---

### Post by Booger_Mac on 2011-02-05
After running Ubuntu from a CD for a month now, I've decided I'm going to install it.  
 
I've gone through all the tutorials for partition a hard drive to install Ubuntu, but couldn't find the answer or explanation I was looking for.  When I purchased my computer about a year ago, the hard drive was already partioned into two drives.  One is the standard C drive with all the files and the other is a D drive which has nothing on it.  See the attachment for clarification.
 
My question is, will I be able to install Ubuntu directly to the D partition?  Or do I need to use partion magic to merge the two and create a new partition when installing Ubuntu?
 
If anyone needs more clarity, I'll try to further explain.
 
Thanks and any help and guidance is greatly appreciated.

---

### Post by fabricator4 on 2011-02-05
> **Booger_Mac said:**
> 
My question is, will I be able to install Ubuntu directly to the D partition?  Or do I need to use partion magic to merge the two and create a new partition when installing Ubuntu?


Yes.  You should let the Ubuntu installer re-partion and format the second partition.

Delete the 'D' partition.  You can use Disk utility to do this, but I recommend installing Gparted as it's nicer to use and has more features. You could also use Windows fdisk if you want.  Once the partition has been deleted save the changes, then shut down and boot off the live CD.

When the install asks if you want to use the entire drive or install alongside another OS select "install alongside".

The installer will now use the unpartitioned part of the disk to place Ubuntu. Make sure it has detected your windows OS successfully.  You can also do this manually (the third option) but the second option will also create an appropriate swap partition and make everything boot nicely.

You should of course backup all your important data before making any serious changes to your hard drive.  It's unlikely anything will go wrong, but if it does (like if you accidentally tell the installer to use the entire drive) then it's soooo good to have some backups.

Now, when you boot, the grub bootloader will come up first and ask which OS you want to boot.

Chris.

---

### Post by aeronutt on 2011-02-05
I don't believe there's a need to do anything other than boot from CD, and tell the gui to load Ubuntu onto the D partition.

---

### Post by fabricator4 on 2011-02-05
I should have said, if you delete the partition under Ubuntu, it won't be called 'D'.  Instead what you know as the 'C' partition will be called sda1.  Do not delete that one :-)

You will need to delete sda2 which you will know as 'D'.


If by chance you see a third partion there and you got the machine with windows pre-installed, it may be a recovery partition placed there by the computer vendor.  You should not delete this partition unless you have a good working copy of the Windows installation disks, as this will be the only way to re-install windows if you need to.

Chris.

---

### Post by aeronutt on 2011-02-05
> **fabricator4 said:**
> ...
You will need to delete sda2 which you will know as 'D'.

...

Chris.

Ha...yes....it certainly will  not be 'D'. Still, I don't believe there's any reason to delete sda2. Just install to sda2. Correct?

---

### Post by fabricator4 on 2011-02-05
> **aeronutt said:**
> I don't believe there's a need to do anything other than boot from CD, and tell the gui to load Ubuntu onto the D partition.

I'm not sure it gives the option.  If it detects the second Windows partition it may start moving and resizing partitions, resulting in something other than the desired result.

I should have also remembered that Gparted is already on the live CD

Chris.

---

### Post by quadproc on 2011-02-05
> **Booger_Mac said:**
> 
My question is, will I be able to install Ubuntu directly to the D partition?  Or do I need to use partion magic to merge the two and create a new partition when installing Ubuntu?
 
The preferred approach is to use the entire disk for Ubuntu: partition it into at least four logical partitions so that you can have one partition for each of the OS, swap, /home, and a spare for the next release.

Of course, the above will not work if you want to keep Microsoft.

quadproc

---

### Post by Booger_Mac on 2011-02-05
Thanks for all the tips.  I'm planning on installing Ubuntu tomorrow morning alongside Windows.  Hopefully everything goes smoothly and I'm not posting a "freaking out" thread tomorrow.
 
Thanks again and I'll keep y'all updated.

---

### Post by Booger_Mac on 2011-02-06
Again, thanks for all the help everyone; however, I'm not going to install it after all since my wife gave me permission to purchase a new computer for  Ubuntu and my software development work :).

---

### Post by fabricator4 on 2011-02-06
There's only one thing better than a machine with Ubuntu on it.  TWO machines running Ubuntu ;-)

Dang, go ahead and install it anyway.  You will want a second machine for testing you know...

Chris.

---

