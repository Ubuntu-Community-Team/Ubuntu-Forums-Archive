---
title: "disk problems"
date: 2009-11-23
forum: New to Ubuntu
---

### Post by ErrUmm on 2009-11-23
I am completely new to all this. I have attempted to install 9.10. The install ran ok and when rebooting it hangs up. I get Grub loading.
 
Note I had previously loaded 8.04 ok, then tried to clean the disk with dban prior to putting in 9.10. This was I think a mistake as it didn't seem to work (I have not used it before) So I abandoned the cleaning exercise and stuck in the 9.10 disk. It seemed to load ok but hangs on reboot.
 
Suspecting my hard drive may have been affected by all this, at the terminal I typed:
 
sudo lshw -C disk
 
Sorry I didnt know enough to be able to copy the output for you to see, but I am concerned that against the bus info: entry it says [EMAIL="scsi@2:0.0.0"]scsi@2:0.0.0[/EMAIL] which seems odd to me as its an IDE drive. Is there a problem here, if so how do I fix it?

---

### Post by halitech on 2009-11-23
the newer kernels are using the SDx method of identifying drives so it showing up as /dev/sda is normal.

Does the Live cd boot properly?

---

### Post by ErrUmm on 2009-11-23
live cd aok
 
sorry dont understand your reply /dev/sda. Is ref to scsi ok?

---

### Post by halitech on 2009-11-23
if you open a terminal and run
```
sudo fdisk -l
```
the drive will probably show up as /dev/sda1 which indicates a scsi drive but the newer kernels use the scsi drive mode for drives. This is normal.

---

### Post by ErrUmm on 2009-11-23
> **halitech said:**
> if you open a terminal and run
```
sudo fdisk -l
```
the drive will probably show up as /dev/sda1 which indicates a scsi drive but the newer kernels use the scsi drive mode for drives. This is normal.
 
 
So even though I physicaly have an IDE drive, it shows as scsi??
 
I guess you meant fdisk -l rather than fdisk -1!!!
 
Anyway with fdisk -l it gave me
 
dev/sda1 Linux
dev/sda2 Extended
dev/sda5 Swap
 
Does this indicate my hard disk is ok and my problem lies elewhere?

---

### Post by halitech on 2009-11-23
yes, because of the way the kernel identifies drives now they all show as SDx (at least with Ubuntu, other distros are using older kernels that will show an IDE drive as HDx)

I did tell you to type in fdisk -l and not 1

I would say yes, the issue is elsewhere and not with the drives.

---

### Post by ErrUmm on 2009-11-23
[quote=halitech;8372645]
 
I did tell you to type in fdisk -l and not 1
 
 
My apologies, thats the way it looked to me on the screen.:redface:
 
Do you have any further suggestions  as to how I can get out of this impasse? I basically dont have a clue!

---

### Post by halitech on 2009-11-24
What exactly do you see on the screen when it hangs?

---

### Post by ErrUmm on 2009-11-24
> **halitech said:**
> What exactly do you see on the screen when it hangs?
 
I have been playing around with Ultimate Boot CD, and found that the HD diagnostics reported mcb chain corrupt.
 
So I replaced my brand new 120Gig WD drive with my old 12Gig IBM - ran same tests - looks ok - so am just now in process of installing 9.10 on it.

---

### Post by ErrUmm on 2009-11-26
ok - sorry for delay. Messing around with disks takes ages! I think I have some sort of hardware problem. With my old 12Gig disk I get the same symptoms. However, if I connect the disk to a spare IDE port rather than the ATA100 one using HighPoint HP370 controller, then this is basically what happens on reboot after fresh install:
 
black screen with Keith-desktop tty1 at top. asks for login & password.
 
when entered, I get -bash: cannot create temp file for here -document: Read only file system
 
Keith @keithdesktop:~$ (system hung at this point)
 
Not knowing any better, at this point I pressed reset on the system unit. This gave me
 
GNU GRUB version1.97~beta4 with a menu selection of 4 items:
 
Ubuntu Linux 2.6.31-14-generic
Ubuntu Linux 2.6.31-14-generic (recovery mode)
Memory test (memtest86+)
Memory test (memtest86+ serial console 115200)
 
Selecting the first option resulted in "file system checks in progress" and after all this I got into the desktop. In janitor it reports bash missing. Otherwise system running as far as I can see!
 
Makes me think there is a problem with the Highpoint controlleras this system unit was running Win ME ok with the disk on the ATA100 port. What I dont understand is with a completely clean hard disk, where is the software stored that sets up the controller? Since I can test the clean drive using my Ultimate Boot CD HD diagnostics. Is it stored within the controller chip on EEPROM? Has it got corrupted somehow?

