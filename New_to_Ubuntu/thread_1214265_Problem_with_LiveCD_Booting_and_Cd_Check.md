---
title: "Problem with LiveCD Booting and Cd Check"
date: 2009-07-15
forum: New to Ubuntu
---

### Post by Ergo0100 on 2009-07-15
Hi!

I'm new in Linux and I want to install Ubuntu 9.04 in my VERY old computer. I have downloaded Ubuntu from Torrent two times. For testing them I first use them in a virtual machine in my laptop (yes, i have a desktop and a laptop). I have booted correctly and verified that there were no errors in the ISO image. Then I have burned the image in a cd using PowerISO. I have asked PowerISO to verify the writtend data after the burning. In both it sent me a (in spanish) "Error de redundancia Ciclica". I ignored it and stopped the verification. Then I used the CD in my laptop and asked him to boot. Nothing happened. The Cd started running and the system hanged on. The up and down buttons didn't worked!!! I rebooted and tested the cd error check but it hanged on again... I don't know what to do. I'm now downloading Ubuntu but from the servers. Yes i know that it's slow but maybe it can work.

Can anybody help me please? 

Greetings!

Ergo0100

PS: Sory for the english! I'm from Chile!

---

### Post by NightwishFan on 2009-07-15
Try to burn the cd using Infrarecorder. I have found it to be much better quality. Please note, Ubuntu should be run with more than 256mb of ram. I recommend 512mb. If you have less, then you should look at Xubuntu or even Puppy Linux (for under 128mb)

If your keyboard does not want to move, then try to use a ps/2 port keyboard until you get the system up.

