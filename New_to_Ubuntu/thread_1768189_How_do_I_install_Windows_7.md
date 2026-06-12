---
title: "How do I install Windows 7?"
date: 2011-05-26
forum: New to Ubuntu
---

### Post by BlockDudez on 2011-05-26
Some time ago, I installed ubuntu as i was bored of windows 7. Now i have realised that im not able to play all my favourite games. I installed wine, in order to run steam, but the problem is that I cant run black ops. Because of this, i want to install windows 7 again, i have the CD and tried installing it but both partitions are of the wrong format? 

Please Help me, i have been trying four about a week now, but i haven't found anything.

Thanks

---

### Post by fractalman on 2011-05-26
Ok, i'm still a newbie when it comes to linux but i am going to have a guess,

Install gparted in your ubuntu/linux install and then format one of the partitions

Windows 3.x, 95, 98, 98SE, and ME usually use a MSDOS or a VFAT  formatted partition. (VFAT is a replacement file system, which is more  efficient than the older MSDOS one.)


         Windows NT4, 2000, and XP generally use a more advanced file system called NTFS.




i think you can use fat32,  if you format the partition to that first with gparted and then try and install windows


you could try running windows on a virtual box inside ubuntu, but you wont get the full ram of your computer that way.


hope this helps :-)

---

### Post by MSPdwalt on 2011-05-26
When you boot to the windows 7 CD.  Click advanced when it asks you to choose a disk.  It will show you the 2 Linux partitions as un recognized.  This will be your root (/) and swap partitions.  You can delete these and create a new windows partition which will and should be formated NTFS.

DELETING PARTITIONS WILL DESTROY THE DATA ON THEM so be sure you've backed up anything important.

---

### Post by gandaran on 2011-05-26
> **BlockDudez said:**
> Some time ago, I installed ubuntu as i was bored of windows 7. Now i have realised that im not able to play all my favourite games. I installed wine, in order to run steam, but the problem is that I cant run black ops. Because of this, i want to install windows 7 again, i have the CD and tried installing it but both partitions are of the wrong format? 

Please Help me, i have been trying four about a week now, but i haven't found anything.

Thanks
use gparted on ubuntu live cd to create a ntfs partition on the disk then boot the windows 7 cd and point the install to the ntfs partition, you will have to fix the ubuntu grub after installing windows so do some reading about fixing grub, either use [easyBCD]("http://neosmart.net/") on windows 7 or [rescatux]("http://www.bootproblems.com/rescatux/")

edit: this is if you want to dual boot windows and ubuntu, if you just want windows then format the whole disk.

---

### Post by eb3ha4el on 2011-05-26
I'm absolutely rookie as well, but according what you say, you've got 2 partitions
but only OS installed is Ubuntu. so you can install your windows in one of them that doesnt have any OS. (or you can format whole HD and just install win7)

As other one suggested already, install Gparted. 
This program will allow you to partition your hard drive and change its file format.
Since you told us that you cannot install Windows because it tells you file format is wrong, you can use Gparted to change a partition's file format which does not have your Ubuntu - thus the one you're going to install windows 7. 



I recommend NTFS file system. 
reason: [http://en.wikipedia.org/wiki/NTFS](http://en.wikipedia.org/wiki/NTFS)



Strange thing is I belive, when you boot with Windows 7, 
you are going to have an option to change your current partition state of your HD, 
so you don't actually need to go into process of all Gparted thing, 
but just boot with win7 and change file format directly from there.
(you also can format whole HD and install win 7)

---

### Post by MSPdwalt on 2011-05-26
> **eb3ha4el said:**
> I'm absolutely rookie as well, but according what you say, you've got 2 partitions
but only OS installed is Ubuntu. so you can install your windows in one of them that doesnt have any OS. (or you can format whole HD and just install win7)

Even with ubuntu installed you always have at minimum 2 partitions root (/) and swap which serves the same function as a page file in windows.  One of those partitions is NOT empty, they are both critical to ubuntu functioning properly.

---

### Post by eb3ha4el on 2011-05-26
> **MSPdwalt said:**
> Even with ubuntu installed you always have at minimum 2 partitions root (/) and swap which serves the same function as a page file in windows.  One of those partitions is NOT empty, they are both critical to ubuntu functioning properly.



Thanks for correction.
i just think I didn't choose to make a swap space when I installed Ubuntu. I searched wikipedia about Swap space and it seems like making a dedicated space for assisting RAM, correct? It reminds me of Ready Boost of Windows 7 where connected USB flash memory works as secondary RAM. Is Swap space basically the same?


Wikipedia says:
> 
The main advantage of paging is that it allows the physical address space of a process to be noncontiguous. Before the time paging was used, systems had to fit whole programs into storage contiguously, which caused various storage and fragmentation problems.


But i do not quite understand this. What is "physical address space of a process"? In particular what process is it designating? 

and what does contiguous means here? does it mean continued space as a whole? and noncontiguous as chunks?

---

### Post by wildmanne39 on 2011-05-26
> **BlockDudez said:**
> Some time ago, I installed ubuntu as i was bored of windows 7. Now i have realised that im not able to play all my favourite games. I installed wine, in order to run steam, but the problem is that I cant run black ops. Because of this, i want to install windows 7 again, i have the CD and tried installing it but both partitions are of the wrong format? 

Please Help me, i have been trying four about a week now, but i haven't found anything.

ThanksHi, here i a guide in case you want to dual boot and not just get rid of ubuntu. [http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=1](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=1)

---

### Post by MSPdwalt on 2011-05-26
> **eb3ha4el said:**
> Thanks for correction.
i just think I didn't choose to make a swap space when I installed Ubuntu. I searched wikipedia about Swap space and it seems like making a dedicated space for assisting RAM, correct? It reminds me of Ready Boost of Windows 7 where connected USB flash memory works as secondary RAM. Is Swap space basically the same?


No problem,

1st off ReadyBoost is crap..it doesn't do much, it's a waste of a flash drive, just add ram or switch to ubuntu :)

