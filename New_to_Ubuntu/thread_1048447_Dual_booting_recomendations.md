---
title: "Dual booting recomendations"
date: 2009-01-23
forum: New to Ubuntu
---

### Post by psychobot on 2009-01-23
I am new to Ubuntu and have a few questions regarding the different distributions. I apologize in advance if I posted this in the wrong section and kindly ask for this thread to be moved to the proper forum if it is.

First of all, I would like to know if there is a difference between 8.04 long term support and 8.10. I've always thought it to be better to go for the newest version but the 8.04 has a longer support life. So any guidance as to which version to take will help me a great deal.

Second, my computer is capable of handling a 64 bit operating system. Is there a benefit of the 64 bit distros over the 32 bit? In my past experience with XP I've had tough times with software support even they had the wow emulator to allow 32 bit programs in a 64 bit environment. Do the 64 bit distros have such an emulator or is it a strict 64 bit environment? I only use 2GB of ram so I don't need the 64 bit os for memory support. I guess my main question is should I use a amd64 distro or a i386 distribution?

My third and last question involves installing it. Currently I am running XP pro 64 bit. I want to dual-boot XP with whatever Ubuntu distro I am recommended. I have 2 hard drives and am able to set the two operating systems on the faster of the two with my swaps and documents on another. Does Ubuntu run better in that way like Windows? Am I able to setup a swap partition on the second drive to be used by both windows and Ubuntu? What would be the best setup to use with this kind of scenario?

I thank you all in advance and apologize for being such a newb.

---

### Post by russu52 on 2009-01-23
i am using ubuntu 8.10 32 bit version on a 64 bit machine and it is working fine. you can install ubuntu on the second drive, and then you choose which os to use when booting. i had vista and ubuntu 8.10 as dual boot.

---

### Post by overdrank on 2009-01-23
> **psychobot said:**
> I am new to Ubuntu and have a few questions regarding the different distributions. I apologize in advance if I posted this in the wrong section and kindly ask for this thread to be moved to the proper forum if it is.

First of all, I would like to know if there is a difference between 8.04 long term support and 8.10. I've always thought it to be better to go for the newest version but the 8.04 has a longer support life. So any guidance as to which version to take will help me a great deal.

Second, my computer is capable of handling a 64 bit operating system. Is there a benefit of the 64 bit distros over the 32 bit? In my past experience with XP I've had tough times with software support even they had the wow emulator to allow 32 bit programs in a 64 bit environment. Do the 64 bit distros have such an emulator or is it a strict 64 bit environment? I only use 2GB of ram so I don't need the 64 bit os for memory support. I guess my main question is should I use a amd64 distro or a i386 distribution?

My third and last question involves installing it. Currently I am running XP pro 64 bit. I want to dual-boot XP with whatever Ubuntu distro I am recommended. I have 2 hard drives and am able to set the two operating systems on the faster of the two with my swaps and documents on another. Does Ubuntu run better in that way like Windows? Am I able to setup a swap partition on the second drive to be used by both windows and Ubuntu? What would be the best setup to use with this kind of scenario?

I thank you all in advance and apologize for being such a newb.

Hi and welcome, I would suggest Hardy 8.04 as it is LTS. If you like the bleeding edge and need support for your devices then you may need 8.10.
Just try the live cd before install.
As for the 64bit I would save if your system can support it then use it. I have used the 64bit Ubuntu since Feisty 7.04 and have not looked back. :)
Lastly I am moving this to ABT.Absolute Beginner Talk :)

---

### Post by TJCIB on 2009-01-23
I would also suggest going with 8.04 if you're new.

I can't speak about 32 vs. 64 bit...I have no experience.

But dual booting I can offer you my setup.

I have two hard drives. 
HD 1 is XP
HD 2 is Ubuntu (as well as the swap partition)

Since Ubuntu has NTFS support, you can read all of your files from the XP hard drive with no problem.

