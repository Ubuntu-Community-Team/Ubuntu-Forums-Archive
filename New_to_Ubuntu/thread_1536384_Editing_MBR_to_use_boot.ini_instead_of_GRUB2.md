---
title: "Editing MBR to use boot.ini instead of GRUB2"
date: 2010-07-22
forum: New to Ubuntu
---

### Post by woopdeedoo on 2010-07-22
Hi Guys.  I'm a complete noob but decided to install Lucid as a dual boot thanks to the awesome review the OS got on the register. Now  I have a problem. This is what happened:  My HP laptop runs XP Pro. I booted off the live disc and installed Lucid to an External HDD(due to space issues). The result is that I need to have my External HDD plugged in when I boot or I get an error. This is extremely irritating. According to a previous thread, this article explains what I did wrong: [http://ubuntuguide.org/wiki/Ubuntu:Lucid#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Lucid#Dual-Booting_Windows_and_Ubuntu)  My question, how do I fix my MBR without repairing Windows? If anyone can help me, I would be much obliged!  Woopdeedoo.

---

### Post by Oak37 on 2010-07-22
Hi woopdeedoo,

Normally this can be quite easily fixed using the Windows install CD and booting into the command line but is this what you don't want to do when you say without repairing windows?

---

### Post by woopdeedoo on 2010-07-22
> **Oak37 said:**
> Hi woopdeedoo,

Normally this can be quite easily fixed using the Windows install CD and booting into the command line but is this what you don't want to do when you say without repairing windows?

Hi Oak

I mean that I don't want to run an OS repair on my Windows OS, in short, I don't want to reinstall the OS (without formatting). If you can do this using the recovery console (command line), can you run me through it?

---

### Post by john newbuntu on 2010-07-22
I think what has happened here is that a part of grub2 has been installed on the MBR of your internal HDD.  You will need to fix your bootloaders.   You will not have to repair any of your OS partitions.

This post by talsemgeest explains it in the section titled "How to restore the Windows XP bootloader": [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Remember that once you do this, you could lose the ability to boot to Ubuntu.  This can be repaired by restoring grub to the MBR of your external drive as expained in the section titled "How to restore the Ubuntu grub bootloader (9.10 and beyond)" in the same post.  While doing this, make sure that all your drives and partitions of the commands point to the external HDD.(which could be sdb in your case)

After you do this, make sure that your BIOS boot order shows your external drive as the first bootable drive and then your internal HDD.  Any issues or otherwise, please post back.

---

### Post by anewguy on 2010-07-22
As long as it's not Windows 7 (as I don't know if the software works for that or not), just boot up Windows (obviously with your external driver attached so you can) and do the following:

- go to [www.downloads.com](www.downloads.com)

- search for and download a short free program called mbrfix.

- check the readme that comes with it for proper syntax, but basically you just run the program with a couple of simple parameters and it restores you drive mbr so it just boots to Windows.

- if you want to dual-boot using the external drive, see one of the many posts here for updating grub2.

Dave ;)

---

### Post by woopdeedoo on 2010-07-23
John

Thanks. My XP boot menu works again! Now what i need to do is edit my boot.ini so that there is an option to boot into ubuntu as 2nd OS option. Any ideas guys? And thanks, you are all awesome! 1m free internets for you all!!!

---

### Post by oldfred on 2010-07-23
The easiest thing is just to install grub2 to the external and set the external to boot first in BIOS. If it is plugged in it boots thru grub, if not it defaults to your windows in sda internal.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Install from LiveCD install on sdb1 and want grub2 in drive sdb's MBR:
Find linux partition, change sdb1 if not correct, and/or even sdb if it mounts it as another drive letter:
sudo fdisk -l
sudo mkdir /mnt/sdb1
sudo mount /dev/sdb1 /mnt
sudo grub-install --root-directory=/mnt /dev/sdb
If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt /dev/sdb

After rebooting into Ubuntu:
to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
spacebar to choose drive, enter to accept, do not choose partitions

---

### Post by john newbuntu on 2010-07-24
I am assuming that you restored grub2 to the MBR of the external drive as I described or as oldfred did.  Once this is done, boot using an ubuntu liveCD.  Have the external drive plugged in.  Confirm that /dev/sdb is your external drive by running the command "sudo fdisk -l".

Then run this command from a terminal (applications->accessories->terminal):
```
dd if=/dev/sdb of=ubuntu.mbr bs=512 count=1
```
This will create a file called ubuntu.mbr .  If for whatever reason, /dev/sdb is not your external drive, change the command to point to the correct external drive.

Copy the file "ubuntu.mbr" to the C:\  folder in windows.  Then edit the C:\boot.ini file and add this as the last line:
```
c:\ubuntu.mbr=”Ubuntu Linux”
```
You could try and do the last 2 steps using "gksu nautilus".  You could also change "Ubuntu Linux" to any string of your choice.

Save, reboot and test.

---

