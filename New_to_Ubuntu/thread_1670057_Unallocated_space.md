---
title: "Unallocated space"
date: 2011-01-18
forum: New to Ubuntu
---

### Post by czerdrill on 2011-01-18
Ok I have a Windows installation on a 500gb disk, and a ubuntu as a 50gb partition.  i want to add more space to the ubuntu so with gparted i shrunk the windows by 50gb hoping to add that to the ubuntu.

however, the 50gb shows as unallocated space and i'm unable to extend the ubuntu partition.

how can i make the 50gb into free space which I can then extend into the ubuntu using gparted?

---

### Post by gordintoronto on 2011-01-18
Ubuntu has full access to the Windows hard drive, so you could easily store data files there without worrying about partitions. I am sure there is a way to turn the unallocated 50 GB into /home, but it's not something I would tackle.

---

### Post by Is Mise on 2011-01-18
gparted can't resize the Ubuntu partition while it's in use. Run gparted off the Ubuntu LiveCD if you want to extend your partition.

---

### Post by czerdrill on 2011-01-18
> **Is Mise said:**
> gparted can't resize the Ubuntu partition while it's in use. Run gparted off the Ubuntu LiveCD if you want to extend your partition.

Yeah I was using the LiveCD but when I write click the unallocated area my only option is "New" and then it says I cant do that because I have the maximum amount of partitions.  The unallocated space appears to the left of my Ubuntu partition...

---

### Post by czerdrill on 2011-01-18
> **gordintoronto said:**
> Ubuntu has full access to the Windows hard drive, so you could easily store data files there without worrying about partitions. I am sure there is a way to turn the unallocated 50 GB into /home, but it's not something I would tackle.

This is true but what about trying to install software from the software center or setting up a virtual machine using VirtualBox.  Can this stuff utilize the Windows drive somehow?

---

### Post by tobier on 2011-01-18
> **czerdrill said:**
> Ok I have a Windows installation on a 500gb disk, and a ubuntu as a 50gb partition.  i want to add more space to the ubuntu so with gparted i shrunk the windows by 50gb hoping to add that to the ubuntu.

however, the 50gb shows as unallocated space and i'm unable to extend the ubuntu partition.

how can i make the 50gb into free space which I can then extend into the ubuntu using gparted?

You have to shrink the Windows partition so that there is either unallocated space left before or after the Ubuntu partition. If you shrunk the Windows partition so that there is unallocated space next to the Windows partition but not the Ubuntu partition, then you'll need to move the Windows partition. Make backups before you do this though (you should always do this when messing with partitions), if you care about your data.

---

### Post by czerdrill on 2011-01-18
> **tobier said:**
> You have to shrink the Windows partition so that there is either unallocated space left before or after the Ubuntu partition. If you shrunk the Windows partition so that there is unallocated space next to the Windows partition but not the Ubuntu partition, then you'll need to move the Windows partition. Make backups before you do this though (you should always do this when messing with partitions), if you care about your data.

The space appears in between the Windows and Ubuntu partition:

Windows/unallocated/Ubuntu

The only option I have is to extend the Windows back into the unallocated.  I can't extend the ubuntu, or merge the unallocated to the ubuntu somehow...

---

### Post by Is Mise on 2011-01-18
> **czerdrill said:**
> Yeah I was using the LiveCD but when I write click the unallocated area my only option is "New" and then it says I cant do that because I have the maximum amount of partitions.  The unallocated space appears to the left of my Ubuntu partition...

Don't right-click the unallocated space, right-click the Ubuntu partition itself and pick Resize/Move. And yes, as Tobier said, backup first!

---

### Post by czerdrill on 2011-01-18
> **Is Mise said:**
> Don't right-click the unallocated space, right-click the Ubuntu partition itself and pick Resize/Move. And yes, as Tobier said, backup first!

Ok just tried this and then I get "Unable to satisfy constraints on partition" when I try to grow my ubuntu partition.  Any idea what that means?

---

### Post by Is Mise on 2011-01-18
Maybe you need to Swapoff your swap partition first.

---