According to this [FAQ]("https://help.ubuntu.com/community/SwapFaq")

Swap is for idle processes that need to stay open, but don't necessarily need RAM.  RAM = FAST Disk = SLOW.  Swap also comes into play when RAM is full and you still need more active memory.

In the windows world the page file is used much the same way, it's just a file instead of a partition.  In windows if you have enough RAM you can turn off the page file.  I think it's 8GB.

Not sure if Linux will work without swap.  I've seen some posts where people with tons of ram trying to get it to work without swap, not sure if they were successful and if that is best practice.



> **eb3ha4el said:**
> 
Wikipedia says:



But i do not quite understand this. What is "physical address space of a process"? In particular what process is it designating? 

and what does contiguous means here? does it mean continued space as a whole? and noncontiguous as chunks?


This part is beyond me...sounds like a question for a developer...

---

### Post by Allavona on 2011-05-26
Think of the pagefile.sys as a swap drive.

It's windows' very own idea! I wonder where they got it from???

Windows is using the NTFS file system. Format to this.

If you only want Windows then use the Gparted Live CD to delete all partitions, including the extended partition around the ext4 Ubuntu and swap partitions. Once all is gone, click on new and format to NTFS. Shut down, Gparted will eject, stick in windows and your on your way.

If you want to keep Ubuntu you'll need to do some resizing to free up space for windows. There are a gazillion guides on how to do this.

---

### Post by pablo180 on 2011-05-26
> **MSPdwalt said:**
> 
Not sure if Linux will work without swap.  I've seen some posts where people with tons of ram trying to get it to work without swap, not sure if they were successful and if that is best practice.

It will work without a swap partition if you have enough RAM however you will need a swap partition at least as large as your amount of RAM for hibernating as that is where the data in RAM is stored when you hibernate.So unfortunately it is best to have swap even if it is never used.

---

### Post by BlockDudez on 2011-05-27
Ok guys, i tried doing what you told me but i think i did something wrong because now when i start the computer it says "reboot and select proper boot device or insert boot media in selected boot device". I have the windows 7 CD in but i dont know how to install.

---

### Post by eb3ha4el on 2011-05-27
> **BlockDudez said:**
> Ok guys, i tried doing what you told me but i think i did something wrong because now when i start the computer it says "reboot and select proper boot device or insert boot media in selected boot device". I have the windows 7 CD in but i dont know how to install.


You have to boot your computer from CD.
You can choose which media to use for booting in BIOS. (or sometimes there is separate menu for this function) When you turn on your computer, the key to enter BIOS menu (or entering separate menu for changing boot media) must be indicated somewhere (usually in the bottom) on the screen first appear (manufacturer logo screen usually). It's F12 I guess.. just try all F keys if you can't find where it is written.

Once you go in BIOS (or the other menu), find boot selection menu and change them to CD. then restart your computer.



Correct me please if I'm wrong.

---

### Post by eb3ha4el on 2011-05-27
> **MSPdwalt said:**
> No problem,

1st off ReadyBoost is crap..it doesn't do much, it's a waste of a flash drive, just add ram or switch to ubuntu :)

According to this [FAQ]("https://help.ubuntu.com/community/SwapFaq")

Swap is for idle processes that need to stay open, but don't necessarily need RAM.  RAM = FAST Disk = SLOW.  Swap also comes into play when RAM is full and you still need more active memory.

In the windows world the page file is used much the same way, it's just a file instead of a partition.  In windows if you have enough RAM you can turn off the page file.  I think it's 8GB.

Not sure if Linux will work without swap.  I've seen some posts where people with tons of ram trying to get it to work without swap, not sure if they were successful and if that is best practice.





This part is beyond me...sounds like a question for a developer...





Thanks. Great reference. Ubuntu documentation always helps me a lot.

---

