---
title: "Live CD won't boot on old  Laptop"
date: 2010-11-22
forum: New to Ubuntu
---

### Post by pmbritkg on 2010-11-22
Hi,
The title of [this thread]("http://ubuntuforums.org/showthread.php?p=10149336") caught my attention as I am having a problem booting on an old laptop the ubuntu installation CD I created on a Windows XP machine, following the recommended procedure, including the recommended ISO burner.

I have a Toshiba laptop which is about four years old and which I would like to run Ubuntu on. To make the install nice and clean, I first booted a DBAN cd which is about two years old to completely clear the hard drive. It worked very nicely. I have used DBAN many times in instances where an old computer is given away.

There seems to be something odd about the boot process of this laptop, however, as I found it will boot from old CDs but not new ones. The DBAN CD boots, a MINUX 3 CD boots and Windows installation disks boot. These disks have been sitting around for a few years. By now I have created ISO disks, which are supposed to be bootable for MemTest86, OpenBSD4.8, Knoppix 6.2.1 and finally Ubuntu 10.10. These disks were created on different computers running windows XP and windows 7. All these new disks were found to be bootable on the computers which created them. None of these new CDs would boot on the target laptop however. Please note that all the CDs are CD-R 700MB, 80min, 52x speed.

So my question is, why would an old CD boot but a new CD not boot when the difference seems to be age? Did something change in the boot process that means the current CDs will no longer boot on this older laptop?

Thank you for your help!

---

### Post by Dr Watts On on 2010-11-22
You mentioned the High-speed CD media. I think the older CD's are not the 52x, and that the old laptop drive can't read 52x (the only "straw" I could think of to "grasp" for). Though, I never heard of 52x, once successfully written to, not being readable on old players. Very intriguing problem (for me; maddening for you, I'm sure).
DrWattsOn

---

### Post by uRock on 2010-11-22
pmbritkg,

Welcome to Ubuntu Forums.

I have moved your post to a new thread for better chances of getting an answer.

Regards,
uRock

---

### Post by Iowan on 2010-11-22
From Code of Conduct:
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

### Post by pmbritkg on 2010-11-24
Since my initial post, I have found a Suse Linux version 9.1 CD that boots, a Fedora 9 DVD that boots and a Suse 10.0 DVD that boot. 

A friend who is running Ubuntu 10.10 burned the downloaded ISO to CD and we tested it by booting a more recent laptop successfully. Unfortunately, the target laptop would still not boot from this current CD.

---

### Post by amsterdamharu on 2010-11-24
If your laptop can boot off a usb you can try unetbootin. This program is available for linux and windows. You just point the program to the iso file (it can redownload but it will take forever) and it will make a usb memory drive bootable and have all the files needed to install.

---

### Post by pmbritkg on 2010-11-24
The fastest successful boot on the target laptop (manufactured by Toshiba) has been for a Minux 3 CD-R 700MB 52x speed. Interestingly, if Nero on a windows XP platform is used to copy this CD, the new CD is no longer bootable. The new CD had the same parameters as above.

What commands would be used to create a legacy bootable CD of minimal size for Ubuntu? I found the following for a different linux flavor. Would it still work? Please see below:

mkdir -p iso/boot/grub
cp /lib/grub/i386-pc/stage2_eltorito iso/boot/grub
cp /lib/grub/i386-pc/menu.1st iso/boot/grub
Copy all files, OS files, etc to iso that you wish to put on the CD
mkisofs -R -b boot/grub/stage2_eltorito -no-emul-boot -boot-load-size 4 -boot-info-table -o grub.iso iso

---

### Post by pmbritkg on 2010-11-24
Unfortunately, the BIOS of the target laptop does not provide for boot from USB.

I did create a bootable USB of Ubuntu 10.10. Would there be a way of using the successfully bootable Minux 3 CD to start with and somehow pointing control over to the Ubuntu ISO on the USB?

---

### Post by uRock on 2010-11-24
Try using a burner program made for burning ISOs.

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[http://infrarecorder.org/](http://infrarecorder.org/)

---

### Post by amjjawad on 2010-11-24
> **pmbritkg said:**
> Unfortunately, the BIOS of the target laptop does not provide for boot from USB.

[There you go]("http://blog.brothersoft.com/2008/12/09/boot-computer-from-usb-or-cdrom-even-if-bios-not-supported-using-plop/")

---

### Post by pmbritkg on 2010-11-24
I tried infrarecorder from a Windows XP Pro and a Windows 7 machine but it did not succeed in producing any bootable disks for the target laptop.
Clearly something did make bootable CDs for this laptop at some time, since I have 5 non-commercial CDs/DVDs that will boot.

---

### Post by amjjawad on 2010-11-24
> **pmbritkg said:**
> I tried infrarecorder from a Windows XP Pro and a Windows 7 machine but it did not succeed in producing any bootable disks for the target laptop.
Clearly something did make bootable CDs for this laptop at some time, since I have 5 non-commercial CDs/DVDs that will boot.

And I assume you're burning it as iso (image) not as a data CD or anything else, right?

This is the first time I read about such issue. If the CD is bootable with other machines, it should be bootable with the laptop as well.

---