### Post by czerdrill on 2011-01-18
> **Is Mise said:**
> Maybe you need to Swapoff your swap partition first.

How would I do that...sorry for the noobness :)

---

### Post by Is Mise on 2011-01-18
It's ok, I should have explained better. Right-click on your swap partition in gparted and select Swapoff.

---

### Post by srs5694 on 2011-01-18
> **gordintoronto said:**
> Ubuntu has full access to the Windows hard drive, so you could easily store data files there without worrying about partitions.

This is unwise. Linux doesn't understand most of the NTFS security features that Windows uses, which means that it's easy to accidentally trash your Windows installation from Linux if you muck about in there on a regular basis. Furthermore, although the general consensus is that NTFS-3g is pretty reliable, I wouldn't want to bet on its being as reliable as or more reliable than Microsoft's own NTFS implementation. Although many people do as you describe without problems for months or even years, I have seen horror stories of problems developing. It's best not to risk it unnecessarily.

[quote=czerdrill]Ok just tried this and then I get "Unable to satisfy constraints on  partition" when I try to grow my ubuntu partition.  Any idea what that  means? [/quote]

This seems to occur because of rounding that libparted does to align partitions to cylinder (old-style) or 1MiB (new-style) boundaries, when surrounding partitions don't align in this way. There's a check box or option in one of the dialog boxes that enables you to set alignment to cylinder, alignment to 1 MiB boundary (on the newest versions), or no alignment. Adjust that setting and the problem should go away. If you still have problems, try leaving the smallest gap possible between the partitions and it should work.

If you still have problems, try posting a screen shot of the GParted window, and perhaps any error messages you see.

---

### Post by czerdrill on 2011-01-18
> **srs5694 said:**
> This is unwise. Linux doesn't understand most of the NTFS security features that Windows uses, which means that it's easy to accidentally trash your Windows installation from Linux if you muck about in there on a regular basis. Furthermore, although the general consensus is that NTFS-3g is pretty reliable, I wouldn't want to bet on its being as reliable as or more reliable than Microsoft's own NTFS implementation. Although many people do as you describe without problems for months or even years, I have seen horror stories of problems developing. It's best not to risk it unnecessarily.



This seems to occur because of rounding that libparted does to align partitions to cylinder (old-style) or 1MiB (new-style) boundaries, when surrounding partitions don't align in this way. There's a check box or option in one of the dialog boxes that enables you to set alignment to cylinder, alignment to 1 MiB boundary (on the newest versions), or no alignment. Adjust that setting and the problem should go away. If you still have problems, try leaving the smallest gap possible between the partitions and it should work.

If you still have problems, try posting a screen shot of the GParted window, and perhaps any error messages you see.

so should it be set at cylinder or no alignment?  it defaults to 1MiB.

---

### Post by czerdrill on 2011-01-18
> **Is Mise said:**
> It's ok, I should have explained better. Right-click on your swap partition in gparted and select Swapoff.

I will try this also...thanks!

---

### Post by czerdrill on 2011-01-19
> **czerdrill said:**
> so should it be set at cylinder or no alignment?  it defaults to 1MiB.

Just bumping this...should it be cylinder or no alignment?

---

### Post by czerdrill on 2011-01-19
Solved it by leaving 1Mib between partitions.  Thanks for your help.

---

### Post by srs5694 on 2011-01-19
> **czerdrill said:**
> so should it be set at cylinder or no alignment?  it defaults to 1MiB.

Try all the options.

The old cylinder alignment improved disk performance on the disks of 25 years ago. Very old versions of DOS require cylinder alignment. Today it's meaningless at best, unless you're running one of those old DOS versions.

The modern 1 MiB alignment improves disk performance on some devices -- namely, Advanced Format disks, SSD disks, and some types of RAID array. It serves no purpose on most single disks, but it also does no harm, so it's being used as the new standard.

If you've got a conventional spinning disk with true 512-byte sectors, partitions can start anywhere (no alignment) and it will work fine.

Mixing and matching can cause utilities to get confused (as illustrated by this thread), but once it's set up, Linux (and most or all other modern OSes) will be fine with it.