---

### Post by halitech on 2009-11-26
I have to admit, this is over my head as until you posted the message, I'd never heard of it. If the drive(s) work on another connection, I would say an issue with the add-on controller card but I'm guessing.

---

### Post by ErrUmm on 2009-11-27
> **halitech said:**
> I have to admit, this is over my head as until you posted the message, I'd never heard of it. If the drive(s) work on another connection, I would say an issue with the add-on controller card but I'm guessing.
 
 
Well, I was getting really frustrated with it, so I scanned the local ads and bought another secondhand system unit. This one is a 64 bit machine. Is there any issue with that? It all loaded up ok (with my new disk installed) Phew!! Now awaiting a router for internet connection.

---

### Post by halitech on 2009-11-27
there shouldn't be any. I'm using 64bit and it works fine. Only issue might be flash if you are a big youtube user.

---

### Post by ErrUmm on 2009-11-28
Oh, thats good.

Now got my router and have internet. The first problem I have is graphics stuck at 800 * 600. The display comes up as "unknown"

System is based on ALiveNFG6-DVI motherboard with on board NVIDIA GeForce6 class graphics card. The monitor is Emprex LM1904 19" widescreen LCD which can do 1440 * 900 @75Hz.

I tried to set these up using the command gksu displayconfig-gtk. It asked me for my password which I entered. It then went straight back to the prompt without doing anything. Can you help with this?

---

### Post by halitech on 2009-11-28
for the video card, did you check Hardware drivers to see if it has a driver for you to install?

---

### Post by ErrUmm on 2009-11-28
> **halitech said:**
> for the video card, did you check Hardware drivers to see if it has a driver for you to install?


No. How do you do that?

---

### Post by halitech on 2009-11-28
I think its under System - Admin - Hardware drivers if I remember right. I'm using XFCE so I don't have the same menu as you.

---

### Post by ErrUmm on 2009-11-28
> **halitech said:**
> I think its under System - Admin - Hardware drivers if I remember right. I'm using XFCE so I don't have the same menu as you.


It just tells me "No proprietary drivers are in use on this system"

---

### Post by halitech on 2009-11-28
ok, so we will need to manually add them. I've never used an Nvidia card so I'm not totally sure but info is available here:

[https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)

driver is available here:
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

Fixing the resolution is here:
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

---

### Post by ErrUmm on 2009-12-02
Halitech
 
Again, sorry for delays. Various problems including psu blow up on my main Windows machine. I will be following up your lead as time permits - thanks.
 
Just one detail...
 
On the first link it scared me a bit as the first thing it says is "This is not the recommended way...."
 
Then there is a link to BinaryDriverHowto/Nvidia which is supported. I take it thats the way to go??

---

### Post by halitech on 2009-12-02
the link to the BinaryDriverHowto basically tells you to use the Hardware drivers but you have already checked and there is nothing there so it won't work. Also it is outdated as it only includes instructions up to version 8.10.

Don't let the warning about it not being the recommended way scare you. Alot of people use those steps and have no issues.

---

### Post by ErrUmm on 2009-12-05
ok the first thing it asks me to do is back up my xorg.conf file from /etc/x11

I can get to /etc/x11 ok but I dont see this file. What now?

---

### Post by halitech on 2009-12-05
9.04 and 9.10 don't use the xorg.conf file so no need to back it up. You might want to create one first though since it doesn't exist

```
sudo touch /etc/X11/xorg.conf
```
make sure you have the X11 in uppercase as *nix is case sensative.

---

### Post by ErrUmm on 2009-12-05
I put the 23 Meg driver file NVIDIA-Linux-x86-190.42-pkg1.run in my home/keith directory. 
 
Then opened a terminal and typed sudo apt-get install build-essential linux-headers-'uname -r'
 
This reported couldnt find package linux-headers-uname -r

---

### Post by mikewhatever on 2009-12-05
Try this one:

```
sudo apt-get install build-essential linux-headers-$(uname -r)
```

---

