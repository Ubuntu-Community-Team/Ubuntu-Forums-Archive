---
title: "Booting Bt3 from Hd with ubuntu and xp installed"
date: 2009-02-18
forum: New to Ubuntu
---

### Post by F4r4Zm0In on 2009-02-18
Hey all,

I am running ubuntu 8.10 & WIn Xp

I just downloaded bt3final.iso 

I tried booting from the cd (which i have just burned) and all worked fine :)

Now, the thing is i want to install it on my hard drive, just like ubuntu & Win xp

After some search i found various articles on "How to install Bt3"

**What i did so far:**

I issued cfdisk @ ubuntu terminal & created a logical partition (10 Gb)  from my free space

**Results of my fdisk -l command:**

> root@ubuntu:/home/f4r4z# fdisk -l

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc791c791

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1217     9775521    7  HPFS/NTFS
/dev/sda2            1218        4865    29302560    f  W95 Ext'd (LBA)
/dev/sda5            1218        2434     9775521   83  Linux
/dev/sda6            2435        3651     9775521    b  W95 FAT32
/dev/sda7            3652        4865     9751423+   b  W95 FAT32


I then issued this command to make a ext3 file system for bt3 installation

```
mke2fs -j /dev/sda5
```

I then rebooted the pc & Inserted the bt3final cd i had burnt previously

@ Backtrack shell, i have issued these commands

> root@bt:~#umount /dev/hda5
root@bt:~#cd / && mkdir /mnt/bt && mount /dev/hda5 /mnt/bt/
root@bt:~#cp --preserve -R /{bin,dev,home,pentest,root,usr,boot,etc,lib,opt,sb in,var} /mnt/bt/ && mkdir /mnt/bt/{mnt,tmp,proc,sys}
root@bt:~#chmod 1777 /mnt/bt/tmp/ && mount -t proc proc /mnt/bt/proc && mount -o bind /dev /mnt/bt/dev/
root@bt:~#chroot /mnt/bt/ /bin/bash

