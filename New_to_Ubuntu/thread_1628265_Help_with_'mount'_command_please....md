---
title: "Help with 'mount' command please..."
date: 2010-11-22
forum: New to Ubuntu
---

### Post by Robert.Thompson on 2010-11-22
Hello:

I am trying to repair grup and the instructions are that I must do some mounting - I seem to be striking out at this. I booted by using Ubuntu 10.10 Live-CD.

I did:  sudo mount /dev/sda1 /mnt and received no error msg - success, I think?

Then:

ubuntu@ubuntu:~$ sudo mount /dev/sda2 /mnt/boot
mount: you must specify the filesystem type
ubuntu@ubuntu:~$ 


Then I tried:

ubuntu@ubuntu:~$ sudo mount -t ext4 /dev/sda2 /mnt/boot
mount: wrong fs type, bad option, bad superblock on /dev/sda2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
ubuntu@ubuntu:~$ 

Any help would be appreciated.

Thanks,

---

### Post by nothingspecial on 2010-11-22
Looks like it`s not ext4.

Is it ext3?

---

### Post by oldfred on 2010-11-22
Please do not start duplicate thread unless topic is totally different.

See:
[http://ubuntuforums.org/showthread.php?t=1626427](http://ubuntuforums.org/showthread.php?t=1626427)

---

### Post by nothingspecial on 2010-11-22
To be fair, it is a different question.

Advice on mount, is different to fixing a dual boot problem even if it relates to the underlying problem.

---

### Post by ddnev45 on 2010-11-22
> **Robert.Thompson said:**
> Hello:

I am trying to repair grup and the instructions are that I must do some mounting - I seem to be striking out at this. I booted by using Ubuntu 10.10 Live-CD.

I did:  [COLOR="RoyalBlue"]sudo mount /dev/sda1 /mnt[/COLOR] and received no error msg - success, I think?

Then:

ubuntu@ubuntu:~$ [COLOR="RoyalBlue"]sudo mount /dev/sda2 /mnt/boot[/COLOR]
mount: you must specify the filesystem type
ubuntu@ubuntu:~$ 


Then I tried:

ubuntu@ubuntu:~$ sudo mount -t ext4 /dev/sda2 /mnt/boot
mount: wrong fs type, bad option, bad superblock on /dev/sda2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
ubuntu@ubuntu:~$ 

Any help would be appreciated.

Thanks,

Once you've mounted a partition to /mnt (or any top level folder), I don't think you can mount another partition to a subfolder - /mnt/boot in this instance. Or, is /boot a folder on sda1 that you're trying to mount sda2 at - that may be causeing the bad option/bad superblock error. Try mounting the partitions to /mnt/<subfolder1> and /mnt/<subfolder2>.

---

### Post by garvinrick4 on 2010-11-22
Why are you mounting boot if I may ask? Below is code must mount and bind:
#This is just to show you more or less how and why you mount, copy and unmount in Live Cd or from another O.S.
with same architecture (32 or 64 bit).
```

