---
title: "Uninstalling from Xubuntu/Kubuntu Dual Install"
date: 2011-07-17
forum: New to Ubuntu
---

### Post by Zhixin on 2011-07-17
As a brand new Linux user, I installed Xubuntu and Kubuntu on the same machine to try out different configurations.
Now that I'm done messing around, I want the Kubuntu gone so I have all my disk space.

How do I do this? I've found lots of guides to removing Linux from a dual-boot setup with Windows, but no hints about what to do with a setup that's 2 versions of Ubuntu.

I didn't deal with any important data in Kubuntu, so it's OK if everything in that part of the disk gets wiped out. But I do want the remaining Xubuntu to be able to use the entire disk efficiently afterward.

From what I've heard, it sounds like running GParted from Xubuntu might be useful. When I do run it, I see 6 sections of the HD: two with the ext4 system, two linux-swap sections, an "unassigned" section that only 3MB, and an "extended" section that includes the second ext4 part plus the two linux-swaps and the unassigned part. 

I have never used GParted before. What should I do to turn this into a single-boot machine without having to do a complete reinstall?

---

### Post by wildmanne39 on 2011-07-17
Hi, use gparted from a live cd and delete the partitions that have kubuntu on, then resize your partition of xubuntu here is a guide to do that. This guide is to be used to recover the extra disk space created by deleting the kubuntu partitions. 

Do not worry that it says for resizing widows to make your system partition bigger the principal is the same.
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

### Post by lmarmisa on 2011-07-17
Before to use Gparted I recommend to reinstall grub2. This example is valid if your computer has only one hard drive. Boot into Xubuntu and type these commands:

```

sudo grub-install /dev/sda
sudo update-grub
sudo apt-get install gparted

```

Open Gparted and format the old Kubuntu partition(s).

Finally, type this command again:

```

sudo update-grub

```

If you want to enlarge the current Xubuntu partition for recovering the space used by Kubuntu, the procedure is more difficult.

Best regards,

Luis

---

### Post by Elfy on 2011-07-17
> and an "extended" section that includes the second ext4 part plus the two linux-swaps and the unassigned part. one of these swaps will be the one created with the xubuntu install. 

While running xubuntu - look in /etc/fstab ```
gedit /etc/fstab
``` to see which swap is being used in that OS. 

You could though without too much trouble - edit fstab to remove the swap - delete all of the extended and partitions within it and then create a new swap and add it to fstab. 

Though to be sure a 

```
sudo fdisk -l
```

from a terminal will at least give us more certainty.

You could do all of this from within Xubuntu - _as long as you did not want to add the gained space to the xubuntu install_ and wanted to create a new partition for data storage or something.

---

### Post by Zhixin on 2011-07-17
Many thanks for the many levels of suggestion. I proceeded to wreck my system.

I made a GPartd Live USB and booted with that. (I forgot to upgrade to Grub2 first - don't know how much difference that would have made).

My partitions were originally:
1 primary partition labeled "boot" that contained Xubuntu.
1 logical partition that contained three subsections: Kubuntu and two swap partitions (one for each OS, I assume).

Since I wanted Xubuntu to be able to use the entire HD, I:
1. deleted the entire logical partition and everything in it, 
2. created a new 2GB swap partition (since both had just been deleted)
3. enlarged the remaining "boot" ext4 partition to fill up all of the disk space left over from the new swap partition.

Now the computer won't boot from the HD. After the BIOS startup screen I just get a "grub rescue>" prompt. 
Booting from the GPartd USB shows that my disk has 2 partitions, one ext4 labeled "boot" and one linux-swap. This is what I wanted, except that it doesn't function. 

Where did I go wrong?

---

### Post by Elfy on 2011-07-17
Try reinstalling grub, probable that your previosuly installed grub was the kubuntu one. 

[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)

---

### Post by Zhixin on 2011-07-17
Many thanks for the quick reply.

I followed the directions on the page you pointed me to. Everything went fine until the command 
sudo grub-install --root-directory=/mnt /dev/sda1

[FONT=Arial][SIZE=2]This gave the error message "The file /mnt/boot/grub/stage not read correctly" and no other response.
What am I missing?

Thanks!
[/SIZE][/FONT]

---

### Post by Zhixin on 2011-07-17
Maybe the problem was that I was using the gpartd live USB. I'll try again with a Xubuntu USB and report back.

--later--

Fixed! My system is booting into Xubunto again, and my files and settings are intact. 

The guide in this blog had the details I needed:
[http://odzangba.wordpress.com/2011/05/14/455/](http://odzangba.wordpress.com/2011/05/14/455/)

The only problem is that now when I boot up, this line of text appears  under the Xubuntu logo (and disappears when my desktop comes up):
"Keys: continue to wait, or press S to skip mounting, or M for manual recovery"

It doesn't seem to slow down the system startup, but I can't help  wondering if it's a symptom of something being not quite right. 

But anyway things are 99% back to normal and I consider the problem solved. 

Thanks to everyone for your help, and for the lessons along the way.

---

### Post by Elfy on 2011-07-18
Once you've booted please open a terminal and run these, paste the results

```
cat /etc/fstab
sudo blkid
```

---

### Post by Zhixin on 2011-07-18
Here's what I got for those two commands. Anything strange?


cat /etc/fstab:
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=75526e34-d768-4390-828a-42b05eb4bd19 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=a91d751d-06e3-48f0-bd2d-7aff8d63209e none            swap    sw              0       0

sudo blkid:
/dev/sda1: UUID="75526e34-d768-4390-828a-42b05eb4bd19" TYPE="ext4" 
/dev/sda3: UUID="09f0e826-cc7e-4fe3-a176-a0aec95d9f9b" TYPE="swap"

---

### Post by lmarmisa on 2011-07-18
> **Zhixin said:**
> Here's what I got for those two commands. Anything strange?


Yes. The reference in fstab to the swap partition is not correct.

Please, type this command

```

sudo gedit /etc/fstab

```

and change the UUID of the swap partition to the value marked in blue:

```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc nodev,noexec,nosuid 0 0
# / was on /dev/sda1 during installation
UUID=75526e34-d768-4390-828a-42b05eb4bd19 / ext4 errors=remount-ro 0 1
# swap was on /dev/sda5 during installation
[COLOR="Blue"]UUID=09f0e826-cc7e-4fe3-a176-a0aec95d9f9b none swap sw 0 0[/COLOR]

```

Save & Quit.

Reboot your system.

If you wish to verify that the swap is correct, type this command:

```

swapon -s

```

---

### Post by Zhixin on 2011-07-18
Excellent. Now the message on bootup is gone, and the proper swap partition is being used. 
It makes sense that just because a swap partition was created on the disk, that doesn't mean that the OS would automatically start using it. Now I know what the fstab file is for.

Thank you!

---

