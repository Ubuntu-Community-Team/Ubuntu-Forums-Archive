---
title: "Time to install Ubuntu"
date: 2010-09-29
forum: New to Ubuntu
---

### Post by Benup on 2010-09-29
Received my hard drive today and i have backed up everything i would like to keep, now im ready to install Ubuntu as my permanent OS but im not sure how you do this?

If anyone could tell me or if there is a guide about i would very much appreciate it.

~Ben

---

### Post by GaryTheCat on 2010-09-29
It depends on 'how' you want to install it - on its own or as a dual boot.

I just followed the instructions on [HTML]http://www.ubuntu.com/desktop/get-ubuntu/download[/HTML] with no problems at all.

---

### Post by Benup on 2010-09-29
> **GaryTheCat said:**
> It depends on 'how' you want to install it - on its own or as a dual boot.

I just followed the instructions on [HTML]http://www.ubuntu.com/desktop/get-ubuntu/download[/HTML] with no problems at all.

Sorry if i didnt make it clear but i said as my permanent OS meaning on its own.

thanks for link will go through it now

---

### Post by garvinrick4 on 2010-09-29
[Download Ubuntu | Ubuntu]("http://www.ubuntu.com/getubuntu/download")

---

### Post by mastablasta on 2010-09-29
please follow the link in my signature for a nice guide with lot's of pics. instalation is page 11 onwards i believe).
 
there is also a very good Ubuntu pocket guide book avaulable for free online. Though it is made for 8.04 it is still valid today.

---

### Post by philinux on 2010-09-29
> **Benup said:**
> Received my hard drive today and i have backed up everything i would like to keep, now im ready to install Ubuntu as my permanent OS but im not sure how you do this?

If anyone could tell me or if there is a guide about i would very much appreciate it.

~Ben

Is this a single internal HD?

---

### Post by Benup on 2010-09-29
Yes, i bought a Hard drive today to back up my folders incase i need them again

---

### Post by philinux on 2010-09-29
> **Benup said:**
> Yes, i bought a Hard drive today to back up my folders incase i need them again

Should be dead easy then. Either using livecd or usb.

I would suggest manual partitioning.

Say about 12 gig for /.
Swap well see this. [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
And the rest /home on it's own partition.

---

### Post by amjjawad on 2010-09-29
> **Benup said:**
> Received my hard drive today and i have backed up everything i would like to keep, now im ready to install Ubuntu as my permanent OS but im not sure how you do this?

If anyone could tell me or if there is a guide about i would very much appreciate it.

~Ben

[http://www.facebook.com/pages/Ubuntu-Beginners-Guide-Unofficial/154937727857763](http://www.facebook.com/pages/Ubuntu-Beginners-Guide-Unofficial/154937727857763)

---

### Post by bbqsandwich on 2010-09-29
> **Benup said:**
> Received my hard drive today and i have backed up everything i would like to keep, now im ready to install Ubuntu as my permanent OS but im not sure how you do this?

If anyone could tell me or if there is a guide about i would very much appreciate it.

~Ben

If you have backed your files up onto an external hard drive and don't need anything on your internal drive anymore...

1. Download the Ubuntu .iso -- [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

2. Burn to a CD (if you need a CD-burning program for Windows you can use ImgBurn -- [http://www.imgburn.com/](http://www.imgburn.com/)

3. Restart the computer with the CD in it to boot from the CD. Then the installer will walk you through the everything, it should be easy. Just let it do its thing.

4. If for some reason your computer is not set to boot from CD before booting from the hard drive, you will need to enter the BIOS (hit probably either F2 or F8 when the computer is first starting up, it will say "Hit F2 to enter Setup" or something like that) and change the boot order.

Hope that helps! :)

---

### Post by oldfred on 2010-09-29
Since it is a nice new hard drive, I assume it is fairly large. I agree with philinux on manual partitioning as then you can plan ahead a little more than the simple install that gives you just root & swap. 

Do you plan on lots of data? If so maybe a separate data partition. Do you plan and trying other installs? Then maybe several extra root partitions of 10-20GB for future use. Partition planning requires some idea of what you may want do do for the next few years or until you buy your next drive and then re-plan.

[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)
[https://help.ubuntu.com/community/PartitioningSchemes](https://help.ubuntu.com/community/PartitioningSchemes)
[http://ubuntuguide.org/wiki/Multiple_OS_Installation](http://ubuntuguide.org/wiki/Multiple_OS_Installation)
Partitioning basics with some info on /data older but still relevant
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)

---