[CODE]sudo mount /dev/sda5 /mnt
``````
sudo mount -o bind /boot /mnt/boot
``````
sudo mount -o bind /proc /mnt/proc
``````
sudo mount -o bind /dev /mnt/dev
``````
sudo mount -o bind /dev/pts /mnt/dev/pts
```They have to have the bind. 
Notice how it is written you select /proc to be mount in /mnt/proc
You select /boot to be mounted with /mnt/boot.
Tell it to mount to bind to /proc to /mnt/proc with a space between each.
Notice there is a rhythm to it.
Like to copy below: 
```
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
```To copy from one to the other with a space between from and to.

And the unmount is.
```
sudo umount /mnt/dev/pts
``````
sudo umount /mnt/dev
``````
sudo umount /mnt/boot
``````
sudo umount /mnt/proc
``````
sudo umount /mnt
```[/code]

---

### Post by Robert.Thompson on 2010-11-22
To all:

Thank you for your help and I am sorry if I have breached a forum rule.

I was trying to recover my Ubuntu after trying to install Fedora in a dual-boot configuration. I, wrongly, assumed that if I chose the 'shrink' option during the Fedora install that I'd end up with a dual-boot.

I was pointed to [https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

where it says:

Example: sudo mount /dev/sda1 Note: If the user has a separate /boot partition, this must be mounted to /mnt/boot Note: If the user has a separate /home partition, this must be mounted to /mnt/home.

I thought that I had created root, boot, swap and home partitions when I originally installed Ubuntu - it seems that I did not, go figure.

So, I guess by virtue of this error, the commands to mount boot and home failed. So I skipped them and did the update-grub, all the time wondering if I was suppose to do that after re-booting from the live-cd again or from the terminal after re-booting the PC. I did it from the PC.

Well, as you guys have probably already guessed, I still did not have a dual-boot but I did have my ubuntu back.

That's when the towel came over the ropes. I backed up my data; used Gparted ISO to remove all partitons and did a fresh install of PCLinuxOS, which I am using at this moment.

I plan to try to install Ubuntu now and see if I can create a dual-boot system. Before I do this, I will study the existing partitions and make some notes. I will even try to 'Label' them, if that is possible.

I think that Fedora should come with the warning: "Installation of Fedora may be hazardous to your health!"

I think that my 'posts' should come with the warning: "Answering this post could be hazardous to your sanity!"

Thanks again,

---

### Post by garvinrick4 on 2010-11-22
Fedora uses a different grub. grub-legacy and Ubuntu grub2. When you install Fedora just choose not to install grub at all during install, 
it is  there at grub install, a check mark I believe. Then install and boot first into Ubuntu and run update-grub below:
(You will find most other distro's use grub legacy) I like grub2 myself.
```
sudo update-grub
``` Above will put Fedora in your grub config and the grub menu and you are done;
```

If you have a /boot partition you must mount it when reinstalling grub
such as. /boot being sda1 and / at sda2. Using media directory:
Make the directorys; use any name you want as directory names.
[CODE]sudo mkdir /media/boot
``````
sudo mkdir /media/root
``````
sudo mount /dev/sda1 /media/boot
``````
sudo mount /dev/sda2 /media/root
``````
sudo grub-install --recheck --root-directory=/media/root /dev/sda
```Now you have to unmount;
```
sudo umount /media/boot
``````
sudo umount /media/root
```You have now installed grub to mbr of drive looking in sda2 for grub files.
When you have a /boot partition always has to be mounted when installing grub
from Live Cd or another partition with same 32 or 64 bit architecture. 

## When there is no /boot partition I use /mnt instead of /media such as:
      because do not have to make directories using /mnt 
```
sudo mount /dev/sda2 /mnt
```[/code]

---

### Post by garvinrick4 on 2010-11-22
##This is not intended to OP but for the /boot partition now in Windows 7 or Vista that OP
was referring to.

You know it may work for some but I also have a boot partition and it has Windows BCD files in a Boot folder.
If I mount using /mnt for / and /boot partition it will put an extra boot folder in my /boot partition or not mounting /boot partition when installing grub at times and or installing in sda1 instead of sda.
That of course is not suppose to be there when I install grub to mbr. I can rename it or throw it away and I can boot Windows again. I seem to see a lot of boot folders and Boot folders in Windows 7 boot partition since it now seems to come with a /boot partition from Manufacturer. Just have to make sure you do not mess with the Boot folder it has the BCD files in it. Windows see's boot and Boot folders as the same. It will at times make boot menu not appear at all.
 You will also see it in bootscript in the /boot partition. I have missed it a few times when looking at it. So I reproduced it multiple times in my own machine and saw the extra file
and its effect on booting. Renamed it or tossed it, reinstalled grub2 and could boot all installs again. I do believe now a lot of Windows 7 new users that have boot troubles this should be looked at first since it is so easy to reproduce. 
##Just a personal opinion from reproducing error over and over on own machine with /boot partition to experiment with. 
 Most will use Lilo to boot into Windows or use their Windows disks and of course they never get Ubuntu booting.
 #This has been discussed before but it is nice to see it reproduced and its affects and fixes.

---

