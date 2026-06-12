---
title: "initramfs corrupt"
date: 2011-05-12
forum: New to Ubuntu
---

### Post by ktechman on 2011-05-12
Is it possible to use a live cd (Ubuntu) to repair the initramfs file? I do not have another kernel to boot into to make repairs.  I have tried to use the CL with no success by mounting the hd and writing to it when I attempt to chroot the partition it gives me a format error. Using 10.04 32-bit 

ktechman

---

### Post by wojox on 2011-05-12
Have you [tried this?]("http://www.ardyans.co.cc/how-to-fix-initramfs-boot-trouble-ubuntu.htm")

---

### Post by drs305 on 2011-05-12
I would think you would have to do a chroot if using the LiveCD. 

Using the same release's LiveCD, chroot into the real Ubuntu partition and then running the following would work:
```
update-initramfs -c -k <version>
``` 
Example: update-initramfs -c -k 2.6.32-24-generic
Sudo wouldn't be required while chrooting.

For instructions on how to chroot from the livecd you can click the 'Chroot' link in my signature line. Perhaps following these instructions will prevent the error you are getting.

The thread is about Grub, but the instructions for chrooting are the same.

---

### Post by ktechman on 2011-05-12
Yes, the reply is update-initramfs is disabled since running on read-only media.  Any suggestions would be helpful

Ktechman

---

### Post by ktechman on 2011-05-12
DRS35,

How would you chroot into the partition I have tried various methods to no avail. Thank you for the link and information

Ktechman

---

### Post by drs305 on 2011-05-12
> **ktechman said:**
> DRS35,

How would you chroot into the partition I have tried various methods to no avail

Ktechman

See the instructions in my "Chroot" link. Some of the reasons for chroot failures include not using the correct version (use a **Lucid** CD) and also not using the correct architecture (32-bit or 64-bit, whichever is installed).

---

### Post by ktechman on 2011-05-12
When I input ```
sudo cp /etc/resolv.conf /mnt/temp/etc/resolv.conf
``` I receive this error ```
cp: cannot stat `/etc/resolv.conf': No such file or directory
```

Thank you for your reply

Ktechman

---

### Post by drs305 on 2011-05-12
> **ktechman said:**
> When I input ```
sudo cp /etc/resolv.conf /mnt/temp/etc/resolv.conf
``` I receive this error ```
cp: cannot stat `/etc/resolv.conf': No such file or directory
```

That one is not a 'show stopper' as long as the Internet works. Continue with the other commands and chroot. And in your case, you don't even need the Internet unless you are going to try to install or reinstall another kernel. If you don't need the Internet, don't worry about the 'apt-get update' command either. Once you are at the 'root' prompt, you don't need to follow any more of the instructions except 'exit' to leave the chroot environment.

I think somewhere on the page I explain that but it might not be in the section you are accomplishing.

---

### Post by ktechman on 2011-05-12
Even after I run ```
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/temp$i;  done
``` It will not allow me to chroot.  I am running a dual boot with windows. Isn't the file initramfs on the patition that contains my /home folder?

---

### Post by drs305 on 2011-05-12
> **ktechman said:**
> Even after I run ```
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/temp$i;  done
``` It will not allow me to chroot.  I am running a dual boot with windows. Isn't the file initramfs on the patition that contains my /home folder?

The initramfs file (initrd.img-<version> is in /boot (with a link in /). You need to mount the partition containing / and should also mount the partition containing /home if you have one. The instructions earlier show how to include separate /home and/or /boot partitions, which need to be mounted if you have them.

Once you have mounted the correct partition(s) to /mnt/temp, the code above will accomplish the the rest of the mountings automatically.

---

### Post by ktechman on 2011-05-12
Gparted show the boot flag on the ntfs partition I always assumed this only applies to windows and that the actual boot files and initramfs are on / so when I mount sda7 which is where / is I also need to mount the /home partition please explain.  I have no separate /boot or /home partition they all exist on /sda7.

Ktechman

---

### Post by drs305 on 2011-05-12
> **ktechman said:**
> Gparted show the boot flag on the ntfs partition I always assumed this only applies to windows and that the actual boot files and initramfs are on / so when I mount sda7 which is where / is I also need to mount the /home partition please explain.  I have no separate /boot or /home partition they all exist on /sda7.

Ktechman

Then you dont' have to worry about /home or /boot. Just mount your Ubuntu partition (/dev/sda7) on /mnt/temp.

The boot flag isn't used by Linux.

---

### Post by ktechman on 2011-05-12
I still receive the error, after mounting ```
chroot :cannot run command `/bin/bash': Exec format error
``` I have also tried in another terminal to sudo -i and sudo su to no avail

---

### Post by ktechman on 2011-05-12
The complaint ```
chroot :cannot run command `/bin/bash': Exec format error
``` is usually cause by the live cd not being the same architecture as the OS but this is not the case both the cd and OS are 32-bit. Can anyone tell me why I am getting this error?

---

### Post by drs305 on 2011-05-12
If you are using a Lucid 32-bit CD and the installation is also 32-bit, these procedures should work from a fresh boot of the LiveCD:

```
sudo mkdir /mnt/temp
sudo mount /dev/sda7 /mnt/temp
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/temp$i;  done
sudo chroot /mnt/temp

```
At which point you should be at a "root" prompt.

I don't know why it isn't working for you.

You can verify the architecture of the CD from and of the LiveCD with:
```
file `which bash`  # 64-bit will return x86-64
```

---

### Post by ktechman on 2011-05-12
Do you think the kernel on the live cd is conflicting with the kernel of the OS? The live cd does not have the pae portion of the kernel, any suggestions? This is what I get being so anal about not leaving a second kernel in play. Time for a reinstall unless I can build a live cd with the pae kernel. This should be marked as solved unless someone has a suggestion.

Ktechman

---

### Post by ktechman on 2011-05-12
I am going to download the 32-bit dvd install disk and see if it takes care of the issue.

Ktechman

---

### Post by drs305 on 2011-05-12
The only other thing I can think of is that there were two subsequent releases of the Lucid CD. Assuming you kept Lucid updated, perhaps you need to use the 10.04.2 LTS CD if your CD was still the original release. But that is a pretty long shot.

---

### Post by ktechman on 2011-05-12
I installed the 10.04.2 release.  > Exec format error

If the chroot command returns with the error "chroot: cannot run command `/bin/bash': Exec format error", this usually indicates that the live CD environment is not compatible with that of the installed system.

For example, the error is most frequently seen when trying to chroot to a 64-bit system (eg. amd64) from a 32-bit live CD (eg. x86).

The solution is to use a live CD which is using the same architecture as the installed system.  from [http://en.gentoo-wiki.com/wiki/Chroot_from_a_livecd]("http://en.gentoo-wiki.com/wiki/Chroot_from_a_livecd") It may be the case.  It worked!!!! I guess the fact that the pae portion of the kernel is not installed on a live cd did have an impact on my ability to chroot.

Ktechman

---

