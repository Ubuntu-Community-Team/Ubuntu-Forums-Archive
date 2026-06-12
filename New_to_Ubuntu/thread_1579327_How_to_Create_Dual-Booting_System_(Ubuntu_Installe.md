---
title: "How to Create Dual-Booting System (Ubuntu Installed First)"
date: 2010-09-21
forum: New to Ubuntu
---

### Post by tb75252 on 2010-09-21
First of all, let me confess that I am an absolute newbie with Linux!

I currently have Ubuntu 10.04 LTS installed on my PC. I installed it on the HD without doing any manual partitioning and I accepted all the defaults that Ubuntu  suggested.  So as far as I know right now Ubuntu "owns" the whole HD, i.e. Ubuntu is the only OS currently installed on the HD.

I now would like to create a dual-boot system by installing openSUSE 11.3 _alongside_  Ubuntu 10.04 LTS.  By reading things here and there, my guess is that I  need to create a partition for openSUSE by shrinking the one for  Ubuntu.  But I am really not sure.

So I downloaded the CD version (GNOME only) of openSUSE, launched the  installer and the process came to the following suggestions which is  basically all Greek to me:

     * Delete partition /dev/sda1
     * Create root volume /dev/sda1 with ext4
     * Create volume /dev/sda3 for /home with ext4
     * Use /dev/sda5 as swap

As I said before, what I would like to do is install openSUSE _side-by-side_ with Ubuntu and create a dual-boot system.  I do _not_  want to delete Ubuntu!  I got scared by that "Delete partition  /dev/sda1" line mentioned above and so I aborted the installation.

I do not quite understand how Ubuntu installs itself on a HD, so I am wondering if you can tell from the lines quoted above whether or not openSUSE is trying to wipe my Ubuntu installation.

PS:  I want to install two Linux distributions for testing purposes.  Eventually I will only use one.

---

### Post by spiky001 on 2010-09-21
Hi the way i done it was opensuse 1st allocating the space I wanted for it then ubuntu 2nd grub loaded fine all worked straight away

---

### Post by lkjoel on 2010-09-21
> **tb75252 said:**
> First of all, let me confess that I am an absolute newbie with Linux!

I currently have Ubuntu 10.04 LTS installed on my PC. I installed it on the HD without doing any manual partitioning and I accepted all the defaults that Ubuntu  suggested.  So as far as I know right now Ubuntu "owns" the whole HD, i.e. Ubuntu is the only OS currently installed on the HD.

I now would like to create a dual-boot system by installing openSUSE 11.3 _alongside_  Ubuntu 10.04 LTS.  By reading things here and there, my guess is that I  need to create a partition for openSUSE by shrinking the one for  Ubuntu.  But I am really not sure.

So I downloaded the CD version (GNOME only) of openSUSE, launched the  installer and the process came to the following suggestions which is  basically all Greek to me:

     * Delete partition /dev/sda1
     * Create root volume /dev/sda1 with ext4
     * Create volume /dev/sda3 for /home with ext4
     * Use /dev/sda5 as swap

As I said before, what I would like to do is install openSUSE _side-by-side_ with Ubuntu and create a dual-boot system.  I do _not_  want to delete Ubuntu!  I got scared by that "Delete partition  /dev/sda1" line mentioned above and so I aborted the installation.

I do not quite understand how Ubuntu installs itself on a HD, so I am wondering if you can tell from the lines quoted above whether or not openSUSE is trying to wipe my Ubuntu installation.

PS:  I want to install two Linux distributions for testing purposes.  Eventually I will only use one.
From what I understand, openSUSE is trying to delete Ubuntu.
I have never installed openSUSE, so I do not know how to install Ubuntu and openSUSE side by side.

---

### Post by spiky001 on 2010-09-21
I know you dont want to unistall ubbuntu but i,m not sure how there grub loader works as I said i done it opensuse 1st

---

### Post by tb75252 on 2010-09-21
> **spiky001 said:**
> Hi the way i done it was opensuse 1st allocating the space I wanted for it then ubuntu 2nd grub loaded fine all worked straight away


Unfortunately I have already installed (and customized!!) Ubuntu, so I am trying to avoid having to redo everything from scratch...

---

### Post by spiky001 on 2010-09-21
always the way ok you have to shrink the ubuntu partition to what you want with gparted it,s on the cd boot into live cd

---

### Post by Dustin2128 on 2010-09-21
it's pretty simple, you should be able to use a knoppix or gparted live disc (I haven't used suse in years, if it has a good partitioner, that'll work) to set aside some free space. Afterwards, install suse to the largest amount of free space, which should be that which you set aside, but *don't *install a bootloader if it prompts you. If it doesn't prompt you, google 'suse install without bootloader' or something similar. Once you reboot, ubuntu should still be the only thing in your grub list. Once you log back on, type this in the terminal to add suse
```
sudo update-grub
```That's how I setup my slackware dual boot, and should work for all distributions.

---

