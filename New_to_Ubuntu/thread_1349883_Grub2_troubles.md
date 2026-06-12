---
title: "Grub2 troubles"
date: 2009-12-08
forum: New to Ubuntu
---

### Post by steigerjb on 2009-12-08
ok, lets see if i can get this all explained for you guys. I had Windows Vista Home Premium and Ubuntu 9.10 Karmic on my computer. Vista died (big surprise LOL) So i reinstalled it. Funny thing is, i could then not boot into windows or ubuntu. So I was like, OH FORGET THIS! I figured I'll just delete the Vista partition and i will just boot into Ubuntu, WRONG! (btw, see grub image, gparted wouldn't let me use up the unallocated space with my ubuntu partition) Anyway, so what I did next was install Ubuntu on the 50gb unallocated space to get back to my Ubuntu.


Yeah, I know if coulda just updated my grub2 but i couldn't get that to work.

Now finally for what I want to do. I want to remove that extra ubuntu install i just did and resize the main Ubuntu partition to fill my hard drive. A little side note: if you look at the gparted pic, i don't know why the new ubuntu install's sway partition (sda7) is under my main ubuntu (sda2)

**P.S.:** I don't think you all will help me with this. I will still need Windows for school in Feb. and probably for a job after that. I don;t wanna have to worry about putting another windows partition on this hard drive. I have an extra 160gb external hard drive here. Can I install Vista on that? How?

---

### Post by chaanakya_chiraag on 2009-12-08
To answer your PS question: Try connecting the external hard drive **and disconnecting all other drives**  Otherwise, you might accidentally mess up your internal hard drives by accidentally selecting the wrong one.  That should install the MBR and Vista on the external hard drive.  Whenever you want to boot Vista, you'll have to plug in the external hard drive and set that to boot in the BIOS.

---

### Post by steigerjb on 2009-12-08
> **chaanakya_chiraag said:**
> To answer your PS question: Try connecting the external hard drive. That should install the MBR and Vista on the external hard drive.

hmm, can't seem to be able to install

---

### Post by ranch hand on 2009-12-08
I do not think that Vista will go anywhere but on an internal.

I think that I would try to install it on your unallocated space.  Good luck with Vista on that small a partition.  The little time we left that bugger on here had it eating HDD space.  But that may be because it had the whole 320Gb and needed to use it.

Assuming that it installs and boots, use these directions for fixing grub2;

[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

Ignore the instructions about editing files.  You need the bugger back on the MBR and updated.

This may not pick up you Win JerryLewis Pro.

If not boot in to Ubuntu and, in terminal, run;
```

sudo update-grub

```
This will fix that problem 90 to 95% of the time.

If not, post back and we will get it one way or another.

---

### Post by steigerjb on 2009-12-09
> **ranch hand said:**
> If not, post back and we will get it one way or another.

```
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x30000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6254    50233344    7  HPFS/NTFS
/dev/sda2            6255       19457   106053097+   5  Extended
/dev/sda5            6255       18926   101787808+  83  Linux
/dev/sda6           18927       19457     4265226   82  Linux swap / Solaris
ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt
ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt/boot
ubuntu@ubuntu:~$ sudo mount --bind /dev /mnt/dev
ubuntu@ubuntu:~$ sudo chroot /mnt
root@ubuntu:/# update-grub
Generating grub.cfg ...
grep: /proc/mounts: No such file or directory
Cannot find list of partitions!
done
root@ubuntu:/# grub-install --recheck /dev/sda
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)	/dev/sda
root@ubuntu:/# rub-install --recheck /dev/sda5
No command 'rub-install' found, did you mean:
 Command 'grub-install' from package 'grub-efi-amd64' (universe)
 Command 'grub-install' from package 'grub-efi-ia32' (universe)
 Command 'grub-install' from package 'grub-coreboot' (universe)
 Command 'grub-install' from package 'grub-ieee1275' (universe)
 Command 'grub-install' from package 'grub' (main)
 Command 'grub-install' from package 'grub-pc' (main)
rub-install: command not found
root@ubuntu:/# 

```

what did i do wrong? I say what went wrong cuz there seemed to be errors up there. also, if you look at my grub2 (see attached), where's the Vista choice? my gparted is also attached for reference

---

### Post by steigerjb on 2009-12-09
> **steigerjb said:**
> what did i do wrong? I say what went wrong cuz there seemed to be errors up there. also, if you look at my grub2 (see attached), where's the Vista choice? my gparted is also attached for reference

Nevermind, i just restarted my computer to see what that sda1 boots and my Grub2 was updated to show vista, not another linux sda1. weird.

It's a shame I had to put Windows back on my computer :( but it couldn't be put on my external hard drive. bummer. Maybe when I am done with school I can go to **ALL UBUNTU!!!**

---

### Post by ranch hand on 2009-12-09
After reading your first post I was going to tell you that booting to Ubuntu and running "sudo update-grub" would probably get Vista back on the menu but I see that it is there so all is well.

Great.

The problem causing your error is that in your chroot set up you never mounted "proc".  This is not appearantly needed for the procedure.
```

sudo mount -o bind /proc /mnt/Daily-root/proc

```
this is a line that I use when updating on of my test (10.04) OS on my test system.  My partitions are all labeled and you weren't using the "-o bind" instruction (please do not ask for expaination of that, I'm a noob too), but you get the idea.

Speaking of 10.04.  We had an update yesterday that gave use grub1.97 as opposed to grub1.97beta4 which you are using.  This should hit 9.10 sometime.  those of use who have followed this from 9.10-testing-Alpha2 when it was introduced have been aware that the "update-grub" command was not going to last.

If (or when) you get grub1.97 remember that to get the results like "update-grub" you need to run "grub-mkconfig".  It is better as it displays your whole /boot/grub/grub.cfg file in the newly generated form.  Really nice.

You can see that "update-grub" was left in as a "comfort" as it is an old grub-legacy command.  Grub2 uses the form "grub-whatever" for most commands like one you may have run into "grub-install /dev/sda".

---

