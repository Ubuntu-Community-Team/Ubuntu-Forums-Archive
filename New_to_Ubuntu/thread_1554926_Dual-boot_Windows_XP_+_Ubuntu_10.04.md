---
title: "Dual-boot: Windows XP + Ubuntu 10.04"
date: 2010-08-17
forum: New to Ubuntu
---

### Post by veroslav on 2010-08-17
Hi all,

first of all, I would like to say thank you to all of you that are part of this community for providing such a great place for all of us Ubuntu newbies.

I've spent the last few days browsing these forums and searching for the explainations, that would clear my doubts regarding the process involved in installing Ubuntu 10.04, on a PC where Windows XP is already installed. I would like to be able to dual-boot and choose the operating system on the startup.

Now, as I understand, the Live CD provides some great features that enable this, however, I still have some doubts that need to be cleared before I dare to proceed.

First of all, this is my current configuration for the Windows partition:

C drive: Max 103 GB, Available: 46 GB (I am planing to do some cleanup and hope to have as much as 76 GB free space when done)

System Recovery Partition (D drive): Max 7.18 GB, Available: 5.83 GB
    
My HP Laptop specifications:
HP Pavilion dv5187eu
AMD Turion 64 (2.2 GHz)
120 GB Hard Drive
1024 MB DDR
ATI Radeon Express 128 MB DDR

1. Now, as I understand, one can partition a drive either manually directly in Windows or let the Live CD do it during the Ubuntu installation. What are the pros and cons for each method respectivelly? If possible, I would rather let the Live CD do it automatically in order not to mess up things.

2. What partition sizes should I choose for my system for Windows and Ubuntu partitions respectively? I read somewhere that the recommended size for Windows should be at least 20 GB and that is alright I guess. I would like Ubuntu to use as much space as possible, but I don't want Windows to be messed up as a result.

3. How can I be sure that my hardware will be supported? I am especially worried about the network card as I read that setting up the wireless connections might be a tricky thing to do in Ubuntu. My network card is Broadcom 802.11b/g WLAN

4. Are my hardware specs enough for Ubuntu to run smoothly? Will I be able to run Compiz window manager?

5. Is there anything else I should do or take care of before installing?

I know that these are somewhat hard questions to answer, but when answered they will make my life much easier ;)

Thank you in advance.

Kind Regards,
Veroslav

---

### Post by kiridude on 2010-08-17
1. Do the partitioning with the live cd.
2.partition sizes depend on what you want to do. If you do not plan to download or install anything else on windows, then just leave a couple of extra gigs and give the rest of the space to ubuntu.
3. You should not have any problems with your hardware. Most issues are fairly easy to solve.
4.Your specs are fine for Ubuntu. In fact Ubuntu requires significantly less than windows. Compiz will be fine.
5.Just back up your important files.

You will be surprised how user friendly Ubuntu is.

---

### Post by M93 on 2010-08-17
1. partioning in windows using 'wubi' is much easier and safe way to install ubuntu.

2. u need minimun 4-7 GB....but 17-23 is recommended.

3. wireless connection is very easy u just click on 'network connection' on the upper panel, click ur network, enter password and ur connected.

4. yes they are and yes u'll be able.

5. no, nothng else before installing :)

---

### Post by jonnywombat on 2010-08-17
1. My personal choice would be to us the ubuntu installation cd, and select the manual partitioning. Resize your windows partition down, and then create two new ext4 partitions, one mounted as / (root) and one as /home.

2) your would want at least 20gb for each.. but with 120gb i would go for 30gb windows, 30 gb for / partition and the rest for your /home partition.

3) does it work off a live cd... give it a go before you make any chances. If not there are loads of threads on getting broadcom wireless to work.

4) once you get the ATI drivers installed compiz should run just fine

5) have fun, play with a live cd before you commit to change.

---

### Post by silverglade00 on 2010-08-17
1. The LiveCD does an excellent job and has more flexibility to it in my opinion. It also works much faster than the XP one on the machines I used it on. And it can see all of the partitions, not just the FAT32 and NTFS ones.

2. If you have all the programs and files you need in Windows already then splitting the drive down the middle (50GB each) would be good. I tried to make a dual boot computer once and had a lot of trouble becuase I kept running out of room on the Windows side. 

3. This can be the tricky part. After you install, the Hardware Drivers application will run and show you available drivers. These should include your wireless and video card drivers. Just choose the wireless one and click Activate. It will then download... oh wait. Problem. You will need to hook up to a wired connection just this once to be able to do this. After that, you shouldn't have any problems with wireless.

4. I have a similar HP laptop. You will run just fine with Compiz and everything. You might want to purchase another 1GB RAM stick to toss in there to help out your Windows side. You will be much happier with Windows that way and it will help out Ubuntu too.

5. Back up your important files if you can before starting on this just in case. Keep a notebook for changes you make until you are comfortable with the system. After install, you will want to do a full upgrade (it will nag you for it when you boot up) after installing your drivers. Linux is different from Windows. Don't expect to do everything the same way, especially when installing software. You no longer need to scour the net for programs to install. Finally. don't forget to ask questions here. We are here to help! :)

---

### Post by veroslav on 2010-08-17
Thank you so much for your fast and encouraging replies! This community is great!;)

Now I feel much calmer and at ease, I will try my way around the Live CD without installing it first, and check how it feels.

Thanks again.

Kind Regards,
Veroslav

---

### Post by muteXe on 2010-08-17
number 5: defrag your xp, maybe even a couple of times.

---

### Post by AliG112 on 2010-08-17
I found that Ubuntu was slower when installed from wubi than when it was a proper dual boot. The ubuntu installation is very easy to follow and hard to go wrong with. 

Also keep the xp installation disk in case you ever need to recover the windows mbr.    

Good luck! :D

---

