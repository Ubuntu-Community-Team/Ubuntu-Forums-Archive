---
title: "Courrupted filesystem?"
date: 2009-11-24
forum: New to Ubuntu
---

### Post by Rave Gloves on 2009-11-24
When i try to boot ubuntu 9.10 it will say "one or more mounts could not be found" or something along those lines. then it will go into recovery and say my whole file system could not be found. Then when i restart when its loading i have a few choices as to what i want to boot - almost like i have another operating system installed - one of the options dose not boot while the second dose. Please help. :(

---

### Post by phidia on 2009-11-24
If you boot from the live cd there is an option to reinstall grub-I think that is probably the simplest way to start with this.
If that works all's good if not you will need to provide more info like the output from > sudo fdisk -l and your /boot/grub/menu.lst file.

---

### Post by phidia on 2009-11-24
Double posted :(

---

### Post by Rave Gloves on 2009-11-24
```
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x72d5f5d8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29651   238171626   83  Linux
/dev/sda2           29652       30401     6024375    5  Extended
/dev/sda5           29652       30401     6024343+  82  Linux swap / Solaris
```


here is the out put. i couldnt find the /boot/grub/menu.lst file.

---

### Post by sandyd on 2009-11-24
> **Rave Gloves said:**
> ```
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x72d5f5d8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29651   238171626   83  Linux
/dev/sda2           29652       30401     6024375    5  Extended
/dev/sda5           29652       30401     6024343+  82  Linux swap / Solaris
```
here is the out put. i couldnt find the /boot/grub/menu.lst file.
run this
```

sudo fsck /dev/sda1 -y

```

---

### Post by Rave Gloves on 2009-11-24
```
WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.

```


should i ? D:

---

### Post by Rave Gloves on 2009-11-25
Right Guys i need to get this sorted. I am really not up for doing a clean install. I was impressed with this os at the start but now its really proving a pain. It took me 30mins to boot up today my system would go into recovery shell and stay that way until i Pressed Ctrl+D  that canceled. it would tell me that my filesystem could not be mounted and there are errors in my file system. Finally i went to recovery to back up all my data but instead it took me to an os chooser i guess would be how to decribe it with two 9.10 and the recoverys. Only one of them would let me boot up after waiting for the recovery to work. Please tell me i wont need a clean install :(


Edit: since this has been happening i have noticed that my programs stop responding allmost frequently now. Banshee and firefox seem to just stop responding alot now.

Edit Edit:  Nothing will now open. the terminal is a blank screen. 
Damn it i wanted to back my files up :(

---

### Post by Paqman on 2009-11-25
> **Rave Gloves said:**
> ```
WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.

```


should i ? D:

Yes, as long as you're using the LiveCD as was suggested. In the LiveCD none of your filesystems are mounted by default (except maybe a swap partition)

---

### Post by philinux on 2009-11-25
> **Rave Gloves said:**
> When i try to boot ubuntu 9.10 it will say "one or more mounts could not be found" or something along those lines. then it will go into recovery and say my whole file system could not be found. Then when i restart when its loading i have a few choices as to what i want to boot - almost like i have another operating system installed - one of the options dose not boot while the second dose. Please help. :(

If this is your problem then....

[https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/447747](https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/447747)

See last post for fix. You'll need to boot the livecd.

---

### Post by Rave Gloves on 2009-11-25
> **Paqman said:**
> Yes, as long as you're using the LiveCD as was suggested. In the LiveCD none of your filesystems are mounted by default (except maybe a swap partition)

I wont lose any files by reinstalling grub will i?

---

### Post by Some Penguin on 2009-11-25
> **Rave Gloves said:**
> I wont lose any files by reinstalling grub will i?

The boot loader is at most 446 bytes of executable code, written to either the master boot record or the first sector of a bootable partition.   It's possible to cause frustration if you install to the wrong partition (say, mistakenly obliterating the first sector of an NTFS partition instead of your extN /boot or /, and thus making it difficult to boot your Windows installation, if you have one -- fixable using a Windows installation disk, perhaps) but it shouldn't affect the partition table (as that's the last 64 bytes of the MBR) and shouldn't lose any files.

---

### Post by Rave Gloves on 2009-11-25
> **philinux said:**
> If this is your problem then....

[https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/447747](https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/447747)

See last post for fix. You'll need to boot the livecd.

How is it i boot the live CD, i know that you restart and it boots. But what then? do i boot from hard drive in the options?

---

### Post by philinux on 2009-11-25
> **Rave Gloves said:**
> How is it i boot the live CD, i know that you restart and it boots. But what then? do i boot from hard drive in the options?

No not boot from hard drive. You want the live cd to run itself.

1st option. "Try Ubuntu" 

It will load a desktop for you in ram. It runs slow as it is all in ram.

---

### Post by Rave Gloves on 2009-11-25
> **philinux said:**
> No not boot from hard drive. You want the live cd to run itself.

1st option. "Try Ubuntu" 

It will load a desktop for you in ram. It runs slow as it is all in ram.

Apparently only root can mount, what now?

---

### Post by philinux on 2009-11-25
> **Rave Gloves said:**
> Apparently only root can mount, what now?

Just put sudo in front of those commands.

---

### Post by Rave Gloves on 2009-11-25
> **philinux said:**
> Just put sudo in front of those commands.

Well it seemed like it had done something but when i went to boot again i was getting the same story. And i still cant mount my filesystem :/

---

### Post by philinux on 2009-11-25
The first bit of those commands was to get you into a chroot.

The last two commands the update and upgrade should have updated your system on the hard drive. Did it run all ok without errors.

Maybe back to the live cd and while doing it post back the output you get while in the terminal. You can have Firefox and a terminal running from the livecd no problems.

---

### Post by Rave Gloves on 2009-11-25
> **philinux said:**
> The first bit of those commands was to get you into a chroot.

The last two commands the update and upgrade should have updated your system on the hard drive. Did it run all ok without errors.

Maybe back to the live cd and while doing it post back the output you get while in the terminal. You can have Firefox and a terminal running from the livecd no problems.

All the commands worked, there was no errors when i sudo apt-get update

When i did sudo apt-get upgrade it did some code no errors but then it said that 0 packages had been changed.
i will try and get the output for you, give me 5mins and i will be able to get it.

Edit: i tried to boot again and lots of code came up each saying failed
then it asked me to login and would not accept my password

---

### Post by Rave Gloves on 2009-11-25
```
ubuntu@ubuntu:~$ sudo mkdir /mnt/ubuntu
ubuntu@ubuntu:~$ sudo /dev/sda1 /mnt/ubuntu
sudo: /dev/sda1: command not found
ubuntu@ubuntu:~$ sudo /dev/sda1 /mnt/ubuntu
sudo: /dev/sda1: command not found
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt/ubuntu
ubuntu@ubuntu:~$ sudo mount -t proc none /mnt/ubuntu/proc
ubuntu@ubuntu:~$ sudo mount -o bind /dev /mnt/ubuntu/dev
ubuntu@ubuntu:~$ sudo chroot /mnt/ubuntu
root@ubuntu:/# sudo apt-get update
sudo: unable to resolve host ubuntu
Hit http://gb.archive.ubuntu.com karmic Release.gpg                            
Ign http://gb.archive.ubuntu.com karmic/main Translation-en_US             
Ign http://gb.archive.ubuntu.com karmic/restricted Translation-en_US
Ign http://gb.archive.ubuntu.com karmic/universe Translation-en_US
Ign http://gb.archive.ubuntu.com karmic/multiverse Translation-en_US
Hit http://gb.archive.ubuntu.com karmic-updates Release.gpg
Ign http://gb.archive.ubuntu.com karmic-updates/main Translation-en_US
Ign http://gb.archive.ubuntu.com karmic-updates/multiverse Translation-en_US
Ign http://gb.archive.ubuntu.com karmic-updates/universe Translation-en_US
Ign http://gb.archive.ubuntu.com karmic-updates/restricted Translation-en_US
Hit http://security.ubuntu.com karmic-security Release.gpg
Ign http://security.ubuntu.com karmic-security/main Translation-en_US
Hit http://gb.archive.ubuntu.com karmic Release
Ign http://security.ubuntu.com karmic-security/restricted Translation-en_US
Ign http://security.ubuntu.com karmic-security/universe Translation-en_US
Ign http://security.ubuntu.com karmic-security/multiverse Translation-en_US
Hit http://gb.archive.ubuntu.com karmic-updates Release             
Hit http://security.ubuntu.com karmic-security Release
Hit http://gb.archive.ubuntu.com karmic/main Packages
Hit http://gb.archive.ubuntu.com karmic/restricted Packages
Hit http://gb.archive.ubuntu.com karmic/main Sources
Hit http://gb.archive.ubuntu.com karmic/universe Packages
Hit http://security.ubuntu.com karmic-security/main Packages
Hit http://gb.archive.ubuntu.com karmic/universe Sources
Hit http://gb.archive.ubuntu.com karmic/multiverse Packages
Hit http://gb.archive.ubuntu.com karmic/multiverse Sources
Hit http://security.ubuntu.com karmic-security/restricted Packages
Hit http://security.ubuntu.com karmic-security/main Sources
Hit http://security.ubuntu.com karmic-security/universe Packages
Hit http://gb.archive.ubuntu.com karmic-updates/main Packages
Hit http://gb.archive.ubuntu.com karmic-updates/multiverse Packages
Hit http://gb.archive.ubuntu.com karmic-updates/universe Packages
Hit http://gb.archive.ubuntu.com karmic-updates/restricted Packages
Hit http://security.ubuntu.com karmic-security/universe Sources
Hit http://security.ubuntu.com karmic-security/multiverse Packages
Hit http://security.ubuntu.com karmic-security/multiverse Sources
Reading package lists... Done
root@ubuntu:/# sudo apt-get upgrade
sudo: unable to resolve host ubuntu
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

Dont mind the silly mistakes on it, i kept forgetting to put mount. Should still work none the less

What do you think?

---

### Post by Rave Gloves on 2009-11-25
Bumpp, i thinking about just doing a clean install :(

I would rather not lose all my music though.

---

### Post by philinux on 2009-11-25
Well you got into the chroot ok. But not sure why upgrades not happening.

Looking at other chroot commands, try this slightly modified code from the livecd. sda1 is defo the right partition eh?

```
sudo mkdir /mnt/ubuntu
sudo mount /dev/sda1 /mnt/ubuntu
sudo mount -t proc none /mnt/ubuntu/proc
sudo mount -o bind /dev /mnt/ubuntu/dev
sudo cp /etc/resolv.conf /mnt/ubuntu/etc/resolve.conf
sudo chroot /mnt/ubuntu /bin/bash
sudo apt-get update && sudo apt-get upgrade
```

When you're on livecd just use copy and paste into a terminal.

---

### Post by Rave Gloves on 2009-11-25
```
ubuntu@ubuntu:~$ sudo mkdir /mnt/ubuntu
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt/ubuntu
ubuntu@ubuntu:~$ sudo mount -t proc none /mnt/ubuntu/proc
ubuntu@ubuntu:~$ sudo mount -o bind /dev /mnt/ubuntu/dev
ubuntu@ubuntu:~$ sudo cp /etc/resolv.conf /mnt/ubuntu/etc/resolve.conf
ubuntu@ubuntu:~$ sudo chroot /mnt/ubuntu /bin/bash
root@ubuntu:/# sudo apt-get update && sudo apt-get upgrade
sudo: unable to resolve host ubuntu
Hit http://gb.archive.ubuntu.com karmic Release.gpg                         
Ign http://gb.archive.ubuntu.com karmic/main Translation-en_US              
Hit http://security.ubuntu.com karmic-security Release.gpg
Ign http://security.ubuntu.com karmic-security/main Translation-en_US
Ign http://gb.archive.ubuntu.com karmic/restricted Translation-en_US
Ign http://gb.archive.ubuntu.com karmic/universe Translation-en_US
Ign http://gb.archive.ubuntu.com karmic/multiverse Translation-en_US
Hit http://gb.archive.ubuntu.com karmic-updates Release.gpg
Ign http://gb.archive.ubuntu.com karmic-updates/main Translation-en_US
Ign http://gb.archive.ubuntu.com karmic-updates/multiverse Translation-en_US
Ign http://gb.archive.ubuntu.com karmic-updates/universe Translation-en_US
Ign http://gb.archive.ubuntu.com karmic-updates/restricted Translation-en_US
Ign http://security.ubuntu.com karmic-security/restricted Translation-en_US
Ign http://security.ubuntu.com karmic-security/universe Translation-en_US
Ign http://security.ubuntu.com karmic-security/multiverse Translation-en_US
Hit http://gb.archive.ubuntu.com karmic Release
Hit http://security.ubuntu.com karmic-security Release
Hit http://gb.archive.ubuntu.com karmic-updates Release
Hit http://security.ubuntu.com karmic-security/main Packages
Hit http://gb.archive.ubuntu.com karmic/main Packages
Hit http://gb.archive.ubuntu.com karmic/restricted Packages
Hit http://security.ubuntu.com karmic-security/restricted Packages
Hit http://security.ubuntu.com karmic-security/main Sources
Hit http://security.ubuntu.com karmic-security/universe Packages
Hit http://security.ubuntu.com karmic-security/universe Sources
Hit http://gb.archive.ubuntu.com karmic/main Sources
Hit http://gb.archive.ubuntu.com karmic/universe Packages
Hit http://gb.archive.ubuntu.com karmic/universe Sources
Hit http://gb.archive.ubuntu.com karmic/multiverse Packages
Hit http://gb.archive.ubuntu.com karmic/multiverse Sources
Hit http://gb.archive.ubuntu.com karmic-updates/main Packages
Hit http://gb.archive.ubuntu.com karmic-updates/multiverse Packages
Hit http://security.ubuntu.com karmic-security/multiverse Packages
Hit http://security.ubuntu.com karmic-security/multiverse Sources
Hit http://gb.archive.ubuntu.com karmic-updates/universe Packages
Hit http://gb.archive.ubuntu.com karmic-updates/restricted Packages
Reading package lists... Done
sudo: unable to resolve host ubuntu
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

Still the same, how would i check what the right partition would be?

---

### Post by philinux on 2009-11-25
Looking back your post #4 says it's defo sda1. 

You must have a different problem from the launchpad one. The fix for this has been released so your system must be up to date I guess.

I would back up your stuff if you haven't already. Looking like a reinstall coming, unless anybody else can help you.

I have home on it's own partition so a reinstall is dead easy.

---

### Post by Rave Gloves on 2009-11-25
> **philinux said:**
> Looking back your post #4 says it's defo sda1. 

You must have a different problem from the launchpad one. The fix for this has been released so your system must be up to date I guess.

I would back up your stuff if you haven't already. Looking like a reinstall coming, unless anybody else can help you.

I have home on it's own partition so a reinstall is dead easy.

I think im just going to do a reinstall. *sigh*

saves all the trouble. Once its installed and such i wont install the new grub. I have had the problem for a few days before the update. its when im trying to boot it says a few mounts could not be loaded. Since the update its just stoped working alltogether.

Edit: would it be possible to backup my home file from the try ubuntu im on right now?

---

### Post by philinux on 2009-11-25
> **Rave Gloves said:**
> I think im just going to do a reinstall. *sigh*

saves all the trouble. Once its installed and such i wont install the new grub. I have had the problem for a few days before the update. its when im trying to boot it says a few mounts could not be loaded. Since the update its just stoped working alltogether.

Edit: would it be possible to backup my home file from the try ubuntu im on right now?

To be honest you only need the important stuff. Backed up to a usb stick or dvd. I.e. your data etc. Unless you get a lot of app settings that you've customised a lot.

It's easier to start set up a home partition from the installer.
/ 12 gig
/swap Mine set at 2 gig as I've got 2 gig memory. I hibernate.
/home for the rest

---

### Post by Rave Gloves on 2009-11-25
Oh my, right i tried to do a clean install. it got to 98% and tole me some things could not be removed as they were read only. And it looks like it canceled the install. 

Can someone help :(

---

### Post by Rave Gloves on 2009-11-25
I had another go at installing, and its saying the language packs could not be deleted... anyone know what this means?

---

### Post by cariboo on 2009-11-25
I would suggest running Check cd for defects from the start menu.

---

### Post by Rave Gloves on 2009-11-25
> **cariboo907 said:**
> I would suggest running Check cd for defects from the start menu.

good call, it seems to frezze when i try to use the disk checker. i will burn another disk

---

### Post by Rave Gloves on 2009-11-25
> **Rave Gloves said:**
> good call, it seems to frezze when i try to use the disk checker. i will burn another disk


Still the same thing with the next disk, im burning at the slowest speed too. i let it sit for a few mins and i got this error when trying to check the disk ```
casper/vmlinuz
```

Any idea what that means?.

---

