---
title: "Install ubuntu on separate hard drive"
date: 2009-08-14
forum: New to Ubuntu
---

### Post by TRG1 on 2009-08-14
I am installing ubuntu on an older x86 machine (256Mb ramx, 733Mhz processor, 232Gb HD, 9Gb Hd).  The resident OS is WinXP.  I am doing this mainly out of curiosity so I really don't want to change anything about my basic system until I know for sure ubuntu is going to work well.  The small hard drive is completly empty, so my idea was to install ubuntu there, but the hard drive is not bootable as it is and the ubuntu installation procedure does not give me the option of installing there.  Is there a way to make both hard drives bootable and select the one I want at startup?  I know I can switch the drives around to make the small one the boot drive, but is there another option?  Thanks.

---

### Post by Bartender on 2009-08-14
Well, what do you mean by the HDD is not bootable?
Is this a hardware problem, as in the drive is damaged, or the data cable isn't firmly attached, or the jumpers on the back aren't set up correctly?
First thing I'd do is get into BIOS and see if BIOS recognizes the smaller disk.  If it doesn't then the jumpers might be on wrong.

---

### Post by CorruptedClone on 2009-08-14
When you say "not boot-able" do you mean that the Windows hard drive takes priority over it (easily fixable using BIOS), or that it does not appear in the partition stage of the installer?

I recently installed Ubuntu on a machine with similar specs; after a few minor setbacks, I'm glad to say it is performing admirably (especially since the machine in question was previously bricked!)

---

### Post by TRG1 on 2009-08-14
The small drive did not show up in the bios boot selection list, so I will look to see what I must do to make it show up there.  Thanks.

---

### Post by TRG1 on 2009-08-14
Ok, I opened the box and changed the jumpers from CS on both to master and slave; this changed nothing.  For reasons that I'm not clear on the empty drive is labeled C: which is a 10MB drive and the 250 MB drive is labeled E:. D: is the CD-ROM.  The BIOS recognizes all the drives with the two hard drives being primary 1 and primary 0 and the CD-ROM being secondary 1.  The empty hard drive does not show up on the boot list.  My question remains; how do I install ubuntu on the 10MB drive?  

FYI, the computer originally had 2 10MB drives and I eventually replaced one of them with a 250 and left one of the 10's empty for who knows what.

TRG

---

### Post by bodhi.zazen on 2009-08-15
From your I can not tell if it is a BIOS problem or a failed hard drive. Does the hard drive work in windows ? But Ubuntu does not recognize it ?

---

### Post by egalvan on 2009-08-15
So are the drives **MEGA** bytes..
or are they  **GIGA** bytes

You have called them by both prefixes...

If the drive is truly a **TEN MEGA BYTE** drive,
then an Ubuntu install will not fit...

---

### Post by sideaway on 2009-08-15
I'd give him the benefit of the doubt and say GB. If the drive works in windows but is not detected by BIOS that is very strange....

---

### Post by egalvan on 2009-08-15
As for the BIOS not seeing the "smaller" drive...

I suggest the following...

disconnect ALL drives....

jumper the "small" drive as MASTER

and connect it as the only drive on the primary controller.

boot and see what BIOS says about it...

if problems arise, then try another drive cable...
if problems persist, then the drive may be toast.

you may want to download PartedMagic LiveCD to do more checking and partitioning... 
it boots a bit faster than an Ubuntu LiveCD.

partedmagic.com

---

### Post by TRG1 on 2009-08-15
Sorry, I meant Gb on the drive sizes.  The BIOS does recognize both hard drives, but only one shows up on the boot sequence list and just now rechecking this I see the the drive listed in the boot sequence is actually C:, which is the empty drive.  So, I am evidently booting from E: which is connected as the master, while C: is the slave.  This still leaves me not knowing how to install ubuntu on C:.  I read a number of the other threads on this subject in the intervening period and did not find any that I could make sense out of.  I also went through the installation process again and could not arrive at a point where I was able to select drive C: as my target.  I'm going to read a little more and if I don't find an answer in short while, I'm just going to go ahead and partition the E: drive.  Thanks for all your help.

---

### Post by Bartender on 2009-08-15
+1 on egalvan's suggestion.  Start out with the little drive.  

