---
title: "[SOLVED] /home on external hard drive"
date: 2009-01-11
forum: New to Ubuntu
---

### Post by DucksAndDolphins on 2009-01-11
Okay, so I know its not right to put your /home on your external hard drive and that many problems can arise. I also know that if I do so, I need to have the hard drive connected in order to boot my computer. I am ready to take certain risks and I'm wondering how to put my /home on my external, because it seems to be the best fit for what I am planning to do with my computer(s).

Help??

---

### Post by taurus on 2009-01-11
I assume you want to put /home on your external harddrive but with ext3 filesystem instead of fat32/vfat!  

Just mount your external harddrive (probably /dev/sdb1) to /home during the installing process and that is all you have to do.

---

### Post by earthpigg on 2009-01-11
when you initially install ubuntu, it asks you what partition to use.

it lets you pick a partition/drive and you can choose the 'mount point'.

leave your internal hard drive set to mount at /.

pick the external drive and tell it to set its 'mount point' to /home, then that will do it... assuming ubuntu's install picks up on the existence of said external hard drive.

i've never tried moving /home on an existing install, so i can't advise on that.

---

### Post by adult swim on 2009-01-11
if you boot to the ubuntu live desktop before you install, youll need to unmount your external drive before you begin the installation process.

---

### Post by DucksAndDolphins on 2009-01-11
do you know of any way i can do it with an existing install?

actually...now that i think about it...

should i just reinstall ubuntu? because ive had various problems.

---

### Post by earthpigg on 2009-01-11
google searching "move /home to different partition ubuntu 8.10" returned a bunch of results, but i have no idea which guides are good so i wont recommend any ;)

i myself do a fresh install every release, its entirely up to you when/why you do a fresh install.

---

### Post by DucksAndDolphins on 2009-01-11
how do you go about doing a reinstall?

---

### Post by minsf on 2009-01-11
for existing installation, maybe try this: assuming you already have ext3 file sytem on the external drive, move /home to the external (you are going to need "sudo mv /home current_mount_point", where current_mount_point is probably /media/disk, but we can tell you for sure if you post your /etc/mtab file), and change the /etc/fstab so that it mounts /dev/sdb1 automatically to /home (instead of /media/disk or wherever it mounts it now). 
i have to admit that i am not so sure if the moving part will work, but i do think that the fstab change is good.
also, we may need to think about how to get it mounted in the boot process, before processes that need /home are starting. not sure how to do this.

---

### Post by Xiong Chiamiov on 2009-01-11
> **DucksAndDolphins said:**
> do you know of any way i can do it with an existing install?

Just copy the folder over, then change your /etc/fstab to mount it as /home.  If you decide to do this, ask here and we can help.

> **DucksAndDolphins said:**
> how do you go about doing a reinstall?
Install it again, and write over your previous install.

---

### Post by mjheagle8 on 2009-01-11
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome) 

this addresses moving your home directory on an existing installation. just make sure your external is formatted ext3.

---

### Post by DucksAndDolphins on 2009-01-11
i think ill try moving it.

i dont think i have ext3, ive got FAT32, if theyre the same thing.

---

### Post by perlluver on 2009-01-11
> **DucksAndDolphins said:**
> i think ill try moving it.

i dont think i have ext3, ive got FAT32, if theyre the same thing.

They are not the same thing, it has to be ext3 to put your home folder on it.

---

### Post by DucksAndDolphins on 2009-01-11
how do i uninstall ubuntu in order to install it again?

---

### Post by perlluver on 2009-01-11
You will need the CD with Ubuntu on it, put it in your CD-Rom drive and choose to install it.  You can also select to format the mount point, that will un-install Ubuntu, make sure you have important files backed up first.

---

### Post by linfidel on 2009-01-11
> **DucksAndDolphins said:**
> i think ill try moving it.

i dont think i have ext3, ive got FAT32, if theyre the same thing.
If I were you, I'd copy it, not move it.  You can always delete it later - or rename it first to make sure it's definitely out of the picture.

Otherwise, it should be a simple matter of simply entering the new partition in your fstab.

---

### Post by DucksAndDolphins on 2009-01-11
okay, sounds simple enough.

how do i change to ext3?

---

### Post by mjheagle8 on 2009-01-11
i'd move the partition. you can format by booting the gparted live cd or by using the gparted cd on the ubuntu live cd. just select the ext3 format and check the format box on the external hard drive.

---

### Post by earthpigg on 2009-01-11
> how do i change to ext3?

gparted is the easiest way to do that. all graphical and pointey-clickey.

if **not **on a live cd:

> sudo apt-get install gparted
then, 'sudo gparted' to run it.

it is installed by default on the live cd, so you can just 'sudo gparted'.

click around, find the external hard drive, format it to ext3. (all data on the external drive will be lost in the process.)

---

### Post by mjheagle8 on 2009-01-11
yeah, i should have warned. reformatting means you lose EVERYTHING on the drive. so back it up if you want to keep it.

---

### Post by DucksAndDolphins on 2009-01-11
okay.

well, ive taken things into consideration, im thinking reinstalling ubuntu is best for me because ive been having problems anyway. ill make it so that its on my external when i reinstall.

the problem is, i didnt use live cd, i used wubi.

what should i do with that?

---

### Post by earthpigg on 2009-01-11
> **DucksAndDolphins said:**
> the problem is, i didnt use live cd, i used wubi.

what should i do with that?

boot from the live CD instead, its just as easy ;)

---

### Post by DucksAndDolphins on 2009-01-11
okay.

so just go burn a live cd, then reinstall off of that??

---

### Post by earthpigg on 2009-01-11
yup

---

### Post by DucksAndDolphins on 2009-01-11
okay everyone, thank you much.

---

### Post by thomas228 on 2009-01-11
> **DucksAndDolphins said:**
> okay everyone, thank you much.

Hi

There should be a Ubuntu dir in your windows. If I remember right it is best to use the uninstall program that's in that dir. (In windows)

That will clean up your windows space and get rid of the present grub.

Do the uninstall before the reinstall to reduce your post installation ubuntu problems.

Good luck 

Tom

---