---

### Post by yunone on 2011-01-21
i am in a similar boat as the OP, i am dual booting and shrank my WIN7 partition and now have unallocated space between WIN7 and UBUNTU. 34gb/43gb/71gb . i want to take that newly freed up 43gb unallocated space and add it to my 71gb ubuntu partition but when i right click or use the menu to resize the ubuntu partition it says i already have the maximum space for the ubuntu partition, 71gb. Argh :) i want to extend the Ubuntu partition.

any other ideas? 

thanks in advance

---

### Post by Quackers on 2011-01-21
yunone, please post a screenshot of your gparted window, if that's what you are using.

---

### Post by dBuster on 2011-01-21
I too am in a similar boat.  I am wanting to take the unallocated space and use that though for my /home.  I am hesitant as I do not want to mess anything up.  I plan on using clonezilla tomorrow and making a clone of the drive in case I mess something up.

But can I just create a new primary partition without fear of hosing something up?

[IMG]http://ubuntuforums.org/picture.php?albumid=1154&pictureid=7298[/IMG]

---

### Post by Quackers on 2011-01-21
> **dBuster said:**
> I too am in a similar boat.  I am wanting to take the unallocated space and use that though for my /home.  I am hesitant as I do not want to mess anything up.  I plan on using clonezilla tomorrow and making a clone of the drive in case I mess something up.

But can I just create a new primary partition without fear of hosing something up?

[IMG]http://ubuntuforums.org/picture.php?albumid=1154&pictureid=7298[/IMG]

Not really, until you are sure that you don't already have 4 primarys.
Please bear in mind that an extended partition is a type of primary partition, so 3 primarys and an extended partition is the max on any single hard drive.
Once you have an extended partition, you can create as many logical partitions as you want to, within that extended partition.

---

### Post by dBuster on 2011-01-22
> **Quackers said:**
> Not really, until you are sure that you don't already have 4 primarys.
Please bear in mind that an extended partition is a type of primary partition, so 3 primarys and an extended partition is the max on any single hard drive.
Once you have an extended partition, you can create as many logical partitions as you want to, within that extended partition.

So from what I know and remember when I first set up this laptop, I have the one primary, the NTFS partition, and then an extended partition with the two linux partitions there in.  So with that in mind and seeing my partition table I am going to say that a new primary is acceptable.

---

### Post by Quackers on 2011-01-22
Just have a look at the disk management screen in Windows. That will tell you. Primary partitions have a thick, dark blue line above them in the pictorial display. In the textual display of the same screen it gives more details.

---

### Post by SeijiSensei on 2011-01-22
> **dBuster said:**
> I am wanting to take the unallocated space and use that though for my /home.

Just format the unallocated partition as ext4 then mount it as /home in /etc/fstab.  

Suppose your unallocated partition appears as /dev/sda2.  Then you'd run:

```

sudp mkfs -t ext4 /dev/sda2
sudo mkdir /mnt/tmphome
sudo mount /dev/sda2 /mnt/tmphome
sudo cd /home
sudo rsync -av . /mnt/tmphome

```

This will create an ext4 filesystem on the partition and mount it on /mnt/tmphome.  The rsync command will transfer the contents of /home to /mnt/tmphome.  Check to make sure everything is intact before moving on.

Now we just need to edit fstab.  Use "sudo nano /etc/fstab" and add a line at the bottom like this:

```

/dev/sda2     /home      ext4     defaults 0 0

```

Now comes the tricky part.  Reboot and choose "rescue mode".  You'll end up at a "#" prompt.  Now enter:

```

mv /home /home.old
mkdir /home
reboot

```

(Note that you don't need sudo here, since you're already the root user if you boot into rescue mode.)

Just let the machine boot up as it normally would.  You should see all your files in /home and /home.old.  If you're sure everything is working correctly, you can use "sudo rm -rf /home.old" to delete the old copy and free up space.

Before you do any of this, back up the contents of /home to another device.

---

