---
title: "Hangs during boot"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by Luffer on 2008-12-28
Was using my Ubuntu install fairly pain free until it stopped booting. No idea why it happened, it just suddenly won't boot up.

Tried using the Recovery mode and loads of scrolling text appeared and then it got to:

* Setting kernel variables       [OK]
[     51.309650] BUG: soft lockup - CPU#1 stuck for 11s! [events/1:10]
[     63.114982] BUG: soft lockup - CPU#1 stuck for 11s! [events/1:10]
[     74.916317] BUG: soft lockup - CPU#1 stuck for 11s! [events/1:10]

This same line kept repeating itself over and over again. Several reboot attempts resulted in the same outcome. I've attached a photo of the screen for further confirmation and in case an earlier line gives more information.

No idea what the problem is, Vista still boots and works fine, it's just Ubuntu. I'm a total novice so need baby step instuction if anyone can help!

---

### Post by Luffer on 2008-12-28
I've followed instructions on booting normally by removing the "quiet splash" section from the boot line. Thought I might get more info by doing this, but I got the same thing as before.... except this time it got further and didn't go into its lockup loop until it reached:

* Checking minimum space in /tmp... [OK]

Again, I've attached a photo of the screen. Before it was getting stuck at "Setting kernel variables [OK]", but as you can see, it was fine this time on that part but stopped soon after.

I'm baffled!

---

### Post by 67GTA on 2008-12-28
What kernel version are you using? This is a known bug in 2.24-19.

---

### Post by Luffer on 2008-12-28
> **67GTA said:**
> What kernel version are you using? This is a known bug in 2.24-19.

Using 2.6.24-17 so guess the bug is present in this earlier version as well? If that is the case how would I sort this mess out being a complete Linux / Ubuntu novice?

---

### Post by sirebral on 2008-12-28
I think I have had this problem before and it is why I try to find the actual driver instead of using NDIS Wrapper.

Do you see how NDISWrapper is failing to initilize?  What I did when that happened is I went into my BIOS setup and turned off the internet.  I have a WiFi card.  That worked for me.  I had to restart and turn the WiFi back on from the BIOS and then restart it through NDISWrapper though.

If that is the problem tell me what your internet connection is running through.  Maybe there is a linux driver for your card.

---

### Post by 67GTA on 2008-12-28
I haven't seen this reported for 2.6.24-17. You might want to try booting without the ndiswrapper module loaded to see if it is causing you trouble.

---

### Post by Luffer on 2008-12-28
> **sirebral said:**
> I think I have had this problem before and it is why I try to find the actual driver instead of using NDIS Wrapper.

Do you see how NDISWrapper is failing to initilize?  What I did when that happened is I went into my BIOS setup and turned off the internet.  I have a WiFi card.  That worked for me.  I had to restart and turn the WiFi back on from the BIOS and then restart it through NDISWrapper though.

If that is the problem tell me what your internet connection is running through.  Maybe there is a linux driver for your card.

I don't /think/ NDISWrapper is the problem here, but I could be wrong. It was a long time ago I set up all the wifi driver stuff and it didn't make any sense to me at the time, but it worked.

Apparently there was no driver for my card at the time, I'm using an Atheros AR5007EG Wireless Network Adapter in my laptop.

---

### Post by Luffer on 2008-12-28
> **67GTA said:**
> I haven't seen this reported for 2.6.24-17. You might want to try booting without the ndiswrapper module loaded to see if it is causing you trouble.

Okay, I'll give it a go if someone can explain how.....?

---

### Post by sirebral on 2008-12-28
Like I said.

Reboot, Enter Setup (f5 or f12), then turn off your internet card, save and reboot.  Turn off NDISWrapper through the OS, reboot.

Then: During reboot, enter Setup again, turn on your internet card again, save and reboot.

To get internet back after you reboot you can start it with NDISWrapper again.

That is from my experience.

---

### Post by Luffer on 2008-12-28
> **sirebral said:**
> Like I said.
Turn off NDISWrapper through the OS, reboot.


But how do I do this bit, it was ages ago that I set it up and have no idea what I did. I just followed instructions of a website somewhere and got it going!

---

### Post by 67GTA on 2008-12-28
The easiest way to do it would be to blacklist the ndiswrapper module. Open a terminal and run ```
sudo gedit /etc/modprobe.d/blacklist
``` then at the end of the file add ```
blacklist ndiswrapper
``` and save. This will keep ndiswrapper from loading. If it boots, then I will try to help you get your card going without ndiswrapper. The newest madwifi package supports your card.

