---
title: "Configuration of extra OS, Ubuntu 9.04 to System"
date: 2009-11-23
forum: New to Ubuntu
---

### Post by Uluru on 2009-11-23
Situation: 
I have a dual boot configuration, Win XP + PCLinuxOS MiniMe 2009.

C:\ Drive, were both XP and MiniMe are installed has 9 GB's of free space. Grub controls boot preference.

I do however have an external 500 GB Hard Drive where I keep "Stuff" , and primarily backups.

If I can I'd like to "Install" Ubuntu 9.04 on the External drive.

Also bypassing Grub, and if possible initiating the Ubuntu installation fom external 500 GB Hard Drive.

That's my idea, if not possible any help at doing a similar situation whereby I have the three OS's bootable would be great.

Thankyou for your time.

---

### Post by ukripper on 2009-11-23
When you install 9.04 GRub will be installed by default and will detect your XP and PClinuxOS. You can re-install grub to MBR if you like during install. That is entirely upto you. But you cant install 9.04 without grub from live cd.

---

### Post by Uluru on 2009-11-23
Hi ukripper, I'm not sure you understood my question.

> C:\ Drive, were both XP and MiniMe are installed has 9 GB's of free space. **Grub controls boot preference.**

> If I can I'd like to "Install" Ubuntu 9.04 on the External drive.

I'm asking if I can seperate the Boot process from an install of Ubuntu on a seperate drive, and somehow Boot Ubuntu from the External Hard Drive, seperate to the initial setup I have with Grub.

Or, as the problem is basically not enough room on the Main Hard Drive to install Ubuntu, thus the question, "install to another drive", maybe can be setup from the from live cd, and another option is added to the boot loader Grub: Windows, PCLOS, Ubuntu ?

Is there an option to install Ubuntu to a seperate drive ?

---

### Post by ukripper on 2009-11-23
It is the same process as you would install on any drive. Just pop the live cd in and follow the steps and when it asks for drives then select external drive, so answer is Yes you can install on usb external drive with the same Live cd. 

[QUOTE=Uluru]Also bypassing Grub[/QUOTE]

As i said earlier, you can't separate grub during installation via Ubuntu Live cd. But you can choose where you want your grub to be installed whether on external drive, MBR or any other drive's partition.

---

### Post by Uluru on 2009-11-23
Thanks ukripper for your replies.

The fact that it's possible to install Ubuntu to my External Hard Drive is a positive.
 
Because I _already_ have Grub installed when I configured PCLinuxOS MiniMe has me confused when you say I will install grub again, to somewhere of my choosing.I backed up Windows MBR before PCLOS MM install.

 I've been using GNU/Linux for two and a half years, I don't want to bork my Comp so I suppose I'll leave this alone for the time being till I understand 100%. 

Basically, I see too many exciting permutations, like deleting PCLOS MiniMe, reinstalling it and Ubuntu onto my Externall Hard Drive, to keep things tidy. Maybe best way to go; keep Win XP on separate drive from Linux.
 
By trying to think creatively I've confused the heck out of myself, (;) ) and I don't have the command line knowledge to specify how grub boot options would be configured for a three way boot of PCLOS, Win XP, and Ubuntu. 

Then the issue of partitioning the USB 500GB External HDD, for two Linux OS's. Pretty sure it is NTFS, I have disk images of Windows on there, plus heaps of other stuff I'd hate to loose.

Once I run the Live CD of Ubuntu 9.04 and opt to install, not sure if I can pullout if things get confusing. One way to find out is do it, but that's kinda why I started a thread here hoping someone may walk me through.
Don't I sound confused :D

---

### Post by ukripper on 2009-11-23
i'd suggest you clone your hardisk installation using clonezilla first(here is nice step by step tutorial - [http://www.dedoimedo.com/computers/free_imaging_software.html](http://www.dedoimedo.com/computers/free_imaging_software.html)) as a backup and then install ubuntu on external drive.

As a general rule of thumb you should always have a regular backup of your important data in any case.

---

### Post by Uluru on 2009-11-23
> Then the issue of partitioning the USB 500GB External HDD, for two Linux OS's. Pretty sure it is NTFS, I have disk images of Windows on there, plus heaps of other stuff I'd hate to loose.

yep, that's why I have the External HDD, for weekly disk images.

You just made it clear why it wouldn't be wise to install Ubuntu to my external backup drive, no worries.

It's o.k., was just an idea, Ubuntu is so popular thought I'd give it a whirl.

---

### Post by ukripper on 2009-11-23
How much space do you have on your normal HDD?

---

### Post by snowpine on 2009-11-23
Hi Uluru, yes, you can install Ubuntu entirely to an external drive, without affecting your internal drive in any way. (If I understand your question correctly.)

The two important details are:
1. When you get to the partitioner step, make sure you install to a partition on the external drive! Also choose Manual and make sure you're installing to a new partition, not the data partition with your backups. (Which you should make a backup of in my opinion :))
2. At the last step of the installer, click Advanced and choose the correct drive for GRUB (for example, /dev/sdb if /dev/sdb is indeed the external drive).

Now, when you turn on your computer, press the appropriate key for the BIOS boot menu (typically Esc or one of the Function keys) and choose the external drive. You should get a grub menu with all of the options. 

If you disconnect the external drive, the computer should boot from your original GRUB on the internal hard drive, no problem.

I hope that makes sense. :)

---

### Post by Uluru on 2009-11-23
ukripper:
> How much space do you have on your normal HDD? 
I've got 9 GB's free. That's a 40 GB HDD, with WinXP, and the PCLOS MiniMe, plus Program files, and Misc. I keep it pretty lean by moving anything like music, videos, media onto the External drive .

snowpine:
> " ...2. At the last step of the installer, click Advanced and choose the correct drive for GRUB (for example, /dev/sdb if /dev/sdb is indeed the external drive).

Now, when you turn on your computer, press the appropriate key for the BIOS boot menu (typically Esc or one of the Function keys) and choose the external drive. You should get a grub menu with all of the options.

If you disconnect the external drive, the computer should boot from your original GRUB on the internal hard drive, no problem."
O.K., I get that now. Thanks. :) The Grub bootloader will be on the External drive with Ubuntu, this could be fun ! I'll sleep on it, thankyou both for your replies .

---