Infrarecorder:
[http://infrarecorder.org/](http://infrarecorder.org/)

Puppy Linux:
[http://www.puppylinux.org/](http://www.puppylinux.org/)

---

### Post by Ergo0100 on 2009-07-15
Thanks!

I'm going to try now. I use a PS/2 keyboard always!

Also I want to report that in the cd integrity check there were no errors found but when i boot the livecd or install it, the systems halts.

---

### Post by Jazzy_Jeff on 2009-07-15
We need to know what computers you are using and the specs. We need to know the amount of ram and your cpu as well.

---

### Post by Ergo0100 on 2009-07-15
I'm using a AMD Athlon T-Bird with 1.20 Ghz and 256 MB RAM. The graphic card is a Inno S3 Savage 3D 2000 with 64 MB. I have tried with the 9.04 version of ubuntu (both desktop and altenate) and the alternate went further than the normal. The normal didn't started the installation and the alternate copied some files and then many corrupt files. I have only one cd left (maybe there's another) and I want to install ubuntu in my PC. I can also be Xubuntu.

Please help!

---

### Post by scrooge_74 on 2009-07-15
Try to burn it at the slowest possible speed

---

### Post by Ergo0100 on 2009-07-15
I have also tried that and... wait... I have tried it with a normal installation... not an alternate... CD that menas that I can... OMG!! Thanks to all of you guys! You really helped me!!!! i I have añy problems I will write again!!!

Thanks!!!

---

### Post by Ergo0100 on 2009-07-15
Ok. It's me again. I'm now using x1 recording, ubuntu 8.04.2 alternate i386 and with InfraRecorder (thanks NightwishFan for the tip) but i have a doubt. It's my last CD available and i can't go and buy more. What type of writing method i have to use? the SAO, TAO, TAO without pauses or raw96r? Please answer soon!!!!

---

### Post by BinaryFeast on 2009-07-15
I have similar symptoms on an old PC (Pentium II, 96MB RAM). It won't install any Linux whatsoever (tried a dozen distros). It won't even boot DSL properly. The thing is, after booting for a few minutes, it either hangs or ends in a kernel panic.

However, I may have identified the problem. You should check your memory with memtest86 (comes on the ubuntu cd); the results for me is that it lists every single memory address with an error. Now, this is a bit strange since it ran Windows 98 just earlier (before I wiped the HDD to install Linux), although with frequent bluescreens during file transfer operations (which could have been the result of damaged hardware). One would think it could at least install an operating system. 

So, yeah. Check your memory and avoid LiveCDs for now.

---

### Post by scrooge_74 on 2009-07-16
Those old laptop I think run better on old plain Debian

---

### Post by LewRockwell on 2009-07-16
1996 Gateway 2000 Solo Laptop Loves Damn Small Linux but Puppy Linux was a dog!

specs:

150MHz MMX Processor

224MB ram

USB1 ports

cdrom drive

floppy drive

3GB hard drive

PCMCIA 10/100 Ethernet LAN card

(BIOS will boot from cd-rom drive but not USB ports)

CMOS battery expired, difficult to replace so we do without...

.

---

### Post by NightwishFan on 2009-07-16
In infrarecorder the default settings are normally very good.

However on 256mb of ram you may want to go with Debian or Puppy, as that is pretty trim. Ubuntu should 'work' though.

If it is your last CD then, good luck. If you get hard lockups there may be a kernel parameter you can pass. Perhaps try a new thread for help on that.

---

### Post by CompizDoDo on 2009-07-16
i agree with the first reply infra-recorder is the best:D

---

### Post by Ergo0100 on 2009-07-16
Thanks to all of you!! I have used my last CD burning Xubuntu 8.04.2 alternate i386 at x4 (the minimum) but it have failed... Now I have founded 5 CD's more!!!! What do you recommend me? Ubuntu? Xubuntu? or another distro? and what type? alternate or dektop?

Thanks!

PS: I'm doing now a memtest. When it finishes I'll put the results...

---

### Post by Ergo0100 on 2009-07-16
It is normal that some patterns are very slow and other very fast?

---

### Post by NightwishFan on 2009-07-16
Memtest does not 'finish'. It will go until you quit it. However, if it IS a memory problem, we really cannot resolve it, so I recommend you skip that step.

For 256mb, perhaps try Xubuntu Hardy Heron (8.04.2). It is more stable and you may have more luck. It may also be a bit lighter.

[http://www.xubuntu.org/get](http://www.xubuntu.org/get)

(The lower release is hardy, pick a mirror near you)

EDIT: If you want to use the newest release, perhaps we can help you more. Try booting the live CD, with these options:

When at the main screen, press f6, then escape, and you should see a bunch of text near the bottom. Delete the 'quiet' and 'splash' options, and push enter. It may tell you what is wrong.+

---

### Post by Ergo0100 on 2009-07-16
OK! It doesn't have errors!! I'mnow installing Xubuntu 8.04 in my USB and then (if it fails) I'll use a CD. Do you have a special procedure on how to burn and install correctly Xubuntu on a CD? because i don't want to spend 5 CD's more. Also I'm going to travel for one week. I need to install Xubuntu, Ubuntu or Whatever in my PC today before 3 PM (GMT -4)

Please help me! Im completley noob with linux!

---

### Post by NightwishFan on 2009-07-16
It should be fine, there is no special way. Just choose burn iso to cd, and use the slowest speed. There are simple instructions here.

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

When the iso is burned, simply insert it in the drive and reboot. I recommend you use the Live CD, and not alternate. The first option should cause the live image to boot.

If it freezes, yet keeps trying (you can hear the cd keep loading), you may not have enough RAM.

If it simply crashes, then you may have an odd hardware issue.

If either, perhaps try Debian Linux.

---

### Post by Ergo0100 on 2009-07-16
OK! thanks! now i'm downloading and then making the USB booteable with UNetbootin and burning at the lowest speed Xubuntu 8.04 Desktop i386. I hope all can go good and I can install it!! i have another question. When i choose in mi BIOS (Award BIOS) the booting order, i have two USB obtions: the USB-FDD and the USB-ZIP. What type i have yo use and in what format have to be the usb? i have it un FAT32.

---

### Post by Ergo0100 on 2009-07-16
It seems that Xubuntu is burned correctly! But when i try to put the LiveCD the status bar finishes and the monitor goes off... and then nothing happens... I'm now doing the integrity check and then install it!

---

### Post by Ergo0100 on 2009-07-16
I have made the integrity check and there were 32 corrupt files!!!!!!! now i have used the live cd without the quiet and spalsh settings and it shows me mani I/O Errors!!!!!! also some SQUASHFS errors and Buffer I/O Errors!! Please Help!!!!!

---

### Post by scrooge_74 on 2009-07-16
Seems you need to find a better way to burn those CDs

---

### Post by NightwishFan on 2009-07-17
Make sure the CD/DVDs you use are clean and unused. Burn it at 2x speed not 1x. I/O errors means the CD is burned wrong, and if you fix that you should be fine. Try a few different burners, and good luck!

---

### Post by Ergo0100 on 2009-08-08
Problem solved! It wasn't the writer! it was the CD drive of my desktop!

---

### Post by NightwishFan on 2009-08-08
Congrats, glad you figured it out. Good luck!

---