Is your IDE data cable 40-wire or 80-wire?  See. here's the thing - the CS option only works on an 80-wire data cable.  If you set a 40-wire cable and an 80-wire cable next to each other on the table, the difference is obvious.  If you don't have one of each to compare, the best advice I can offer is to start at one edge and count.  You can tick across the grooves with a fingernail to help you keep track.  By the time you're halfway across the data cable it will be clear whether it's 40 or 80.
If it's a 40, jumper the little drive as Master, plug it into the further of the two clips, and boot into BIOS.  Does the PC see the drive, and identify it correctly?  If so, boot into your install CD or a GParted LiveCD and see if either CD recognizes the drive.
Work back from there.  Take the little drive off, jumper the big drive to Master, boot into BIOS.
Then try both drives, configured both ways.  Little one Master, then the big one Master.  Make sure to keep the jumper position and the clip position correct; the drive that's jumpered to Master should be on the furthest clip.
Take notes!
Sooner or later something's going to make sense - the results will point to a bad power plug, a bad data cable, whatever.  It could be something really weird like a damaged pin or a failing controller board on the little drive.  
Start with the simplest setup and work back from there.

If the little drive is seen when it's by itself, can you install Ubuntu to it?

---

### Post by TRG1 on 2009-08-16
I disconnected the 250GB drive and booted with the ubuntu install disk and installed ubuntu on the 10GB drive.  With this setup, the computer would boot to ubuntu and seemed to run very well.  I've now reconnected the 250GB drive and the computer now boots to XP.  Next step is to figure out how to get it to boot to either system with both disks hooked up as is. I suppose this means running the ubuntu installation again. 

It was nice to see how well it ran though.  I definitely have seen enough to want to proceed with ubuntu.

---

### Post by meindian523 on 2009-08-16
You need to install Grub,the Linux bootloader again,no need to run the entire installation again.And oh,welcome to the Ubuntu family.

---

### Post by TRG1 on 2009-08-16
Ok, thanks for the tip.  For now I have just switched the jumpers on the hard drives to make the small drive the master. It booted right up on ubuntu so I'm typing this from my new ubuntu box.  Works great!

---

### Post by Bartender on 2009-08-16
OK, something else to look for - I don't know when they started introducing this into the BIOS options.  At least 8 years ago or so.  Problem is finding it. :)

Your BIOS may have an option built into it so that as the PC is booting up you tap on a key.  If the option is in there it'll be F8, Del, Enter, or similar.  You tap the key, the PC stops booting, and you get a DOS-looking window that asks which bootable device you want to use.  It should list every device that BIOS recognizes as bootable - floppy, optical, and both of your drives.  This is an easy, painless way to choose between drives without screwing around with bootloaders.  Windows is installed on one drive, Linux is on the other, and you make the choice.  The only thing is you have to be sitting there tapping on the key as the PC is booting.  

Sooner or later you'll find that you're starting up in Linux or Windows most of the time, and then you can set your default either by moving clips and jumpers or picking the default in BIOS.

If you can't tell for sure whether your BIOS has the option I describe above, tell us what model PC you have and who makes the BIOS.  It should be identified as AMI, Phoenix, etc.

---

### Post by TRG1 on 2009-08-16
The machine I'm working on is a Dell Precision 220 (A09 BIOS).  I can access the BIOS at startup (F2) to set the boot sequence, but this does not allow me to choose between hard drives.  Is there another procedure that allows you to select which hard drive to boot from?

---

### Post by LewRockwell on 2009-08-16
> **TRG1 said:**
> The machine I'm working on is a Dell Precision 220 (A09 BIOS).  I can access the BIOS at startup (F2) to set the boot sequence, but this does not allow me to choose between hard drives.  Is there another procedure that allows you to select which hard drive to boot from?

not with that machine/BIOS

it will only boot from the primary(master) hard drive

.

---

### Post by LewRockwell on 2009-08-16
our recommendation is to physically set the larger drive as the master and the smaller drive as the slave

you will need to make sure they are connected to the proper points on the IDE ribbon cable leading to the primary IDE connection on the motherboard(sometimes these are colored blue to highlight the fact that that connection is the primary one)

for your frankenbox kit-up with the two drives, each with it's own active operating system...you'll need to install the Grub Bootloader

