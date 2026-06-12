---
title: "need bios info"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by Mgs9 on 2008-12-28
I just built a new computer and want to run ubuntu on it.
Now the mother board i have is an ASUS AMD Mobo. The bio disk that i ahve to run for set up is Windos xp/vista geared. What settings do i have to do so i can run Ubuntu.  

I also plan on running vista 64 on a seperate RAID HD that i ordered but i dont have the money for vista OS right now. My question is will the Linux bio set up Interfear with the Vista setup?

I am new to building a comp and setting up bios, so i appoligize if my questions are confusing, and or uneducated. Im hoping that maybe some of you can help me understand alittle.

I appritiate your knowledge and advice.
Thanks'
- Kris

---

### Post by Dedoimedo on 2008-12-28
Linux distributions usually come as live CD. So you can boot from CD and check if the particular distro works well with your hardware.

As a rule of thumb, if you have 4-6GB of free hard disk space and 512MB ram, you should be fine, the more the better.

Regarding the installation: windows (vista) and linux (ubuntu) can coexist together nicely. The bios is not really important for the task at hand. If you place the two operating systems on a single hard disk with different partitions, you will have a bootloader controlling the two, allowing to switch between them. If you place them on separate hard disks, then you will have to use bios to change the boot order between the hard disks.

Hope this helps you with your questions. Ask more if you need.

Dedoimedo

---

### Post by Mgs9 on 2008-12-28
thanks Dedoimedo.

So when i turn my computer on, ( first time it will ever run)do i run my bios disk and set up my HDs and such or can i just put the Ubuntu disk (downloaded) in and run it?

---

### Post by Dedoimedo on 2008-12-28
Are we talking about a computer that has already been setup or one that needs bios configured? If it's already configured, then yes, just pop in the CD. If the bios has CD in boot order before the hard disk, then it will boot.

If you need to configure the bios, then yes please do so first.

Dedoimedo

---

### Post by ajgreeny on 2008-12-28
> If you place them on separate hard disks, then you will have to use bios to change the boot order between the hard disks.
This is not true; you can have all your hard disks and operating systems showing on Ubuntu's grub if it is your chosen bootloader, without a need to go into the BIOS each time you boot the system in order to choose which disk/operating system to run.  I have Ubuntu and windows on sda and Linux Mint on sdb, and can boot to windows or either linux from the ubuntu grub without any problems at all.

Luckily, both ubuntu and mint will find and add other installed linux distros to the new grub menu automatically when they are installed.  Regrettably most other linux distros I've tried are less likely to do that, or at least, they used to be; things may have changed now.

---

### Post by Dedoimedo on 2008-12-28
Did you notice the fact the user is not exactly ubuntu guru and you're already talking about setting up grub to boot from second hard disk... Slow down... let him get things sorted our first, then slowly advance to more complex procedures...
Dedoimedo

---

### Post by halitech on 2008-12-28
setting up GRUB is complex? funny, I found it pretty easy even the first time I installed Ubuntu. Do you want to install grub? yes. Install to Master Boot Record? Yes. Here is a list of your other operating systems, is this correct? Yes. all done.

the fact that he's going to dual boot (by the sounds of it) and installing Vista second will be the hard part of it all even if it is on a seperate hard drive.

---

### Post by BDNiner on 2008-12-28
Well he will have to setup GRUB since he is planning on installing Vista after he installs Ubuntu, and he is planning on setting up his hard disks in some kind of RAID configuration. So it will be a good idea to read up on GRUB to make sure you understand what is going on and there are few surprises when you try to install Vista.

---

### Post by Mgs9 on 2008-12-28
Thanks for the help,
Whats this Brub? am i going to need this if i boot with ubuntu first.

---

### Post by halitech on 2008-12-30
you need GRUB (or something else like it) to take care of booting. Even windows uses a form of a boot loader (granted it only sees windows OSes).

---

