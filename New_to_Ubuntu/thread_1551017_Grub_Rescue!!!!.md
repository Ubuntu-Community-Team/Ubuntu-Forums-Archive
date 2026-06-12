---
title: "Grub Rescue!!!!"
date: 2010-08-11
forum: New to Ubuntu
---

### Post by PumaMania on 2010-08-11
So I got absolutely tired of Linux and I went back to Windows and deleted the Ubuntu Partition. When I rebooted, I get a blank screen that says "grub rescue". I have no access to Windows (XP) or Ubuntu anymore. All I can do is go to that screen, my setup, and my BIOS. (I'm on my smartphone typing this now!) I have a Dell DV051 (E310) Desktop with an "A04" BIOS I believe. I NEED to recover Windows, can anyone help me pleeeease?? Also, I have no access to a Windows restore CD, and My disc drive does not work so CD's/DVD's are out.

---

### Post by theboxseat on 2010-08-11
Very simple
Boot your windows cd
choose keyboard type
DO NOT chose install
Choose RECOVERY options
Have windows reinstall its boot manager, bootloader, etc, by choosing automatic revovery

Oops..sorry..did not read the last part of your post.

No installation disk, no recovery disk, no cd drive.

best possible advise is to take your computer into a shop to get fixed

---

### Post by Nytram on 2010-08-11
Can your computer boot from a flash drive? (It's usually an option in the BIOS)

---

### Post by PumaMania on 2010-08-11
> **Nytram said:**
> Can your computer boot from a flash drive? (It's usually an option in the BIOS)

Yes it can but I no longer have Ubuntu on my flash drive.

---

### Post by PumaMania on 2010-08-12
If I reboot Linux from a Flash Drive, could I possibly fix my computer?

---

### Post by Nytram on 2010-08-12
Yes you should be able to fix your computer with an Ubuntu Live disk. Download the Ubuntu ISO file and write the image to a flash drive (will need 1Gb or more capacity.)

Boot up Ubuntu and and open a terminal:
[B]
sudo apt-get install lilo

sudo lilo -M /dev/sda mbr[/B]

*Note replace **sda** with the name of your hard drive.

---

### Post by abybaddi on 2010-08-13
I've same problem. But when I put ubuntu 9.10, select "try ubuntu", the underscore goes on blinking and blinkling and blinking....
Can anybody help me???

---

### Post by Nick_Jinn on 2010-08-13
How did you delete your partitions? I would use Gparted and delete everything...back up your data to external hard drive. Then use Gparted from live CD (Dont use 10.04 if live version gave you problems....use Knoppix or an older version). Delete everything and everything then start fresh.

Do you have 2 different hard drives like I have? I have had the same problems with grub and none of the solutions I have been given work. I just keep my Operating systems on my small laptop hard drive and use the entire TB desktop hard drive as my data partition. 250 is enough for Windows and Linux, though I wish I had an easier time getting grub to work with various operating systems when its spread across multiple internal hard drives.

---

### Post by abybaddi on 2010-08-13
I cannot even boot.
Tried 8.04 and 8.10 nothing works....
btw i didn't delete any partitions it just went awful on it's own.

---

### Post by Nick_Jinn on 2010-08-13
Have you tried Knoppix? Knoppix worked for me when Ubuntu failed.


You WANT to delete your partitions before installing Windows. Do you use a seperate /data folder or can you delete the entire hard drive and start fresh? Do you only have 1 hard drive?

---

### Post by abybaddi on 2010-08-13
I'll try that.
And yes I have only one Hdrive...

---

### Post by PumaMania on 2010-08-16
Nick_Jinn: I went into Windows and edited the hard drives and just removed the partition I had Ubuntu on. 

Anyways I reinstalled Ubuntu and I have it all working fine now, thank you!

---

