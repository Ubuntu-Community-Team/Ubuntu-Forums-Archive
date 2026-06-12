---
title: "new install 10.4 won't boot"
date: 2010-07-02
forum: New to Ubuntu
---

### Post by Madds on 2010-07-02
Hi - I'll start with an apology for being a clueless newbie... I've just tried 3 fresh installs (on 2 different hdd) of 10.4 on a fairly old pc without a cd drive, using a bootable pen drive. LIVE runs fine, and after installing I can reboot to the hdd provided I leave the pen drive in and select 'boot from first hdd'. If I remove the pen drive I can't boot, I get a no system disk error. I think maybe I should be installing/repairing a boot manager, but don't know what or how... Please help - I'm so stuck!

---

### Post by -humanaut- on 2010-07-02
Where are you installing Grub? Try installing it to the MBR also what kind of message do you get when you bootup with out the pen drive? and from the live media open a terminal and post the results back of this
cat /etc/fstab

---

### Post by Madds on 2010-07-02
Hi - thanks for helping! The error I get is: 'disk boot failure, insert system disk and press enter'. I haven't installed Grub unless it was done automatically during the install. I'm on a win pc right now (sorry!) - I'll reboot the other one and try the terminal command you suggest, then reply again from that one!

---

### Post by Yvan300 on 2010-07-02
Most likely GRUB has been installed on the pendrive instead of the flash drive. I don't know how it happened, but that might explain why you could only boot fine while the flash drive is connected to your pc. What i suggest you do is to install ubuntu and on the last step of the installation process, it asks you where you wish to install grub, select hd0.0 and that should do it...... not sure if it will be hd0.0, but you get the idea!

---

### Post by Madds on 2010-07-02
I'm on the ubuntu live cd nw, and what I get is this:

ubuntu@ubuntu:~$ cat /etc/fstab
aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda5 swap swap defaults 0 0

---

### Post by Madds on 2010-07-02
Hi Yvan - I don't think it asked me where I wanted to install Grub! Is there a way of doing it from where I am now, ie running the live cd from pendrive? BTW it's just a single boot, so I suppose hd0.0 would be right.

---

### Post by Yvan300 on 2010-07-02
On the last step, where the button is marked as "install", there is a advanced button, click that and it would allow you to choose where to install grub.....

---

### Post by Madds on 2010-07-02
Thanks - I'll try again and give that a go. I'll let you know how I get on!

---

### Post by Yvan300 on 2010-07-02
Hope it works, and welcome to ubuntu my friend ! :)

---

### Post by Madds on 2010-07-02
Sadly, no go... The options I was given under the boot loader were just /dev/sda (maxtor 40gb) or /dev/sda1 (ubuntu 10.4). The previous installs I left it on the default (hdd) so this time I tried the other one - and it didn't like it. I'm just rebooting to the live cd now...

Tried installing from an actual cd too - still won't boot from hdd, same error:  'disk boot failure, insert system disk and press enter'. Only 2 options to choose for boot loader install and neither works.

Could anyone please give me step by step instructions to instal Grub from the live cd? I've tried following some from other threads but never seem to get the expected result, eg sudo grub gives me a command not found.

I've installed ubuntu 9.04 and 9.10 successfully before (tho' not on this machine) - should I give up and go back to one of those?

thanks

---

### Post by Yvan300 on 2010-07-02
Wait, i still don't understand which one you chose?

---

### Post by -humanaut- on 2010-07-02
Try manually partitioning and make sure your installing on the HDD instead of the pendrive it looks like to me from the fstab that it's only installing swap on your harddrive.

---

### Post by Madds on 2010-07-03
Hi again guys - I was going to try your suggestions but decided first to try the install on another (even older) pc - and it went first time! Same cd, cd-rom and hdd as the first time. So I suppose it's the board/BIOS. Doesn't make a lot of sense to me, but maybe I need to flash the BIOS? 

So it looks as if it's not a Ubuntu problem, which has restored my faith as I was thinking 'this is the distro that's supposed to be easy??!!!' 

Thanks very much for your time and expertise, guys; I hope you don't feel it was wasted as I do appreciate it, and apologise that my difficulty seems to have turned out to be a hardware problem...

---

### Post by xzimppledink on 2010-07-04
This may sound elementary but did you change BIOS to "boot to CD" before installing Linux?

---

### Post by Madds on 2010-07-05
Yes - boot order at install time set to cd, removeable drive, hdd. I've  also tried setting all the options to hdd after the install but it  definitely won't recognise the boot info on the drive although another  pc boots the same hdd without any trouble.

I've also installed from pendrive, in which case it will boot to the hdd  as an option from the boot menu on the pendrive, but still not directly  to the hdd.

I don't know if it would boot to Windows, I might install a copy of XP  to see, but I don't want to use it on that machine so it would only be  to test. I'm very puzzled!

---

### Post by Oldieone56 on 2010-07-05
Most of what I have been reading about boot issues today is related to graphics drivers. I messed with this before then gave up and waited for the new LTS on CD. Today various Installation attempts and forum suggestions have not resolved the issue. Apparently there is nothing I can do using the driver I have (Intel 82845G/GL integrated graphics). So I've reinstalled Ubuntu 9.04 until I replace this pc. Fortunately 9.04 has been working flawlessly for me sinse last year.

---

### Post by imondanet174 on 2010-07-06
Hello Madds
 
Try the instructions in this tutorial.
 
It will be identical for Lucid Lynx (Ubuntu 10.04)
 
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Kellemora on 2010-07-06
Some folks aren't going to want to hear this, but we have two different machines here that work perfect with Ubuntu 8.04, neither will work with 10.04 for some reason.  I even tried installing a new unused 500 gig HD on one of the machines and clean install from a CD, the install appears to go OK, but 10.04 just won't run on it.  The other machine I dual booted with Windows XP-Pro and 8.04, have tried loading 10.04 onto it several times and it just won't work.  So I wiped that partition and put 8.04 back onto it and it runs flawlessly.

So, for now, I'm holding off on trying 10.04 until 8.04 is no longer supported and then cross my fingers I don't have to return to using WinDOZE in order to have my computers working.

TTUL
Gary

---

### Post by Madds on 2010-07-06
Thanks imondanet, that looks interesting and I shall bookmark it! 

My problem does seem to have been with the BIOS as the booting has been  fine since resetting it to defaults! I had been thinking it might need  flashing, but it wasn't even that complicated, doh... I can't even say  it was my own suggestion - it came from someone younger and wiser :)

Thanks everyone for your help. x

---