### Post by BlockDudez on 2011-05-27
> **eb3ha4el said:**
> You have to boot your computer from CD.
You can choose which media to use for booting in BIOS. (or sometimes there is separate menu for this function) When you turn on your computer, the key to enter BIOS menu (or entering separate menu for changing boot media) must be indicated somewhere (usually in the bottom) on the screen first appear (manufacturer logo screen usually). It's F12 I guess.. just try all F keys if you can't find where it is written.

Once you go in BIOS (or the other menu), find boot selection menu and change them to CD. then restart your computer.



Correct me please if I'm wrong.

I have now done what you have said and chosen the CD/DVD but it still says the same thing. Before i installed ubuntu, i had windows 7 installed from the same CD that i am using now. Is it because it was only usable once? Do i need to re-activate it or something. 

If i cant use it again, does anybody know how i can be able to play games on linux? I have tried using wine to open steam but the actual games wont run.

Thanks

---

### Post by neba on 2011-05-27
I use a virtual box on my ubuntu. I am able to play counter strike with out lagging. but this is on an I7. my old 32bit dual core it lagged a lot

---

### Post by eb3ha4el on 2011-05-27
> **BlockDudez said:**
> I have now done what you have said and chosen the CD/DVD but it still says the same thing. Before i installed ubuntu, i had windows 7 installed from the same CD that i am using now. Is it because it was only usable once? Do i need to re-activate it or something. 

If i cant use it again, does anybody know how i can be able to play games on linux? I have tried using wine to open steam but the actual games wont run.

Thanks



No. As far as I know, Windows 7 install CD can be used many times. This is highly likely to be true.

I assume that it might be because of some physical defect on CD itself like scratch. If you have CD/DVD RW, you can make any linux install CD. try installing with it, see if it works. This will clarify whether the problem comes from physical defect on CD itself or not. If both Linux & Windows doesn't work, I assume problem is probably from your mistake. 
 

But it is possible that there are other causes to this problem which is beyond my knowledge. Hope someone else help with this.

Regarding WINE, I don't think it'd work well with gaming as you said early. You can use virtual box if your computer's tech spec is decent. However, for now you will see the same problem occur again.

---

### Post by BlockDudez on 2011-05-28
My computer is an i7 with 16 gb of ram (two times eight) do you think that i can be able to play games like black ops in virtual box without lagging?

---

### Post by eb3ha4el on 2011-05-28
> **BlockDudez said:**
> My computer is an i7 with 16 gb of ram (two times eight) do you think that i can be able to play games like black ops in virtual box without lagging?


well that is certainly decent machine, but as i said, (as far as I know) you will not be able to install Win7 since installing OS in virtual box is essentially the same with installing it as you start your computer.

Do you not see any scratch on your install CD?
Fast way to check defection on your CD is to try your Win CD on another computer. If it works, (if same message does not appear), then problem is in your CD.


Not sure... may be you can download Win7 CD image and install it with your Serial key. If you have 4GB USB/CD/DVD/External HD, you can do it. If you don't have them, you can still intall it within virtual box.


Hope somebody helps.. as i don't know much about computer.
but my guess for your problem is probably in your error/mistake in executing installation process.

---

### Post by Mark Phelps on 2011-05-28
All of you keep saying "CD" -- but the fact of the matter is that Win7 comes on a DVD, not on a CD.  So, if it really IS a CD, not a DVD, you won't be able to install from it.

If it is a DVD, as already mentioned, all you should have to do is boot from it, select an unused area of your drive, and go through the install.

---

### Post by eb3ha4el on 2011-05-28
> **Mark Phelps said:**
> All of you keep saying "CD" -- but the fact of the matter is that Win7 comes on a DVD, not on a CD.  So, if it really IS a CD, not a DVD, you won't be able to install from it.

If it is a DVD, as already mentioned, all you should have to do is boot from it, select an unused area of your drive, and go through the install.


Oh, yes DVD.

but the thing is he has done what you say, and it didn't work.
please help. Lack of knowledge prevents me to help him and also curious how it can be done.

---

### Post by rimibchatterjee on 2011-06-01
@ Blockdudez
Go back to the bios menu on startup after POST and check that your bios really has selected your DVD drive as the first boot device. You might have erroneously exited without saving to CMOS. Then if you are cool with opening your computer case, open it up and check that the IDE cable and power line are securely plugged into the back of your DVD drive, and also the other end of the IDE is securely stuck into your motherboard. If your comp is failing to detect the DVD drive on boot it may be a hardware problem. Your comp is advanced enough not to need additional drivers to run the DVD drive on boot. I know it's weird that the cables would choose to come loose right now, but the number of times i've had comps go weird on me and then found it was a loose cable (after much useless shuffling around with the software) is unbelievable. :-k

---

### Post by Mark Phelps on 2011-06-01
Sometimes, even when you have the BIOS set correctly to select the CD/DVD device as the first boot device, it throws up a line of text on the screen, saying something like "press any key to boot from CD" -- and if you miss that, it skips ahead and boots from the next device, usually the hard drive.

So, check to see if this line of text is being displayed, and if it is, press the space bar -- to select the DVD.

---

