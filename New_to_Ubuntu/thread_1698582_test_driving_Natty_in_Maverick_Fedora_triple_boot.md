---
title: "test driving Natty in Maverick Fedora triple boot"
date: 2011-03-02
forum: New to Ubuntu
---

### Post by beew on 2011-03-02
Hi,

Here is the situation. I would like to test drive Ubuntu 11.04. I am going to carve out a small partition in an external drive which already has Maverick and Fedora installed for it. 

Now the problem. The Natty installer does not have an option of not installing the boot loader. That is no good as grub is currently in Maverick. When I installed Fedora I simply chose not to install grub and when the installation was completed, I just booted into Maverick to run sudo update-grub and it automatically detected Fedora and added it to the start up manual. I want to do the same with Natty (it is just a test installation, I am not going to let it control boot up, besides I am not really going to use Natty, all my Maverick installations will be good til December then I would upgrade to 11.10)

I can see two ways around it but neither is very elegant. First is to install the bootloader back into the live usb, that way it won't be installed in the actual drive where all these systems are. The second one would be to go ahead and install grub into the hard drive, then when done, boot into Maverick and run ```
sudo grub-install recheck /dev/sdc
``` (this seems potentially risky and I need to double check that the command is correct)

Please advise, thanks.

---

### Post by philinux on 2011-03-02
I'll chuck this in.

I have maverick on disk1 and natty on disk2. Both internal drives.

Maverick has controlling grub and as I installed natty earlier I told it to install grub to sdb1. So I chainload in to natty from mav.

Now here's the rub. Every time natty gets a grub-pc update it runs update-grub as expected but it also takes over the boot process and fails to detect my mav install. Had to run grub-update within natty to get it back. Arrghh I hear you say.

So now I chroot into natty to upgrade and if there's a grub related update I just run sudo grub-install /dev/sda to get control  back within mav.

---

### Post by beew on 2011-03-02
> **philinux said:**
> I'll chuck this in.

I have maverick on disk1 and natty on disk2. Both internal drives.

Maverick has controlling grub and as I installed natty earlier I told it to install grub to sdb1. So I chainload in to natty from mav.

Now here's the rub. Every time natty gets a grub-pc update it runs update-grub as expected but it also takes over the boot process and fails to detect my mav install. Had to run grub-update within natty to get it back. Arrghh I hear you say.

So now I chroot into natty to upgrade and if there's a grub related update I just run sudo grub-install /dev/sda to get control  back within mav.


Well after reading your post I went for option 1, installing grub back into the live usb, it gave an error message (that there is no proper mount pt in the usb) and I went ahead anyway, it was happily installing for about 15 minutes and then complained that it couldn't install grub in the location specified and prompted me to choose another. In the dialogue there was the option "continue without installing bootloader", which I checked.

I booted back into Mav and ran sudo update-grub, it detected Natty and added it to the boot manual. But when I tried to boot into Natty I got error message and it wouldn't boot, complaining that some files are missing (probably things that were installed after installing grub).

So I am back to square one. I wonder if it is possible to install grub in the proper location, boot into Mav and do sudo install-grub recheck and then, to avoid the problem you are having, delete grub in natty.

There are so many threads where people get into troubles dual booting with Windows or Fedora, it turns out dual booting with another Ubuntu is the real challenge!

---

### Post by beew on 2011-03-03
Hello? Anyone with an idea?

---

### Post by beew on 2011-03-03
Bump!

---

### Post by beew on 2011-03-03
Well I am not going to risk my Mav installation, just dug out an old 4 G external drive and install Natty on it.  But if anyone has a good idea for the original problem I am still interested so I won't mark this thread as solved yet and will bump it once in a while so it won't be dead and buried.

---

### Post by wilee-nilee on 2011-03-03
Over the last week I installed archbang and fedora 14 both grub legacy, along side my W7 and maverick setup. I just let both put grub legacy in the mbr booted to them updated and upgraded set them up then used super grub to boot into maverick and just reloaded grub to the mbr from there. Same commands you posted in the other thread.

You can use the commands we used to get your Lucid back to get your lucid in control every time, if all is in order, even if you install Natty. Here is the grub2 link with the commands.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

Here is a link the supergrub, I have it on a multiboot thumb, the middle grub2 version.
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by beew on 2011-03-03
Thanks,  I will have a look at those links.

So basically it is like what PhilLinux said earlier to switch back and forth between Natty and Mav to put grub control back to Mav?

---

### Post by wilee-nilee on 2011-03-03
> **beew said:**
> Thanks,  I will have a look at those links.

So basically it is like what PhilLinux said earlier to switch back and forth between Natty and Mav to put grub control back to Mav?

That's what I do, the supergrub thumb makes it really easy I save like 3 minutes over reloading the mbr with the cd, lol.:)

---

### Post by beew on 2011-03-15
Hi,

I have been doing some searching, I found that if I choose to put GRUB in the partition where Natty is (instead of the drive) during installation Mav would retain control of GRUB (i.e choosing to put GRUB in, say, sdc12 instead of just sdc when installing Natty, sdc12 is Natty's / partition)

About an hour ago I got an update for grub-pc in Natty. I rebooted and automatically booted into Maverick. So I am marking this thread as solved.

---

