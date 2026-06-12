---
title: "Install on SD Card, software and data on HDD"
date: 2010-11-23
forum: New to Ubuntu
---

### Post by IltikA on 2010-11-23
Hi, 
I am kind of new on Linux, (let say back), and I want to try xubuntu but I can't get rid off my current windows installation (for D3D/PS/Lightroom).

My laptop is a Asus A7SN (so just one HDD sadly). As I currently have limited free space (lot of raw photos and games), I would like to use my old camera SD Card (Transcend 4GB 150x) to get linux on it, and have the application / home on my hard drive.

So I would get:
SD => system files
HDD => /home, /usr (I think it's the main app folder), swap,shared windows

From the few I saw It is possible but my question are:
- What is the main application install folder, I am not sure if with /usr I would cover most app (I don't want to run out of space on the SD because I have too much app/VM/system file)
- Would I get a very slow OS or will I be find using it? (I want to try visualization and the photo tools on it)

Thanks in advance

---

### Post by tea for one on 2010-11-23
Good evening

You have a choice of methods to experiment with Xubuntu:-

(a) Install Xubuntu OS on your SD card and then use a section of your HDD for a Home directory i.e Software on SD card and Data on HDD.

(b) Perhaps consider installing a Live Xubuntu system on your SD card and create a persistent area on the same media to store data (although 4GB will not allow much room for data)

(c) You can install the OS and Data on a USB stick (8GB for example) as a "Hard Drive" installation but you have to be very careful where you place the Grub bootloader so as not to overwrite the Windows boot system. I generally place the Grub bootloader on the external device when I want to experiment with another OS. This style of installation will allow you to create a user account and also save settings/data.

Please be careful when installing because the partition utility (Gparted) can be a bit tricky if you have never used it before.

Good luck

---

### Post by Old_Grey_Wolf on 2010-11-23
If you put /home on the HDD and everything else on the SD, I think you will be able to experiment with Xubuntu. If you put both /home and /usr on the HDD then there is almost no benefit in using the SD card as you will probably be using about 1GB of the 4GB. My /usr is about 2.7GB for a Gnome desktop Ubuntu, with additional games and applications like EtherApe, Wireshark, GIMP, KoulorPaint, Gramps, Chromium browser, Virtualbox, etc, etc, installed. 

Try putting everything except the /home on the SD card. If you are using it for experimenting with Xubuntu and not putting important data on it, then you can change it later.

Also, be very careful when doing the installation. Make sure you have the CDs/DVDs to restore your MS Windows system, and if you can back up your system then do so before installing. If something doesn't seem right, stop what you are doing and ask for help.

---

### Post by C.S.Cameron on 2010-11-23
You can make a ext3 partition on your internal HDD and name it home-rw.
Then do a persistent install to the SD using usb-creator using max extra space, (giving ~3GB casper-rw file).
when you boot the SD from that computer all your home stuff will end up in the home-rw partition.


Edit:
If you prefer all your persistent data on the HDD, name the ext3 partition casper-rw then delete the casper-rw file from the SD after installing to it with usb-creator. you can also use the home-rw partition if you want a separate home.
A persistent install looks for the lowest level casper-rw and home-rw space to use for persistence.

---