---

### Post by sirebral on 2008-12-28
I can't remember.  Can you just reboot with your network card shut off to see if NDISWrapper is the problem?  I am guessing you are using a different computer to connect on the forums.

---

### Post by Luffer on 2008-12-28
Well that's wasn't any use, sorry guys. I disabled the network device in my BIOS as suggested and rebooted only to get the same problem. Couldn't boot the OS, same lockup loop.

Back to the drawing board.....

---

### Post by sirebral on 2008-12-28
> **67GTA said:**
> The newest madwifi package supports your card.

This is what I would suggest also.  It seems that network cards are going to have a Linux port somewhere.  The manufacturer of the card will not always provide that, but the maker of the driver sometimes does.  And I think a Linux port needs to be created for Servers and Network Administrators.

Linux makes a good server OS, so Linux drivers are needed.  Corporate Microsoft and other companies seem to just brush them under the rug.

---

### Post by Luffer on 2008-12-28
> **sirebral said:**
>  I am guessing you are using a different computer to connect on the forums.

No, same laptop on dual boot with Vista. Have to keep going backwards and forwards... very frustrating :-)

---

### Post by sirebral on 2008-12-28
Yuck!!  Well then, let's start with the Laptop Make and Model.

---

### Post by Luffer on 2008-12-28
It's a Toshiba Satellite A210-11P, it's been running Ubuntu fine before this problem occured. Had wifi working, and even got all the whizzy graphics stuff fine.

Something changed in the Heron upgrade that has caused this, but what?!

---

### Post by Luffer on 2008-12-28
It's a Toshiba Satellite A210-11P, it's been running Ubuntu fine before this problem occured. Had wifi working, and even got all the whizzy graphics stuff fine.

Something changed in the Heron upgrade that has caused this, but what?!

---

### Post by sirebral on 2008-12-28
You are still using Hardy?  Have you tried Intrepid Ibex?

---

### Post by 67GTA on 2008-12-28
Here is the bug report: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/245779](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/245779)

It is not present in 2.6.27(Intrepid). I have the same card going in Intrepid without ndiswrapper.

---

### Post by Luffer on 2008-12-29
What version number is Intrepid? How do I upgrade the install if I can't boot up?

If I download an iso and burn a boot disc, is it easy to upgrade that way? I don't want to screw up my GRUB menu and exisiting Vista installation.

---

