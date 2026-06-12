---
title: "Newby has UBUNTU Questions.."
date: 2011-03-04
forum: New to Ubuntu
---

### Post by tcharmon on 2011-03-04
Have a couple of questions if you guys could help me out..
 
1. My computer currently has WinXP on its primary 80GB hard drive. I have an external 500GB hard drive connected through USB. Is there a way to keep WinXP on my main HD and then install UBUNTU 10.10 on my external hard drive to see how it works on my machine? 
 
2. Will I need to make up a new partition for that distro?
 
3. Will I need some type of dual-boot setup to run WinXP and Linux on my machine at the same time? Will the install take care of that for me? I think I have the UBUNTU 10.10 Live DVD.. I can try the distro before I install it..
 
4. If I have too many problems with the Linux install or it is too hard for me to understand, is there a way that I can undo the installation?
 
5. Is there a definitive place out there somewhere on the internet that I can go to to learn the ins and outs of Linux? I have absolutely no experience with any types of operating systems outside of WindowsXP..
 
If there is someone out there that can help me out, I would greatly appreciate it..
 
Thanks, 
Todd H 
[EMAIL="tcharmon@yahoo.com"]tcharmon@yahoo.com[/EMAIL]

---

### Post by mikewhatever on 2011-03-04
Hi, and welcome to the forums.


> **tcharmon said:**
> 
 
1. My computer currently has WinXP on its primary 80GB hard drive. I have an external 500GB hard drive connected through USB. Is there a way to keep WinXP on my main HD and then install UBUNTU 10.10 on my external hard drive to see how it works on my machine? 

Yes, but that's too much hassle, imo. Just run it from live cd/usb instead.
 
> 2. Will I need to make up a new partition for that distro?
Yes, however, you can also install 'inside Windows', which requires no partitioning.
 
> 3. Will I need some type of dual-boot setup to run WinXP and Linux on my machine at the same time? Will the install take care of that for me? I think I have the UBUNTU 10.10 Live DVD.. I can try the distro before I install it..

Dual booting doesn't mean running at the same time, it means choosing which OS to run at boot. To run two OSs at the same time, you'll need to use virtualization. Not only can, you should try distros before installing.
 
> 4. If I have too many problems with the Linux install or it is too hard for me to understand, is there a way that I can undo the installation?

Yes. You should only use Linux if you want to.
 
> 5. Is there a definitive place out there somewhere on the internet that I can go to to learn the ins and outs of Linux? I have absolutely no experience with any types of operating systems outside of WindowsXP..

There are lots of places, and incidentally, ubuntuforums.org is one of them. Not sure about the definitive one.

---

### Post by tcharmon on 2011-03-04
Have a couple of questions if you guys could help me out..
 
1. My computer currently has WinXP on its primary 80GB hard drive. I have an external 500GB hard drive connected through USB. Is there a way to keep WinXP on my main HD and then install UBUNTU 10.10 on my external hard drive to see how it works on my machine? 
 
2. Will I need to make up a new partition for that distro?
 
3. Will I need some type of dual-boot setup to run WinXP and Linux on my machine at the same time? Will the install take care of that for me? I think I have the UBUNTU 10.10 Live DVD.. I can try the distro before I install it..
 
4. If I have too many problems with the Linux install or it is too hard for me to understand, is there a way that I can undo the installation?
 
5. Is there a definitive place out there somewhere on the internet that I can go to to learn the ins and outs of Linux? I have absolutely no experience with any types of operating systems outside of WindowsXP..
 
If there is someone out there that can help me out, I would greatly appreciate it..
 
