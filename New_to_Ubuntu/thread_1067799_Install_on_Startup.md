---
title: "Install on Startup"
date: 2009-02-12
forum: New to Ubuntu
---

### Post by daved2424 on 2009-02-12
I have just taken ownership of an eee running Ubuntu 8.04 which was reformatted just before it was given to me. When I start-up my OS the install wizard keeps popping up and I can't get rid of it. Even if I try partitioning the disks as it recommends, it fails. I then quit and carry on using it as normal with no aparent problems. Does anyone know how to stop it from doing this at startup?

---

### Post by freak42 on 2009-02-12
You mean the Ubuntu - Install Wizard??

Do you have by any chance an install-medium (cd-rom, usb stick, or network booting envyronment) still within reachability of the os?

hth

---

### Post by daved2424 on 2009-02-12
Yes, the same thing that you get when you click on "Install" in Administration. I have ni USB device or CD-ROM attached and cannot figure what on earth is triggering it.

---

### Post by LowSky on 2009-02-12
Look under System> Pref > Sessions
and see idf it is one of the application that are booting at start up, and if so, delete it

---

### Post by daved2424 on 2009-02-12
No it's not there.

---

### Post by daved2424 on 2009-02-13
The setting in the BIOS about installation is also set to "Finished"

---

### Post by ugm6hr on 2009-02-13
Did you install Ubuntu, or was it installed by the person who gave it to you?

It is possible that they did an OEM install, which runs through user setup on 1st boot, but if you don't complete the process, it will not work.

The other possibility is that they installed a bootable "Live" Ubuntu onto the hard drive (or SD).

---

### Post by daved2424 on 2009-02-13
It was installed by the person who gave it to me. I am guessing they did an OEM install as it came with an installation CD.

I have tried going through the setup. In Step 4 I select Guided and SCSI2 (0,0,0). (Other selections will not let me proceed to step 5).

I complete Step 5-7. An installing system window pops up. It gets to 15% then says it Failed to unmount partitions. and Would I like to the installer to try to unmount these partitions again. Clicking continie takes me back to Step 4 and it just keeps going round and round.

---

### Post by roshanjose on 2009-02-13
> **daved2424 said:**
> I have just taken ownership of an eee running Ubuntu 8.04 

never haeard of this system...can you make it more specific

---

### Post by ugm6hr on 2009-02-13
They have clearly installed a Live Installer to the SD / HD.  That was presumably just for demonstartion purposes (to prove it works).

Hence, as it tries to install, it can't, since the OS root folder cannot be unmounted.

You will have to create a bootable USB / SD and install it yourself.

PS: easypeasy is pre-configured 8.10 for the Asus eee

---

### Post by roshanjose on 2009-02-13
> **daved2424 said:**
> It was installed by the person who gave it to me. I am guessing they did an OEM install as it came with an installation CD.


What type of installation is this??

---

### Post by daved2424 on 2009-02-13
So a completely clean install that will result in loosing all my settings?

I don't suppose you know of a guide for absolute beginners on how to reinstall it? Is it considerably easier with a CD-ROM drive?

---

### Post by ugm6hr on 2009-02-13
> **daved2424 said:**
> So a completely clean install that will result in loosing all my settings?

I don't suppose you know of a guide for absolute beginners on how to reinstall it? Is it considerably easier with a CD-ROM drive?

Yes. Everything will be lost.  Are they saved at the moment?

Look here [http://www.geteasypeasy.com/](http://www.geteasypeasy.com/)

---

### Post by daved2424 on 2009-02-13
I have downloaded a few bits of software and set a few options, but nothing major, I should be able to re-do it again. I hope...

Thank you so much for your help.

---

### Post by tarps87 on 2009-02-13
Do you have a computer with a cd drive, or a windows machine, or an internet connection on the eee, and a 1GB+ USB device. If you have on of these it is easy to do.

There are to ways to keep most of you settings:
One is if you have separate /home partition, posting the out put of ```
sudo fdisk -l
```(l = lower case L)
The other is by copping the folder /home/*your_user_name* to a external drive.

edit: you will need to reinstall the programs

---

### Post by ugm6hr on 2009-02-13
It sounds like you have a persistent install of a Live CD.

Do you have to log in?

Do you have a unique username?

Did it ask for a password when you installed software?

You could just try removing the installer if you want to keep the current setup:
```
apt-get remove ubiquity
```

Although I think it will be faster if you install a fresh version.

You sure there isn't an SD card plugged in?

---

### Post by daved2424 on 2009-02-13
When booting up I am asked to enter an administrator password (which used to be nothing and I set it to my own somehow in terminal).

I do not have a unique username, it is just user.

When installing software it asks for the sudo password. Which I have set somehow in terminal.

There is definately no SD card in the machine.

I removed ubiquity and it does not come up with it anymore. Do you recommend installing a clean version anyway? I presume I will have to run apt-get ubiquity first.

---

### Post by ugm6hr on 2009-02-13
I am not really certain what kind of installation you have.

If your username is "user" - then this is not a standard Ubuntu Live environment, since that logs you in as "root"

Equally, I don't know how you can create a username with no password, which was clearly originally the case (before you created a password).

If you trust the person who gave you the computer, and it is working OK, I don't see a major problem.  But there is something very unusual about this, since it is not an oem install either (which defaults to username "oem" and does not offer to install anything - merely runs through username / password choices.

I would personally want to reinstall from scratch for my own peace of mind.

PS: To reinstall, you don't need anything apart from a USB stick and the download linked to earlier, and a computer (Windows or Linux) to create the LiveUSB from the download.  See [http://www.ubuntu-eee.com/wiki/index.php5?title=Get_Easy_Peasy](http://www.ubuntu-eee.com/wiki/index.php5?title=Get_Easy_Peasy)

---

### Post by daved2424 on 2009-02-13
I have, on one or two occasions, just after being prompted for the adminsitrator password and as the install wizard thing starts, a message box has popped up saying something like it has been unable to grab they keyboard and something about a keylogger. Should I be concerned?

---

### Post by ugm6hr on 2009-02-13
There is also another alternative: [http://www.eeebuntu.org/](http://www.eeebuntu.org/)

Instructions here: [http://www.liliputing.com/2008/12/how-to-install-eeebuntu-with-a-usb-flash-drive.html](http://www.liliputing.com/2008/12/how-to-install-eeebuntu-with-a-usb-flash-drive.html)

> Should I be concerned?

Probably.  You know where you got the computer from.  I don't.

---

### Post by daved2424 on 2009-02-13
ebay. new install i think.

---

### Post by ugm6hr on 2009-02-13
Interesting.  A quick google revealed: [http://thelinuxlink.net/forum/viewtopic.php?f=2&t=3801](http://thelinuxlink.net/forum/viewtopic.php?f=2&t=3801)

It appears that EasyPeasy has a flaw in the installer that causes the ubiquity installer to launch at login.

So you may have to uninstall it in any case after a fresh install.  I would recommend a reinstall if it came from ebay anyway.

---

