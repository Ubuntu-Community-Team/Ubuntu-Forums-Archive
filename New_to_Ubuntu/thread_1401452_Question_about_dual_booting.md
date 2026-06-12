---
title: "Question about dual booting"
date: 2010-02-08
forum: New to Ubuntu
---

### Post by Lunami on 2010-02-08
Alright, I eventually planned on running this computer dual boot, simply for the fact that not everything runs through Wine so smoothly, if at all. I realise that I may have made some mistakes, but I can fix those as I see them. Now, my question to you all is this;

Can I use Ubuntu (9.10) as the primary OS, and Grub give the boot option to choose Windows being the secondary?

I would like to not lose everything right now, so I'm hoping this will work, seeing as this will be a temporary solution to said problems with wine.

Thanks in advance.

---

### Post by nhasian on 2010-02-08
Sure its much easier to install Ubuntu after windows is already installed.  you can install ubuntu onto a second hard disk or partition and it will present you with the choice to boot between windows and ubuntu when you boot the computer.

If you only have one hard disk and windows is on the entire partition you will need to shrink the partition to make room for ubuntu.

---

### Post by Grenage on 2010-02-08
You can indeed, you'll just need to reinstall grub as the boot loader after the Windows install.

---

### Post by Puck7 on 2010-02-08
Hi.

Yes, you can use ubuntu for primary, and windows as seconday. All you need to do is have windows installed, then install Ubuntu, the installation will detect your windows, and you can choose in grub which one to load.

---

### Post by Lunami on 2010-02-08
Perhaps I worded this wrong?

This computer is already installed with Ubuntu 9.10. It does have a slave drive currently plugged in, which is what I was planning on using to hold Windows. I just wanted to make sure that Windows could be installed second on the disks. I just don't want to lose the files and programs I've installed and configured thusfar.

---

### Post by Puck7 on 2010-02-08
It can, but you will need to reinstall grub, or more like re-configure grub. [This wiki page]("https://wiki.ubuntu.com/Grub2") can help you understand grub2 more.

---

### Post by Lunami on 2010-02-08
So, there is a way to simply reinstall grub afterwards? I'm not proficient enough in the scripts to edit one, and I don't trust my ability to just yet.

---

### Post by Grenage on 2010-02-08
> Perhaps I worded this wrong?

You worded it fine, people have a tendency to reply based on the thread title, not content...

---

### Post by Grenage on 2010-02-08
[http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7](http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7)

---

### Post by Keltenbleich on 2010-02-08
[QUOTE=nhasian;8793008]Sure its much easier to install Ubuntu after windows is already installed.

I wished I had  done it that way, but I installed Windows later on a second hard drive. My BIOS recognizes it as slave device.

I could only boot from the Windows drive changing the boot priority. 

I tried to change my GRUB to tell UBUNTU 9.10 that there is a second hard drive with Windows 7 on it and I have completely ruined it! Seems that my GRUB is gone! 

Now I only can start UBUNTU with the aid of a live CD, choosing the option start from a hard drive. 

I then thought I would like to have my GRUB repaired so that, I could choose to start from one or the other disc drive... I started doing some reading and I finally dared to open a terminal and type: grub-install /dev/ sdb but it says wtf are you writting pal, there isn´t such device, or so... I´m reading now that it is a lot easier to have Windows first and THEN install Ubuntu. So it automatically will install itself in the right way... Seems we only learn through mistakes..!

---

### Post by Lunami on 2010-02-08
Shame that happened to you Kelten.

Thanks for the link Grenege, I'll most certainly look into it. I'll start working on my files and such now, just in case something does decide to go awry during this process, but hopefully, I won't lose the ability to use my slave drive. But, you never know.

Thanks for the tips everyone, I'll be getting right on that now then. Nothing says a better night than spending all of it working on it. Here's some hope, may as well resolve the thread as solved for now. Either way, if it works or not, I will be sure to post about it, and my results, just in case a future user decides to look this up.

> **Grenage said:**
> You worded it fine, people have a tendency to reply based on the thread title, not content...

It's quite alright. Another forum I go to for computer questions does the same thing. The question I used to label the thread was quite general, and perhaps could have had better thought placed into it.

---

