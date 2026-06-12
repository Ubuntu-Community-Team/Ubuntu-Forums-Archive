---
title: "unsure which distribution of Linux to go with at this point, if any"
date: 2011-03-17
forum: New to Ubuntu
---

### Post by lewis-jones on 2011-03-17
I recently discovered an old Compaq Presario with about 224 Mb's of RAM in the closet. Ran it in safe mode after a normal boot resulted in a loading screen for 5 minutes. Downloaded some malware protection and removed what I could, but whatever it had on there got past the registry and is beyond retrieval. So Windows is done. I'm figuring at this point that a free OS sounds a hell of a lot better than attempting to pay for or pirate a copy of windows. Plus, with such suboptimal RAM I'm beginning to believe a more streamlined OS actually sounds like a great idea. Linux, Debian, and more specifically Ubuntu and Xubuntu drew my attention. I downloaded the latest ISO of Xubuntu along with the Universal USB Installer to turn my flash drive into a live bootable version of a startup cd and ran a boot manager, because my laptop didn't support booting from USB, only ... the iso doesn't work. There's some bug affecting installation that's inherent to the source file, making my laptop freeze. Just to be sure this was actually what I was experiencing I used a utility to check the hash code of my copy of xubuntu with the source file on the xubuntu website. They matched. The solution I'm offered since I can't get a copy of the full OS that will work is to go with another, smaller version of xubuntu and download any components or firmware I need during the installation. I try this, reformat the flash drive to boot the new OS and load it. After a few steps I'm prompted to set up a DHCP server address for the internet manually because it can't detect anything to auto configure. Now I exclusively borrow internet or this wouldn't be a problem. I used the command prompt to find my current IP info and copy it, thinking I could just supply that and be done. As it turns out, these distributions of linux don't come loaded with a driver to run the wireless adapter within the laptop, so the numbers for my neighbors' router were irrelevant and my only option is now to maintain a wired connection throughout the install. Which as I've just alluded to, is not possible.
 
After my third day of this (download speeds have not proven desirable with concurrent malware processes hijacking windows), I'm at a complete impasse. I can either download an older ISO without the bug and attempt to install that, choose some other distribution of linux less apt for running on a slow machine, or give up and reinstall windows. Any thoughts?

---

### Post by Dutch70 on 2011-03-17
Welcome to UF lewis-jones

I don't think that computer is going to run Xubuntu very well anyway. You should try Lubuntu. Just as Xubuntu is lighter than Ubuntu, Lubuntu is lighter than Xubuntu & will run much better with your hardware. It's still a very nice OS. 

Not to steer you away from the buntu family, but LXDE, Peppermint One, Peppermint Ice & of course Puppy are also good alternatives. 

Good luck

---

### Post by nothingspecial on 2011-03-17
My first thought is that you shouldn't be borrowing your neighbours connection without permission. [-X

My second thought is that you should look at this blog about running linux on old computers.

[http://kmandla.wordpress.com/](http://kmandla.wordpress.com/)

---

### Post by sidzen on 2011-03-17
lewis-jones says,
"I recently discovered an old Compaq Presario with about 224 Mb's of RAM . . . Any thoughts?"

Begin by downloading an early version (1.3.5) of SystemRescueCD at sourceforge ([http://sourceforge.net/projects/systemrescuecd/files/sysresccd-x86/1.3.5/](http://sourceforge.net/projects/systemrescuecd/files/sysresccd-x86/1.3.5/))

Next, either a) get UNetbootin from the same source ([http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)) then make a bootable small USB Flash Drive using UNetbootin and the sysresccd-x86-1.3.5 ISO file, both just downloaded or b) download the ISO file and burn it to a CD at no more than 8X

Set your system BIOS to boot to either USB or cdrom first, then boot to your new System Rescue CD USB stick or CD.

After it boots, SysRescCD wants you to hit defaults (hit Enter) a couple times. When you end up at the multi-colored prompt on the page asking user to enter either "startx" or "wizard," type in 

[PHP]dd if=/dev/zero of=/dev/sda bs=4096 conv=notrunc,sync[/PHP]

After it finishes (it will take some time, depending on hdd size), a message of about four lines appears giving some statistics saying 'no more space . . . xxxMB/s')

type in at the same prompt the desired "startx" and Enter.
This brings up the XFCE mouse then a yellow-colored terminal.
In the yellow-colored terminal, type the command "gparted".

