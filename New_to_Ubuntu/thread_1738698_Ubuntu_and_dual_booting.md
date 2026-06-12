---
title: "Ubuntu and dual booting"
date: 2011-04-25
forum: New to Ubuntu
---

### Post by mushypeas on 2011-04-25
Hi

I have a netbook that runs ubuntu fine.  I also have a alptop that runs Windows 7 and I want to install ubuntu too in a dual boot system.

My laptop is 64 bit but when I look at the ubuntu page it says the 32 bit ubuntu is recommended but not the 64 bit.  Are there issues with 64 bit ubuntu?

Also, how do I install as a dual boot? Just install as normal and then follow some options?

---

### Post by Jonker on 2011-04-25
Hi, 

I don't know about the 64-bit problems, but to be on the safe side I would go for the 32-bit one.

Now, concerning the dual boot:
Just choose the options "install Ubuntu alongside an other system" (or something similar) when you need to chose an options in "allocate drive space". The Ubuntu installation will do the partitioning for you.

If you want to partition the drive manually, then I can help you but I would need to know, how big your partitions are (and your hard drive). Or if you feels sure enough to do it yourself, have a look at this :[http://www.linuxbsdos.com/2011/01/28/dual-booting-windows-7-and-ubuntu-10-10/](http://www.linuxbsdos.com/2011/01/28/dual-booting-windows-7-and-ubuntu-10-10/)

---

### Post by grahammechanical on 2011-04-25
Some of us are of the opinion that the reason for the recommendation of 32bit Ubuntu is because 32bit will run on both 32bit processors and 64bit processors. Whereas, 64bit Ubuntu will only run on a 64bit CPU. Some people might not know that their machine has a 32bit CPU and they might blame Ubuntu when the 64bit installation that they are trying fails to work. So, it is considered safer to recommend the 32bit Ubuntu.

My first installation of Ubuntu was 32bit but now I run 64bit. There are no problems. Get a working Ubuntu installation, become familiar with Ubuntu and then expand your experience with Ubuntu.

Regards.

---

### Post by mushypeas on 2011-04-25
Thanks

If I install ubuntu is a new partition (using the installer) and then in October want to update ubuntu, what do I do?

Do I delete the partition with ubuntu and start over? Or just try and re-install ubuntu with the installer and install over the partition containin the old ubuntu?

I know you cna upgrade from within ubuntu but I've been told that's less stable than a clean install?

Thanks

---

### Post by skyzthelimit230 on 2011-04-25
I deul boot between Windows 7 and Ubuntu 64 bit and haven't had any issues finding software or anything of the sory. Ubuntu is snappy, works like it should, and seamless.

Go for the 64 bit, you shouldn't have an issue

---

### Post by collisionystm on 2011-04-25
> **mushypeas said:**
> Hi

I have a netbook that runs ubuntu fine.  I also have a alptop that runs Windows 7 and I want to install ubuntu too in a dual boot system.

My laptop is 64 bit but when I look at the ubuntu page it says the 32 bit ubuntu is recommended but not the 64 bit.  Are there issues with 64 bit ubuntu?

Also, how do I install as a dual boot? Just install as normal and then follow some options?


use 64. 

32 bit says recommended because its part of Caonical's approach to make Ubuntu 'New-people' Friendly.

32 bit will run on anything. 64 will take advantage of your hardware and will be much faster.

---

### Post by stoneage on 2011-04-25
The only potential problem with upgrading is that it will try to retain all your custom configs, so if there is a conflict it might create a problem. I often upgrade rather than reinstall as I use a few custom built applications and it is way quicker for me that way. Never had a serious problem with it.

It is, however still safer to do a clean install as it will use settings that are known to work. 

Just mark the Ubuntu partition as the one you want to install to, and it will be overwritten.

---

### Post by sandyd on 2011-04-25
dp

---

### Post by sandyd on 2011-04-25
> **mushypeas said:**
> Thanks

If I install ubuntu is a new partition (using the installer) and then in October want to update ubuntu, what do I do?

Do I delete the partition with ubuntu and start over? Or just try and re-install ubuntu with the installer and install over the partition containin the old ubuntu?

I know you cna upgrade from within ubuntu but I've been told that's less stable than a clean install?

Thanks
Hold back for 3 more days. then 11.04 comes out.

but then again, when it is first released, it will be more unstable, and will stabilize over time. But then again.... there are always people like me who install the latest beta, rc, and alpha programs on their computer and watch aseverything crumbles around them...... (to be honest, im using kernel 2.6.39-rc4 right now...)

---

### Post by mushypeas on 2011-04-25
Thanks

How much hard drive space will I need for ubuntu? 150 gig sufficient?  I will only use ubuntu for the internet and a couple of programs (SCID for chess)

I have a 500 gighard drive and am using 130 gig of it. I take photos in RAW and use Adobe Elements on Windows 7 (and will continue to do so for photo manipulation) so want to keep most of the partition on the windows side

---

### Post by collisionystm on 2011-04-25
150 is more than enough. Probably to much if you do the majority in Windows.

---

### Post by stoneage on 2011-04-25
> **mushypeas said:**
> Thanks

How much hard drive space will I need for ubuntu? 150 gig sufficient?

Yes. You can install on a 4GB flash drive. :)

---

### Post by oldfred on 2011-04-25
If you think you may want to experiment with new alpha/betas or even other distributions create another 20-25GB partition to use just for that.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
But, I like to have several 25GB roots if hard drive is large enough, I prefer separate /data over /home but that requires a little more configuration after the install to set up.
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

If you install 10.10 use manual install. The buttons on auto install are not labeled correctly and will overwrite your entire system.
Some examples of installs and issues with 10.10:
Issues on dual boot in same drive:
[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)
From kansasnoob:
[http://ubuntuforums.org/showpost.php?p=10145206&postcount=15](http://ubuntuforums.org/showpost.php?p=10145206&postcount=15)
Trust me here! If you choose either "Use entire partition" or "Use entire disc" you are not likely to end up with "Alongside" anything! You will most likely lose the OS and any data contained therein!

Ubuntu Install steps - then choose guide, close to what you want.
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)
Installs with good screenshots/examples:
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

---

### Post by mushypeas on 2011-04-25
So is it better to partition before? I thought I could just partition during the installation?

---

### Post by oldfred on 2011-04-25
You can partition during install. It did not let you create NTFS or do some other partitions before, but they have improved it. Manual install is not that different to partitioning in advance.

---

### Post by mushypeas on 2011-05-02
> **stoneage said:**
> The only potential problem with upgrading is that it will try to retain all your custom configs, so if there is a conflict it might create a problem. I often upgrade rather than reinstall as I use a few custom built applications and it is way quicker for me that way. Never had a serious problem with it.

It is, however still safer to do a clean install as it will use settings that are known to work. 

Just mark the Ubuntu partition as the one you want to install to, and it will be overwritten.

Thanks. So if I have Windows 7 and ubuntu both installed (as I do now), and I insert the USB stick; when I get to the menu saying do I want to overwrite or do I want to install alongside, which do I choose?

If the first, how do I know it won't wipe the entire hard drive? If the second, how do I know it won't install a third partition?

Thanks

---

### Post by mushypeas on 2011-05-02
Also, I guess I don't really need to upgrade until the support runs out.  Will Libre Office still be updated if I stay on Natty for 12 months?

---

