---
title: "Windows 7/Ubuntu dual boot - Noob help please :)"
date: 2011-01-29
forum: New to Ubuntu
---

### Post by aaron88_7 on 2011-01-29
Hi guys, this is probably a stupid question but I think I might be going about installing Ubuntu in the wrong way.

Basically I've got a new PC I built last week and I have 2 500GB drives in RAID 0 with 3 partitions set up.  1 is for Windows 7, one is for where I'd like to install Ubuntu, and one is a general data partition.

How exactly do I go about installing Ubuntu without fubar-ing Windows 7?  I thought it would be pretty simple considering I've already set up the partitions in advance, but after running the CD I burnt I wasn't sure how to install it on the Ubuntu partition I have already created, nor was I sure of what method of formatting to choose.  

This is basically where I get to before I start scratching my head....

So I go ahead and choose to select my partition...
[IMG]http://img517.imageshack.us/img517/4483/screenshotinstall.png[/IMG]


Then I can see the partition I created for Ubuntu; it is the one I have selected in the picture below at 64424MB (volume 3).  The one right above, (volume 2), at 85878 is the Windows 7 partition, and below is the data partition, (volume 5).  The 104MB partition was created when I installed Windows and I'm not exactly sure what that is for but I'm not going to mess with it:
[IMG]http://img39.imageshack.us/img39/2586/screenshotinstall02.png[/IMG]


When I click "change" for the partition I want to use for Ubuntu ,(volume3), I get this next window and I don't have the slightest clue what options to choose here, but I read somewhere linux can't be formatted with NFTS which is what I already did previously.  What should I format it with? (picture got a little cut off, there were a lot more to choose from than what is shown below)
[IMG]http://img194.imageshack.us/img194/5578/screenshoteditpartition.png[/IMG]

If I back out from that and go into the previous screen I get more options I'm unsure of what to do with under "Boot Loader":
[IMG]http://img34.imageshack.us/img34/3525/screenshotinstall04.png[/IMG]


I don't want to screw up my boot loading sequence so I figured before I mess something up I better post a question and ask for some advice first.  I've used Ubuntu briefly before but I did it with a WUBU installation.  Do I need to create a small partition similar to the small 104MB partition Windows created, or will Ubuntu do that for me?  Should I have waited on creating the partition for Ubuntu?  Also, what happened to volume 4?  I just now noticed that was missing, hmm, odd?

Any and all help would be greatly appreciated! :KS

If it matters I'm trying to install Ubuntu 10.10 64 bit and I currently have Windows 7 Ultimate 64 bit (OEM)

---

### Post by Quackers on 2011-01-29
Ubuntu won't install in a NTFS formatted partition. It will need to be formatted as ext4 (others will work, but ext4 is now the default). The main Ubuntu partition should have a mount point of " / ". A separate home partition can also be set up with a mount point of "/home", if desired. A swap space should also be considered.
However raid0 setups require special instructions for installing grub iirc. 
Hopefully ronparent will be along some time to give more detailed info in that respect :-)  He'll put you right :wink:

---

### Post by jd2012 on 2011-01-29
I too did something similar to this (Dual booting Win7 + 10.10) Not knowing at the time what exactly what to do I ended screwing up the windows MBR (Easy fix)

The only advice I can offer at 1 oclock in the morning I KNOW the format has to be either
ext3 or ext4 for the partition which you are installing 10.10 (I used ext4)

Also dont worry too much about "fu-barring" (As you said) Windows (So long as you dont format it) It can usually be brought back to life with start-up repair.

Sorry I couldnt be of more help as i dont want to steer you in the wrong direction. :confused:

---

### Post by mikewhatever on 2011-01-29
Linux distros don't use ntfs file system for their installations. Delete the partition you created for Ubuntu and make a new one when installing. Pick the file system to be ext4 and the mount point - /.
If you don't want the boot loader installed to the MBR, select the Ubuntu partition instead, in which case, you'll have to figure out how to boot it.

---

### Post by jd2012 on 2011-01-29
> **mikewhatever said:**
> 
 select the Ubuntu partition instead, in which case, you'll have to figure out how to boot it.

Correct me if im wrong (plz), but can he not put the bootloader on /dev/sda (which will create the GRUB menu) and simply fix his W7 MBR with the W7 Install disk via start-up repair? This is what i did, and "Windows 7 (loader) was added to the bottom of the GRUB menu.

Again, please correct me if im wrong as I am also learning.

---

### Post by Quackers on 2011-01-29
Normally that would be fine. However a raid0 setup has difficulties booting that way.

---

### Post by jd2012 on 2011-01-29
> **Quackers said:**
> Normally that would be fine. However a raid0 setup has difficulties booting that way.

Ah, understood. My mistake @ forgetting about RAID :lolflag:

---

### Post by mikewhatever on 2011-01-29
> **jd2012 said:**
> Ah, understood. My mistake @ forgetting about RAID :lolflag:

Besides, the OP doesn't want to 'screw up [the] boot sequence'.

---

### Post by aaron88_7 on 2011-01-29
> **mikewhatever said:**
> Linux distros don't use ntfs file system for their installations. Delete the partition you created for Ubuntu and make a new one when installing. Pick the file system to be ext4 and the mount point - /.
If you don't want the boot loader installed to the MBR, select the Ubuntu partition instead, in which case, you'll have to figure out how to boot it.

