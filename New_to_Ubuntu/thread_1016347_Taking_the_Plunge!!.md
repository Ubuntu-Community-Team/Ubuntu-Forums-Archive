---
title: "Taking the Plunge!!"
date: 2008-12-19
forum: New to Ubuntu
---

### Post by tazbo28 on 2008-12-19
Ok, so i guess  you could call me a super-newb, but im trying to cut-off the microsoft cord!! the only thing is- Im an animator and i use Maya 2008 heavily as well as Adobe CS3 suite. i have seen info on Maya 7 for linux and the Gimp. so i want to try them out. But i cannot delete my xp drive just yet. there in lies my prob i guess.

so ive already downloaded the 32bit and 64bit iso files for ubuntu 8.10. i burned the 64bit version to a cd. i wanted this version mainly cause im running 4gb of ram and a new intel q6600 quad core cpu. i also have a newish asus p5k-e wifi mobo as well. so this would all help with my video editing and 3d work. however my HP cd rom/burner will not show in my bios unless my main hard drive(xp) is connected as well.  

my main problem here is that my computer only allows to have two IDE devices connected at a time. so i have 2 hard drives and a cd drive. at any given time i can only have two connected! this sucks for me. the secondary drive-20gb quantum fireball drive is fat32- this is where i want to install Ubuntu. Im just having a bit of trouble getting there. I dont want it to be connected in any way to my windows drive- 160gb maxtor ata/100 ntsf format. 

ive installed the wubi thingy- then went into ubuntu from reboot-(man this OS is SOOOO FAST!!!) i tried to use the "install" icon on the ubuntu desktop. went through the guide, and then chose to setup the install on my 20gb drive with 15gb as the main partition and 5gb as swap? i figured this would work, however after it started it would begin the install and stop and give me an error. and would not let me install in this way. it kept sending me back to the setup-partition part of the wizard. this is so frusterating but i am patient. all i want to do is install this on the extra ide hard drive that i have. both are IDE however. 

anyone----please!! show me the way of the force!! hehe. i would greatly appreciate it. 

p.s. i am horrible at inputing commands in the command lines thing!! please bear with me!

thanks, vince.

---

### Post by Muffinabus on 2008-12-19
The two IDE devices at a time isn't a problem at all.  When I installed Ubuntu I completely disconnected my XP drive.  If you install it this way, you can boot into Ubuntu then edit GRUB and tell it where your windows drive is located so that you can dual boot in to both of them via GRUB upon a restart.

I've never installed or used Wubi before though, so I can't offer any help there.

If you want to do it the other way, unplug your windows drive (and set it to slave with your Ubuntu drive set to master), install Ubuntu on your desired drive, plug back in your Windows drive, boot up into Ubuntu, then type this in Terminal:

```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
sudo gedit menu.lst
```

then at the very bottom of menu.lst add:

```
title           Windows
root            (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1
```

The first line changes your directory, second line creates a backup of menu.lst just in case, and the third line opens up menu.lst as a super user so you can edit and save it.

The second code block is you tricking Windows into thinking that it is a master drive when GRUB boots into it.  Windows is very picky about this, it doesn't like to play nice with other operating systems.

Assuming you do everything right, GRUB should display upon restarting and give you the option to boot to Ubuntu and Windows.

---

### Post by albinootje on 2008-12-19
> **tazbo28 said:**
> 
ive installed the wubi thingy- then went into ubuntu from reboot-(man this OS is SOOOO FAST!!!) i tried to use the "install" icon on the ubuntu desktop. went through the guide, and then chose to setup the install on my 20gb drive with 15gb as the main partition and 5gb as swap? i figured this would work, however after it started it would begin the install and stop and give me an error. and would not let me install in this way. it kept sending me back to the setup-partition part of the wizard. 

Can you provide us the details of that error message please ?

And with such a fast machine, you can very safely play with Ubuntu first by installing VirtualBox and install Ubuntu in that.
No boot-loader problems, and Ubuntu installations in VirtualBox should always work without any problems.

