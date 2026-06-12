---
title: "How to upgrade ubuntu 8.04 to 10.04"
date: 2011-02-17
forum: New to Ubuntu
---

### Post by chitragurung on 2011-02-17
Hello,
 
I have been using Ubuntu 8.04 hardy with dell inspiron mini. Now I wanted to upgrade to new version. But I could not upgrade.
 
When I go to update manager, it never show me new release. So, I have downloaded ubuntu-10.04.1-i386.iso file in my computer and also ubuntu-10.04.1-alternate-i386.iso files but I do not know how to use this upgrade file.
 
I try to some options available from forum but does not work.
 
I try this command as well
 
sudo mount -o loop ~/Desktop/ubuntu-10.04-alternate-i386.iso /media/cdrom0
 
it does not worked.
 
I did trying using unetbooting-linux-494 and it works but in the installation step 4 0f 7 could not fix.
 
Which one to selet sdc, sda etc.
 
How is the easiest way to upgrade

---

### Post by sh4d0w808 on 2011-02-17
Check this: [https://help.ubuntu.com/community/LucidUpgrades#Upgrade%20from%208.04%20LTS%20to%2010.04%20LTS](https://help.ubuntu.com/community/LucidUpgrades#Upgrade%20from%208.04%20LTS%20to%2010.04%20LTS)

---

### Post by waynefoutz on 2011-02-17
The easiest way is to back up your personal data and do a clean install. I tried the 8.04 to 10.04 upgrade with update manager, it took over 4 hours with a really fast Roadrunner cable connection. The end result was a complete mess. I had to reinstall all but two or three of my programs. The boot up time on my new 10.04 was excruciatingly slow. I ended up doing a clean install. The upgrade was a complete waste of time.

---

### Post by NightwishFan on 2011-02-17
On the other hand I have had a lot of success with upgrades. It really is what suits your needs. If you have the machine the way you want it, doing an upgrade might be the best option. If you do not mind backing up data and getting a fresh configuration (not to mention the new ext4 filesystem, but I actually recommend ext3 still anyway) then do a fresh install.

If it is of no never mind to you I say do the upgrade. The method outline in the link in the post a few above should work.

---

### Post by trey31357 on 2011-02-17
I second the motion for a clean install (of course I come from a Windows mentality where it's necessary, frequently). There is likely a huge amount of new data in the 10.04 release, and it would save you time (since you have the .iso already) to just burn the .iso to CD (natively supported in Brasero) and run the CD for a clean install. Remember to back up your personal data first!

---

### Post by pekon on 2011-02-17
Ubuntu Documentation is Awesome.. Follow on any of following Methods to install Ubuntu 10 directly from HardDisk without using CDs

-------------------------------------------------- 
WARNING: In one of the methods you need to make a bootable image of ur ISO file to ur disk.. using a command called "dd" 
BEWARE OF "dd" command :)
It may destroy you if the target disk is wrong ..

I recently lost my 5yrs of Data, due to a small mistake ..
**But it was worth learning & experimenting **

[LIST]
[*][Installation/FromHardDriveWithFloppies]("https://help.ubuntu.com/community/Installation/FromHardDriveWithFloppies") - Installing without a CD drive or network capabilities from a hard drive. 

[/LIST]
-------------------------------------------------- 


[LIST]
[*][SmartBootManager]("https://help.ubuntu.com/community/SmartBootManager") - Installing from a PC which will not boot from a CD. 
[*][Installation/FromUSBStickQuick]("https://help.ubuntu.com/community/Installation/FromUSBStickQuick") - A quick guide to installing from a USB memory stick. Intended for less technically-minded readers. 
[*][Installation/FromUSBStick]("https://help.ubuntu.com/community/Installation/FromUSBStick") - Installing from a USB memory stick. 
[*][Installation/FromCForUSBStick]("https://help.ubuntu.com/community/Installation/FromCForUSBStick") - Similar to above but using *grub*. 
[*][Installation/WithFloppies]("https://help.ubuntu.com/community/Installation/WithFloppies") - Installing without a CD drive over a network. 
[*][Installation/FromHardDriveWithFloppies]("https://help.ubuntu.com/community/Installation/FromHardDriveWithFloppies") - Installing without a CD drive or network capabilities from a hard drive. 
[*][Installation/FromWindows]("https://help.ubuntu.com/community/Installation/FromWindows") - Installing from Windows without using floppies, a CD, or any other removable media. 
[*][Installation/FromLinux]("https://help.ubuntu.com/community/Installation/FromLinux") - Installing using a spare partition from an existing Linux system to house the Ubuntu CD image. 
[*][Installation/FromVM]("https://help.ubuntu.com/community/Installation/FromVM") - Installing using a physical disk to a Virtual Machine. 
[*]See also the network installation options below
[/LIST]

---

### Post by chitragurung on 2011-02-17
Thank you all for sharing your  experiences. Well, I have downloaded upgrading iso files of nearly 675 mb. Both Alternate  CD and Desktop iso files. Is it full new installation files or just upgrading files only ?
 
Other hand I did trying installation, but I confuse while seting up of drive. I am asked where should put UBUNTU and got three options and I clicked to place where more space available but it does not work. That is the point I want to solve. So, how can I solve it ? I think other issues may be o.k.

---

### Post by waynefoutz on 2011-02-18
> **chitragurung said:**
> Thank you all for sharing your  experiences. Well, I have downloaded upgrading iso files of nearly 675 mb. Both Alternate  CD and Desktop iso files. Is it full new installation files or just upgrading files only ?
 
Other hand I did trying installation, but I confuse while seting up of drive. I am asked where should put UBUNTU and got three options and I clicked to place where more space available but it does not work. That is the point I want to solve. So, how can I solve it ? I think other issues may be o.k.

This is a pretty good video showing how to set up your drive, reinstall Ubuntu, without formatting so you can keep your data. .

[http://www.youtube.com/watch?v=QGnsYuWS0xY]("http://www.youtube.com/watch?v=QGnsYuWS0xY")

the big difference is 8.04 uses ext4 instead of ext4, so you'd have to pick ext3 if you want to keep your data and settings.

---

