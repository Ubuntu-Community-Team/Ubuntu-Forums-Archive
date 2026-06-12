---
title: "Help a newbie with install of ubuntu 8.04 i386"
date: 2008-12-11
forum: New to Ubuntu
---

### Post by bellamama68 on 2008-12-11
I'm hoping someone can help me.  I am pretty new to ubuntu and had installed a previous version, later updating to 8.04.  I had problems trying to make updates to 8.04 and thought that if I purchased a CD and did a fresh install, I would be okay.  When I load the CD, an icon comes up on the desktop "Ubuntu 8.04 i386."  When I double-click it, I have all of these files available to me, but I don't know where to start.  I chose "install" which seemed to make the most sense, but when I click on that, I'm faced with yet more choices which don't seem to work.  

If someone does respond to this post, please be very specific if possible with the steps I should take.  I've been searching all over the internet for help, but I don't often understand the solutions.

Thank you so much!

---

### Post by sneeks on 2008-12-11
what type of install are u trying,a full install,or wubi?

---

### Post by Michael.Godawski on 2008-12-11
hi bellamama68,

first of all do not be scared :p.

Tell us please in which operating system you are right now. 

Do you want to install Ubuntu? Or did you already managed to install it, some time in the past?

---

### Post by karlr42 on 2008-12-11
You need to reboot, then boot from the CD like you did when you first installed Ubuntu. Then you can install the new install over your current one.

---

### Post by Duck2006 on 2008-12-11
If you are installing a Wubi this will help.

[http://www.psychocats.net/ubuntu/wubi](http://www.psychocats.net/ubuntu/wubi)

If not this will help.

[http://www.psychocats.net/ubuntu/dualboot](http://www.psychocats.net/ubuntu/dualboot)

---

### Post by bellamama68 on 2008-12-11
I already have Ubuntu 8.04 on my computer, but when I tried to do routine updates, they can't be completed, so I thought that  doing a full install of 8.04 with a CD would help.  This is the only OS on my computer.  One of the reasons the updates wouldn't work is that I'm missing Package libc6, whatever that is.  Anyway, like I said earlier, when I load the CD and double-click Ubuntu 8.04 on my desktop, I wasn't expecting to see all these files, but rather a button that says install.  I originally put 8.04 on my computer as an upgrade from an earlier Ubuntu.  I bought the CD because it appears that some critical items are missing from my original upgrade to 8.04.  I hope this makes sense.

---

### Post by karlr42 on 2008-12-11
Then do as I suggested in a previous post- pop the CD in your drive, shut down, then on next turning on your PC, make the BIOS boot from the CD drive.
[https://help.ubuntu.com/community/BootFromCD](https://help.ubuntu.com/community/BootFromCD)
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

---

### Post by bellamama68 on 2008-12-11
karlr42,

I referred to the links you recommended and I am seeing all the files and directories that I'm supposed to, so it seems I am booting from the CD drive like I should.  But now that I see all of these files and directories, where do I go next?  I see files like casper, dists, install, isolinux, pics, pool, preseed, ubuntu, autorun.inf, md5sum.txt, README.diskdefines, umenu.exe & wubi.exe.  I clicked on install which led me to mt86plus, README.sbm & sbm.bin.  Help!

Thanks!

---

### Post by abn91c on 2008-12-11
go here to upgrade [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

---

### Post by Kellemora on 2008-12-11
Hi Bell

Your listing of the CD sounds right for an .iso burned CD!

However, instead of BOOTING the CD, your computer is RUNNING IT using the AutoRun feature for some reason.

Can you go into your computers BIOS and select Boot from CD or change the CD Drive to your 1st Drive in line up of BootUp drives?

You should get a black screen with the colorful UBUNTU at the top and the options to Run without Install, Install, etc. that you can select from.

If you are NOT getting this, you may have a COPIED CD that is not really a bootable .iso CD.  It MUST be burned as an .iso to work!

One thing has me puzzled though, you said you PURCHASED a CD.  Do you mean a blank CD and burned the .iso or did you buy a copied CD from someone?  Copies don't work!

TTUL
Gary

---

### Post by ajcham on 2008-12-12
> One thing has me puzzled though, you said you PURCHASED a CD. Do you mean a blank CD and burned the .iso or did you buy a copied CD from someone? Copies don't work!

If it's a copy of an existing bootable CD it will certainly work - I'm not sure why you believe otherwise.  A lot of people sell Ubuntu CDs - on ebay, or in classifieds etc.  Whether they're doing disc-to-disc copies or iso burns is irrelevant, the disc will usually be good.

As you mentioned the likely issue is that the BIOS is not set to boot from the CD, so instead the computer is just booting the existing installation.

---

### Post by bellamama68 on 2008-12-12
Okay, here's where I'm at now:  I booted from the CD.  I got to the menu where you can try Ubuntu or just install.  I tried both options, but the only one that would proceed was to try Ubuntu.  I clicked that and got to the desktop where there are 2 files:  1with examples & the other "install."  I double-clicked install only to be told that there are restricted drivers in use which are not supported.  The install then starts, but crashes, & I'm just left at the desktop looking at the examples & install files, but can't do anything else.

---

### Post by sneeks on 2008-12-12
ok,have been following this post a lot over 24 hours,and here's what i believe you should do(but don't take my word for as im sure someone will say if im wrong).
firstly get yourself a copy of gparted,copy the iso to disk.(by the way make sure you back up all the data you want to keep)
boot from the gparted disk and re-format the whole disk so it is just one large disk(Ubuntu will do the rest for you when you install).
i know Ubuntu has gparted,but am just trying a failsafe way.
now you have no os on the disk,you should be able to boot from your hardy disk into the GUI,on the desktop will be the install icon.
click on it and bobs your uncle and fanny's your aunt.
just one last thing,you do have the correct version for your pc i hope,what i mean is 32 or 64 bit,i know thats a silly question but just in case eh.
p.s. what are your machine specs?

---

### Post by bellamama68 on 2008-12-12
What exactly is gparted & why do I need that?

---

### Post by sneeks on 2008-12-12
> **bellamama68 said:**
> What exactly is gparted & why do I need that?

its a partioning program that runs from disk,I'm just trying to make it as easy as possible for you,so you dont have any hiccups...
once you have run it,you exit the program and take the disc out,and then re-boot with ubuntu disk,sorry should have elaborated more,but was not sure on how much experience you have.

---

### Post by Duck2006 on 2008-12-12
> **bellamama68 said:**
> What exactly is gparted & why do I need that?

To partition the drive.
Some info on gparted.

[http://wiki.partedmagic.com/index.php/Using_GParted](http://wiki.partedmagic.com/index.php/Using_GParted)

---

