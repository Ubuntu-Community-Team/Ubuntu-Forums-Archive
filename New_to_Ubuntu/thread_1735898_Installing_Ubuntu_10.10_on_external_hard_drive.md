---
title: "Installing Ubuntu 10.10 on external hard drive"
date: 2011-04-21
forum: New to Ubuntu
---

### Post by Jimtucket on 2011-04-21
I'm using a samsung rv511, and 320g ehd seagate free agent go, I went into boot priorty in bios
And my bios couldn't find ehd, so I change USB port then it found it, I tried to boot using the USB ehd
Then it locked up on black screen now in bios it won't find the external hard drive no matter which port I put it in, any ideas?

---

### Post by lmarmisa on 2011-04-21
> **Jimtucket said:**
> I'm using a samsung rv511, and 320g ehd seagate free agent go, I went into boot priorty in bios
And my bios couldn't find ehd, so I change USB port then it found it, I tried to boot using the USB ehd
Then it locked up on black screen now in bios it won't find the external hard drive no matter which port I put it in, any ideas?

I would like to know what Operating System is installed on your Rv511. Are you able to boot into this system normally?.

Do you have a Ubuntu Live CD/USB from where you can boot your netbook?.

Did you install properly Ubuntu on your external hard drive?.

---

### Post by rosencrantz on 2011-04-21
Erm, if your hardware isn't broken, the port shouldn't matter - at least, my laptops (Samsung & Asus) always identified the USB drive correctly at boot.
What did you do with the hard drive before you plugged it in? It needs to be bootable and to have some kind of OS and bootloader on it to work - e.g. a live Ubuntu with Unetbootin or sommthing similar.

---

### Post by Jimtucket on 2011-04-21
I am currently using windows 7, I had downloaded the iso file directly to my external and tried to install from there. I read to use wubi to install along side with windows but I want use the ehd only for ubuntu, and I didn't know if it would conflict with the laptops hdd. I was reading a guide last night when attempting the install, which im trying to relocate. Bare with me at my house I'm only limited to my phones Internet.

I'm kinda winging it and assuming I'm attempting the installs correctly, but am at a lost locating the ehd in bios. I might have misunderstood my guide when downloading the iso on ehd and it would read the file as the computer boots and I wouldn't have to do much besides the install from there.

---

### Post by lmarmisa on 2011-04-21
Do you have an external CD/DVD drive unit?. I suppose your netbook has no one.

---

### Post by lmarmisa on 2011-04-21
I do not recommend to use Wubi in your case. 

The installation of Ubuntu on an external hard drive is not difficult but you have to be careful because you have to select the correct options during the installation for not changing any information of your internal hdd, mainly its Master Boot Record.

So you should select the manual selection of partitions during the install procedure.

If you wish, I can send you a detailed description of the install procedure.

The installation requires booting from a Ubuntu Live CD or a Ubuntu Live USB. You should prepare one of them. You will need a USB flash drive or an external CD/DVD drive unit for this purpose.

In relation with your problem about the detection of the external USB drive, maybe some data structures of your ehd have been damaged when you unplugged it. Try always to unplug your ehs in a safe way. You should to run some repair procedure from Windows 7.

---

### Post by rosencrantz on 2011-04-21
Did you just save the .iso file to the drive and try to boot?
.iso files are not bootable, they are compressed CD images which need to be burnt first.
Do you just want to try out Ubuntu? In this case, you might be OK with the persistent mode Live USB install:
Install unetbootin on your Windows system
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
and let it unpack the iso image to your USB drive.
That's also one way to get a 'real' Ubuntu install on the drive: create two partitions, let Unetbootin put a live linux on the first and, from there, install Ubuntu to the second. I'm not quite sure, though, how boot loader and partition order are handled with this method.
I found another Howto using VirtualBox (on Windows), but that's a rather large download.
[http://mintarticles.com/read/operating-systems-articles/how-to-install-portable-linux-ubuntu-on-a-bootable-usb-flash-drive-from-sun-virtualbox,13641/](http://mintarticles.com/read/operating-systems-articles/how-to-install-portable-linux-ubuntu-on-a-bootable-usb-flash-drive-from-sun-virtualbox,13641/)
Another option (see lmarmisa above), if you have a spare flash drive and free USB port, try putting a Live Ubuntu on it with unetbootin, boot it and install to the EHD from there.

---

### Post by Jimtucket on 2011-04-21
Yeah I'd like the procedure description you can send it in a pm or my 
This site isn't as mobile friendly as others. How large of a flash drive would I need? I have a 4gb ready with me, but id have to get some burnable CDs to make a cd.
As far as external optical cd, I don't, but I do have internal.

---

### Post by lmarmisa on 2011-04-21
Jimi,

do not post your personal email address here. Please edit the previous post and delete this information.

---

### Post by rosencrantz on 2011-04-21
Well, if the internal works, you'll have the least hassle with burning the iso to a disk - don't add it in the file manager, open it with the burning program.
Or, using the flash drive:
Follow the Unetbootin instructions for using your own ISO file:
[http://unetbootin.sourceforge.net/#other](http://unetbootin.sourceforge.net/#other)

Then, follow the instructions here:
[http://www.ubuntugeek.com/a-much-easier-way-to-install-ubuntu-on-a-usb-device-stick-or-hd.html](http://www.ubuntugeek.com/a-much-easier-way-to-install-ubuntu-on-a-usb-device-stick-or-hd.html)

---

### Post by oldfred on 2011-04-21
Herman has a lot of detail on installing to an external drive. Not as complex as it may look as he gives lots of detail & explanation.

Installing Ubuntu in Hard Disk Two (or more) internal or external
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

Basics of partitions:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
Error in below - you cannot make /home NTFS and should not share /home with other installs.
[https://help.ubuntu.com/community/DualBoot/Partitions](https://help.ubuntu.com/community/DualBoot/Partitions)

---

### Post by h3llt0y0 on 2011-04-24
I for one would like a detailed description of its installation on an external hard drive please. I am using the exact same External hard-drive as Jimtucket However I will be dual booting it with another OS after whilst leaving some space for regular memory space. :S

---

