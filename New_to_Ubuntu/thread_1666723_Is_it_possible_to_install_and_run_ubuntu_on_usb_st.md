---
title: "Is it possible to install and run ubuntu on usb stick?"
date: 2011-01-14
forum: New to Ubuntu
---

### Post by Guitar-maniac on 2011-01-14
Computers at our school are SLOW, and i thought wuold it be possible to run ubuntu from usb stick/wuold it work normally or slow? How big USB stick wuold i need/and what version of ubuntu wuold be the best? All i need is basic apps, like openoffice.
 
If you guys can link to me a site with instructions how to do this, it wuold be great. School atm and then going to work, so i don't time now to google.

---

### Post by bioterror on 2011-01-14
Two different ways.
You can make a persistent LiveUSB stick.
Or you can boot liveCD and install your preferred ubuntu on that USB stick when you have booted to desktop and then insert disk.

Remember to use EXT2 then, as it's not writing so much on the USB sticks.

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent]("https://wiki.ubuntu.com/LiveUsbPendrivePersistent")
[http://www.howtogeek.com/howto/14912/create-a-persistent-bootable-ubuntu-usb-flash-drive/]("http://www.howtogeek.com/howto/14912/create-a-persistent-bootable-ubuntu-usb-flash-drive/")

I'm using the installation method from CD on my own USB stick.

---

### Post by SteveDee on 2011-01-14
Yes it is!

I recommend you use Lubuntu: [https://wiki.ubuntu.com/Lubuntu](https://wiki.ubuntu.com/Lubuntu)

If you have access to a system already running Ubuntu, just download Lubuntu and create the USB memory stick install from the Admin menu. Otherwise you need to create a LiveCD, then boot a system from the CD and create the USB stick install from there.

Although Lubuntu does not come with OpenOffice, its easy to go to Preferences > Synaptic and remove AbiWord & Gnumeric and install OpenOffice (if that is your preference).

Remember that memory sticks have a limited endurance (write cycles) but I'd expect your stick to last a few years. You only need a 2 or 4 GB stick but it should be a relatively fast one (Sandisk is good).

---

### Post by RedFirewall on 2011-01-14
[http://www.ubuntu.com/netbook/get-ubuntu/download](http://www.ubuntu.com/netbook/get-ubuntu/download)

This link has instructions on how to install Ubuntu on a USB from either another Ubuntu computer or a Windows Computer.

---

### Post by ikt on 2011-01-14
This may help you as well:

[http://www.linuxliveusb.com/](http://www.linuxliveusb.com/)

---

### Post by Runckle on 2011-01-14
I agree with Redfirewall's method...

---

### Post by Guitar-maniac on 2011-01-14
Thanks! I'm currently using ubuntu 10.10 at home, Checked Bioterror's link, and there was usb creator. That is on 10.10 as well, or do i have to hunt it down from synaptic? Seemed like the easiest way. I'm just an average computer user and this whole process scares me a bit :D I am thinking about putting 10,04 on it since i have the live cd already. Lubuntu could too be one, i could use this opportunity to explore Linux world little bit more.

---

### Post by amjjawad on 2011-01-14
3rd link in my signature is a full guide, hope that will help you. Just ignore the wubi part.

---

### Post by C.S.Cameron on 2011-01-14
> **Guitar-maniac said:**
> Thanks! I'm currently using ubuntu 10.10 at home, Checked Bioterror's link, and there was usb creator. That is on 10.10 as well, or do i have to hunt it down from synaptic? Seemed like the easiest way. I'm just an average computer user and this whole process scares me a bit :D I am thinking about putting 10,04 on it since i have the live cd already. Lubuntu could too be one, i could use this opportunity to explore Linux world little bit more.

If you have 10.10 installed you can use Startup Disk Creator to make a persistent install.

If you wish to make a Full install of 10.04 to USB here is a step by Step:

Turn off and unplug the computer. (See note at bottom)
Remove the side from the case.
Unplug the power cable from the hard drive.
Plug the computer back in.
Insert the flash drive.
Insert the Live CD.
Start the computer, the CD should boot.
Select language
Select install Ubuntu 10.04.
Fill in "Time Zone" and "Keyboard layout".
At "Prepare disk space" select "Specify partitions manually (advanced)".
Select "New Partition Table" click Continue on the drop down.
Click "Free space" and "Add".
Select "Primary".
Make "New partition size..." about 1GB.
Location = Beginning.
"Use as:" = "FAT32 file system"
And "Mount point" = windows.
Select "OK"
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 3 to 4 GB, Beginning, Ext4, and Mount point = "/" then OK.
(Optional)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 1 to 2 GB, Beginning, Ext2, and Mount point = "/home" then OK.
(Optional)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = remaining space, (1 to 2 GB), Beginning and "Use as" = "swap area" then OK.
Click "Forward".
Insert your name, username, password, computer name and select if you want to log in automatically or require a password.
Select forward.
Select Install.
Wait until install is complete.
Turn off computer and plug in the HDD.
Stick the side panel back on.

Note:
You may omit disabling the hard drive if after partitioning you select the "Advanced" button and choose to install grub to the root of the usb drive you are installing Ubuntu to, (ie sdb not sdb1). Be cautious, many people have overwritten the HDD MBR.
At boot you will then be given the option to boot your hard drive, even when booting another computer.

---

### Post by I2k4 on 2011-01-15
You can also use the Ubuntu download "Show me how" Step 2, very user-friendly _but it doesn't include the "Persistence" step:  the Pendrive installer has an option to set Persistence that will save all your settings from one boot to the next._  I suggest getting a 4GB USB drive and setting 3GB of Persistence during the installation. 

After testing several Ubuntu versions last few weeks I've found the netbook edition unaccountably slow and used up too much of the small screen, the 10.05 LTE and 10.10 Desktop editions run pretty well with a lot of preinstalled features and software, and recently Lubuntu to be fastest and slickest but has less GUI support.  Have fun.

---

### Post by I2k4 on 2011-01-15
You can also use the Ubuntu download "Show me how" Step 2, very user-friendly _but it doesn't include the "Persistence" step:  the Pendrive installer has an option to set Persistence that will save all your settings from one boot to the next._  I suggest getting a 4GB USB drive and setting 3GB of Persistence during the installation. 

After testing several Ubuntu versions last few weeks I've found the netbook edition unaccountably slow and used up too much of the small screen, the 10.05 LTE and 10.10 Desktop editions run pretty well with a lot of preinstalled features and software, and recently Lubuntu to be fastest and slickest but has less GUI support.  Have fun.

---

