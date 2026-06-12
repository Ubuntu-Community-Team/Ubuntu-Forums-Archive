---
title: "Cannot boot, because accidently removed kernels"
date: 2010-12-12
forum: New to Ubuntu
---

### Post by irpsit on 2010-12-12
Hi all,

I did a fatal beginner mistake
I removed the linux-alsa-drivers-modules-2.6.32-26-generic and now after reboot it says "error file not found, kernel has to be load first"

Not even in recovery mode works, it just says the same thing
I am shocked! I have all my files and stuff there.

What do I do now?

I can type e to edit boot commands, or c to access GRUB.
Is there any way to recover the system, by typing something in GRUB?

I have installed my Ubuntu in dual boot with Wubi /UNETbootin , so when I boot I have a Ubuntu/Windows/UNETbootin choice. If I choose UNETbootin I access a linux desktop (installed by WUBI) but this has not the files and stuff which I have (because I installed my ubuntu from this desktop).

Please help me!!
Any help would be greatly appreciated!!!
Is there any way to type something in GRUB to solve this?

---

### Post by drs305 on 2010-12-12
I have only experimented with this after reading your post. I believe you can use the chroot procedure below:

You will need to mount Windows, then Wubi. I am not 100% sure I understand your installation, but alter the following to mount the 'root.disk' file, wherever it is found.
```
sudo mkdir /mnt/windows /mnt/wubi
sudo mount /dev/sdXY /mnt/windows  # Your Windows partition (sda1, etc)
sudo mount -o loop /mnt/windows/ubuntu/disks/root.disk /mnt/wubi
for i in /dev /dev/pts /proc /sys ; do sudo mount -B $i /mnt/wubi$i ; done
sudo chroot /mnt/wubi

```
You should now be at a root prompt. Now install the most recent kernel, update grub and exit the chroot.

```

apt-get update
apt-get install linux-image
update-grub
exit
```

---

### Post by irpsit on 2010-12-12
Drs305,

First, thanks a lot for helping me so quickly!

How I installed Ubuntu: From Windows XP I first installed WUBI. From the WUBI linux desktop, there was an option to install separately install Ubuntu (where I have my own files) and in a separate partition.

Using UNETbootin, I boot into this WUBI desktop.
First, using disk utility I find my two partitions
/dev/sda1 where is Windows (mounted in /cdrom) 52GB/NTFS
/dev/sda2 where is Ubuntu (mounted in /media/A000B2F2CF12) 100GB/NTFS (this is what I want to access)

I used Nautilus and discover where is the Root.disk file that I want to recover

It is in /media/A000B2F2CF12/ubuntu/disks
In this folder, there is a subfolder with Grub (with has the different ubuntu booting options, including recovery mode)

[B]Back to your trick, I tried first to 
sudo mkdir /mnt/recoverubuntu (to avoid confusion with names)
sudo mount /media/A000B2F2CF12/ubuntu/disks/root.disk /mnt/recoverubuntu[/B]

Until here, these commands were without errors.
I don't understand the next commands.

What do I do next?

---

### Post by drs305 on 2010-12-12
> **irpsit said:**
> Until here, these commands were without errors.
I don't understand the next commands.

What do I do next?
Editing.

Normally you have to use the "loop -o" option to mount the root.disk file. I think you are referring to a real partition with an Ubuntu installation. As long as you can see your Ubuntu files in a file browser when viewing /mnt/recoverubuntu it should work. If so, you now chroot into your /mnt/recoverubuntu folder:
```
for i in /dev /dev/pts /proc /sys ; do sudo mount -B $i /mnt/recoverubuntu$i ; done
sudo chroot /mnt/recoverubuntu
```

If these commands run without error and you end up at a root prompt, you have successfully entered the 'chroot' and now the commands you issue will affect your Wubi installation.

Revised.

Now run the 'apt-get update', 'apt-get install linux-image' and 'update-grub' commands as previously listed.

---

### Post by irpsit on 2010-12-12
Ok,

Almost there.

