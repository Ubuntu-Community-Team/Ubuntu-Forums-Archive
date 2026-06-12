---
title: "How do I make a new UUID for this HD?"
date: 2011-06-19
forum: New to Ubuntu
---

### Post by s1baker on 2011-06-19
hello,
I just recently cloned my main Ubuntu working HD to another HD. After the experts on this forum got me up and going with setting up the correct UUID's for the partitions in the fstab file, I now have two working HD's, my main working HD and a backup HD, in case I have some sort of problem with the main HD.
 Now I want to hook these two HD's on the same ribbon. oldfred mentioned something about needing to change the UUID on one of the drives, so that there will not be two UUID's that are the same. Both of these drives have only two partition's, a main sda1 and a swap partition, sda2. the swap partitions, for some reason have different UUID's, but the main partitions, the sda1, have identical UUID numbers.

 Can someone help as to how to get a new UUID number for this HD I am on now? I have read that tune2fs can be used ( file types are ext4 ), and I know how to edit the fstab file. But I don't know what to do about the grub and any thing else I might need to know.
Thanks

---

### Post by vanadium on 2011-06-19
> **s1baker said:**
> hello,
I have read that tune2fs can be used ( file types are ext4 ), and I know how to edit the fstab file. But I don't know what to do about the grub and any thing else I might need to know.

You won't need anything else: all you need to do is change the UUID and adapt fstab accordingly.

---

### Post by s1baker on 2011-06-19
So, if I understand you correctly, I won't need to do anything to the grub? Also, do I use tune2fs to get a new UUID, and how do I use it to do this?

---

### Post by s1baker on 2011-06-20
bump

...anybody..?

---

### Post by bodhi.zazen on 2011-06-20
> **s1baker said:**
> So, if I understand you correctly, I won't need to do anything to the grub? Also, do I use tune2fs to get a new UUID, and how do I use it to do this?

See the [man page](http://linux.die.net/man/8/tune2fs) =)

tune2fs -U random /dev/your_partition

Yes you need to then update grub and fstab.

---

### Post by s1baker on 2011-06-20
my main partition in /dev is sda1 so this would be:

```
tune2fs -U random /dev/sda1
```

correct?

and how do I update grub
like this? 
```
sudo grub-update
```

---

### Post by oldfred on 2011-06-20
You have to update fstab & the UUIDs that grub uses. It should just require a reinstall of grub2's boot loader to the MBR so it points to the correct UUID & edit of menu.lst. It may be easier to edit the file we are not supposed to edit grub.cfg and to get it to boot initial and run update-grub or chroot in and reinstall grub & update-grub inside the chroot so the grub.cfg is updated with new UUID.

(This is why I think it is a bit easier just to do a clean install, copy over /home and reinstall apps and system settings from /etc. Still a lot of editing but it can be done from working systems.)

Change examples from sda1 to sdb1 or whatever your drive X and partition Y are.
Change UUID see also man pages:
uuidgen
sudo tune2fs /dev/sdaX -U numbergeneratedbyuuidgen
or:
sudo tune2fs -U random /dev/sdaX

#Normally we do not directly edit grub.cfg. Edit from liveCD.
sudo mount /dev/sda1 /mnt
gksu gedit /mnt/boot/grub/grub.cfg
#May have to do this first as it is write protected also:
sudo chmod +w /mnt/boot/grub/grub.cfg
#Or even this first:
sudo chmod 777 /mnt/boot/grub/grub.cfg

Edited version, see post #12
#Comments are anything after the #, enter commands in terminal session
 #Install MBR from LiveCD, Ubuntu install on sda1 and want grub2's bootloader in drive sda's MBR:
 #Find linux partition, change sda1 if not correct:
 sudo fdisk -l
 #confirm that linux is sda1
 sudo mount /dev/sda1 /mnt
 sudo grub-install --root-directory=/mnt/ /dev/sda
 #If grub 1.99 with Natty uses boot not root
 sudo grub-install --boot-directory=/mnt/ /dev/sda
 #If that returns any errors run:
 sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
 # If no errors on previous commands reboot into working system and run this:
 sudo update-grub

---

### Post by s1baker on 2011-06-20
also, the tune2fs man page shows that it is for ext2 and ext3, I have ext4

---

### Post by bodhi.zazen on 2011-06-20
> **s1baker said:**
> also, the tune2fs man page shows that it is for ext2 and ext3, I have ext4

tune2fs works on ext4

---

### Post by s1baker on 2011-06-20
I have some questions about this part of the list :
( also, I am using 10.10 32 bit )

```
#confirm that linux is sda1
sudo mount /dev/sda5 /mnt
```
I don't have a sda5, my main partition is on sda1 and the
swap is on sda2  



```
sudo grub-install --root-directory=/mnt/ /dev/sda
If grub 1.99 with Natty uses boot not root
sudo grub-install --boot-directory=/mnt/ /dev/sda
```
should the "If grub 1.99 ....." be a comment (#) or is that
something that is run in the terminal?

---

### Post by s1baker on 2011-06-20
also my grub.cfg file as it sits now is in /boot/grub directory

---

### Post by oldfred on 2011-06-20
My post uses sda5 as an example and I tried changing to sda1. I missed an entry. And the 1.99 boot is a comment.  Sorry for confusion and I will edit first post just for those who might see thread and not read this far.

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD, Ubuntu install on sda1 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda1 if not correct:
sudo fdisk -l
#confirm that linux is sda1
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#If grub 1.99 with Natty uses boot not root
sudo grub-install --boot-directory=/mnt/ /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
# If no errors on previous commands reboot into working system and run this:
sudo update-grub

---

### Post by oldfred on 2011-06-20
I thnk Bohdi has a typo, you still use tune2fs as ext2, ext3 & ext4 are the same basic file systems with each increment including additions/improvements:

From man tune2fs
> tune2fs allows the  system  administrator  to  adjust  various  tunable
       filesystem  parameters  on  Linux ext2, ext3, or ext4 filesystems.  The
       current values of these options can be displayed by using the -l option
       to tune2fs(8) program, or by using the dumpe2fs(8) program.

---

### Post by s1baker on 2011-06-20
No, actually thank you for your time and patience with us novices

---

### Post by bodhi.zazen on 2011-06-20
> **oldfred said:**
> I thnk Bohdi has a typo, you still use tune2fs as ext2, ext3 & ext4 are the same basic file systems with each increment including additions/improvements:

From man tune2fs

Doh -)

Fixed that typo

---

### Post by s1baker on 2011-06-20
Thanks guys.
I will called this solved. Fascinating, although I had to call the chmod commands twice before the system would let me edit the grub.cfg file for some reason, but every thing went clean as a whistle after that.

I am going to make a copy of the list of commands as to how to do this and put it in my notebook.

---