the bootloader installs to the master boot record of your primary hard drive and when you boot the machine it directs the system to your /boot/grub/menu.lst(which is normally found in your ubuntu partition, but may be placed in a small partition created for that purpose on your primary hard drive)

for this task you may use the Ubuntu LiveCD or any one of a number of other distributions that install grub

we use both Puppy Linux LiveCD and Super Grub Disk

.

---

### Post by TRG1 on 2009-08-16
I looked around for a way to install GRUB, but wasn't able to make much sense out of any of it, so I decided to just go ahead and do a parallel installation of ubuntu and let it install itself on the large hard drive along with WinXP.  I went through the installation procedure without deviating from any of the standard choices.  It was exactly the same as when I installed in on the small hard drive.  Now, when I tried to boot the machine, the first thing I get is, "Grub loading, please wait....   Error 18", and then the machine is locked up.  This of course is the reason I didn't want to install it on the main hard drive in the first place, but now that it's done, how do I undo it?

---

### Post by OooBuntuRox on 2009-08-16
> **TRG1 said:**
> I looked around for a way to install GRUB, but wasn't able to make much sense out of any of it, so I decided to just go ahead and do a parallel installation of ubuntu and let it install itself on the large hard drive along with WinXP.  I went through the installation procedure without deviating from any of the standard choices.  It was exactly the same as when I installed in on the small hard drive.  Now, when I tried to boot the machine, the first thing I get is, "Grub loading, please wait....   Error 18", and then the machine is locked up.  This of course is the reason I didn't want to install it on the main hard drive in the first place, but now that it's done, how do I undo it?


While it depends on your bios, My preference is to set both drives to CS (cable select). That is the option that seems to allow you to select the boot drive using the bios without setting either drive to a master/ slave setting. If you were able to install to a single drive using the linux install cd, then the hd may not have been properly partitoned, formatted or perhaps it was not even initialized yet. I have also seen Linux install to an HD with a bad controler card that windows did not even recognise as being available. It is hard to know exactly what was going on. For instance. If you have a dab contoler card (on the HD). It may work fine as a secondary drive. I think the controler on a secondary dive may not be used in the same way (perhaps not at all) as a controler on a primary drive. 

Being that linux (ubuntu) installs so quickly, I would just reinstall it. If you have trouble, boot using your windows drive, then reformat (or repartion if needed) your Ubuntu drive to erase the installation.

Then reinstall using your ubuntu Live CD, install, etc. Ubuntu should install the boot loader this time (being that you had a successful ubuntu install).

OooBuntuRox :guitar:

---

### Post by TRG1 on 2009-08-16
You can read about Error 18 at [http://wiki.linuxquestions.org/wiki/GRUB]("http://wiki.linuxquestions.org/wiki/GRUB") if you like.  My hard drive is 250GB which is beyond the BIOS capability so the thing won't boot.  I'm going to follow the repair recommendation at that url.

p.s. I ran the fixmbr and that restored the full use of the large hard drive.  I think I'm finished with ubuntu.  What little I used it I found that my browser (chrome) runs faster on my stripped down XP machine (it has minimal software and non of the typical windows overhead bs) than the one running in ubuntu.  I was hoping to look at some other things, but it does not appear to be worth my trouble.  One reason for looking at ubuntu was to get an operating systems with fewer bells and whistles, but hopefully simpler to install and maintain and more reliable and more secure over the long run.  I didn't get the feel from my brief exposure that these were things I would get.  I had a lot of trouble with this two hard drive installation and that cannot be all that uncommon.  I forgot to mention that the machine locked up on me when I was doing a trial run booting from the CD. Maybe it's because it's a 10 year old computer, but it runs XP without much trouble.  Best of luck to all you people in the ubuntu community, but I'm outa here.

---

### Post by meindian523 on 2009-08-18
Ok,goodbye.Me hopes this doesn't become another "Come back" thread.

---

### Post by Bartender on 2009-08-18
I applaud the OP's persistence and willingness to research the problem.  However, I object to his conclusions.

IMO a two drive dual-boot is just as easy to create, and provides more options than, a single drive dual-boot.

The stone-age BIOS is what made the project unworkable, not Ubuntu or GRUB.

---

### Post by meindian523 on 2009-08-19
LOL.OP is comparing full featured Ubuntu with stripped down XP.Apples and Oranges!

---

