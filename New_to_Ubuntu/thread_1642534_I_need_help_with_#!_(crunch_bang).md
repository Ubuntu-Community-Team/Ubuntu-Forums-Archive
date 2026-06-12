---
title: "I need help with #! (crunch bang)"
date: 2010-12-10
forum: New to Ubuntu
---

### Post by darkely1024 on 2010-12-10
As a lot of people know Linux crunch bang is a varient of Ubuntu (that was just an fyi). Anyway I tryed installing linux crunch bang onto my hard drive 65% through it gave me an error message saying cannot write to some sector on the disc. I tried a few other versions of Linux (i.e. Debian, Puppy dog linux, Yellow dog, Ubuntu) - all of which failed to write to the hard drive (or finish install). I asuumed my hard drive was dead. So I got peppermint, and crunch bang to both work (the cds) - then bought a USB (4gb) from a computer store (i made sure it worked before hand) and picked the usb drive as the install destination (when I was trying to install crunch bang). It went all the way through and it said restart the computer so I removed the cd and selected the usb to boot [from]. My computer said it could find no operating system. I was ticked and I tried to boot from the [crunch bang] live cd. Now neither one of the two cds will boot. Please help me out with this problem or if I am doing anything wrong. I am planning on using the Universal USB Installer to try to make a bootable usb. I am open to suggestions and help (please do not be rude I am a total nube to this). 

My computer type: 
HP Compaq nc6120

thanks in advance

---

### Post by cariboo on 2010-12-10
Always check the simple things first. Have you got the boot order set correctly in the bios?

---

### Post by amjjawad on 2010-12-10
If you suspect your HDD, then I would suggest to run this command from Terminal:

```
dd if=/dev/zero of=/dev/sdx
```Where "x" refers to the HDD you're trying to install on, say sda.

As for booting from CD/DVD, please follow Cariboo's advice :)

NOTE THAT:
```
dd if=/dev/zero of=/dev/sdx
``` will remove everything on your HDD so do that ONLY if you think your HDD is dying. Backup any important data in case you have some there.

---

### Post by cariboo on 2010-12-10
Please don't suggest zeroing out a hard drive for a suspected problem, there are several other things that should be done first. Once the op is able to boot from a Live CD he should run fsck on the partition from it. 

Once at the desktop open a Applications->Accessories->Terminal and type:

```
sudo fsck -y /dev/sdXx
```

where /dev/sdXx = the / partition of the Ubuntu install.

If everything seems to work OK you are done, if not go to the hard drive manufacturers web side and download and the use their diagnostic tools to check the hard drive, that should give you an answer on whether the hard drive is a problem or not.

---

### Post by Ahava591 on 2010-12-10
The #! forums are very good for questions about #! and troubleshooting. The help sections, including those devoted to problems with the latest version, (Statler, I believe it is either Alpha 2 or 3, and is based on Debian, unlike the previous versions of #! which were based on Ubuntu,) are full of people that will be better able to help you than these, as their focus is on #! and not Ubuntu.
I suggest you ask there and bump your thread once or, at most, twice every 24 hours if you don't get replies sooner. Also, try searching there for threads which deal with similar situations.



Please clarify some things for me, so that I can try to help you better:

-Which version of #! are you trying to install? I ask this because it is usually the case with different distributions of Linux, (indeed, different versions of each distribution,) that each has specific problems, sometimes especially with installation. Letting us know which version you are trying will help us figure out what could be going wrong with that specific version.



Something that I noticed, if I am not wrong. What do you mean that 65% of the way through, the installation failed? After that statement, you state that you got both Peppermint OS and #! to work, you mention the CD's. Do you mean that the Live CD's originally worked, you could boot from them and use those operating systems in Live mode, but that when you tried to install to the hard drive, that is what failed?
-It seems to me that you are trying to use the Live CD of #! to install to the USB drive. 

Have you tried downloading the #! Live CD iso, (this is the disk image, the iso is what you will burn to a CD, then use that CD to boot a distribution in "Live," mode or to install from the Live CD to your hard drive,) and burning it to the USB? I understand that you want to create a boot-able USB drive. 
To do this, you shouldn't need to use a Live CD, you only need the iso disk image; then you would use a program like Unetbootin to create the Live USB, (a boot-able USB stick.)



Thank you for your patience, we *are *paying attention and we *will *help as soon as we can.

---

### Post by amjjawad on 2010-12-10
> **cariboo907 said:**
> Please don't suggest zeroing out a hard drive for a suspected problem, there are several other things that should be done first. Once the op is able to boot from a Live CD he should run fsck on the partition from it. 

Once at the desktop open a Applications->Accessories->Terminal and type:

```
sudo fsck -y /dev/sdXx
```where /dev/sdXx = the / partition of the Ubuntu install.

If everything seems to work OK you are done, if not go to the hard drive manufacturers web side and download and the use their diagnostic tools to check the hard drive, that should give you an answer on whether the hard drive is a problem or not.

I'm sorry, I jumped to the final step!

---

### Post by snowpine on 2010-12-10
CrunchBang is no longer based on Ubuntu (it's now based on Debian and previous Ubuntu-based releases are obsolete and unsupported) so grab the new "Statler" release at crunchbanglinux.org and say hi on the forums!

FYI you'll find the official instructions to create a CrunchBang Live USB here: [http://crunchbanglinux.org/wiki/statler_usb_installation](http://crunchbanglinux.org/wiki/statler_usb_installation)

---