### Post by halitech on 2009-12-05
try this way
```
sudo apt-get install build-essential linux-headers-`uname -r`
```
I think you need the backtick ( ` ) and not the single quote ( ' ) around the uname -r

---

### Post by ed-koala on 2009-12-05
Just a note so you will know. Installing the nvidia drivers the way you are doing it will require you to reinstall the drivers any time there is a kernel update.

If you open the Synaptic package manager and search for nvidia you'll see some packages with nvidia and modaliases in the name.  Install those and then the restricted drivers will show up in the list to install that way.

---

### Post by ErrUmm on 2009-12-05
> **halitech said:**
> try this way
```
sudo apt-get install build-essential linux-headers-`uname -r`
```
I think you need the backtick ( ` ) and not the single quote ( ' ) around the uname -r
 
 
using the bactick got rid of that problem.
 
When it asks do I want to continue Y/n, can I enter y or Y - is it case sensitive?
 
I used y first and got errors, but suspect its because I was off line. Do I need to be online for this?

---

### Post by halitech on 2009-12-05
either way should work but you certainly need to be online as it is going to grab files from the repos to get things installed.

---

### Post by ErrUmm on 2009-12-05
ok well I have problems using my new router until I get my wireless usb adaptor. Should be here in a couple of days. Thanks for your patience. Trying Ubuntu is a steep learning curve!!

---

### Post by ErrUmm on 2009-12-08
Now got my wireless usb adators. Set up ok on Widows machine using new router. Now need to set up the internet connection on the Ubuntu machine using a second wireless USB adaptor same as first.
 
I need to install NdisWrapper Config tools to use windows drivers for wireless adaptors.
 
Saved the 3 required files (as described in my beginners book) - incredibly long path names & saved onto memory stick ok - copied to desktop
 
When I do   sudo dpkg -i ndis*
 
I get   dpkg:error processing ndis* (--install): cannot access archive: No such file or directory
 
Help!! I can see the files on my desktop  - whats wrong?

---

### Post by halitech on 2009-12-08
did you change to the Desktop before you tried to run the command? The terminal should show ~/<username>/Desktop if you did. If you didn't, do cd Desktop and then run the dpkg -i command again.

---

### Post by ErrUmm on 2009-12-08
Ah... now it works!!
 
So [EMAIL="keith@keith-desktop:~$"]keith@keith-desktop:~$[/EMAIL] is not the desktop????
 
I'll carry on tomorrow - thats enough excitement for one day!

---

### Post by halitech on 2009-12-08
> **ErrUmm said:**
> Ah... now it works!!
 
So [EMAIL="keith@keith-desktop:~$"]keith@keith-desktop:~$[/EMAIL] is not the desktop????
 
I'll carry on tomorrow - thats enough excitement for one day!

no, desktop and Desktop are not the same. Linux is case sensitive so you have to type it in exactly the way it is listed.

Also, keith-desktop is the name of your computer and ~ indicates you are in your home folder.

for example, when I first open the terminal, mine shows up as

daryl@debian:~$

When I change to the Desktop, it shows up as 

daryl@debian:~/Desktop$

---

### Post by ErrUmm on 2009-12-11
hi halitech - glad you are still there!!

As you pointed out earlier, I need to be online to sort out my graphics driver. To that end I have now got a wireless router and a couple of USB wireless adaptors. All working fine on my windows PC. 

However, I am stuck when it comes to getting the wireless adaptor to work with Ubuntu. I have a copy of "Beginning Ubuntu Linux" Fourth Ed by Keir Thomas et al. So far I have installed device manager and determined that my USB adaptors are reported as:

Vendor: Ralink Technology, Corp
Model: 802.11g WLAN
PCI ID:  148f_2070

The book then suggests looking up [http://sourceforge.net/projects/ndiswrapper/](http://sourceforge.net/projects/ndiswrapper/) to see if these devices will work with NdisWrapper, but I can't see the list of devices referred to, so I suppose I could ignore this bit and extract the .sys and .inf files from the .exe I used under Windows for these devices??

---

### Post by halitech on 2009-12-11
Before we go the NDISwrapper route, lets check something. Boot into Ubuntu, plug the USB adapter in and run lsusb and post the info here.

---

### Post by ErrUmm on 2009-12-12
Not being sure of the best way to go about it....  I clicked on screenshot - but where did it go - how do I use it, please explain.
 
So, I copied and pasted the screen output to a text file - saved it as "screenshot.txt" on my memory stick - back to my windows machine - attached file. Hope you can see what you want this way!

---

### Post by halitech on 2009-12-12
that works perfectly for me :)

doing some searching found this thread, first post should have you up and running

[http://ubuntuforums.org/showthread.php?p=8071728](http://ubuntuforums.org/showthread.php?p=8071728)

---

### Post by ErrUmm on 2009-12-12
I have read through the link and I can't say I follow all the comments made, but post #28 seems to suggest the current driver is not suitable for my 2070 device?

---

### Post by halitech on 2009-12-12
just try following the instructions from the very first post. If it doesn't work or you get any errors, post them here and we'll see what you need to do.

---

### Post by ErrUmm on 2009-12-12
Halitech, I'm really out of my depth trying to follow all this.
 
Step 3 says navigate to os/linux - what is this? couldn't find any such location
 
I blindly typed in the code listed, but not sure what it means from  "add:" ........
 
Attached screen shot of my progress, or lack of it!

---

### Post by halitech on 2009-12-12
when you type in the commands, # means to do it as root (or sudo), you don't actually type in the #

so the commands would be 
```
tar jxvf 2009_1110_RT3070_Linux_STA_v2.1.2.0tar.bz2
cd 2009_1110_RT3070_Linux_STA_v2.1.2.0tar/os/linux
pico usb_main_dev.c
```

---

### Post by ErrUmm on 2009-12-14
now unpacked ok, but the cd to ........../os/linux doesn't work. see attached
 
could you explain why this procedure is needed? why won't the driver work as downloaded?

---

### Post by halitech on 2009-12-14
can you run
```
ls > ls.txt
```
and copy that info here

Basically we need to put the files in the correct locations in order for linux to find them

---

### Post by ErrUmm on 2009-12-14
I managed to find the file usb_main_dev.c  in /os/linux and add the line to it.
 
Now when I get to step 4 "Compile the module" running cd ../..;make gives me an error as attached. Suspect its because I'm not at the right place. Where to go & how to get there?

---

### Post by ErrUmm on 2009-12-14
ok... figured out I had to set the terminal window to be in  ..../os/linux
 
then, to run step4, I typed cd ../..;make 
 
the result is attached - not sure if this is ok or not.

---

### Post by halitech on 2009-12-14
try doing this
```
cd 2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux
```
then run
```
make
```

---

### Post by ErrUmm on 2009-12-15
> **halitech said:**
> try doing this
```
cd 2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux
```
then run
```
make
```
 
can't find that folder, guess you meant 2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux
 
I tried that which didn't do much. see attached
 
Do I need to use sudo at start of each command, (I haven't done this) or does it remain effective once used at the start? Presumeably you could always use sudo at the start of each command line with no ill effect?

---

### Post by halitech on 2009-12-15
sorry, typo on my part for the folder name

should only need sudo if the line is indicating to do it as root ( # )

I wonder if you have the compile tools installed. try running this
```
sudo apt-get install build-essential
```
then run the make command again from the proper folder

---

### Post by ErrUmm on 2009-12-16
installed compile tools ok.
 
not sure what the "proper folder" was, so did cd to
2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux and ran the make command again.
 
This failed, so I did cd ../..;make. See attached result of all this.
 
please explain cd ../..;make. Is it the same as cd / (return) make???

---

### Post by halitech on 2009-12-16
cd ../.. should take you back 2 directories so I think we need to determine just which folder you were supposed to be in before running that so we end up in the correct folder.

I think we should be in this folder

~/2009_1110_RT3070_Linux_STA_v2.1.2.0.tar/os/linux 

so if we run cd ../.. it should take us back to 2009_1110_RT3070_Linux_STA_v2.1.2.0 where we then want to run make

---

### Post by ErrUmm on 2009-12-16
ok, I  did  a cd to
2009_1110_RT3070_Linux_STA_v2.1.2.0
 
then ran the make command.
 
Result attached, which predictably from what you said looks similar if not the same (I havent studied it closely)

---

### Post by halitech on 2009-12-16
the results look good except this line

[color="red"]/home/keith/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/Module.markers: Permission denied[/color]

I'm not sure why you would get a permission error on that file though. Did you untar the file either using sudo or had you done sudo su or su -i or did you untar it as yourself?

---

### Post by ErrUmm on 2009-12-17
halitech,
 
you may be relieved to hear I have got some new Asus WL-167G v2 USB wireless adaptors, which I understand should work ok with Ubuntu. (yet to find out)!
 
The lesson learnt is: before buying any hardware, check linux support! 
 
Will post here just to let you know if this cunning plan has worked.
 
Thanks for your help :)

---

### Post by ErrUmm on 2009-12-17
just looking at
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsAsus](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsAsus)
 
troubles me as the WL-167G v2 is listed twice. one with driver rt2500, the other with rt73usb
 
doing lsusb shows 0b05 1723 which agrees with the second case. but how to be sure which driver I need? This is maddening.

---

### Post by halitech on 2009-12-17
if the number agrees with the second driver then that is the driver to use.

---

### Post by ErrUmm on 2009-12-18
halitech,
I have posted a new thread "install WG-167G v2" to give more focus

---

