---
title: "Dual boot Maverick with Lucid"
date: 2010-10-04
forum: New to Ubuntu
---

### Post by beew on 2010-10-04
Hi, 

I am thinking of giving Maverick a try but my main  system is still going to be Lucid. I already have Lucid installed in my hard drive, my plan is to carve out a "temporary" partition in my hard drive for testing Maverick.  

I am going to use gparted to create the extra partition (right now it is unformatted as I have quite a lot of hard disk space) in ext4 and then install Maverick in it. Now I would like to know what do I have to do to ensure that the isntallation would not overwrite my Lucid partition. Would making the mount point to be / sufficient?  Also, would the installation process put grub2 in  the Maverick partition  and remove it from the Lucid partition just like dual booting Lucid with Windows would put grub2 in the Lucid partition?

In case I  want to remove the Maverick partition later(Or i may keep it, but just in case). What should I do to make sure that the Lucid partition would remain bootable once the Maverick partition  is deleted?

Thanks

---

### Post by oldfred on 2010-10-04
I keep at least three partitions in rotation. Previous install, current install and beta. I have all my data in a separate partition so I can mount it easily in any new install and have the same data available in all of them. I prefer to create partitions in advance and use manual install to choose root. If /home is separate you can also choose it. It will auto find swap and use it.

You have to decide which grub you want as primary, it will be the default. At any time you can reinstall grub from your install or from the liveCD. When you install choose not to install grub if you do not want it. It used be the advanced button on the last partition screen but now is a combo box. Not sure if no drive is a choice but you can install to a partition (which is not recommended) which then will not be used.

After any changes in either system you will have to run sudo update-grub in the system you are booting.


Install MBR from LiveCD, Ubuntu install on sda5 and want grub2 in drive sda's MBR:
Find linux partition, change sda5 if not correct, and/or even sda if sdb wanted:
sudo fdisk -l
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda

reinstall from working (not liveCD) system - first find Ubuntu drive:
sudo fdisk -l
if it's "/dev/sda"  then just run:
sudo grub-install /dev/sda
If that returns any errors run:
sudo grub-install --recheck /dev/sda
Then:
sudo update-grub
to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
spacebar to choose/unchoose drive, enter to accept, do not choose partitions

---

### Post by beew on 2010-10-04
oldfred

Thanks for the detail reponse. It will take sometimes to digest. I am sure I'll be back to ask further questions before I actually install (which will be after the final release of 10.10).

Cheers.

---