Thanks, 
Todd H 
[EMAIL="tcharmon@yahoo.com"][COLOR=#444444]tcharmon@yahoo.com[/COLOR][/EMAIL]

---

### Post by Mudvayne on 2011-03-05
You can just boot from the ubuntu cd and it will load up when finished it will ask if you want to try or install but if your machine is slow it might take awhile to load and it responds slow as well cause its running from your computer memory.

---

### Post by cariboo on 2011-03-05
Please don't create multiple threads on the same subject, I have merged your two threads.

---

### Post by lisati on 2011-03-05
By the way, I'd advise against putting your email address in your posts. This forum is regularly "spidered" by search engines, and you can't be sure who might get hold of it.

---

### Post by tcharmon on 2011-03-05
So, from the replys above, im guessing it would NOT be wise to install Linux to a partition on my external hard drive?    I played around with the Live CD last night and had hard time getting drivers to work and the system to recognize my wireless card..
 
Todd

---

### Post by oldfred on 2011-03-05
Install to USB external would be a bit better than wubi or just testing with liveCD. Did you have a Ethernet connection when testing CD/DVD? It usually after a few minutes offers to download drivers. But even a USB hard drive is not as fast as an internal drive, since the USB port is slower.

Installing Ubuntu in Hard Disk Two (or more) internal or external
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

It is best to partition in advance.

Basics of partitions:
[https://help.ubuntu.com/community/DualBoot/Partitions](https://help.ubuntu.com/community/DualBoot/Partitions)
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

Shared NTFS partition 
[http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/](http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

If you want to uninstall then you have to delete partitions and reformat to NTFS or whatever you want.

---

### Post by candtalan on 2011-03-05
> **oldfred said:**
> Install to USB external would be a bit better than wubi or just testing with liveCD
Be aware that if you do a normal install to an external drive then ok it will run, however, if you then remove the external drive and then try to use the (Windows) system on the computer  it may not boot because the essential boot files have been installed to the external drive.

---

### Post by maqtanim on 2011-03-05
If you are unsure about Ubuntu or just want a test drive, then I would suggest you to install "Ubuntu Inside Windows". To do so 
a. Start your PC in Windows.
b. Insert the CD. Double click on the CD drive in windows.
d. An installer will open. Select the necessary options and install Ubuntu.
e. After completion of the installation reboot the PC. You'll have option to choose the OS from Ubuntu and Windows. 

Try Ubuntu in this way. After using several days, if you donot like it, you can just remove it from the Control panel of Windows.

---

### Post by mikewhatever on 2011-03-05
> **tcharmon said:**
> So, from the replys above, im guessing it would NOT be wise to install Linux to a partition on my external hard drive?    I played around with the Live CD last night and had hard time getting drivers to work and the system to recognize my wireless card..
 
Todd

Some wireless cards don't work out of the box because they require proprietary drivers, but you can't install drivers while running from the cd. That says, the majority of those cards have drivers available from the special Ubuntu repository, so that once Ubuntu is installed, you get a prompt to install the driver. Check what wireless card model you have by running the following command from Applications->Accessories->Terminal. 
```
lspci | grep -i net
```

---

### Post by tcharmon on 2011-03-06
It is going to be hard to get the wireless going on my desktop because i am not going to be able to hard wire internet to my machine. I live in an apartment with a wireless router in an adjacent room. I managed to find some Broadcom B43 drivers on the internet (The UBUNTU Webpage) and I will try to run them on the TryCD to see if that works before I do an install to my external HD. 
 
Thanks again everyone for people who have helped me out..
Todd

---

### Post by I2k4 on 2011-03-06
The best way to experiment is with a "Live" USB drive with "Persistence" - unfortunately the perfectly clear and foolproof Ubuntu instructions here:

[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

don't refer to the "Persistence" alternative at Step 2.  If you don't install "Persistence", you can't save settings and add/delete packages to the basic installation.  You'll find the "Persistence" option on the PenDrive USB installation software.

I'm running the lightweight Lubuntu very happily on a 4GB USB drive with 2GB Persistence.  As with learning Windows, I'm screwing up now and then, and always grateful that there's nothing more to worry about than reinstalling on the USB drive.  When I've worked out which version of Ubuntu and which software works, and the kinks, I'll consider installing to the hard drive, but not before.

---

