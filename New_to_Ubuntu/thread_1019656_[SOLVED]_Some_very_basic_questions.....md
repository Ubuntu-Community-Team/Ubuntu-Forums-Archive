---
title: "[SOLVED] Some very basic questions...."
date: 2008-12-23
forum: New to Ubuntu
---

### Post by pgf5312 on 2008-12-23
Hi Everyone,

Greetings from Ireland!
I'm completely new to Linux/Ubuntu, so please be patient.....
I've got a mainframe programming background and have also used Windows pc's at work for years. I've retired now and I got a new home pc with the ***appalling*** Vista - which has given me nothing but trouble almost since I bought it! Anyway, I've decided to give Ubuntu a try, so I'm downloading the ISO file which I can burn to a CD and then boot it..... and my initial novice questions are:
1. Given that this would, initially at least, be a 'standalone' boot from the CD, where do user files under Ubuntu get written, given that Vista has 'hogged' the entire C drive?
2. I've been looking at the dual-boot option but does that mean re-partitioning the disk drive? I'm a bit nervous about doing that, as I've read some horror stories and I don't want to lose the Windows-based data - at least not yet!
3. Is it possible to install a 'portable' version of Ubuntu on a removeable drive (e.g. a large-capacity USB stick) and also keep user files there?
Many Thanks for any help and I'm, sure to be back with more questions!
Regards, Peter.....:)

---

### Post by Duck2006 on 2008-12-23
Welcome to ubuntu. These may help.

[http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm](http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm)
[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

---

### Post by Raynman37 on 2008-12-23
Check out [http://www.pendrivelinux.com/](http://www.pendrivelinux.com/) for instructions on how to make a bootable Linux USB from a LiveCD!

Edit: Duck beat me to it :P

---

### Post by snowpine on 2008-12-23
Hi and welcome to the forums!

1) If you are running Ubuntu from the Live CD, your session will be lost each time you power down the computer. You can manually store any files you create on a USB drive or somewhere on your internal hard drive, if you wish.
2) Always a good idea to back up important data before partitioning, but nothing to be scared of. I'm not a Vista user myself, but I have read that you should partition the drive from within Vista, then install Ubuntu into the freed space, as opposed to letting the Ubuntu installer do the partitioning. Perhaps an experienced Vista/Ubuntu double-booter can share his/her experience?
3) Yes, absolutely! The Ubuntu 8.10 Intrepid Ibex Live CD has a 'Create Live USB' application in the System menu. (Note however that a lot of older computers can't boot from USB.)

Good luck, please don't be shy about asking lots of questions.

---

### Post by pgf5312 on 2008-12-23
Thanks, folks..... Those quick replies are much appreciated.....:)

---

### Post by Idefix82 on 2008-12-23
1. You won't be able to save anything onto the hard drive when you boot from the CD until you actually install Ubuntu.
2. You can use the partitioner which is built into Vista to resize the Vista partition. This is reasonably safe. After that you can ask the Ubuntu installer to use the unallocated space, which should be completely safe, provided you really point it to the unallocated space and not to the Vista partition.
3. Yes, it is. You just have to make sure that GRUB installs itself into the MBR of the external medium.

---

### Post by wizard10000 on 2008-12-23
> **Raynman37 said:**
> Check out [http://www.pendrivelinux.com/](http://www.pendrivelinux.com/) for instructions on how to make a bootable Linux USB from a LiveCD!

Edit: Duck beat me to it :P

Intrepid will allow you to create a bootable USB device directly from the live CD or from an installed version with a live CD available.  Look in System --> Administration --> Make a USB Startup Disk

:)

---

### Post by Raynman37 on 2008-12-23
Ooooh, fancy!  I'll have to download a liveCD quick and check that out.

---

### Post by pgf5312 on 2008-12-23
> **Idefix82 said:**
> .....You won't be able to save anything onto the hard drive when you boot from the CD until you actually install Ubuntu.....

That's what I would have thought but when I booted Ubuntu from the CD, I appeared to be able to write a file to the C drive from an Ubuntu application. I was later able to access this same file under Windows and edit it using Notepad (having added a file extension of .txt); I'm a bit confused - does Ubunti have simuntaneous access to the (Windows) C disk? Another issue: an Ubuntu option appears to be an installation as an application under Windows. How does this work, i.e where would Ubuntu - and its files - actually reside in such a situation? Thanks Again.....:)

---

### Post by balaknair on 2008-12-23
> Another issue: an Ubuntu option appears to be an installation as an application under Windows.

That's the Wubi installer. In this case it would create a virtual disk image in C:\Wubi\ and install Ubuntu on that image, and modify the bootrec.exe file in Vista to add Ubuntu as a boot option. The advantage here is that if you want to try out Ubuntu and later want to uninstall it, you can simply uninstall it from using the Add/Remove Programs menu in Vista.

---

### Post by minsf on 2008-12-23
pgf, the fact that you are worried so much about losing your windows data, means that you have no backup. 
i hope you dont mind me saying, but this is bad practice... 
let me tell you a story: yesterday, my friend was sitting in a coffee shop with his laptop and a very talented girl spilled her entire drink on his laptop... fortunately, it was beer (as in free beer) and the laptop seems to like it... it was a bit drunk for a few minutes, but now all is fine. 
backup. backup. backup.
just a friendly advice. 
this way you'll have the piece of mind to tinker with your new ubuntu system. and let me tell you- the best way to learn is by breaking things and fixing them :)
oh, and welcome to ubuntu, where fixing is possible! (well, most of the time...)

---

### Post by minsf on 2008-12-23
> **Idefix82 said:**
> 1. You won't be able to save anything onto the hard drive when you boot from the CD until you actually install Ubuntu.

Idefix, i think it is possible to mount the hard drive and save it there, even when booting from the cd.

---

### Post by Idefix82 on 2008-12-23
> **minsf said:**
> Idefix, i think it is possible to mount the hard drive and save it there, even when booting from the cd.

You are right, sorry, I should have been more precise. What I should have said was pretty much what snowpine said: Ubuntu won't store anything by default and will not create a /home folder by default, when booting from the LiveCD. There is of course nothing to stop you to do whatever you want with the hard driver while running a live session, including creation of folders, complete destruction of all data and many things inbetween :)

---

### Post by pgf5312 on 2008-12-23
> **minsf said:**
> .....backup. backup. backup. just friendly advice....
Thanks, Minsf. You're right, of course - backups are ultra-important. I know this, given my systems programming background - I go back to the time when we backed up data to reel tapes at 1200 bpi or something crazy like that.... What I should really have said was that I did not want to wreck the Windows system itself and have to re-install the o/s plus service, software, etc. I have most of my data backed up but must formalize things a little better. Thanks for the reminder. :)

---