sudo mkdir /mnt/recoverubuntu (to avoid confusion with names)
sudo mount /media/A000B2F2CF12/ubuntu/disks/root.disk /mnt/recoverubuntu
for i in /dev /dev/pts /proc /sys ; do sudo mount -B $i /mnt/recoverubuntu$i ; done
sudo chroot /mnt/recoverubuntu

I could browse there with Nautilus and see my files!! 
[B]This is a very positive sign!
[/B]
Then I moved to the root: cd /mnt/recoverubuntu
done "apt-get update" the packages were download, no errors
[B]Another very positive sign!!
[/B]
[B]But when I did "apt-get install linux-image"
there was an error[/B]

What should I do now?
Maybe I don't have the root previleges? Maybe I have to input my root password? But it does not ask me for a password

The kernel I had was the 2.6.32-26-generic


> 
ubuntu@ubuntu:/mnt/recoverubuntu$ apt-get install linux-image
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

---

### Post by irpsit on 2010-12-12
Wait, I forgot to so "sudo"
It's working now, its installing

I will reply again when I finish this
Thanks a lot, drc305!

---

### Post by irpsit on 2010-12-12
Ok, "sudo apt-get install linux-image" gave some errors (see below)


These errors are the same I was having before I remove the kernels (that was actually the reason I remove the kernels, to see if I could install them again, to eliminate that error)
But those errors do allow me to do normal work in ubuntu

However "sudo grub-update" gives me a serious error (see below)

The kernel I had before, was the 2.6.32-26-generic


> After this operation, 107MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Abort.
ubuntu@ubuntu:/mnt/recoverubuntu$ sudo apt-get install linux-image
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  linux-generic linux-image-2.6.35-23-generic linux-image-generic
Suggested packages:
  fdutils linux-doc-2.6.35 linux-source-2.6.35 linux-tools
The following NEW packages will be installed:
  linux-image linux-image-2.6.35-23-generic
The following packages will be upgraded:
  linux-generic linux-image-generic
2 upgraded, 2 newly installed, 0 to remove and 194 not upgraded.
Need to get 34.2MB of archives.
After this operation, 107MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main linux-image-2.6.35-23-generic i386 2.6.35-23.41 [34.2MB]
Get:2 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main linux-generic i386 2.6.35.23.25 [4,908B]
Get:3 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main linux-image-generic i386 2.6.35.23.25 [4,922B]
Get:4 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main linux-image i386 2.6.35.23.25 [4,902B]
Fetched 34.2MB in 1min 17s (443kB/s)                                           
Selecting previously deselected package linux-image-2.6.35-23-generic.
(Reading database ... 124417 files and directories currently installed.)
Unpacking linux-image-2.6.35-23-generic (from .../linux-image-2.6.35-23-generic_2.6.35-23.41_i386.deb) ...
Done.
Preparing to replace linux-generic 2.6.35.22.23 (using .../linux-generic_2.6.35.23.25_i386.deb) ...
Unpacking replacement linux-generic ...
Preparing to replace linux-image-generic 2.6.35.22.23 (using .../linux-image-generic_2.6.35.23.25_i386.deb) ...
Unpacking replacement linux-image-generic ...
Selecting previously deselected package linux-image.
Unpacking linux-image (from .../linux-image_2.6.35.23.25_i386.deb) ...
Setting up linux-image-2.6.35-23-generic (2.6.35-23.41) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-23-generic
gzip: /boot/initrd.img.gz: No such file or directory
cp: cannot stat `/boot/vmlinuz': No such file or directory
[B]Failed to create initrd image.
dpkg: error processing linux-image-2.6.35-23-generic (--configure):[/B]
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.35-23-generic; however:
  Package linux-image-2.6.35-23-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.35.23.25); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image:
 linux-image depends on linux-image-generic (= 2.6.35.23.25); however:
  Package linux-image-generic is not configured yet.
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            dpkg: error processing linux-image (--configure):
 dependency problems - leaving unconfigured
[B]Errors were encountered while processing:
 linux-image-2.6.35-23-generic
 linux-image-generic
 linux-generic
 linux-image
E: Sub-process /usr/bin/dpkg returned an error code (1)[/B]

[B]ubuntu@ubuntu:/mnt/recoverubuntu$ sudo update-grub
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
ubuntu@ubuntu:/mnt/recoverubuntu$[/B] 

---

### Post by irpsit on 2010-12-12
Ok, I was not supposed to do "sudo"

When I run "apt-get update" "apt-get install linux-image" or "update-grub", it gives me the same error, that I am not at root level

So I could do everything until chroot and visualize the files, but still cannot install nothing in the console

> u**buntu@ubuntu:/mnt/recoverubuntu$** apt-get install linux-image
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

---

### Post by drs305 on 2010-12-12
We are mixing chroot and non-chroot procedures. In a chroot environment (with a root# prompt) you do not use sudo. In a normal environment, you use chroot. You had successfully chrooted but then switched directories. I suppose you are trying to fix a normal installation via a Wubi chroot. While that I guess is possible, let's just use the LiveCd and repair the installation directly. It should be easier that way!

It looks like you may just have a normal installation with a bad 'lock' file. We can fix that easily.

Since things are pretty muddled, at this point it's probably best to just run the boot info script from the following site and post the results.
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

And just confirm your Wubi installation works fine, and it is the separate Ubuntu on it's own partition that has the problem.

---

### Post by irpsit on 2010-12-12
Results attached.

So, everything was correct until the chroot. I do visualize all most of my files.

However doing apt-get install linux-image gives me the root error

Please have a look at the results, if you could help me finishing this I would be very glad!!

---

### Post by drs305 on 2010-12-12
You almost had it in Post #5. You had successfully chrooted and then veered off course. 

You have a normal Wubi installation with a standard Wubi partition.

Reboot if you haven't since you did all the mount commands just so we can start fresh.

```