### Post by 67GTA on 2008-12-29
Intrepid is 8.10. You can do a fresh install of Intrepid without screwing anything up. Is it just Vista and Ubuntu on the hard drive? Just choose "manual" during install, and tell it to use the existing Ubuntu partitions. You might want to look at the release notes for the known bugs: [http://www.ubuntu.com/getubuntu/releasenotes/810](http://www.ubuntu.com/getubuntu/releasenotes/810) and solutions to some known bugs here: [http://ubuntuforums.org/showthread.php?t=966436 ]("http://ubuntuforums.org/showthread.php?t=966436")
Since you will have to reboot before updating to get your wireless working, you will want to look at the alsa shutdown bug. It is fixed after updating. 

To get your wireless card working:
Install and boot to desktop.
Load the install CD into Synaptic(package manager, there are packages on there).
From the CD repository, install "linux-backports-modules-intrepid-generic"
Open the restricted drivers manager(Menu>System>Administration>Hardware Drivers)
There will be two entries for atheros wifi support. You want to leave the one that starts with "5XXX" and disable the other. Reboot.

---

### Post by Luffer on 2008-12-29
Yeah, except as I explained above, the install wont work.

---

### Post by 67GTA on 2008-12-29
I must have missed it. Why won't Intrepid install?

---

### Post by 67GTA on 2008-12-29
Earlier in the thread you said "dual boot", so I assume you have Vista and Ubuntu both installed to your hard drive. Ubuntu has it's own partitions right now. When you install Intrepid, tell it to use the existing Hardy partitions. Nothing will be messed up. If there is something on the Hardy partiton you need, boot a linux live CD and copy it to your Vista partition until after the install.

---

### Post by Luffer on 2008-12-29
> **67GTA said:**
> I must have missed it. Why won't Intrepid install?

Weird, my post disappeared. I remember posting it too, very odd.

When I use the 8.10 Live CD I see the splash screen and after a while the screen goes black and the cursor blinks at the top left of the screen. Then nothing happens.

If I choose to the "install" option at the boot menu on the CD instead, after a few checks, it just stops doing anything.

---

### Post by 67GTA on 2008-12-29
Have you tried booting in safe mode?

---

### Post by Luffer on 2008-12-29
> **67GTA said:**
> Have you tried booting in safe mode?

How does one do that? I can't see a safe mode option on the CD boot menu.

---

### Post by 67GTA on 2008-12-29
After you choose your language, and before you hit enter to boot, hit F4 to choose the boot mode.

---

### Post by Luffer on 2008-12-30
Tried booting in safe mode and removed the quiet splash from the boot command. It still didn't boot up, but now I've got a command prompt instead of the GUI. Not sure what's going on here....

Screen shot attached:

---

### Post by 67GTA on 2008-12-30
That means your booted up, but without a desktop. Try booting again and add ```
acpi=off
``` to your kernel line at the grub screen. As soon as you see the grub screen, hit "e" to edit, then go to the line that starts with "kernel" and hit "e" again. Then go to the end of this line, leave a space, and type this in. Hit enter once, and then "b" to boot the line you just edited.

---

### Post by Luffer on 2008-12-30
Nooooo, I got the command prompt from booting off the LiveCD to do a fresh install. The GRUB screen was never involved, if I try and boot the installed Ubuntu then nothing happens.

---

### Post by 67GTA on 2008-12-30
That stinks. Did you originally install from the 8.04 CD? We really need to get a desktop loaded to try and find out what is happening. Do you have any other Linux CD's that will boot? If you could post the output of ```
dmesg
``` from a terminal, it might tell us what is happening. If your not afraid of the command line, and have a USB stick, we might be able to do it from the live CD.

---

### Post by tanxiaojing on 2008-12-30
My friends,

Are you hunting for cheap-vogue clothing and shoes?

I think this is the best choose for you, look at our website, I believe you will be moved by our products and service. 

Firstly, the clothing and shoes have high quality and reasonable price.
Secondly, the clothing and shoes have fresh and famous design that can make you charming.
Welcome to [www.nikeboss.com](www.nikeboss.com)
We are supplying Brands as following:

Nike,Jordan,Airforceone,AirMax,Adidas,Gucci,Dunk,James,Shox,Bapestar,Puma,Prada,Evisu,
Bape, ED Hardy.Chanel, Coach, Choel, Dior, Fendi, Timberland D&G, LV and so on.
Website: [http://www.nikeboss.com]("http://www.nikeboss.com") MSN: [http://nikeboss@live.com]("http://nikeboss@live.com")Service telephone: +86 029 86266726

---

### Post by Luffer on 2008-12-30
Where do I type dmesg? Is that at the command line when I boot from the LiveCD? It's the only way I can get a command line at the moment.

I'm not afraid of the terminal, though I don't understand it all. But I'll give it a go!

---

### Post by 67GTA on 2008-12-30
Once you get back to the command line on the live CD. Dmesg will show info from boot up. It usually contains info on errors also. It will put out A LOT of info, so if you have a USB stick, it will be easier. If not, we can try and copy it to your Vista partition. If you have a USB stick:

Boot CD
Plug in USB stick
run ```
sudo fdisk -l
```
Find your USB stick from the output. It will usually be something like /dev/sdf1 or /dev/sdc1
Once you have that, try to mount it with sudo mount /dev/sdf1(replace sdf1 with yours)
Hopefully the USB drivers are loaded, and it will mount.
Then run ```
sudo dmesg > /dev/sdf1/dmesg.txt
```
This will put a text file on the USB stick with the dmesg output in it.

If you don't have a USB stick, then do the same thing, but with your Vista partition. Replace sdax with your Vista number from the fdsik output.
Mount it, ```
sudo mkdir /media/vista
```
```
sudo mount /dev/sdax /media/vista
```
Then run dmesg and copy it to your Vista desktop
```
sudo dmesg > /media/vista/Users/yourusername/Desktop/dmesg.txt

```

Is your brain scrambbled? If you manage to get a copy of dmesg, post it here.

---

### Post by Luffer on 2008-12-30
Tried that with a USB stick, which was listed as sdb1, but when I typed:

```

sudo mount /dev/sdb1

```

I got the following response:

```

mount: can't find /dev/sdb1 in /etc/fstab or etc/mtab

```

Then I couldn't find any references to the Vista partition to try that method.

---

### Post by 67GTA on 2008-12-30
Try making a directory for it before mounting it.

```
sudo mkdir /media/usb
```

Makes directory to mount it in.

```
sudo mount /dev/sdb1 /media/usb
```

Mounts USB stick in /media/usb directory you created.

```
sudo dmesg > /media/usb/sdb1/dmesg.txt
```

Should put dmesg output on USB stick.

---

### Post by Luffer on 2008-12-30
It was all working this time up until this point:

```

$ sudo dmesg > /media/usb/sdb1/dmesg.txt

-bash: /media/usb/sdb1/dmesg.txt: No such file or directory

```

---

### Post by 67GTA on 2008-12-30
It may be a different name. You can change into the media directory and list the names of everything in there. You just need the name of the device so you know where to tell it to write the dmesg file. It may not be sdb1. You might only need to specify /media/usb. First just try 

```
sudo dmesg > /media/usb/dmesg.txt
```

If that doesn't work, see what is actually mounted in /media.

```
cd /media
```
```
ls
```

---

### Post by decoherence on 2008-12-30
> **Luffer said:**
> It was all working this time up until this point:

```

$ sudo dmesg > /media/usb/sdb1/dmesg.txt

-bash: /media/usb/sdb1/dmesg.txt: No such file or directory

```

I think 67GTA meant to say

```
$ sudo dmesg > /media/usb/dmesg.txt
```

which oughta put dmesg.txt on the root level of your c: drive or whatever

---

### Post by Luffer on 2008-12-30
If I try:

```

$ sudo dmesg > /media/usb/dmesg.txt
-bash: media/usb/dmesg.txt: Permission denied

```

---

### Post by 67GTA on 2008-12-30
Maybe try becoming root with ```
sudo su
``` and then run all of the commands.

---

### Post by decoherence on 2008-12-30
sorry i haven't been following the thread too well... but if it's an ntfs partition instead of

```
sudo mount /dev/sdb1 /media/usb

```

try

```

sudo mount -t ntfs-3g -o rw,uid=1000,gid=100,umask=0022 /dev/sdb1 /media/usb
```
this command should give you read/write with normal linux permissions.

i believe ntfs partitions are still mounted read-only by default. you can confirm this with the command

```
mount
```

and seeing if the line that contains /dev/sdb1 also contains "ro" (for read-only)

---

### Post by Luffer on 2008-12-31
***STOP PRESS***

I've managed to get to the Heron desktop by booting:

Ubuntu 8.04, kernel 2.6.22-14 (recovery mode)

When the menu comes up I select resume normal boot and then I'm in! But what do I do now to get things working properly? Can I up upgrade to Intrepid from here using a LiveCD? It doesn't detect my Atheros network card so can't run any updates via the update manager.

---

### Post by 67GTA on 2008-12-31
We need to figure out what is going on. Try to get us a copy of dmesg, /var/log/kern.log, and /var/log/messages.

---

### Post by Luffer on 2008-12-31
lol... yeah, that would be good! I'd love to know what's going on.

Attached are the files requested

---

### Post by 67GTA on 2008-12-31
I didn't see anything obviously wrong there. Post the output of ```
dmesg
``` from a terminal.

---

### Post by Luffer on 2008-12-31
Had to split the output into three files because it exceeds the size limit.

---

### Post by 67GTA on 2008-12-31
It seems to be choking on your CPU's. It starts out looking for one, and then halfway through starts over with a dual CPU setup. Do you have dual processors? Also, have you ever made/used a custom DSDT file?

---

### Post by Luffer on 2008-12-31
I've got an AMD Turion 64 x2 CPU. No idea what a DSDT file is and certainly never made one.

Having said that, I couldn't rule out the possibility...... I was told to do lots of things when my original Gutsy install was giving me problems. But I've no idea what now, it possibly may have involved this DSDT file what ever it is. I just don't know.

---

### Post by 67GTA on 2008-12-31
If we ever get you going again, you need a custom DSDT file. You have a lot of acpi errors at boot. I would be glad to help. For now, it seems that there is a problem between your motherboard and the kernel. This is always hard to solve/diagnose. My advice would be to try and boot Ubuntu from your hard drive and adding boot papameters. I laid that out earlier by editing the kernel line at the grub screen. Try these boot arguments one at a time to see if you can boot the hard drive normally.

noapic[FONT=monospace]
[/FONT]acpi=off
acpi=noirq[FONT=monospace]
[/FONT]nolapic[FONT=monospace][/FONT][FONT=monospace]
[/FONT]pci=noacpi[FONT=monospace]
[/FONT]nopcmcia  #only if you have pcmcia[FONT=monospace]
[/FONT]irqpoll
all_generic_ide[FONT=monospace]
[/FONT]pci=nomsi (to be avoided as long as possible)

---

### Post by Luffer on 2008-12-31
how do I use these? Is it a case of editing the kernel line by pressing F6 etc... then do I delete the "quiet splash --" bit and replace it with noapic etc?

If the first one doesn't work do I try the second one on it's own, or do I add it, so it becomes noacpi acpi=off etc....?

---

### Post by Luffer on 2008-12-31
Sorry, you mean from Grub don't you, so I press 'e' to edit etc... not F6. Same applies for my other questions though.

---

### Post by Luffer on 2008-12-31
Okay, **noapic** results in:

```

* Setting up kernel variables... [OK]
[92.787120] BUG: soft lockup - CPU #0 stuck for 11s [events/0:9]
etc....

```

**acpi=off**

```

* Checking minimum space in /tmp... [OK]
[66.796032] BUG: soft lockup - CPU #0 stuck for 11s [events/0:9]
etc....

```

**acpi=noirq**

```

* Checking minimum space in /tmp... [OK]
[67.970321] BUG: soft lockup - CPU #0 stuck for 11s [events/0:9]
etc....

```

**nolapic** - Odd this one, ended up with a BusyBox V1.1.3 Built-in shell (ash) and a (initramfs) prompt. Didn't know what that was about.

**pci=noacpi**

```

* Setting up kernel variables... [OK]
[76.793219] BUG: soft lockup - CPU #0 stuck for 11s [events/0:9]
etc....

```

**irqpoll**

```

* Setting up kernel variables... [OK]
[63.830852] BUG: soft lockup - CPU #0 stuck for 11s [events/0:9]
etc....

```

**all_generic_ide**

THIS ONE WORKS!!!!!!!!

Now what?

---

### Post by 67GTA on 2008-12-31
If that one will consistently let you boot without problems, then you can add it to your /boot/grub/menu.lst so it will use that argument at each boot. Then once you can boot normally, we can continue to try and diagnose. This kind of thing is fun for me:D Are you pulling your hair out yet?

```
sudo gedit /boot/grub/menu.lst
```

Then at the end of the "kernel" line (leave a space) add 

```
all_generic_ide
``` and save.

I have a HP dv6815. I had to make a custom DSDT file to get any Linux distro to work correctly. The operating system writes rules for ACPI to follow during install by reading the DSDT in your BIOS. If your PC/Bios manufacturer wrote it with Microsoft in mind, it can cause problems for Linux. Care to try a little experiment before you edit grub? Boot again and add ```
acpi_osi="Linux"
``` to your kernel line without any other arguments to see if it boots. If it does, it is just your DSDT file. our dmesg message said your bios was asking for that argument. If it doesn't boot with just that argument, then add both and post the output of dmesg again after booting with them.

---

### Post by Luffer on 2008-12-31
> **67GTA said:**
> If that one will consistently let you boot without problems, then you can add it to your /boot/grub/menu.lst so it will use that argument at each boot. Then once you can boot normally, we can continue to try and diagnose. This kind of thing is fun for me:D Are you pulling your hair out yet?


Not pulling my hair out no, but it is frustrating making such slow progress.... but at least it is progress! It would be great to have someone like you here for an hour to sort it all out and then tell me why it all went wrong.

For example, I'm doing all these things you're telling me, but I don't actually know what they are doing. What does the argument all_generic_ide mean? Why does that boot up successfully?

> Care to try a little experiment before you edit grub? Boot again and add ```
acpi_osi="Linux"
``` to your kernel line without any other arguments to see if it boots. If it does, it is just your DSDT file. our dmesg message said your bios was asking for that argument. If it doesn't boot with just that argument, then add both and post the output of dmesg again after booting with them.

Hmmm, the acpi_osi="Linux" argument worked fine and booted normally. So what should I do now? Add the all_generic_ide to my menu.lst file, or can I add the acpi_osi="Linux" instead? Which is better?

BTW: Thanks for all your help up to this point!

---

### Post by 67GTA on 2008-12-31
I would definitely prefer acpi_osi="Linux". The all-generic-ide argument just tells it to load all the ide modules and hope one sticks. I'll try to lay it all out. I might get confused myself. The acpi_osi argument affects how the operating system interacts at boot with your hardware. You could use any OS name there like "Windows XP", or "Windows NT", etc. The "Linux" argument tells the BIOS at boot that your using Linux, and makes it look at your hardware with that in mind. If the OS doesn't see/read your hardware correctly, it tries to use a generic driver/module to virtualize it and make it work. This can cause problems with CPU's, thermal temps, fans, hard drives, etc. You probably see lots of posts on the forums about these things not working right, and 99.9 percent of the time, they have a buggy DSDT file. If your DSDT file was compiled with the Microsoft compiler(Usually the case), it can cause errors when Linux tries to read it at boot. The other arguments vary. Acpi=off/noapic just makes it not try to look/configure any acpi functions on your PC. The rest are just variants of the ACPI system. Once you are comfortable with it booting everytime, you can get started debugging your DSDT. Open a terminal and run ```
sudo apt-get install iasl
``` This will install the Intel DSDT compiler. Then 
```
sudo cat /proc/acpi/dsdt > dsdt.dat
``` This will copy your DSDT file to your home folder as dsdt.dat Then ```
iasl -d dstd.dat
``` This should disassemble it and create dsdt.dsl, which contains the disassembled DSDT. Then recompile the DSDT with ```
iasl -tc dsdt.dsl
``` This will show you all the errors/warnings so we can fix them. Once that is done, we will load the new DSDT, and tell the system to use it instead of the default one. It sounds confusing, but it isn't that hard. Once you get the results from ```
iasl -tc dsdt.dsl
``` post them here, and I will try to help you get it fixed.

---

### Post by Luffer on 2008-12-31
Okay, just one slight niggle left. I've rebooted numerous times using the acpi_osi="Linux" argument. And it's been working, but not every time... twice it's done the ```
BUG: soft lockup - CPU #0 stuck for 11s [events/0:9] 
```
routine.

So is there still another underlying problem? Do we need to do more investigation or should I go onto DSTD stuff you just mentioned?

---

### Post by Luffer on 2008-12-31
Also, is it worth me connecting the laptop to the internet when I've got it booted in Ubuntu and let the update manager do its thing? Or are we better off keeping things as they are for now?

---

### Post by 67GTA on 2008-12-31
I would find an argument that makes it boot consistently before trying to fix the DSDT. Try the linux and ide together. Is this a new install with no updates? It might be worth updating first. There are a couple of bug fixes in there if you can spare the bandwidth.

---

### Post by Luffer on 2008-12-31
It was an install of Gutsy which had been working for a couple of months that was upgraded to Heron which has never worked until today. I'll let update manager do stuff and then get back to you when it's finished doing whatever it is that it does :)

---

### Post by Luffer on 2008-12-31
I'm posting this from my Ubuntu install now, but it's not all good news. While we seem to be getting somewhere, I've installed all the updates etc... but the boot is still not consistent.

Doesn't matter if I use ```
all_generic_ide
``` or ```
acpi_osi="Linux"
```
it still does the ```
BUG: soft lockup - CPU #0 stuck for 11s [events/0:9]
``` loop. Seems very hit and miss, but if I leave it as a standard kernel line it never boots.

---

### Post by 67GTA on 2008-12-31
I would see how buggy the DSDT is. Go ahead and run these commands. They won't change anything yet.
```
sudo apt-get install iasl
``````
sudo cat /proc/acpi/dsdt > dsdt.dat
``````
iasl -d dsdt.dat
``````
iasl -tc dsdt.dsl
```If the last command doesn't work, you may have to just type ```
iasl -tc
``` and then drag and drop the dsdt.dsl file from your home folder into the terminal. Then post the results from the last command.

---

### Post by Luffer on 2008-12-31
Is this what you mean?

```

Intel ACPI Component Architecture
ASL Optimizing Compiler version 20061109 [May 16 2007]
Copyright (C) 2000 - 2006 Intel Corporation
Supports ACPI Specification Revision 3.0a

dsdt.dsl     1: ACPI               Store (0x40, ^TPOS)
Error    4094 -    ^ syntax error, unexpected PARSEOP_NAMESEG, expecting PARSEOP_DEFINITIONBLOCK

ASL Input:  dsdt.dsl - 7244 lines, 279508 bytes, 0 keywords
Compilation complete. 1 Errors, 0 Warnings, 0 Remarks, 0 Optimizations

```

---

### Post by 67GTA on 2008-12-31
Yes that's it, but I expected it to have more errors. Open dsdt.dsl with text editor, go into preferences and turn on line numbers, and copy/paste line 1. That is where the error is.

---

### Post by Luffer on 2008-12-31
```
ACPI Warning (nsaccess-0709): NsLookup: Type mismatch on INFO (RegionField), searching for (Buffer) [20061109]
```

---

### Post by 67GTA on 2008-12-31
I've never seen that at the beginning of a DSDT file. It doesn't look good. It starts out with an error which probably explains why it is so "hit and miss". I hate to say it, but your laptop may not be very Linux friendly. I've only found three google hits for your model. Your thread, an older Ubuntu thread about your model and wireless running Gutsy, and a post about not being able to boot the live CD. If your serious about Linux, I would try other distros to see if they handle ACPI differently. My favorites in order are:

Opensuse (Gnome/KDE)
Mepis (KDE)
Mandriva (Gnome/KDE)
Fedora (Gnome/KDE)

---

### Post by Luffer on 2008-12-31
Sorry but I can't belive that, my Gutsy install worked fine. I only really had problems with the Atheros wireless network card, but even that was resolved. It wasn't until the Heron upgrade that things went wrong.

Even now I'm typing this in Heron having used your help to get this far. It clearly was compatible, so why would it suddenly not be now?

---

### Post by 67GTA on 2008-12-31
It is possible to get it running, but your probably going to continue to have eratic boot problems. As long as your fan(s) and thermal are within limits, and you can live with the few bugs present, then you will be fine. I was just suggesting trying other distros to see if they worked any better. They are all Linux underneath, but they are all developed a little differently on top. Maybe Opensuse or Mandriva will handle your ACPI a little better. It seems like your whole DSDT is incompatible with Linux, that is why you are having eratic problems. One possibility is to contact the laptop manufacturer about fixing the DSDT.

---

### Post by Luffer on 2008-12-31
Sorry, can you expalin what the DSDT is and what it does and why Ubuntu isn't compatible with my laptop?

---

### Post by 67GTA on 2008-12-31
I said your DSDT was incompatible with Linux, it can't read it properly. You CAN use Ubuntu, bu it will probably continue to be buggy. DSDT is an acronym for *Differentiated System Description Table*. This table contains the *Differentiated Definition Block*, which supplies the configuration information about the base system. It is always inserted into the *ACPI Namespace* by the OS at boot time. Then ACPI knows how to configure hardware like CPU's for example. Unfortunately, many hardware vendors and OEMs don't supply fully functional tables for every OS. They mainly focus on Microsoft. Yours looks like an extreme case because it actually starts with an ACPI error because it can't read the DSDT, instead of having a few errors some where in the DSDT table. This is resulting in a "shotgun" or "spray and pray" aproach when you boot. The PC or the operating system is not inteligent, so it depends on what info it gets from your hardware (while trying to read a buggy DSDT) at boot time. This also causes some hardware functions/capabilities to be "virtualized" or "faked" because a generic driver/module is used because it could not get the info it needs to match the actual hardware with the right driver. Hopefully ACPI will catch up to you in a few more releases. I'm actually looking now to see if someone has a compatible DSDT that might work with yours. I will let you know if I find something.

---

### Post by 67GTA on 2008-12-31
Speak of the devil. I found a couple of DSDT files for Toshiba that start with "DefinitionBlock" instead of "ACPI" like yours does. That is what ACPI was looking for. If you can zip up a copy of your dsdt.dsl and email it to me, I will try to edit it and send it back. Then you can recompile it and see if it still gives the error.

---

### Post by Luffer on 2008-12-31
Thanks but this will have to wait until tomorrow now. I'll be in touch!

BTW: HAPPY NEW YEAR!

---

### Post by Luffer on 2009-01-05
As I wasn't getting anywhere, I decided I had nothing to lose by getting getting the update manager to install 8.10. All was going well, but alas I still have boot problem. But it's a different one now, this time it hangs on:

```

* Setting up console font and keymap...

```

No more CPU hangs though, not sure if this is progress or not. But not sure what to try next!

---

### Post by 67GTA on 2009-01-05
Not sure about that one. It is from the /etc/init.d/console-setup script. It is supposed to use dpkg-reconfigure console-setup to set the keyboard map and font. Try poking around in /var/log to see if you can catch what is happening.

---

