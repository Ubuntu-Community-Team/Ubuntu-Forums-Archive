---
title: "problem with sdhc (acer aspire one)"
date: 2009-01-25
forum: New to Ubuntu
---

### Post by megamoser on 2009-01-25
hello everybody,

a few days ago i installed ubuntu intrepid ibex on my aspire one. after three days of frustration i finally got a (almost) perfectly running system. today i was about to discover the properties-window of my sdhc-card (which was auto-mounted when i started the computer). somewhere i read that it's better to switch to etc2 (whatever this means) to get the device working faster. so there was this line saying "file system" and i wrote in: etc2 (without really knowing what i do). i rebooted the system and from now on ubuntu doesn't mount my sdhc-card anymore. further on if i try to mount it manually (by right-clicking the symbol for the card) ubuntu says: "unable to mount". 

so is there anybody who can help me to get my card back working? 

thanks for your help,
thomas.

---

### Post by neotasic1 on 2009-01-25
> **megamoser said:**
> hello everybody,

a few days ago i installed ubuntu intrepid ibex on my aspire one. after three days of frustration i finally got a (almost) perfectly running system. today i was about to discover the properties-window of my sdhc-card (which was auto-mounted when i started the computer). somewhere i read that it's better to switch to etc2 (whatever this means) to get the device working faster. so there was this line saying "file system" and i wrote in: etc2 (without really knowing what i do). i rebooted the system and from now on ubuntu doesn't mount my sdhc-card anymore. further on if i try to mount it manually (by right-clicking the symbol for the card) ubuntu says: "unable to mount". 

so is there anybody who can help me to get my card back working? 

thanks for your help,
thomas.

You have used the wrong spelling.  ext2 or ext3 (not etc2) are filesystem types much like windows uses fat16 or fat32 or ntfs.  

What do you mean by sdhc card - is this a secure digital card like those used in cameras?

My suggestion is if you can repeat the process whereby you changed the filesystem type to etc2 and replace the type with ext2.

---

