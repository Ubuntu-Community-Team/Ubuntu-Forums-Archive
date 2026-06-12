---
title: "Remove Windows 7 from system leaving only Ubuntu"
date: 2010-01-19
forum: New to Ubuntu
---

### Post by N_L on 2010-01-19
Atm I'm dual booting win7 and ubuntu(newest) and I never log in on my windows and would like to delete it.
I installed ubuntu from cd and I think I pressed side by side installation.
When looking at disk manager in windows I see win partition, system reserved win partition and 2 no name partitions, I assume they are ubuntu.
When looking at Computer from ubuntu I see 2 win partitions and 1 called Filesystem(ubuntu I guess), and last isn't shown, which is 5gb.

Now I'd like to completely remove windows and I don't want to mess things up just by formatting C partition so I would like to know what are things I should to do safely remove windows without hurting ubuntu.

Thanks! :)

---

### Post by fancypiper on 2010-01-19
Open an x terminal and command:

sudo fdisk -l

Paste the output here.

---

### Post by sdowney717 on 2010-01-19
you need a program called gparted
This will let you delete and expand-shrink partitions.
If you eliminate the ntfs partition, you will need to 
"sudo update-grub2"
to update the ubuntu boot manager

---

### Post by jflaker on 2010-01-19
you may find it easier to reinstall....

Save off your home folder data and don't forget hidden folders like .evolution or .purple

Once you have all your data offloaded, reinstall choosing use entire disk then copy your stuff back.

I did mine in 25 minutes about 4 weeks ago....took more time to copy off and back my data than to reinstall.

---

### Post by k64 on 2010-01-19
Boot the Live CD, open a terminal, and run "sudo gparted", selecting the Windows partition, and selecting "Delete".

---

### Post by N_L on 2010-01-19
> **fancypiper said:**
> Open an x terminal and command:

sudo fdisk -l

Paste the output here.
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x936ea9aa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       20113   161449386    7  HPFS/NTFS
/dev/sda3           20114       38913   151011000    5  Extended
/dev/sda5           20114       38145   144842008+  83  Linux
/dev/sda6           38146       38913     6168928+  82  Linux swap / Solaris

> **jflaker said:**
> you may find it easier to reinstall....

Save off your home folder data and don't forget hidden folders like .evolution or .purple

Once you have all your data offloaded, reinstall choosing use entire disk then copy your stuff back.

I did mine in 25 minutes about 4 weeks ago....took more time to copy off and back my data than to reinstall.
I always go for complicated method though haha, and I kinda hate reinstalling even if it's quick. Setting things back up the way I like them takes forever.(unless that's copied with too,  haven't been using ubuntu for that long)
> **k64 said:**
> Boot the Live CD, open a terminal, and run "sudo gparted", selecting the Windows partition, and selecting "Delete".
Was planning something like  that, just making sure nothing will get messed up.

---

### Post by fancypiper on 2010-01-19
> **N_L said:**
> Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x936ea9aa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       20113   161449386    7  HPFS/NTFS
/dev/sda3           20114       38913   151011000    5  Extended
/dev/sda5           20114       38145   144842008+  83  Linux
/dev/sda6           38146       38913     6168928+  82  Linux swap / Solaris
 You want to delete /dev/sda1 and /dev/sda2 and make a Linux partition from the resulting free space.

You will need to edit your /etc/fstab file to reflect your new partitions and do a grub-update before it will boot correctly.

---

### Post by PenguinInside on 2010-01-20
I know this isn't what you asked, but if Windows 7 already came with the computer, I wouldn't obliterate it, just because you might need it later on.

If for nothing else than just to verify if a piece of hardware is faulty or it doesn't work work with Linux.

Another option you have with Gparted is to reduce the size of partitions instead of deleting them.

---