If you want to access your Ubuntu files from XP, you will need to set up a separate /home partition (which could be on either of the two drives) with the FAT file system (to be compatible with both).  That is done through the "manual" option when it comes to the partitioning section of the installer.

Does this sound like what you were thinking?

---

### Post by TJCIB on 2009-01-23
Here is a gruelingly thorough walk through.  If you wanted to do two hard drives, you would need some modifications to it.

Feel free to ask for help.

[http://users.bigpond.net.au/hermanzone/p3.htm]("http://users.bigpond.net.au/hermanzone/p3.htm")

---

### Post by psychobot on 2009-01-24
Thanks for your replies. I've decided I'm going to use 64 bit Intrepid. 

Now back to a previous question. Currently I have XP on the faster HDD with my documents folder and swap file on my second HDD. I was told the OS would run better that way being it's able to simultaneously read both drives instead of having to wait in que to access the swap/docs. Is it possible to setup **HDD 1- Windows/Ubuntu HDD 2- Windows Swap/ Ubuntu Swap/ Windows Documents/ Ubuntu home folder** so that both os can simultaneously access system files and swap?

If my logic is foul with the above mentioned setup, can you advise me to the best way to utilise both hard drives?

Also, if I set my swap and /home on the separate HDD will Ubuntu automatically mount the drive or will I need to mount it manually each time I boot?

---

### Post by alexis777 on 2009-01-24
I think is possible, but maybe will you need to redistribute your partitions in something like:
HDD1: ntfs - ext3
HDD2: swap - ntfs

So you can mount your home directory in the HDD2 ntfs partition, and use it also to keep your windows swap file with your "My Documents" folder. You can use the windows disk manager software to organize your partitions. Maybe you even can use the option to run ubuntu from a windows folder, if you don't want to change partitions. Whatever the configuration you use, if you set it from the Ubuntu install interface, it will configure grub properly to give you dual boot.

---

### Post by psychobot on 2009-01-26
Thanks for the info. Will there be any performance decrease by mounting /home to a NTFS partition? Also, would there be much benefit other than organization to mount the /home to the second hdd? the reason I ask is my primary drive is a 300GB velociraptor and my second is just a average joe 80GB sata II drive. Do you think it would be better to keep /home and my docs on the faster drive while putting the two os swaps on the second drive?

once again, i apologize for being a noob.

---

### Post by -kg- on 2009-01-26
> **psychobot said:**
> Thanks for the info. Will there be any performance decrease by mounting /home to a NTFS partition? Also, would there be much benefit other than organization to mount the /home to the second hdd? the reason I ask is my primary drive is a 300GB velociraptor and my second is just a average joe 80GB sata II drive. Do you think it would be better to keep /home and my docs on the faster drive while putting the two os swaps on the second drive?

once again, i apologize for being a noob.

It really depends on what you are doing with your computer.  If you are running memory and disk intensive software, like video editing or CAD, then you might realize some speed improvement.  If not, the speed improvement would likely be negligible.

I have heard that Windows runs slightly better if it's paging file is put on a separate hard drive, the theory being that the drive with the paging file can be accessed nearly simulaneously as the main hard drive, instead of the heads bouncing back and forth on the same hard drive, and I would assume the same would be true with the Linux Swap file.  I have my Windows installations set up in such a manner, since Windows seems to always use the paging file to one degree or another.

But under Linux, if you don't use memory or disk intensive software, and if you have a fair amount of RAM (and 2 GB is a fair amount for most applications), the swap file will almost never be used, and therefore, little to no gain in speed.  Under these circumstances, the only thing swap would be used for is hibernation (Windows uses hiberfil.sys), with still no gain in speed (maybe a *slight one* when coming out of hibernation).

The following page gives a good description of how the swap file is currently used in Linux:

[https://help.ubuntu.com/community/SwapFaq]("https://help.ubuntu.com/community/SwapFaq")

This, of course, is just my opinions and observations on the subject.

---