Couldn't I just format it again in ext4 this time?  If I delete it and re-create it wouldn't that put it after the data partition?  I wanted to keep both the Windows 7 and Ubuntu partitions at the beginning of the drive if possible, (to be a little more speedy).

I'm still a bit confused about the boot loader and how to set that up properly.  Also, what is MBR?

Lastly, what steps do I need to take with the RAID 0 setup?  I assumed Ubuntu would just see it as a single drive and I didn't expect that to bring any issues.  First time doing RAID so...yea, lots of noob questions here lol

---

### Post by YesWeCan on 2011-01-29
> **aaron88_7 said:**
> I'm still a bit confused about the boot loader and how to set that up properly.  Also, what is MBR?
Don't worry. Dual boot installations are not easy to understand at first and many people, including myself, have been confused too.

MBR= master boot record. (see: [http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record))
Every disk has one. It is located at the start and is 512 bytes long. It is the instructions to the bios software to tell it where the operating system boot loader is located on the disk. It is the way the bios transfers uP control to the OS boot loader.

Originally, your RAID0 disk had Windows 7 installed. The MBR contained code to tell the bios to transfer uP execution to the Windows 7 boot loader. This is located in the 104MB partition.

When you add Ubuntu, you need to tell the bios to transfer uP execution to the Ubuntu boot loader (also called Grub). This requires the MBR to be modified.

The Grub bootloader is quite clever and should detect your W7 bootloader and W7 OS during the Ubuntu installation. Thus when you reboot your PC, Grub will list the W7 in its boot menu. It will default to Ubuntu with a time-out but Grub can be configured to default to W7 or change the timeout.

(aside: unfortunately, the W7 bootloader will not recognize a linux installation. If it did, then you could leave the MBR unchanged and the W7 bootloader would generate a menu that would give you the choice to boot either W7 or Ubuntu. Instead, you have to use the Grub bootloader which recognizes all OSs on the disk and will give you the choice of which to boot.)

(aside2: Some versions of Windows, Vista for example, would get very upset if the MBR did not point to the Windows boot loader. I think this caused Vista to abort on OS upgrades. W7 seems to be a bit more co-operative and is ok with this arrangement. But all Windows installers re-write the MBR which is a pest: so if you re-install W7 in the future the MBR will no longer point to grub and you won't be able to boot Ubuntu. This can be fixed, however.)

> Lastly, what steps do I need to take with the RAID 0 setup?  I assumed Ubuntu would just see it as a single drive and I didn't expect that to bring any issues.  First time doing RAID so...yea, lots of noob questions here lolI assume you are using hardware RAID0 as opposed to software RAID0. I assume this because AFAIK Windows doesn't do software RAID0. I am not an expert on hardware RAID but I would imagine this would make the two disks look like one to any OS. So I'm not sure why this would affect installing the Grub MBR entry.

As has been said, NTFS is the Windows partition format. It is not suitable for linux. Linux uses extn where n=2,3 or 4. These are increasingly modern versions of the linux format and you should now choose ext4.

---

### Post by scottmac112 on 2011-01-29
If I'm right, you can just skip the grub-install at the last step of the install. It should be the very last screen before it starts installing everything. Somewhere on the screen, it should say something like "Advanced Options" and it won't install GRUB to the MBR. Then, after the install finishes, just run "grub-install /dev/<whatever drive you installed it to, minus the partition number>". 

After that, reboot into Seven and install EasyBCD. Add the entry to Windows's boot list. Works a lot more predictably than overwriting Windows's bootloader and it having a hissy fit afterward.

Good luck! I hope this all works with the RAID array (never dealt with one).

---

### Post by aaron88_7 on 2011-02-02
Hey all thanks for the tips.  Just to update, I went ahead and just  formatted the partition I had already created, (during the Windows installation), for Ubuntu.  After  formatting that partition in the ext4 format recommended I then used the mount point of " / ".

After that it was smooth sailing.  Ubuntu saw my 2 drives in RAID 0 as if it was just one big drive so I'm glad I had no issues with that.  Perhaps that's because I'm using the native RAID controller provided by Intel with the P67 chipset?  I don't know, but considering this is a Sandy Bridge board and Intel's recent news I'm considering re-installing everything onto the Marvell RAID controller......oh the fun never ends with this new build! haha

I do have a couple more questions that I don't think deserve a new thread on their own....

Ubuntu now loads by default when I turn on my PC, but I'd prefer it to be Windows 7, I'd also like to configure the countdown time as well.  Next question, when booting into either Windows 7 or Ubuntu the number lock button is off and because both OS passwords have numbers in them, I'd like the num lock key to be turned on by default if possible.  Any help with these last two issues would be just awesome!


After I get these very basic things out of the way I'm going to head down to Barnes & Noble and pick up a good Ubuntu book, I know I'll need it!  Thanks again for everyone's help!

---

### Post by hansolo4949 on 2011-02-02
First of all, congrats on getting your hands on a Sandy Bridge Processor. I want one of those in my next computer, i'm hoping they fix the compatibility issues by then...drool. Anyway, what you want to change the startup screen order is a program called startup manager, which you can install from the software center. It has a menu for changing the default OS, simply select Windows, and that's it!

---

### Post by Mark Phelps on 2011-02-03
> **aaron88_7 said:**
> Ubuntu now loads by default when I turn on my PC, but I'd prefer it to be Windows 7 ...

Install startup-manager.  That will allow you to select the default OS (or kernel) using a GUI.

---