### Post by dBuster on 2011-01-23
> **SeijiSensei said:**
> Just format the unallocated partition as ext4 then mount it as /home in /etc/fstab.  

Suppose your unallocated partition appears as /dev/sda2.  Then you'd run:



Okay so I now have this brand new 74Gig partition and I used ext3 instead of ext4, no big deal.

With my Jaunty the mounting is done in the /media/ not /mnt.  However something strange happened.  When I am in gksu nautilus, the mounts show up with their names, ie. vista and home and so forth.  When I am in regular not su nautilus I see the drive sizes and not the names as they are assigned in the fstab file. 

Did I do something wrong?  Also, as a normal nautilus window open, the one with the drive sizes not names listed, I tried to copy a file over to the new partition and it did not work, something about permissions.  But of course the gksu can copy a file just fine.  I need permissions help now....  I think.

---

### Post by dBuster on 2011-01-23
> **SeijiSensei said:**
> 
Now comes the tricky part.  Reboot and choose "rescue mode".  You'll end up at a "#" prompt.  Now enter:

```

mv /home /home.old
mkdir /home
reboot

```

(Note that you don't need sudo here, since you're already the root user if you boot into rescue mode.)

Just let the machine boot up as it normally would.  You should see all your files in /home and /home.old.  If you're sure everything is working correctly, you can use "sudo rm -rf /home.old" to delete the old copy and free up space.

Before you do any of this, back up the contents of /home to another device.

Okay so that didn't work.  I was doing well up to that point.  I got a device not ready or busy error.  So I could not execute the ```
mv /home /home.old
```

What next?

I have the rsynch done and the fstab changed, but that partition is not mounted now.  Where did I go wrong?  I was so close to being ready to drop in the 10.04.01 cd and get to installing clean...  now I am held up.

---

### Post by SeijiSensei on 2011-01-23
> **dBuster said:**
> Okay so that didn't work.  I was doing well up to that point.  I got a device not ready or busy error.  So I could not execute the ```
mv /home /home.old
```

You did boot up using rescue mode before you tried this, right?  You should have gotten no GUI, just a # prompt in text-mode indicating you had root privileges.

If so, what does the result of "mount" show?  Which device is "not ready or busy?"  

Sometimes Linux won't mount a filesystem for writing because it has errors.  Are there any filesystems listed as read-only ("ro") if you type the "mount" command?

---

### Post by dBuster on 2011-01-24
> **SeijiSensei said:**
> You did boot up using rescue mode before you tried this, right?  You should have gotten no GUI, just a # prompt in text-mode indicating you had root privileges.

If so, what does the result of "mount" show?  Which device is "not ready or busy?"  

Sometimes Linux won't mount a filesystem for writing because it has errors.  Are there any filesystems listed as read-only ("ro") if you type the "mount" command?

When I booted up I did not have a rescue mode, I had a recovery mode option which I choose and then choose the terminal window option.  So I did not boot into the GUI.  I was at a shell only at the root level as well.  Still no luck.

I am not at home right now so I can not run the mount at this time to check for read only attribute.  I do know that last night what ever I did in the "File system - home" made changes to the tmphome folder.  Then I changed the fstab to mount it as tmphome, rebooted and still same thing.  However this morning when I booted up, I had the new partition listed in the menu as the drive size and not the name that I gave it in fstab, but doing a gksu nautilus I get the name instead of the drive size.  Go figure.

I believe though that my /home data is safely on my new partition.  Although a compare of the two I get no verbose response in the shell so I do not know if it did or not.  Might have to try it again tonight since it is now showing up as mounted when I boot up.  hmmf...  If it is safely there is the consensus that I can now go ahead with the clean install of 10.04.1??  Going with 10.04 for the LTS, unless everyone thinks that I should not worry about LTS and go with 10.10???  I do not want to run into the same predicament I am in now with 9.04 not being supported any more, and some things not working as they should, ie not being able to pogo game or yahoo game any more as it seems to be broken on my current install, plus now I have a new wireless N adapter that I want to get up and running and with 9.04 support is tough and I could not get it working without getting kernel panics!!

---

