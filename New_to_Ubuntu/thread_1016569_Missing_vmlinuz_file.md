---
title: "Missing vmlinuz file"
date: 2008-12-20
forum: New to Ubuntu
---

### Post by nandanlbhat on 2008-12-20
Hi,

This is my first attempt at installing Ubuntu (hence the posting in Absolute Beginners area), though I am not entirely ignorant of Linux.

I have received a Multi-boot DVD from Linux for You magazine in India featuring 8.10 Live versions of Ubuntu, Kubuntu, Xubuntu, Edubuntu, Mythbuntu as well as regular installable Ubuntu Studio.

The Live versions boot up fine (I've tried Ubuntu/Kubuntu/Xubuntu), but the installation is complicated because I already have Windows XP Pro and Fedora 10 on a previously partitioned drive. My MBR is used by Windows. I have used the boot sector of the root drive for Fedora and created an entry in Windows boot.ini. On Fedora root partition, I've got Grub running with listing of all Linux options. I intended to add Ubuntu to that list.

The installation of Ubuntu goes fine, except the boot entries in the Automagic section only has memtest. The boot directory does NOT have a vmlinuz file, but does have an initrd file. My guess is I won't be able to boot Ubuntu without a vmlinuz file.

This situation was reproduced every time on a Dell Optiplex 740 and a Dell Vostro 1200 laptop.

Any pointers?

---

### Post by jrusso2 on 2008-12-20
I bet you have vmlinuz since thats the kernel.  I think you will just need to add that line to grub so it can boot it.
[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

---

### Post by logos34 on 2008-12-20
> **nandanlbhat said:**
> The boot directory does NOT have a vmlinuz file, but does have an initrd file. My guess is I won't be able to boot Ubuntu without a vmlinuz file.

This situation was reproduced every time on a Dell Optiplex 740 and a Dell Vostro 1200 laptop.

I agree--it appears there is no vmlinuz in /boot (nor a symlink to it in / as there is for initrd).  Something is definitely amiss.  

I think you'll have to download it from here:

[http://archive.ubuntu.com/ubuntu/dists/intrepid/main/installer-i386/current/images/hd-media/](http://archive.ubuntu.com/ubuntu/dists/intrepid/main/installer-i386/current/images/hd-media/)

---

### Post by nandanlbhat on 2008-12-20
Ok, assume the vmlinuz file is indeed missing for some reason. But why is the /boot/grub/menu.lst file (attached) having no entries other than the memtest? 

I am assuming, the part of copying the vmlinuz file and creating appropriate entry is not working in my case.

---

### Post by logos34 on 2008-12-20
Hardly surpises me...Pretty screwy...If I were you I wouldn't trust that install DVD...Find another way to get ubuntu (download the iso, Shipit CD, etc).

---

### Post by nandanlbhat on 2008-12-20
Thanks for the pointer. I copied the vmlinuz file over from the install DVD itself and created the boot entries I needed. It worked on the laptop. Trying out the desktop now. As you say, must be the DVD having something weird.

Cheers.

---

### Post by nandanlbhat on 2009-01-04
Hi,

I just wanted to update this thread. I downloaded the desktop iso for 8.10 and re-installed. The install completed without any hitch. As pointed out above, it was the magazine DVD that might have got something wrong on it.

Cheers

---

### Post by jrusso2 on 2009-01-04
Very good job for a new user to be able to figure that out.

---

### Post by nstenz on 2009-08-04
I just ran into this trying to do a new installation of Jaunty side-by-side with Intrepid by mounting the .iso as loopback with the Live CD and extracting it to its own temporary partition to install from (after making 2 semi-coasters with 2 different computers- the Live CD would boot, but install failed copying some files). By the way, if you want to do that, the instructions are here- [https://help.ubuntu.com/community/Installation/FromLinux](https://help.ubuntu.com/community/Installation/FromLinux)
As far as I can tell, it worked perfectly otherwise.  

It's up and running now after doing this:
[LIST=1]
[*]Copying vmlinuz from the .iso's /casper folder to /boot on the new partition
[*]Editing /boot/grub/menu.lst- 
[*]Copying the lines for the newest 8.10 kernel and replacing the-
[*]title line with Ubuntu 9.04 (duh)
[*]kernel line with /boot/vmlinuz, and changing the UUID portion to the UUID from the 9.04 memtest line
[*]initrd line with the 9.04 initrd
[/LIST]

It was a shot in the dark after not finding the kernel anywhere on the new partition, but I ran across a mention somewhere of using the kernel from the Live CD image, so I tried it, and amazingly enough, it worked!

---