Partition your hard drive. If you don't know how, use the Slackware basic strategy of 
one partition for root ( / ) -- 10GB (or to copy DVDs use 15GB), use ext4 file system;
one partition for swap -- one gig should do; and
one partition for /home -- most or all of the remainder 
(keep some unallocated should you desire to expand one or add a partition later).

NOTE: in the OS install, when partition dialog pops up, choose Manual and then either Edit or Modify for each partition created previously with gparted, telling it to yes, use the partition, format it using ext4 file system for / and /home; swap should be okay. So, write down how you partition, noting /dev/sda1 or sda2 or sda3, size, label (if any), and file system (ext4).

It's easy.  When done partitioning, simply enter the command "init 6" in the yellow terminal window and reboot follows.  (This would be the time to place your install disk into the tray, just before typing the reboot command, and begin the install process)

As far as a distro goes, ubuntu won't work with so little RAM, and 10.10 dfinitely won't work because the kernel does not support your old pre-P4 processor. (You don't specify your system specs, so it is an educated guess that, with so little RAM, you have a PIII at best).  Is it something like this? 

[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00023777&lc=en&cc=us&dlc=&product=326349](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00023777&lc=en&cc=us&dlc=&product=326349)

I would go with antiX or Crunchbang-10-i486 for a Debian-based distro; something like absolute for Slackware-based.  A Debian distro allows usage of [smxi]("http://smxi.org/"), which is a very handy script for modding your initial install.  I think you will find either Debian-based distro easier to work with than absolute for wireless, but wireless is the bugaboo for Linux in general, at the present time.  

Best wishes!

---

### Post by Dutch70 on 2011-03-17
> lewis-jones says,
"I recently discovered an old Compaq Presario with about 224 Mb's of RAM in the closet
 . . . Any thoughts?"

In who's closet??? #-o :lol:

---

### Post by coolbrook on 2011-03-17
> **lewis-jones said:**
> I recently discovered an old Compaq Presario with about 224 Mb's of RAM in the closet.

[VectorLinux Light Edition.](http://vectorlinux.com/products)

> **sidzen said:**
> 
10.10 dfinitely won't work because the kernel does not support your old pre-P4 processor.

It does. 

> for a Debian-based distro

...[wattOS.](http://www.planetwatt.com)

---

### Post by Old_Man_Unix on 2011-03-17
Definitely Lubuntu.  It's specifically designed for low-spec hardware and it is cool distro in its own right:cool:  And you'll still be in the Ubuntu family.

Ubuntu itself will not run on that machine without considerable tweaking.  Xubuntu is not really a lightweight distro at this time. 

BTW, I lost a black  wool cap about six years ago - you didn't happen to find one in that closet?

---

### Post by mastablasta on 2011-03-17
hello, can you tell which model you have? these older maschines can't boot form USB and you will need to create a liveCD to test it.
 
I am also using old Compaq Presario with 224Mb ram (the rest is graphics card) and i got best results with Ubuntu.
 
XFCE - was crashing, Lxde (lubuntu) used way too much baterry.
 
So i went with Ubuntu 10.04 . BUT i have only 2 virtual desktops, no background immage and theme is clearlooks and no desktop effects. works quite fast. boot is 1 minute. LXDE had faster boot but as already said baterry consumtion was too big. anyway it all works really nice, everyhting out of the box and GNOME is rich in programmes and applications i need/use.
 
you oculd try the latest Ubuntu or Linux Mint LXDE. LinuxMint LXDE is much more feature rich, however i found it slower than Ubuntu (at leats previous version). But again i haven't tried the latest yet that just came out recently.

---

### Post by lewis-jones on 2011-03-17
I love the Ubuntu community; these answers were far more in depth than I expected. I've got a lot of food for thought. Thank you! :P
 
I didn't find a wool hat in there lol. I did find some wool socks though!

---

### Post by crispy_420 on 2011-03-17
I place my vote for Bodhi Linux. It is new (I think?) and should work decently on old hardware too. 

[http://www.bodhilinux.com/](http://www.bodhilinux.com/)

Or there is always the option of a server install to work on some commandline skills.

---

### Post by Dutch70 on 2011-03-18
> **crispy_420 said:**
> I place my vote for Bodhi Linux. It is new (I think?) and should work decently on old hardware too. 

[http://www.bodhilinux.com/](http://www.bodhilinux.com/)

Or there is always the option of a server install to work on some commandline skills.

+1 for bodhilinux

---

