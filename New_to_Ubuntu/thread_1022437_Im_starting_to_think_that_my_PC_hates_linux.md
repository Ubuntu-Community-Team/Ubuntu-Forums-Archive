---
title: "Im starting to think that my PC hates linux"
date: 2008-12-26
forum: New to Ubuntu
---

### Post by shaullx on 2008-12-26
Well first i tried to boot the install from a usb (many ways)
all i got is alot of diffrent errors and problems during/before install
then i burned the LiveCD to a new DVD and it still won't enter the Install or even to the without install desktop
i have no idea why am i getting all this problems my pc is not bad (2gb RAM,Geforce8600GT,AMD3500+athlon64)

is there a way maybe to install directly from the hard drive without any external things like usb flash devices or cd?
and without wubi (i don't like it being part of windows, and it works slower then normal)
I really want to move to ubuntu im sick of windows please help what can i do :(

---

### Post by oldos2er on 2008-12-26
What are the errors you're getting? Try following these directions for burning Ubuntu: [http://psychocats.net/ubuntu/iso](http://psychocats.net/ubuntu/iso)

---

### Post by w4ett on 2008-12-26
Sounds like we have a lot of frustration here :(

Lets look at the major Issues that you have.

Questions: 

1.  Does your computer run from the live cd...i.e.: Does it boot?

2.  When attempting install from the live CD at what point does install fail  (Error Messages are important)

3.  Assuming you are trying to install using the live cd, have you tried using the text-based alternate install CD?

4.  (Certainly not the least important) have you checked hardware compatibility.....searched for problems other users might have have with the same motherboard?

A little more information will be quite helpful.

---

### Post by shaullx on 2008-12-26
> **oldos2er said:**
> What are the errors you're getting? Try following these directions for burning Ubuntu: [http://psychocats.net/ubuntu/iso](http://psychocats.net/ubuntu/iso)

not sure i have any more empty cd/dvds
isn't there a way without it?

---

### Post by shaullx on 2008-12-26
> **w4ett said:**
> Sounds like we have a lot of frustration here :(

Lets look at the major Issues that you have.

Questions: 

1.  Does your computer run from the live cd...i.e.: Does it boot?

2.  When attempting install from the live CD at what point does install fail  (Error Messages are important)

3.  Assuming you are trying to install using the live cd, have you tried using the text-based alternate install CD?

4.  (Certainly not the least important) have you checked hardware compatibility.....searched for problems other users might have have with the same motherboard?

A little more information will be quite helpful.

1. it gets to the point where you can choose to run ubuntu without installing, install, check for defects etc..
2. when i choose to install or to run without installing it shows the loading and loads for about 5 min and then it prints me errors in a dos screen
but the most anoying thing is that i got the install running from a USB but during the "copying files" part it tells me "CD\DVD bad burn at lower speed or move your system to cooler place" something like that
i don't understand how it is possible i didn't burn it
3.isn't the text install is for PCs that are too weak to install in normal mode?
4.well i used ubuntu once with wubi and it worked so i don't belive that the problem is related to my hardware

---

### Post by bwang on 2008-12-26
Yes, you can install without a CD. See [this page]("https://help.ubuntu.com/community/Installation/FromWindows") for instructions. However, in my opinion, its not worth the trouble if you have a CD burner and a computer that can boot from CD.

---

### Post by LowSky on 2008-12-26
sounds like you have a bad download, I suggest redownloading the file and starting from scratch

---

### Post by w4ett on 2008-12-26
> 3.isn't the text install is for PCs that are too weak to install in normal mode?

Not true...the alternate install method provides a non-graphical method for installing Ubuntu....I have found this useful when graphics drivers are troublesome or there are acpi/noacpi issues in a particular system.

> 2. when i choose to install or to run without installing it shows the loading and loads for about 5 min and then it prints me errors in a dos screen

They are all important....What are the errors?

> the most anoying thing is that i got the install running from a USB but during the "copying files" part it tells me "CD\DVD bad burn at lower speed

This tells me there is a problem with the burn method or media you are trying to install from....I have had problems in the past using DVDs to burn the ISO to.  I recommend that you use good quality CD/r's ONLY....and burn at a speed of 4x or lower......R/W disks and DVDs just don't seem to have the stability needed for ISO needs.

> well i used ubuntu once with wubi and it worked so i don't belive that the problem is related to my hardware

Are you using the same cd and version of Ubuntu?

---

### Post by shaullx on 2008-12-26
> **w4ett said:**
> Not true...the alternate install method provides a non-graphical method for installing Ubuntu....I have found this useful when graphics drivers are troublesome or there are acpi/noacpi issues in a particular system.



They are all important....What are the errors?



This tells me there is a problem with the burn method or media you are trying to install from....I have had problems in the past using DVDs to burn the ISO to.  I recommend that you use good quality CD/r's ONLY....and burn at a speed of 4x or lower......R/W disks and DVDs just don't seem to have the stability needed for ISO needs.



Are you using the same cd and version of Ubuntu?
no i used 8.04 back then
and the download isn't bad i tested on VM and it works

---

### Post by dwasifar on 2008-12-26
VM is a different situation.  Loading into a virtual machine does not present the OS with the same hardware profile as if you were loading onto the actual hardware.  It's possible that your actual install is trying to get some files or drivers that are not required for a VM install, and hitting a corrupted spot in the media.

I second the recommendation to try the alternate install disc.  You have nothing to lose except the dime or so that another blank CD will cost you.

---

### Post by w4ett on 2008-12-26
> **shaullx said:**
> no i used 8.04 back then
and the download isn't bad i tested on VM and it works

Well...without knowing the errors, I would recommend installing from the 8.04 disk that seems to work for your new, clean install since it is proven to work, and then immediately upgrade.

---

### Post by kansasnoob on 2008-12-26
Order a disc!

[http://www.linuxcdshop.com/index.php?app=ccp0&ns=catshow&ref=Ubuntu&sid=vw8m82860732021c3h5znnj8555678jn](http://www.linuxcdshop.com/index.php?app=ccp0&ns=catshow&ref=Ubuntu&sid=vw8m82860732021c3h5znnj8555678jn)

---

### Post by dwasifar on 2008-12-26
> **kansasnoob said:**
> Order a disc!

A poor solution, especially when we haven't fully ascertained that the media is the problem.  He could pay the $4.95 plus shipping, wait until mid-January for it to arrive, and ultimately find himself with the same problem.

---

### Post by w4ett on 2008-12-26
> **dwasifar said:**
> A poor solution, especially when we haven't fully ascertained that the media is the problem.  He could pay the $4.95 plus shipping, wait until mid-January for it to arrive, and ultimately find himself with the same problem.

I disagree....If we cannot get information regarding the error messages, and the OP stands by the statement that there is nothing wrong with his system or his ISO Media....then we are grasping at straws...we're looking for a solution that satisfies him personally, and not his computer technically.  A suggestion to order a commercial grade CD is valid...heck for the postage I'd send him one. :)

---

### Post by Miljet on 2008-12-26
I would suggest trying the CD in another computer first. I had similiar problems installing on an older HP computer. Turned out that the CD drive was introducing errors during read. Popped in a new CD/DVD drive and smooth sailing.

---

### Post by shaullx on 2008-12-26
i downloaded the alternate version to try
but how can i boot it from usb?
i ran out of empty disks:/
(directly from the hdd if possible alsow ok)

---

### Post by w4ett on 2008-12-26
I use unetbootin to create a bootable thumbdrive for ISOs: [http://www.zimbio.com/Ubuntu+Linux/articles/318/HOWTO+Linux+USB+Easy+Way+UNetbootin](http://www.zimbio.com/Ubuntu+Linux/articles/318/HOWTO+Linux+USB+Easy+Way+UNetbootin)

also here: [http://www.teamteabag.com/2008/05/17/howto-easy-install-ubuntu-804-hardy-heron-or-most-other-distros-from-usb/](http://www.teamteabag.com/2008/05/17/howto-easy-install-ubuntu-804-hardy-heron-or-most-other-distros-from-usb/)

---

### Post by handydan918 on 2008-12-26
> **shaullx said:**
> i downloaded the alternate version to try
but how can i boot it from usb?
i ran out of empty disks:/
(directly from the hdd if possible alsow ok)

Save yourself the headaches. Get more disks, and make sure they are high quality cd-r's, not cd-rw.

---

### Post by ELF_O8 on 2008-12-26
> **dwasifar said:**
> He could pay the $4.95 plus shipping 
Canonical ships CD's free, I don't know where you get your information.

---

### Post by shaullx on 2008-12-26
> **w4ett said:**
> I use unetbootin to create a bootable thumbdrive for ISOs: [http://www.zimbio.com/Ubuntu+Linux/articles/318/HOWTO+Linux+USB+Easy+Way+UNetbootin](http://www.zimbio.com/Ubuntu+Linux/articles/318/HOWTO+Linux+USB+Easy+Way+UNetbootin)

also here: [http://www.teamteabag.com/2008/05/17/howto-easy-install-ubuntu-804-hardy-heron-or-most-other-distros-from-usb/](http://www.teamteabag.com/2008/05/17/howto-easy-install-ubuntu-804-hardy-heron-or-most-other-distros-from-usb/)

unetbootin is for livecd there is no alternative version there

---

### Post by w4ett on 2008-12-26
> **shaullx said:**
> unetbootin is for livecd there is no alternative version there

Run unetbootin....select the alternate install iso download image (diskimage)--- click on the button [---] to navigate to the desired file and use to load on the usb drive.

---

### Post by shaullx on 2008-12-27
I tried to install in many way with many attempts and always i get problems ><

tried ubuntu 8.10 live usb with unetbootin
and instead of entering the live desktop is gets me to a terminal
tried to format the thumbdisk and to install again and the desktop shows brown background and mouse pointer and doesnt load anything
and if i choose to install it shows black background and "X" mouse pointer
tried with ubuntu 8.04 same problem
tried with ubuntu 8.10 alternative version and during install it request to mount CD-ROM or something
and it request the mounting address or something like that ("dev/cdrom")
i have alot more then enoth RAM to run the livecd (2GB)
my graphics card is nVidia geforce 8600gt witch is supported with ubuntu
proccessor is AMD athlon64 3500+

(i dont have any blank cds and my burner is kinda bad so i would like to avoid burning)

please help me:cry::cry::cry:

---

### Post by w4ett on 2008-12-27
This is a duplicate:  [http://ubuntuforums.org/showthread.php?t=1022437](http://ubuntuforums.org/showthread.php?t=1022437)

---

### Post by w4ett on 2008-12-27
From: [http://ubuntuforums.org/showthread.php?t=1022966](http://ubuntuforums.org/showthread.php?t=1022966)

> I tried to install in many way with many attempts and always i get problems ><

tried ubuntu 8.10 live usb with unetbootin
and instead of entering the live desktop is gets me to a terminal
tried to format the thumbdisk and to install again and the desktop shows brown background and mouse pointer and doesnt load anything
and if i choose to install it shows black background and "X" mouse pointer
tried with ubuntu 8.04 same problem
tried with ubuntu 8.10 alternative version and during install it request to mount CD-ROM or something
and it request the mounting address or something like that ("dev/cdrom")
i have alot more then enoth RAM to run the livecd (2GB)
my graphics card is nVidia geforce 8600gt witch is supported with ubuntu
proccessor is AMD athlon64 3500+

(i dont have any blank cds and my burner is kinda bad so i would like to avoid burning)

please help me

We really need to have the error messages to troubleshoot your install problems.  Also please review: [https://help.ubuntu.com/7.10/installation-guide/ia64/boot-troubleshooting.html](https://help.ubuntu.com/7.10/installation-guide/ia64/boot-troubleshooting.html) :P

---

