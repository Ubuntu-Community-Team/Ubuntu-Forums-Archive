---
title: "I managed to break Ubuntu"
date: 2008-12-27
forum: New to Ubuntu
---

### Post by polksalet on 2008-12-27
This is my first real foray into Linux. I have been dabbling with various live versions for about 2 years and after I got my new laptop I turned the other into an Ubuntu machine. I have found that the best way to learn to fix things is learn how to tear them up. Well I did that apparently.

I was curious how many files would be left over after install so I downloaded some kind of cleaner program. I ran it and it told me to inspect all of the things before I cleaned them but because it found like 18,000 files and I have no idea what they were I just let it go and hoped for the best. I figured the worst case sceneario was that I would have to reinstall the thing.

Well it appeared at fist that everything worked until I rebooted. Now I have no keyboard, mouse, or pointing device. I cant even reboot the thing into the ubuntu disk.

Any ideas??

---

### Post by 2hot6ft2 on 2008-12-27
re-install and don't do it again. Guess that doesn't help considering your last paragraph. 

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
TestDisk is a powerful free data recovery software! It was primarily designed to help recover lost partitions and/or make non-booting disks bootable again when these symptoms are caused by faulty software, certain types of viruses or human error (such as accidentally deleting a Partition Table). Partition table recovery using TestDisk is really easy.
Can be installed with

```
sudo apt-get install testdisk
```
but if you can't boot a disc I don't know what to tell you
Livecd's here
[http://www.cgsecurity.org/wiki/TestDisk_Livecd](http://www.cgsecurity.org/wiki/TestDisk_Livecd)

---

### Post by polksalet on 2008-12-27
> **2hot6ft2 said:**
> re-install and don't do it again

It wont reinstall, at least I don't know how to make it sense and load the disk. Any tips?

---

### Post by 73ckn797 on 2008-12-27
> **polksalet said:**
> It wont reinstall, at least I don't know how to make it sense and load the disk. Any tips?


Did you try rebooting with the Ubuntu Live CD? You then could go to System/Administration/Partition Editor and wipe the drive via reformatting/partitioning and then re-install the OS (operating system).

---

### Post by polksalet on 2008-12-27
> **73ckn797 said:**
> Did you try rebooting with the Ubuntu Live CD? You then could go to System/Administration/Partition Editor and wipe the drive via reformatting/partitioning and then re-install the OS (operating system).


I cant make the thing boot from the cd at all. It just beeps and never brings up the options and goes straight to an unresponsive Ubuntu. I'm dumbfounded here. I know there were some things I would need to learn about Linux but I am not even sure what to say about not being able to figure out how to boot from an hp laptop.

---

### Post by thraxy on 2008-12-27
Try opening the bios menu and putting CD first in boot priority. That should make the computer start from CD no matter what.

---

### Post by CJ Master on 2008-12-27
^what thraxy said, hammer the DEL, F2, and F10 buttons and you should go to bios. (Depends on your comp.)

---

### Post by Hydrid on 2008-12-27
If you didnt erased the recovery partition then try the F11 or some of the other F keys

---

### Post by homer693 on 2008-12-27
When you turn the laptop on, there should be something saying Setup <F10> or something like that, what ever it says to press, press it, then look for boot priority and move the dvd/cd drive to the top of the list, that should tell it to boot the disc before the hard drive.

---

### Post by Miljet on 2008-12-27
When you do access the BIOS Setup, also look for an option to reset defaults. Hopefully, that will at least get your keyboard working again.

---

### Post by lukjad on 2009-01-09
polksalet, did you manage to fix the problem?

---

### Post by steveneddy on 2009-01-09
Cleaner program?

I would just reinstall from the Ubuntu CD.

You must choose the boot sequence from the BIOS.

We all broke Ubuntu at first. It's how we all learned.

I must have reinstalled at least 20 times before I finally came across a setup that I was happy with and that was stable.

---