sudo mkdir /mnt/windows /mnt/ubunturecovery
sudo mount /dev/sda2 /mnt/windows  # Your Windows partition
sudo mount -o loop /mnt/windows/ubuntu/disks/root.disk /mnt/ubunturecovery
for i in /dev /dev/pts /proc /sys ; do sudo mount -B $i /mnt/ubunturecovery$i ; done
sudo chroot /mnt/ubunturecovery
```

When you do this, you will be at root@ubuntu or something similar. You are now root and do not use sudo.

Do not change directories. Update your repositories:
```
apt-get update
```
Now install the linux kernel:
```
apt-get install linux-image
```
If you get an error message about a lock, make sure you haven't opened Synaptic. Nothing should be open, so I suspect you have a lock file that didn't clear. We will remove it.

Be very careful with this command. Make sure you don't leave any extra spaces or you could delete all your Wubi system files:
```
rm /var/lib/dpkg/lock
```
Now try to install linux-image again.

If it works, don't forget to update grub, then exit:
```
apt-get install linux-image
update-grub
exit
```

---

### Post by irpsit on 2010-12-12
I just want to ask you about the syntax of the chroot command !!

Should I type all of this in the same line

for i in /dev /dev/pts /proc /sys ; do sudo mount -B $i /mnt/ubunturecovery$i ; donesudo chroot /mnt/ubunturecovery

Or should I write like this
for i in /dev /dev/pts /proc /sys 

sudo mount -B $i /mnt/ubunturecovery$i

sudo chroot /mnt/ubunturecovery

What is the "done"?
I didnt understand it very well. I am sorry to ask!!
I understand to not change directory in the console, nor use sudo after chroot.

If I type some syntaxs above, the console directory changes to > 
I dont know if this is ok

If I run
for i in /dev /dev/pts /proc /sys ; do sudo mount -B $i /mnt/ubunturecovery$i ; done
and
sudo chroot /mnt/ubunturecovery

Then it gives me this mistake

> ubuntu@ubuntu:~$ for i in /dev /dev/pts /proc /sys ; do sudo mount -B $i /mnt/rec$i ; done
ubuntu@ubuntu:~$ sudo chroot /mnt/rec
chroot: failed to run command `/bin/bash': Exec format error

---

### Post by drs305 on 2010-12-12
for i in /dev /dev/pts /proc /sys ; do sudo mount -B $i /mnt/ubunturecovery$i ; done

