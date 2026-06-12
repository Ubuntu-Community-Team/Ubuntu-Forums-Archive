---
title: "Diagnosis: Bad optical drive or virtualbox shenanigans?"
date: 2010-07-20
forum: New to Ubuntu
---

### Post by new__buntu on 2010-07-20
I recently installed windows xp via virtualbox on my ubuntu machine, and virtualbox claims to be capable of 3D hardware acceleration. From what I've heard 3D hardware acceleration doesn't exist, so I figured I'd put it to the test. I grabbed the nearest 3D program I had and installed in on my virtual machine. After I finished installing LotR:Battle for Middle Earth I reinserted disc one and clicked play. Then I got the attached message box. My optical drive has been a little on the fritz of late, so I'm not sure what exactly to blame for this. Does anybody here have experience which could shed some light on this?

As always, thanks for the help.

---

### Post by jtarin on 2010-07-20
Can you navigate within XP to the drive? MyComputer>DVDdrive
Is it detected by XP? Look in "Device Manager" and see if it is detected there. Did you try another DVD?
Insure you have the correct DVD and it is clean. If you constantly have problems with your optical drive you might try one of the cleaning kits available before you replace.

[3d Hardware acceleration exist. It's very common.]("http://www.gentoo.org/doc/en/dri-howto.xml")

---

### Post by new__buntu on 2010-07-20
> **jtarin said:**
> Can you navigate within XP to the drive? MyComputer>DVDdrive
Is it detected by XP? Look in "Device Manager" and see if it is detected there. Did you try another DVD?
Insure you have the correct DVD and it is clean. If you constantly have problems with your optical drive you might try one of the cleaning kits available before you replace. 

The Device manager and XP detect the DVD, as I said, I used the disc to install the program. I cleaned the CD and blasted the optical drive with canned air and still no dice. To check if the issue was the disc I installed and ran it (techincally I tested Dragon Age, but my computer's been complaining about that one too) on a different computer which had no troubles at all with it.

> **jtarin said:**
> 
[3d Hardware acceleration exist. It's very common.]("http://www.gentoo.org/doc/en/dri-howto.xml")


Heh, I guess that's what I get for not bothering to check the dates on my google search results.

---

### Post by JustinR on 2010-07-21
Try converting the disk to an ISO file and mounting that through Virtual Box.

---

### Post by jtarin on 2010-07-21
> **JustinR said:**
> Try converting the disk to an ISO file and mounting that through Virtual Box.
Good suggestion. Now find a computer that will read it and convert.

---

### Post by new__buntu on 2010-07-21
> **JustinR said:**
> Try converting the disk to an ISO file and mounting that through Virtual Box.

OK, I followed the instructions I found [here]("http://www.cyberciti.biz/tips/linux-creating-cd-rom-iso-image.html") to copy the disc over to an ISO. I tried it first with LotR on a different computer which is running xubuntu via wubi, but after that gave me an input/output error just like my main comp did (each computer will reliably stop dd-ing, but each stops at a different spot) I decided to try it with Dragon Age. I ran it on the computer whose optical drive is in question, but I didn't get any errors (I'm not sure if that actually means anything). Afterwards I mounted the resulting ISO to the virtual machine and cried to myself as I got the same errors from the mounted ISO as from the disc ](*,)(Dragon Age complains about XML files, launches the installer, and then the installer complains about missing files).

EDIT: With all the head-wall smashing that I've been doing I forgot to say thanks. So... thanks for the continued assistance.

---

### Post by JustinR on 2010-07-21
Okay. Well I would use DVDisaster from the Ubuntu Software Center.

It will save the disk to ISO format while checking the disk for corruption errors. It should be fairly easy to use if you don't mind installing it.

So if you choose to install it open Applications > System Tools > Dvdisaster. On the top toolbar that says ISO click the button and choose where to save the ISO file. Select your CD ROM Drive from the list and click the button on the right toolbar that says "Read". This will save the contents of the CD/DVD game to the ISO file.

It reads the CD sector by sector like DD but its visual - it will tell you if there are bad sectors. Also, if the need arises - like if there are bad sectors it has algorithms to try to read the bad sector.

---

### Post by new__buntu on 2010-07-21
There's a tool for everything in the repositories, isn't there? I ran a disc scan of both LotR and Dragon Age and the first one is terrifyingly messed up, but the second read just fine. I have no freaking clue what conclusions to pull from this, except that perhaps some sleep is a good idea.

---

### Post by JustinR on 2010-07-21
Pretty much! :)

So LotR and Dragon Age don't seem like they will be working - but if the disks look fine, if there aren't deep scratches, especially near the inner disk - then it could be the CD ROM drive.

But the last disk you tried seemed to have copied over successfully so I would try to mount the ISO of that disk made from DVDisaster and see if it gives errors.

---