I rebooted my pc again to configure Grub & issued following commands @ ubuntu terminal & this is where i think i got stuck :(

> root@ubuntu:/home/f4r4z# grub-install /dev/sda5
Searching for GRUB installation directory ... found: /boot/grub
The file /boot/grub/stage1 not read correctly.


After this error in grub-install i tried editing menu.lst by issuing the following command

```
root@ubuntu:~#gedit /boot/grub/menu.lst
```

At the end of the file i added :

> title Backtrack 3
root (hd0,6)
kernel /boot/vmlinuz rw root=/dev/**hda5**
initrd /boot/splash.initrd
boot

I reboot the computer again and this time i found Backtrack 3 in the list

When i try booting it, i got this error:

**Error 15: File Not Found**


After this i edited menu.lst again with the following parameters:

> title Backtrack 3
root (hd0,6)
kernel /boot/vmlinuz rw root=/dev/**sda5**
initrd /boot/splash.initrd
boot

But again, i have got the same error

Any help will be really appreciated :)

---

### Post by NewJack on 2009-02-20
Don't know if you read this, but this is written by Jabra from Remote Exploit:

[http://www.offensive-security.com/documentation/backtrack-hd-install.pdf](http://www.offensive-security.com/documentation/backtrack-hd-install.pdf)

---

### Post by F4r4Zm0In on 2009-02-21
> **NewJack said:**
> Don't know if you read this, but this is written by Jabra from Remote Exploit:

[http://www.offensive-security.com/documentation/backtrack-hd-install.pdf](http://www.offensive-security.com/documentation/backtrack-hd-install.pdf)

This is not the right tut for me 

Because in this tut, he used only one 3.5 Gb hard disk to install 

Mine is a different

---

### Post by piroko on 2009-02-21
> **F4r4Zm0In said:**
> This is not the right tut for me 

Because in this tut, he used only one 3.5 Gb hard disk to install 

Mine is a different

as far as your HDD space is involved, that shouldnt matter, just make the partition as big as you want it in cfdisk, then change the type to 83 (Linux), then follow the rest.

if you want to make this all well and easy to install, here's an easy guide:

```
http://kin.calvin.free.fr/blog/?p=16
```

You're going to be using lilo as your MBR I assume.

After you make your ext2 partition for BT, and format your partition into a reiserFS, then create your '/mnt/backtrack' folder, download the Backtrack 3 beta installer and use that to install everything afterwards, then configure your lilo so you can boot your other OS as well.

```
#Windows Boot
Other = /dev/hda* or sda* (I assume you know your hard disk label)
Label = Windows XP (call it whatever you want)
table = /dev/hda or sda
```

Ubuntu should look the same as above. 
I couldn't tell you how to configure grub if you would prefer using that, I havent played with it enough, sorry. In my experience with BT though, lilo works just fine.

BT3 installer : [http://kin.calvin.free.fr/prgms/BT3.kmdr](http://kin.calvin.free.fr/prgms/BT3.kmdr) (right click, save as, then run)

---

### Post by F4r4Zm0In on 2009-02-21
> **piroko said:**
> if you want to make this all well and easy to install, here's an easy guide:
You're going to be using lilo as your MBR I assume.

After you make your ext2 partition for BT, and format your partition into a reiserFS, then create your '/mnt/backtrack' folder, download the Backtrack 3 beta installer and use that to install everything afterwards, then configure your lilo so you can boot your other OS as well.

```
#Windows Boot
Other = /dev/dev/hda* or sda* (I assume you know your hard disk label)
Label = Windows XP (call it whatever you want)
table = /dev/hda or sda
```

Ubuntu should look the same as above. 
I couldn't tell you how to configure grub if you would prefer using that, I havent played with it enough, sorry. In my experience with BT though, lilo works just fine.

BT3 installer : [http://kin.calvin.free.fr/prgms/BT3.kmdr](http://kin.calvin.free.fr/prgms/BT3.kmdr) (right click, save as, then run)

I think i am using Grub & not lilo

This is the result of fdisk -l command

> Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc791c791

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4785    38435481   83  Linux
/dev/sda2            4786        4865      642600    5  Extended
/dev/sda5            4786        4865      642568+  82  Linux swap / Solaris

To be very frank, i am really confused on whether i have to create a new seperate partition for bt3 final or should i install it in the same /dev/sda1

---

### Post by piroko on 2009-02-21
Putting it on the same partition as ubuntu would be fine if you did it all manually, but using the installer will wipe everything. IMHO, I'd create a new linux partition for BT3, and install it then with the beta installer, it'd be a lot easier that way.

How much disk space are you planning to use for BT3, and how much space is already used by previous partitions?

Also, I don't see an NTFS partition for your WinXP boot, are you using a single or dual hard drives?

---

### Post by F4r4Zm0In on 2009-02-21
> **piroko said:**
> Putting it on the same partition as ubuntu would be fine if you did it all manually, but using the installer will wipe everything. IMHO, I'd create a new linux partition for BT3, and install it then with the beta installer, it'd be a lot easier that way.

How much disk space are you planning to use for BT3, and how much space is already used by previous partitions?

Also, I don't see an NTFS partition for your WinXP boot, are you using a single or dual hard drives?

5 Gb, i think will be sufficient for BT3 final

Please have a look @ the output produced by my fdisk -l command

I deleted all my partitions and installed ubuntu just a few hours back

Infact, formatted the whole HD and right now i am having only ubuntu installed

I think i have no other option than installing BT on the same partition

Because i have no free space left on my HD to create a new partition

---

### Post by piroko on 2009-02-21
> **F4r4Zm0In said:**
> 5 Gb, i think will be sufficient for BT3 final

Please have a look @ the output produced by my fdisk -l command

I deleted all my partitions and installed ubuntu just a few hours back

Infact, formatted the whole HD and right now i am having only ubuntu installed

I think i have no other option than installing BT on the same partition

Because i have no free space left on my HD to create a new partition

If I were you, I would use either cfdisk to recreate partitions in adequate sizes to hold all three (ubuntu, BT, and winxp), in either a 10GB, 10GB, 20GB format with either both BT and ubuntu being 10GB, and winxp 20GB, depending on which you use regularly (gamers would need more space for winxp). and leave enough space for your linux swap partition; Or use QTparted from the BT3 liveCD and resize your ubuntu linux partition to about 10GB, create a new linux part thats 10GB, make it into a ReiserFS format, then continue to install BT3 onto the new linux partition (you dont need a swap for BT3, I did mine without it and it ran fine). But, that's just my opinion. (Or you can use Gparted on ubuntu if it's on there, or download/install it, whatever).

What's on your extended partition? I've never had a need to create an extended partition when installing BT, so i'm going to assume something to do with ubuntu. 

Installing BT on the same partition as ubuntu may create boot problems if you add in lilo also, so if you do decide you want to go ahead and install BT on the same part as ubuntu, make sure you avoid anything to do with lilo; then you'll have to configure grub to add in BT / windows into the boot possibilities. The only problem I see, as I said before is that if you don'tinstall BT3 manually (which it looked to me like you were ibn an earlier post by creating / copying the files manually through a bash shell) then it'll clear out your ubuntu from the linux partition.
So, there shouldn't be any problems if you do it manually and leave out lilo, but make sure you know how to edit grub's boot parameters before you go about doing this so you don't end up having to keep rebooting, it'll make things go a lot faster if you get the code beforehand.

Also, I'm not sure about grub, but are you sure this is right?

```
title Backtrack 3
root (hd0,6)
kernel /boot/vmlinuz rw root=/dev/hda5
initrd /boot/splash.initrd
boot 
```

In my experience with lilo, it's all done this way:
```

#Linux Boot
Other = /dev/sda*
label = Linux BT3
table = /dev/sda

```

---

