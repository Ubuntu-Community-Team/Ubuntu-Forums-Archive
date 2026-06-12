---
title: "Lenovo Thinkpad w/ i3 380M + Ubuntu 10.4 (complete linux noob)"
date: 2011-02-04
forum: New to Ubuntu
---

### Post by Aldo4343 on 2011-02-04
Ok, well having called Lenovo for the factory restore recovery disk and been told it will be 5 days I may aswell tell you what has been going on.
I received my L412 on 03/feb/2011 with the Win7 Pro 64bit OS + Thinkvantage and all the other funky lenovo shiz thats standard on Thinkpads.
 
First thing I did, I ran the programme to create a factory restore disk. 
 
Second, I connected to inters**t and downloaded some free antivirus/rootkit/malware etc software.
 
Third, I downloaded, converted onto USB stick installer and tried to install Mint 10 (julia). Eeeeeeverything seemed to be goin hunkydory until about 2 pixels at the end of the install progress bar it stopped, permanently. Everything still moved, so the computer itself hadn't crashed, but Mint just refused to finish installing. Incidentally, like many other Thinkpad Mint/10.10 users, the kernel message telling me the CPU was too hot had come up on the fileload feed. The computer was still virtually COLD. I am informed this is not a new problem.
 
Fourth, I did the same with Ubuntu 10.10 (MM) with same result, resulting in me, (for safety purposes originally) having 3 formatted partitions of my 500GB 7,200rpm hard drive + the recovery partition from the original install 'Rescue and Recovery' operation.
 
Fifth, I ran 'Julia' direct from the USB stick to try and use the disk partition tool to safely erase the partition.
 
Sixth, I erased the partitions with the 2 not properly installed linux distros on.
 
Seventh, I clicked what I thought was an 'ok to exit' button. :confused: NOOOOOO!!! ByeBye everything on hard drive including recovery partition. In a totally British way I declare the profanity highly linked with testicles at the top of my voice, prompting funny glares from my housemates.
 
Eighth, tried to use recovery CD to restore windows. Apparently that disk is worth **** all, it doesn't have windows recovery information on it, just the Lenovo Utilities recovery information, for installation on windows which is no longer on the computer. 
 
Ninth, in order to last the 5 days atleast I am running Ubuntu 10.4 which installed very smoothly (congrats to developers) and is running very smoothly. I am considering staying on 10.4 for a good few months with windows reinstalled once the disk gets here on a separate partition.
 
What I'd love some lovely person to do:
**Tell me how (in 10.4 ideally) to create a partition I can run and have the windows install on, while keeping the 10.4 partition separate and also having my files on a separate partition so they can be accessed by both OS's without threat to the stability. **
**Also, please sort that damn bug out that wrongly tells the install kernel my CPU is overheating so that 10.10 can be installed sweetly :)**
 
(Before anyone suggests leaving Micros**t by the wayside, my University insists on files being in word format and for some reason everything from open office seems to alter in format when it is put onto the Uni computers.) Alas, windows is necessary here. I will write in open office, format in MSoffice, save as new MSoffice document, then send to uni printers over network. 
 
Many Thanks
 
Alex

---

### Post by TeoBigusGeekus on 2011-02-04
In order to create new partitions, boot up with a live cd and open gparted
```
gksu gparted
```
If it isn't in the live cd (can't remember), simply install it
```
sudo apt-get install gparted
```

Once in gparted, create a partition for win7 (I'd give it about 50gb but that depends totally on you) and then another partition, as large as you want, for common storage of linux+windows. In order to be able to access this data partition from both systems, format it as ntfs.

Keep in mind, that when you install windows AFTER you've installed ubuntu, your grub2 bootloader will be overwritten by the windows' one. You then have two choices:
1)Reinstall ubuntu.
2)[Fix grub.]("http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html")

As a personal advice to you, I recommend staying away from Maverick, but it's just my opinion.

---

### Post by cchhrriiss121212 on 2011-02-04
^ That pretty much covers it, but on this note:
> Once in gparted, create a partition for win7 (I'd give it about 50gb but  that depends totally on you) and then another partition, as large as  you want, for common storage of linux+windows. In order to be able to  access this data partition from both systems, format it as ntfs
You can just have one partition, Ubuntu can recognise the Windows partition directly, so there is no need for an extra shared data partition.

And if you only need Windows for Word, WINE or Virtualbox may be a good solution.

---

### Post by Aldo4343 on 2011-02-04
Sweet cheers guys.

Incidentally, anyone know of a good beginners tutorial to using linux systems, executing commands etc? (eg: how to correctly execute *.exe for a given file)

Alex

---

### Post by grey.skylark on 2011-02-23
Hi Alex,

I found this guide helpful in getting used to linux:[URL="http://files.ubuntu-manual.org/manuals/getting-started-with-ubuntu/10.04e2/en_US/screen/Getting%20Started%20with%20Ubuntu%2010.04%20-%20Second%20Edition.pdf"]
http://files.ubuntu-manual.org/manuals/getting-started-with-ubuntu/10.04e2/en_US/screen/Getting%20Started%20with%20Ubuntu%2010.04%20-%20Second%20Edition.pdf[/URL]

Best,
Sarah

---

