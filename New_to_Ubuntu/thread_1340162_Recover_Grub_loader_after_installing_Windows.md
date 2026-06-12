---
title: "Recover Grub loader after installing Windows"
date: 2009-11-28
forum: New to Ubuntu
---

### Post by fleamour on 2009-11-28
I have followed the community documentation carefully so as to restore grub to MBR but get this error:

root@ubuntu:~# sudo grub-install --root-directory=/media/root /dev/sda1

grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea.
grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged.
grub-setup: error: Cannot read `/grub/core.img' correctly
root@ubuntu:~#


Not sure where going wrong.  Created mount point & tried mounting both Windows & Linux partition then installing grub.

My partitions are set out thus:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
100 heads, 5 sectors/track, 625163 cylinders
Units = cylinders of 500 * 512 = 256000 bytes
Disk identifier: 0xfc9dbffb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      152535    38133747+   7  HPFS/NTFS
/dev/sda2          152536      466178    78410750    7  HPFS/NTFS
/dev/sda3          466179      609536    35839500   83  Linux
/dev/sda4          609537      625161     3906250   82  Linux swap / Solaris

Please advise!

---

### Post by fleamour on 2009-11-28
My bad, I need to preserve Windows bootloader not overwrite it...

:oops::oops::oops:

---

### Post by fleamour on 2009-11-28
[B]4. Type "find /boot/grub/stage1". You'll get a response like "(hd0)" or in my case "(hd0,3)". Use the output from this command for the following commands.

Note:

You should have mounted the partition which has your Linux system before typing this command. (e.g. In Knoppix Live CD partitions are shown on the desktop but they're not mounted until you double-click on them or mount them manually) [/B]

Do I mount ***both*** partitions, /dev/sda1 and Linux root, /dev/sda3 before:

"find /boot/grub/stage1"?

Does someone have the code to mount both partitions?

---

### Post by ranch hand on 2009-11-28
We will assume that you are using 9.04 or older Ubuntu and thus grub-legacy.

You need to do your grub repair from the LiveCD.

Boot to live CD
Pull up terminal
Run;
```

sudo grub

```
This will give you a grub prompt like this "grub>"
Run these commands, in this order, at the grub prompt;
```

find /boot/grub/stage1
root (hd0,2)
setup (hd0)
quit

```
This assumes that sda3 is your root partition.  Use the listing that you get with the "find" command.

You will have to edit your /boot/grub/menu.lst  for your MS entry.  I do not have it on my system but I am sure there is an example in the menu.lst.

---

### Post by fleamour on 2009-11-28
> **ranch hand said:**
> We will assume that you are using 9.04 or older Ubuntu and thus grub-legacy.


Thanks for the reply.  It's actually Ubuntu Karmic 9.10.  Does that change things?

---

### Post by ranch hand on 2009-11-28
Yes that changes things quite a bit.

Post the results of;
```

grub-install -v

```
and we will go on from there.

---

### Post by fleamour on 2009-11-28
grub-install (GNU GRUB 1.97~beta4)

---

### Post by ranch hand on 2009-11-28
That is good.

I would recommend that you just install grub on the MBR.  Grub2 should find your MS install and generate a menu entry.

To do this boot to your 9.10 and run;
```

sudo grub-install /dev/sda

```
and
```

sudo update-grub

```
This should put everything in place.

If you can't boot to 9.10 then use a 9.10 LiveCD and follow these instructions;

[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

Ignore the instructions for editing files, this should not be needed.

Reading the link in my sig and the links in it will give you enough information to keep you busy for a while on grub2.

---

### Post by fleamour on 2009-11-28
I cannot boot Karmic so tried the live CD option but threw up these errors:

root@ubuntu:/# **update-grub**
Generating grub.cfg ...
grep: /proc/mounts: No such file or directory
Cannot find list of partitions!
done


root@ubuntu:/# **grub-install /dev/sda**
grub-setup: warn: Your embedding area is unusually small.  core.img won't fit in it.
grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged.
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)	/dev/sda
root@ubuntu:/# **grub-install --recheck /dev/sda**
grub-setup: warn: Your embedding area is unusually small.  core.img won't fit in it.
grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged.
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)	/dev/sda
root@ubuntu:/# exit
ubuntu@ubuntu:~$ **sudo umount /mnt/dev**
ubuntu@ubuntu:~$ **sudo umount /mnt**
umount: /mnt: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
ubuntu@ubuntu:~$ 

This is my second attempt as first booted grub but immediately dumped to console.

---

### Post by Zoot7 on 2009-11-28
The following is a guide on how to reinstall Grub 2 from a liveCD:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

### Post by fleamour on 2009-11-28
Here is command line output:

ubuntu@ubuntu:~$ **sudo fdisk -l**

Disk /dev/sda: 160.0 GB, 160041885696 bytes
100 heads, 5 sectors/track, 625163 cylinders
Units = cylinders of 500 * 512 = 256000 bytes
Disk identifier: 0xfc9dbffb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      152535    38133747+   7  HPFS/NTFS
/dev/sda2          152536      466178    78410750    7  HPFS/NTFS
/dev/sda3          466179      609536    35839500   83  Linux
/dev/sda4          609537      625161     3906250   82  Linux swap / Solaris

ubuntu@ubuntu:~$** sudo mount /dev/sda3 /mnt**

ubuntu@ubuntu:~$ **sudo grub-install --root-directory=/mnt/ /dev/sda**
grub-setup: warn: Your embedding area is unusually small.  core.img won't fit in it.
grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged.
grub-setup: error: Cannot read `/grub/core.img' correctly

ubuntu@ubuntu:~$ **sudo update-grub**
grub-probe: error: cannot find a device for /.

Not sure where going wrong?  Maybe I should try method two.

---

### Post by fleamour on 2009-11-28
Well & truly nuked my bootloader now!  fixmbr under recovery console did not even work, hoorah for disk images.

:)

---

### Post by ranch hand on 2009-11-28
Boot to the liveCD and run this script;

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

and post the results back here.

---

### Post by fleamour on 2009-11-29
Thanks for your help.  fixmbr from Win recovery console would not work after my tinkering& grub was dumping to command line.  So I restored from an old image.  Not lost too much thankfully.

Maybe too hasty on my part, but thanks.

---