### Post by russu52 on 2009-01-25
can you rechange the line of "file system" back to fat or what was there before you changed to etc2? your sd card probably is fat format, but now your pc can only read etc2 card (unless i'm completely wrong !!! which at times i am ;()

hope it works for you

---

### Post by megamoser on 2009-01-25
thanks for your answers.

the card worked just fine until i changed that line (i guess i wrote ext2 and just mixed it up now). i can still open the properties-window for the card but the line which i changed is gone. the properties windows isn't completely the same anymore. it seems that ubuntu is still recognizing that i've inserted a sdhc (i guess so because i can still see "16.1GB device" when i open 'Computer' - i just cant open it anymore).

and yes, i think it's an sdhc like cameras use it. the aspire one has some kind of "storage expansion" which is in fact a sdhc card-reader.

edit: i only used that card in my aspire one and ive never run windows on it.

---

### Post by neotasic1 on 2009-01-25
Right click on the sd card icon on your desktop, select properties, select the volume tab, click on the small triangle with settings next to it, in the filesystem box type vfat. save your settings, unmount the sd card, then remount it.

---

### Post by megamoser on 2009-01-25
there's no sd-card-symbol on the desktop (there would be if it was mounted correctly). so i can go to places > computer and there i see two symbols. one is 'file system', the other one is '16.1 gb media' (which is obviously my card). if i right-click there i can see the following tabs: basic, emblems, permissions, open with, notes.
i can't edit the file system with any of these anymore. 

when i right-click the card-symbol and chose 'mount volume' it says:

"Cannot mount volume
Unable to mount the volume.

Details
mount: wrong fs type, bad option, bad superblock on /dev/mmcblk0p1, missing codepage or helper program, or other error in some cases useful info is found in syslog - try dmesg tail or so"

---

### Post by neotasic1 on 2009-01-25
> **megamoser said:**
> there's no sd-card-symbol on the desktop (there would be if it was mounted correctly). so i can go to places > computer and there i see two symbols. one is 'file system', the other one is '16.1 gb media' (which is obviously my card). if i right-click there i can see the following tabs: basic, emblems, permissions, open with, notes.
i can't edit the file system with any of these anymore. 

when i right-click the card-symbol and chose 'mount volume' it says:

"Cannot mount volume
Unable to mount the volume.

Details
mount: wrong fs type, bad option, bad superblock on /dev/mmcblk0p1, missing codepage or helper program, or other error in some cases useful info is found in syslog - try dmesg tail or so"

Try booting from your Installation CD or installation USB (I don't know which of these you used to install ubuntu - Acer aspire one is a netbook if I am not mistaken and some of these don't have CD rom drives.) 

Or alternatively install GParted from the Add/remove programs options. Use Gparted to reformat your sd card to vfat filesytem type. (or for that matter ext2 if that is what you wanted to acheive.)

---

### Post by megamoser on 2009-01-25
okay, i first tried gparted. unfortunatelly it can't find my sd-card.
so i rebooted the system and plugged my installation-usb-drive. when the system was booted i could see the sd-card on the desktop but actually i didn't know what to do then. i opened gparted but it still can't find the card (although it is mounted and i can open it just like usual). so i checked the properties windows and found the 'file system'-thing again. i entered vfat and rebooted the system (with usb-drive unplugged again) but it didn'T change a thing. i still can't mount the sd-card when i'm in "standard mode".

---

### Post by megamoser on 2009-01-26
still not solved.
i'd be very thankful for some more ideas.

is it possible that i have to edit the file where the devices are listed (i guess its name was fstab) to get my card working?

---

### Post by bailbath on 2009-01-26
If you don't get the solution here try the aspire one forum they have a Ubuntu section.
[http://www.aspireoneuser.com/forum/viewforum.php?f=28](http://www.aspireoneuser.com/forum/viewforum.php?f=28)

---

### Post by Flag on 2009-01-26
Acer Aspire One won't show an icon of this card on yr. desktop.
Gparted : On the right hand top you'll see a window with an arrow, here you can make a choice between the various cards. 
Would suggest to start all over again at the partition menu at setup choose the right formatting fot yr. cards. I have the internal card as / the external card in the left hand slot as /home, both at ext2.
Ubuntu 8.04 runs OK, just need to use ndiswrapper for wifi.

---

### Post by russu52 on 2009-01-26
but your pc will not recognise the card because it is not formatted ext2!! you need to undo those changes that you did way back. try going into boot menu and boot your older version of ubuntu (before you made those changes) something like system restore in windows

---

### Post by megamoser on 2009-01-26
@flag:
the problem is that my pc doesn't recognize the card anymore. it's not only that it isn't shown on my desktop. so i can't change anything with gparted.

@russu:
i'll try that. does that mean that everything i did after changing the card file system will be undone? anyway, i'll figure that out by myself now.




thanks both of you.

---

### Post by russu52 on 2009-01-26
yeps. sort of - especially settings and applications. i don't know if data is touched - backup just in case!

---

### Post by megamoser on 2009-01-26
i'm sorry but how can i boot an older version? i looked in the boot menu but couldn't find anything like that. there was only two options: booting from disk or network-boot.

---

### Post by Flag on 2009-01-27
Sorry, time difference, you stated you can boot from USB, no luck with gparted then ?

---

### Post by seyon on 2009-03-21
fdisk -l /dev/mmcblk0
        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1               5        9595     7925760   83  Linux


If you get something diferent than System = Linux, then you have to select the right System for that partition (you can't format ext2 on a fat32 system).

---

### Post by bigred562 on 2009-05-15
First off, the question doesn't seem to have been understood. megamoser right-clicked on the mounted icon on his desktop and selected properties. Then he click on the Drive tab and under settings ----> File System he typed in ext2. This does not change the filesystem type of the drive. It changes what the system thinks that it is mounting. Therefore it keeps trying to mount a ext2 filesystem when it is actually whatever it was before. Megamoser needs to: Open a terminal and type: gconf-editor (which will open the gconf-editor) under gconf-editor --> system --> storage --> drives there should be a drive. If you click on the drive in the left window pane, the right window pane will have something like "fstype_override | ext2". You need to right-click on that and select unset key. Close the gconf-editor. You should be able to mount the drive now. If not, make sure that you don't have gparted open or it locks the gconf-editor from making the changes till you close it. (That happened to me)

---

