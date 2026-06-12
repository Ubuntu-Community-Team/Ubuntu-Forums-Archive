---
title: "making persistent usb os"
date: 2011-01-29
forum: New to Ubuntu
---

### Post by slixz85 on 2011-01-29
hi ya all have helped me out with alot. only thing left on my mind is making a persistent usb drive with an operating system on it that saves everything to the usb as if it was the main hard drive. then when i boot the computer back up with the stick everything is saved. i use unetbootin and it dont do this i dont see any other options in it. the default startup disk creator doesnt work right even after reinstall.
making a usb stick for temporary use for a friend whose hard drive is out and they cant get one for about 2months

thanks again

---

### Post by eriktheblu on 2011-01-29
My preferred method is to physically disconnect the internal drive, then do a full install on the USB drive. 

Probably excessive caution, but it works.

---

### Post by oldfred on 2011-01-29
I also prefer a full install, but you need a 8GB or larger Flash. With smaller drives you just add persistent.

When Unetbootin finished, shutdown, booted thumbdrive.
At boot menu hit Tab, then typed "(space)persistent"
Ran "gksu nauilus", opened filesystem / cdrom and then opened syslinux.cfg with text editor.
Added "persistent" as shown below:
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash -- persistent
Rebooted, changes were persistent.

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)
With grub2 persistant C.S.Cameron post#5 10.10:
[http://ubuntuforums.org/showthread.php?t=1643791](http://ubuntuforums.org/showthread.php?t=1643791)
With grub2 persistant 10.04 C.S.Cameron post#15:
[http://ubuntuforums.org/showthread.php?t=1593656](http://ubuntuforums.org/showthread.php?t=1593656)

---

### Post by tkoco on 2011-01-29
> **slixz85 said:**
> hi ya all have helped me out with alot. only thing left on my mind is making a persistent usb drive with an operating system on it that saves everything to the usb as if it was the main hard drive. then when i boot the computer back up with the stick everything is saved. i use unetbootin and it dont do this i dont see any other options in it. the default startup disk creator doesnt work right even after reinstall.
making a usb stick for temporary use for a friend whose hard drive is out and they cant get one for about 2months

thanks again

Make sure the friend can boot from a USB device. The BIOS of his machine might not support booting from a USB device. Follow these instructions:
[http://ubuntuforums.org/showthread.php?t=1623663]("http://ubuntuforums.org/showthread.php?t=1623663")

---

### Post by C.S.Cameron on 2011-01-29
This is how I made a Unetbootin install to flash drive persistent.
Booted Live CD, (Live USB should also work)
Plugged in target flash drive.
Started Partition Editor
Created 1GB FAT32 partition, (on the left side of the bar).
Created a 2GB ext3 partition to the right of this, labeled it "casper-rw".
Created a ext2 partition in the remaining space and labeled it "home-rw".
Closed Partition Editor.
Un-mounted and re-mounted flash drive.
Started Windows, started Unetbootin, selected Diskimage, located the iso, selected Type = USB Drive, selected correct drive letter
Pressed OK, waited 5 minutes.
When Unetbootin finished, shutdown, booted thumbdrive.
At boot menu hit Tab, then typed "(space)persistent"
Ran "gksu nauilus", opened filesystem / cdrom and then opened syslinux.cfg with text editor.
Added "persistent" as shown below:
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash -- persistent
Rebooted, changes were persistent.

---

### Post by slixz85 on 2011-01-30
ok great i will do this tomorrow thanks to all

---

### Post by I2k4 on 2011-01-30
I'm still running from USB as a newcomer, but found the regular Ubuntu install instructions for USB at Step 2 here foolproof:

[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

The one thing not explained at Step 2 is that after choosing USB, the "universal usb installer" i.e. PenDrive interface has a user selection for "persistence" and setting the amount of it on the USB.  I've found setting 3GB of "persistence" on a 4GB USB works fine.  (For some reason, Ubuntu seems not to want to encourage folks to use the USB for too long, though I think testing on USB with settings is the best way to reassure novices that they can live with Linux, and lots of us are in no flaming rush to start dual booting or overwriting Windows on the main HDD.)

I fully concur with the comment above, that the Netbook version is a dog that don't hunt.  I found 10.10 Desktop worked fine, but Netbook version was like thick molasses.  After learning a little more about Linux and needing less GUI help, I've found Lubuntu to be the quickest and slickest for running off the USB.  Good luck.

---

### Post by bunny rabbit on 2011-01-31
I've let my laptop bounce and busted my HDD. I've menaged to do this persistent thing on a USB stick.

I'm happy with how I did it too:
I installed the live cd on a 1 Gig usb stick and booted that up.
(try ubuntu without installing)
Then I inserted another usb stick, but this one has 8 Gig.
Then I selected the desktop icon "install ubuntu"
During the install process you can choose to select the location where to install ubuntu manually: I did that.
Then you can select your location from a list. It was easy for me to find and choose my 8 Gig usb stick.

And that was all. I run from a usb stick with everything like suspend and wifi working.
And I didn't see a terminal window once.(not that I have a problem with them of course)

---

### Post by slixz85 on 2011-02-04
lol well i just thought of something. its gonna be harder than i thought. trying to set up friends computer for this and dont have two usb sticks. only got one for the live iso so it cant install on the same stick prolly since its reading from it. gotta go get another usb stick unless you all know a way i can make this work.

just trying to put some extra games on the laptop for friend to use until new hard drive. i installed a live os to the usb stick i got and tried to put some debian game files on it also by just dragging and dropping them into the window after unetbootin installed the os. now i know this aint the way lol but i figured i could see those debian files and just tell them they gotta install them each time but after the files are moved to the folder they are like invisible hidden or something and if you click on show hidden files they dont show up. been away from the computer so just now going to try and make this persisent usb. thanks to all so far

---

### Post by oldfred on 2011-02-04
You can directly boot an ISO on your hard drive. I do not think you then can install to the same partition, but you can install to another drive, partition or the flash drive.

Hard drive:
Direct boot on hard drive:
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
Boot ISO from harddrive. To install it would have to be different partition
[SOLVED] Using grub 2 to boot an iso off hard drive
[http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)

---

### Post by slixz85 on 2011-02-04
i really just need to know the best os for out of box support that would most likely have the hp dv2 wifi driver to be able to get on net with it and download files to it after made persistent. ubuntu doesnt come out of box for the dv2 and neither does crunchbang

---

### Post by slixz85 on 2011-02-04
plus with the one usb stick if i install an iso that needs the wifi driver i dont have an ethernet cord or another usb stick to do this since i cant see files i drag onto the usb folder after the iso installed

---

### Post by slixz85 on 2011-02-04
ah ha. what tool can be used to just copy my computer back it up i guess as a iso or bootable iso. is there one? that would be way easier since i got alot of games and such

---

### Post by oldfred on 2011-02-04
You really should have a hardwired connection for any install. Many systems are missing a wifi driver and the only way is download via the Ethernet driver.

I have not used any of these:

Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

[http://clonezilla.org/](http://clonezilla.org/)
[http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)
[http://www.psychocats.net/ubuntu/remastersys](http://www.psychocats.net/ubuntu/remastersys)

---

### Post by Rhizoid on 2011-02-04
If you're still running WinXP/Vista/7 just go to [http://www.pendrivelinux.com](http://www.pendrivelinux.com) and use their Universal Installer and the .iso you created the liveCD from.

Direct link to the Ubuntu page...
[http://www.pendrivelinux.com/put-ubuntu-10-04-on-flash-drive-using-windows/](http://www.pendrivelinux.com/put-ubuntu-10-04-on-flash-drive-using-windows/)

---

### Post by lindsay7 on 2011-02-04
check this out, It is what you are looking for I think.

[http://www.linuxliveusb.com/en/download](http://www.linuxliveusb.com/en/download)

---

### Post by slixz85 on 2011-02-05
> **lindsay7 said:**
> check this out, It is what you are looking for I think.

[http://www.linuxliveusb.com/en/download](http://www.linuxliveusb.com/en/download)

thanks i have installed the program however i cant read any text on it or anything i am guessing there has to be some there. i left a screenshot


and on pendrivelinux when i boot it with wine what drive letter will it be since the drive letters are like windows letters for my usb is sdc1

thanks

---

