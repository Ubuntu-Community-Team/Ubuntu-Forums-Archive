---
title: "What is a root device?"
date: 2011-03-20
forum: New to Ubuntu
---

### Post by ichigo6420 on 2011-03-20
What does it do and how do you get there?

---

### Post by cariboo on 2011-03-20
I'm assuming you mean the root directory to get there, open an Applications->Accessories->Terminal and type:

```
cd /
```

to see a listing of the directories type:

```
ls -l
```

The graphical way  is to go to Places->Home Folder->File System

---

### Post by The Cog on 2011-03-20
What is the context in which you saw the "root device" mentioned? 

Cariboo thinks you might mean the root directory, the top of the directory tree. I wonder if you mean the device (disk/partition) that contains the root directory. But there is no immediately obvious meaning.

---

### Post by ichigo6420 on 2011-03-21
> **The Cog said:**
> What is the context in which you saw the "root device" mentioned? 

Cariboo thinks you might mean the root directory, the top of the directory tree. I wonder if you mean the device (disk/partition) that contains the root directory. But there is no immediately obvious meaning.

I saw it on this response, I happen to be having the same problem as the asker, but I didn't understand the second explanation. This is the link: [http://ubuntuforums.org/showthread.php?t=1492241](http://ubuntuforums.org/showthread.php?t=1492241)  Maybe you will have a better understanding of what I am asking after flipping through this link. Thank you!

---

### Post by The Cog on 2011-03-21
Ah. That thread is talking about the root device as being the disk (or partition on a disk) that contains the root filesystem. The bootloader's job is to find and mount the filesystem on the root device, and then load the operating system from there.

I didn't read the whole thread, but if the bootloader is giving up waiting for the root device to come ready, to me that suggests that the bootloader is misconfigured to look for a disk that doesn't exist, or the partition has been reformatted so the bootloader can't find it. I doubt it is a complete hard disk failure or the bootloader itself wouldn't be getting loaded.

---

### Post by JKyleOKC on 2011-03-21
The solution given in that thread you referenced is for an older version of grub than the one you are using, so it's not surprising that it didn't work for you. The current version of grub doesn't even HAVE a menu.lst file.

The "root device" it mentions means the boot partition of your hard drive, and translated into plainer language the error message is saying that when it tried to find the boot program on the disk, the disk didn't answer at all, so grub finally gave up. When it does give up in such a case, it quits listening to the mouse and keyboard so you have no option but to power down.

The suggestion to change from UUID notation to the /dev/sda means to alter the disk address from which grub will try to load the boot program. The string of letters and numbers after "UUID=" will be different on each machine; UUID stands for Universally Unique IDentifier, and the string is generated in a way that does make it unique for all practical purposes since it uses clock information and other things when it's first created. Disk partitions can also be identified by a name assigned early in the boot sequence, such as /dev/sda1 which would be the first partition (1) on the first drive seen (a). By changing the address that grub uses, the idea is to make it possible for grub to locate the boot program.

However there's the little problem of getting to the point where you can change the address, when the machine will not boot. Try holding down the left shift key, immediately after applying power, even before the monitor begins to display anything. It may take several tries but this should get you to the grub menu. Select the topmost entry and press "e" rather than Enter. This will get you into a simple editor, with the grub control code showing. Scroll to the line that begins "linux" and look for the "UUID=" part of that line. Delete the UUID= and the following letters and numbers, up to the space. Replace them with /dev/sda1 (assuming that you are not set up for dual booting with Windows; if you are it will be a bit more complicated but still possible -- let us know). Then press CTRL-X to finish booting and see if it all works.

If it does, let us know so we can walk you through making this change permanent. The procedure above is strictly temporary so the next boot will be back to the way it was before.

Hope this helps!

---

