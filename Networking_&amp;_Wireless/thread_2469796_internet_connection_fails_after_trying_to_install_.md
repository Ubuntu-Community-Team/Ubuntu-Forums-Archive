---
title: "internet connection fails after trying to install ntfs-3g driver"
date: 2021-12-09
forum: Networking &amp; Wireless
---

### Post by feral-hippie on 2021-12-09
I am new to Ubuntu. My Windows 7 was ready to be reinstalled. I tried installing Ubuntu alongside Windows and ran into problems, so I just installed Ubuntu. 

I have a 2 TB flash drive that I am trying to get to work in NTFS mode so that I can have files that are larger than 4 GB.
I tried installing ntfs-3g driver using

sudo apt-get install ntfs-3g

after the install the computer does not mount the flash drive giving an 'unable to access' error. (note this was formatted in the discs utility and not in Windows). Note: this flash drive works fine when i format it in FAT using discs. I am no longer able to connect to the internet, but the local network is showing up on wifi and ethernet. I am able to get to the internet when I boot from the USB that I used for install (this how I am posting). Is there a way to use the bootable USB to reset to default on 20.04.3 LTS? When I go through the setup the system recognizes the installed 20.04.3 LTS and has the option to replace or install alongside but not repair. 

I have reinstalled Ubuntu on the computer. I then downloaded and installed Timeshift to create system restore points. I created 2 restore points when I was still able to connect to the internet. again, after trying to get ntfs to work, the internet connection failed. I restored the system to both of the saves, but neither worked

I appreciate any suggestions you may have

---

### Post by QIII on 2021-12-09
May I ask first why you think it is necessary to add an NTFS driver if you have overwritten Windows?  If you install Linux with ext4 partitions, you can have up to 16TB files -- why you'd ever need that for a home PC I don't know.  Will you be accessing NTSF partitions on other machines on your network?  If you plan to use that flash drive on different machines, you use a partitioning tool like gparted to create an NTFS partition.  You'll certainly then need ntfs-3g to work with it.

Did the problem with internet access actually start immediately after adding NTFS-3g, or might there have been other things that you did?

---

### Post by feral-hippie on 2021-12-13
The problem with the internet started immediately after installing ntfs-3g. Should I just format my USB flash drive to another format?

---

### Post by feral-hippie on 2021-12-13
I would like to copy large files to the flash drive and have them work on multiple systems. I may just reinstall Ubuntu and forget about using ntfs. Would using a different formatting utility help?

---