[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

---

### Post by tazbo28 on 2008-12-19
awesome. it sounds pretty straight forward except one thing- i dont have the pins for the drives to indicate which is main and slave. so the only way i usually can do this is by re-ordering them along the connector ribbon, and changing the boot order in the BIOS. other than that- do i install via windows again? because if i leave them both connected i cannot connect the cd rom drive?

i do have a second cd rom drive that my computer seems to recognize- but when i put the cd in there, and try to boot- it says "Error loading Operating System."

---

### Post by tazbo28 on 2008-12-19
ok so im having a bit of trouble trying to figure out how i got the install to work last time around. I did the WUBI install this time. basically i just extracted the contents of the ISO file and ran the Ubuntu menu.exe. i clicked the wubi option(2nd option) and then it installed just fine. 

now i want to pretty much move the installation to my 2nd hard drive so i dont have to have anything on my windows drive. only thing is that now, the "install" icon i had seen before is not on the desktop anymore. so how do i go about it now? 

or do i have to try something else now. an issue im having, is that when i connect my XP drive and the CD rom drive, i can use both, therefore- i can boot from either, but if i only connect my secondary drive, and the CDrom drive- the BIOS will not recognize my CDrom drive. so i wouldnt be able to boot from it in order to setup Ubuntu. im really not sure how im going to solve this problem- 

unless i can install this without having to have any CDrom drive connected.

---

### Post by Moop on 2008-12-19
You could try installing from a usb thumb drive if that's a option. 

Your cd drive should have master/slave pins on it. Check those and see if you can get your bios to recognize it.

---

### Post by tazbo28 on 2008-12-20
ok. i got the pins fixed and the cd worked!!! i booted the cdrom drive first and the 20gb drive second. i got to the install menu, and i clicked on the "check disk for errors" and it did its thing for a while. and it returned a message "I/O image error" and a reboot button. i tried a few times to install and it kept giving me this same message. 

so im going to try a usb install- do i just put the iso on the usb stick and boot from there? 

im using the amd64 bit iso.

---

### Post by Muffinabus on 2008-12-20
Perhaps the disk you burnt is corrupt, or maybe even your download?  I'd check the hash codes on your download to verify that isn't corrupt first, if that's fine maybe try burning another CD.  Or you can try the usb drive install, heh.

---

### Post by zman58 on 2008-12-20
It sounds like you may be having a problem with the CD media you burned. Really, the CD install should work properly. Make sure you have the ISO file on your local hard drive and burn it to CD using CD burning software for Windows. Once you get the CD, you should be able to test it to verify it is working properly.

Do not change your Windows drive to a slave. Leave it alone. Keep in mind that once you install linux to the add-in drive, the you will continue to need that drive to boot your system. This is because Ubuntu will install GRUB, a bootloader utility, that will start before any OS can be selected. GRUB will be installed on that add-in drive. The system will then boot first to GRUB on the add-in drive and allow you to select Windows or Ubuntu.

Another option is to forget the add-in drive and install Ubuntu onto the main 160 GB drive. The partitioner in the Ubuntu install program will allow you to create some freespace on the Windows drive and it will add two new partitions into that freespace to install Ubuntu. It will "resize" the Windows partition to create the necessary freespace.

As for the IDE master/slave identification all you have to do is set the jumper to CS for "Cable Select" on both drives. Then the drive you plug into the end of the cable is always the master and the drive you plug into the middle connector on the IDE cable is always the slave---cable select.

Yet another option you might want to consider which will not impact your Windows system at all would be to set your bios boot order to first boot from USB. Once you do this then you can temporarily disconnect the Windows drive. Get a USB external hard drive and plug it into the system. Install UBuntu to the external USB hard drive. Reconnect the Windows drive. Now whenever you want to boot Ubuntu, just plug in the USB hard drive and boot your system. When you want to boot Windows just unplug the USB hard drive and boot the system. This way you can use Ubuntu to your hearts content and not impact your Windows system one bit. USB hard drives are very fast so the system will run well under Ubuntu.

Using the USB drive as a test bed provides a great way to try out other versions and distributions of Linux too. Perhaps you might find that Ubuntu 8.04.1 LTS might be a better choice. Ubuntu 8.10 is more bleeding edge and you may find some issues, such as lack of Nvidia drivers (not ready yet) as of the last time I checked a couple weeks back.

---

### Post by -kg- on 2008-12-20
> Ok, so i guess you could call me a super-newb, but im trying to cut-off the microsoft cord!! the only thing is- Im an animator and i use Maya 2008 heavily as well as Adobe CS3 suite. i have seen info on Maya 7 for linux and the Gimp. so i want to try them out. But i cannot delete my xp drive just yet. there in lies my prob i guess.

You know, I have read this thread and I keep thinking about your quoted statement.

I don't know what level you create animations at, but it seems to me that, if you can afford it, you might want to upgrade your hard drive system.  Among other things, I do video editing projects, and while a 160 GB hard drive is "adequate," it still leaves little room for larger projects.  I was doing video editing using a 120 GB hard drive for my Windows installation, and an additional 160 GB hard drive for more storage.  The 120 GB drive started going out, so I added a 400 GB drive to replace it.  Now, in addition to the other two drives, I have a 1 TB SATA drive and a 1 TB external drive for portability.

You might want to consider replacing that 20 GB drive (I didn't even know you could get them that small anymore!) with a much larger drive.  15 GB isn't much of an installation size, considering you are wanting to play with animation with Linux.  You are likely going to need some considerable storage space; much more than you're going to have in 15 GB.

I am assuming you have the 20 GB set as a slave drive.  I would get *at least* a 400 GB drive (as large as possible, really) and install it in place of the 20 GB.  Then you should have considerable room for installation and storage, and you should have more than enough space for your Ubuntu installation and anything else you want to try.

You can leave that drive as a slave drive and should be able to install to it.  The installation process should install GRUB in the MBR of your primary drive (you will be able to boot Windows as well as Ubuntu) and you should be able to do the actual installation on the slave drive, probably using the manual partitioning selection.  I'm not sure if the Guided installation process would consider open space on the secondary drive, but if so, you would be good to go.

One thing I would suggest...I would first boot to the live CD and select "System/Administration/Partition Editor," select the new drive, and format the whole drive as an Extended partition (that is, unless you plan to install Windows on that drive).  Linux will run from an extended partition, and you will be able to create any number of logical partitions within it, instead of being limited to 4 primary partitions.

Windows will see and be able to access an appropriately formatted logical partition, so you will have extra storage capability there, and plenty of room for any Linux partitions you see fit to have, and room to expand should you need it.

> ...im running 4gb of ram and a new intel q6600 quad core cpu...

...went through the guide, and then chose to setup the install on my 20gb drive with 15gb as the main partition and 5gb as swap?

Like I said above, I don't know the memory requirements of animation, but 15 GB doesn't seem like much.  As far as swap space, the conventions are twice as much swap space as RAM, so you would need around 8 GB of Swap space since you have 4 GB of RAM.

---

### Post by tazbo28 on 2008-12-20
wow such a wealth of info. 

so to clear things up- i got it working!!!! im pretty excited. I used a method of booting from my usb flash drive and installing from there. I also used UltraISO to create my bootable iso file on the USB flash drive. So i install from that and it worked flawlessly!!! such great advice from everyone, and im happy to see that the Ubuntu community are so nice and helpful. it is really a reassuring thing to know for the future.

i would like to add that i do have an Nvidia video card- QuadroFX 3450 to be exact. And i guess seeing as how there are no drivers, it seems to be working quite nicely. I however dont think that the 3d acceleration will work then since there are no drvrs. 

Also, the animation i do on my computer isnt spectacular yet but i dooo desperatly need a bigger hard drive. I am trying to save up for a cheap 500gb. But im hoping to get a 1tb soon. then ill have enough comfortable room to play. Im also a student still so you can say my projects arent quite huge yet!! lol. but i am working on a new project that will be a short film for my reel. so im going to need plenty of space to work with. and with Maya 2008 taking up 2+gb and CS3 7+gb of space alone! it will be tough to stretch out my space indeed. My 20gb hD is from a really old hp computer that my sister is using. she now has a 320gb hd. so she doesnt need it. Ive had my 160 for like 2yrs now too so its about due for an upgr. i appreciate all your advice, and look forward to getting more info on things here soon!! 

P.S. if anyone can donate any working, clean 100+gb hard drive to a poor college student it would be sooooo greatly appreciated!! thanks again guys! 

-vince-

---

### Post by albinootje on 2008-12-20
> **tazbo28 said:**
> ok. i got the pins fixed and the cd worked!!! i booted the cdrom drive first and the 20gb drive second. i got to the install menu, and i clicked on the "check disk for errors" and it did its thing for a while. and it returned a message "I/O image error" and a reboot button. i tried a few times to install and it kept giving me this same message.im using the amd64 bit iso.

You should check the md5sum of your downloaded iso image.
For Ubuntu 8.10 they're mentioned here : [http://releases.ubuntu.com/intrepid/MD5SUMS](http://releases.ubuntu.com/intrepid/MD5SUMS)
Find a Windows program which can calculate md5sums and produce a md5sum of your downloaded iso image.

Next thing is that it is recommended to burn the iso image at a lower speed to prevent bad quality end results.

---

### Post by tazbo28 on 2008-12-20
well i got it working. but thanks anyways. All i have to do now when i wish to load windows xp is to change my hdd boot order in the BIOS so that it boots my XP drive first. mainly because the boot menu that comes up right now (GRUB?) doesnt seem to be working for xp when the ubuntu drive is primary in the BIOS. 

but i dont mind. one extra step is fine for me right now. My first order of business, however is to really try to get Maya 8.5 installed. I dont have a license file though. Ive used Maya through "alternative torrent methods" mostly and i cant seem to find any info on how to get one of these versions to work on Linux. mainly i just found this thread--

[http://ubuntuforums.org/showthread.php?t=66859&highlight=maya](http://ubuntuforums.org/showthread.php?t=66859&highlight=maya)

it seems like i might be able to follow the guide. I have the maya files for LinuxAMD64 bit-which is what im using at the moment. and i guess i can try to load it up. however, if and when i get to the license install part, im sure ill run into a wall not having an official license. I would really buy this product if i could afford it, but i am a college student with no job! so im really not in a position to do so. 

I wondered also, seeing as how most software key creation tools work in windows- in theory cant you just use these generated keys to enter into the aw.dat file in Ubuntu? i really dont want to over-step forum rules with this, even though these methods and tools are generally well known and documented throughout the internet. but if anyone could let me know why it will or wont work. Im just curious as to how linux handles the license file-aw.dat.
thanks in advance.

---

### Post by jazott3 on 2008-12-20
in terms of hardware:
I'm running the intel q6600 and 4gb ram on the 32 bit and its no difference. the differences are if you go above 4gb then you will want 64 bit.... but i'm not sure how animators consider their hardware, so if you don't plan to go above 4gb ram anytime soon just stick with the 32 bit...

---