sudo chroot /mnt/ubunturecovery

Ask all you need to. :-)

---

### Post by irpsit on 2010-12-12
I did this

sudo mkdir /mnt/rec (i changed directory to make it easier)

sudo mount -o loop /media/A000B2F200B2CF12/ubuntu/disks/root.disk /mnt/rec

for i in /dev /dev/pts /proc /sys ; do sudo mount -B $i /mnt/rec$i ; done

sudo chroot /mnt/rec

But there was this error

> ubuntu@ubuntu:~$ sudo chroot /mnt/rec
chroot: failed to run command `/bin/bash': Exec format error
ubuntu@ubuntu:~$ 

I will restart and try again.

---

### Post by drs305 on 2010-12-12
I would recommend running the commands as I entered them, e.g.:
```
sudo mount /dev/sda2 /mnt/windows
sudo mount -o loop /mnt/windows/ubuntu/disks/root.disk /mnt/rec

```

And if you reboot the LiveCD, don't forget to make /mnt/windows and /mnt/rec again.

Added: I still don't really understand the /media/A000B2F2CF12 .. 

How and why is your root.disk ending up in there?

---

### Post by irpsit on 2010-12-12
I still end with the same mistake

> ubuntu@ubuntu:~$ sudo mkdir /mnt/rec
ubuntu@ubuntu:~$ sudo mkdir /mnt/windows
ubuntu@ubuntu:~$ sudo mount /dev/sda2 /mnt/windows
ubuntu@ubuntu:~$ sudo mount -o loop /mnt/windows/ubuntu/disks/root.disk /mnt/rec
ubuntu@ubuntu:~$ for i in /dev /dev/pts /proc /sys ; do sudo mount -B $i /mnt/rec$i ; done
ubuntu@ubuntu:~$ sudo chroot /mnt/rec
chroot: failed to run command `/bin/bash': Exec format error
ubuntu@ubuntu:~$ 

I think the linux desktop (live CD) from where I am typing this is located in windows partition sda1
and /media/A000B2F200B2CF12 (sorry there was a typo) is sda2 where the separate ubuntu instalation is. 

Now using Nautilis I still see my ubuntu files in /mtn/rec
And in /mnt/windows i see the partition sda2 as I would normally see it from windows (D:)

The problem now is to work sucessfully the chroot command

---

### Post by irpsit on 2010-12-12
Doing dir of both mounted folders. Both are same partition

> ubuntu@ubuntu:~$ cd /mnt
ubuntu@ubuntu:/mnt$ cd windows

[B]ubuntu@ubuntu:/mnt/windows$ dir
28d70a4207427dedef          RECYCLER               ubuntu
37e9f82a5905d1bd5a94233a05c4f361  System\ Volume\ Information
a2659d2f493f972c17e7c0          temp[/B]

ubuntu@ubuntu:/mnt/windows$ cd /mnt/rec
[B]ubuntu@ubuntu:/mnt/rec$ dir
bin   cdrom  etc   host  lib32    lost+found  mnt  proc  sbin    srv  tmp  var
boot  dev    home  lib     lib64    media        opt  root  selinux    sys  usr[/B]
ubuntu@ubuntu:/mnt/rec$ 


In first case, I can browse to disk.file by going to ubuntu/disks

In second case, I _cannot_ browse to disk.file but I can see my files under /home

---

### Post by drs305 on 2010-12-12
The second (/mnt/rec) are your ubuntu system folders, which is what you want to see. 

The /bin/bash error means either the system files are not mounted or you are using an incompatible version to chroot. The most common of those errors would be using a 64-bit CD with a 32-bit Wubi (or vice versa), or a much older CD.

---

### Post by irpsit on 2010-12-12
End of thread. 

I was too tired to go to the effort of recovering the kernels.
But it seems that burning a 64bit liveCD and from there repeating the whole procedure would recover the kernel. Because chroot would only be compatible when running with both being 64bit environments.

As my instalation is a Wubi, and dependent from Windows, I decided I will install ubuntu fresh.

Please feel free to post again, if someone else encounters this same problem and needs help.

---

