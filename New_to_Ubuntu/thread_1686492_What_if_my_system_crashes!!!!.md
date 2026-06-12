---
title: "What if my system crashes????!!!!"
date: 2011-02-12
forum: New to Ubuntu
---

### Post by amitpokhrel on 2011-02-12
I was using Ubuntu 10.10 - 64 bit since 6 month. But suddenly a week ago my system crashed. I couldn't find a way out. So i had to format my system and install it again. The thought gives me a headache that I again have to start from the beginning with installing all the basic software..
Can anyone tell how could i keep backup of all my softwares so that i can recover it in case my system crashes again.

---

### Post by sammiev on 2011-02-12
Should be able to get back up and running with a boot able system CD or DVD.

I myself use [Clonezilla]("http://clonezilla.org/") and make a full system back up. GL :)

---

### Post by thefasterblueone on 2011-02-12
Install Ubuntu with seperate /home folder so if you need to reinstall OS all your settings can be transfered to your new system. 

In case of hardrive failure backup your /home folder to seperate harddrive using a backup software of your chioce, I use Deja Dup, because it is simple and does what I need it to do.

[http://www.n00bsonubuntu.net/content/how-to-make-a-backup-using-deja-dup/]("http://www.n00bsonubuntu.net/content/how-to-make-a-backup-using-deja-dup/")

Also, after a system failure check back here at ubuntuforums to see if someone can help you fix it, before formatting. 
Lots of great people here volunteering thier time to help.

---

### Post by amitpokhrel on 2011-02-12
what should I do to install ubuntu with a separate home folder.....

---

### Post by thefasterblueone on 2011-02-12
Here is an excellent guide to help you. Follow instructions very carefully. If you have questions, ask.

[http://lug.belizebulletinboard.com.bz/2011/01/how-to-install-ubuntu-10-10andsetting-up-the-home-folder-in-a-separate-partition-part-2/]("http://lug.belizebulletinboard.com.bz/2011/01/how-to-install-ubuntu-10-10andsetting-up-the-home-folder-in-a-separate-partition-part-2/")

---

### Post by tednix on 2011-02-12
I use Simple Backup which has made copies of my /home folder among others.
So in case of a crash all I have to reinstall the base system and then copy over my /home folder; is that correct?

---

### Post by sffvba[e0rt on 2011-02-12
> **tednix said:**
> I use Simple Backup which has made copies of my /home folder among others.
So in case of a crash all I have to reinstall the base system and then copy over my /home folder; is that correct?

This will save all of your personal documents etc. as well as settings for the various programs you use... it will however not backup all of the programs themselves so when you re-install you will have to re-install all of the applications you want to use (which aren't installed by default of course).



404

---

### Post by tednix on 2011-02-12
I may go with this full backup system.

[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

It looks like a lot of work for a noob.

---

### Post by georgemc on 2011-02-12
You can mitigate the impact of a total system crash and reload with a few simple actions if you prepared your system.   
 

 
[LIST=1]
[*]Home directories on their own     partition.
[*]In synaptics save the “full     state” of the installed packages.
[*]Backups – backups – backups.
[/LIST]
 

 I personally feel that I can recovery any and all OS and packages from media or the net, however, my data I can only recover from my backups.  I therefor place more emphasis on personal data backups than full system cloning.
 

 This can also be applied to “Clean Install Upgrades”.  I used this to “Clean Install Upgrade” from 9.04/10 to 10.04LTS.
 

 This is a guide, that works for me, and not a copy/paste Howto.
 

 There are implications with encrypted Home directories, encrypted HDD's, Raid Arrays, Wubi, Dual Booting, and what have you, that I will not address here.
 

 In preparation of a clean install upgrade or system crash recovery I have setup my systems with a separate Home partition and backed up various configuration and data files into my Home directory for safe keeping.
 

 _Making a new Home partition:_  
 Load the “live” CD and simply make a new partition and I use rsync -rlpAXogt “SRC” “DEST” to copy my home directories to the new partition.  Add the partition in the /etc/fstab file and make sure you boot up and correct any errors that may occur before proceeding.
 

 Copy any of your configuration files and directories to your home directory for save keeping.  I also backup my “Home Brew” software to my Home directory.  For example see my configuration files list below.   Your list will vary depending on your own unique setup.  Worse case you might have to configure an application or package from scratch or retrieve them from a backup.
 

 The final preparation step is to start Synaptic and save your installed packages list in your Home directory.  Launch Synaptic and goto File > Save markings as … , make sure you checked the “Save full state, not only changes” check box, and save the list.
 

 My rule of thumb is: “Any thing I want to keep is present in my Home directory!”
 

 **Backups – Backups –  and Backups:**
 Now would be a good time to backup your Home directories and other data to an off-line or separate media.  Get into the habit of backing up your data or use one of the many packages available and schedule your backups.
 

 With all of this in place you should be able to Recovery from a system crash or perform a “Clean Install Upgrade”.
 

 _Recovery/Clean Install Upgrade:_
 

 From my perspective the only difference between a Recovery and a Clean Install Upgrade, is that in a case of a Recovery the root file system or partition is borked.
 

 Follow the install script and specify the partitions manually.  If you are unsure which partition is what then nows the time to quit and verify.
 

 Identify your old OS partition, I mark it for format, and the mount point is “/”.  Identify your Home partition and make sure you **DO NOT** mark it for formatting, and the mount point is “/home”.  Double check your settings and hit that “forward” button.
 

 It is easier for me to just recreate the users in the order I initially created them, so the first user gets UID 1000 and lines up with the file permissions in my home directory.
 

 _Post Recovery/Upgrade:_
 

 Let the system boot and when you are logged in and on-line check for updates.  When all the OS updates are completed import the Synaptic file you saved earlier and let Synaptic re-install all your packages.  Check the differences of the new configuration files with your save ones, don't just blindly copy them over.
 

 Reinstall your home brew and check its functionality.  There can be differences between the releases when it comes to the various programs and their behavior.  Some adjustments may be necessary.
 

 I choose to reboot after every major section, i.e. between the install and the updates, just to ensure that I only have to trouble shoot one section at a time.
 

 The first hurdles to overcome are X11 and screen resolution, and network connectivity.  On my desktops I need to identify my monitor to get the resolution I desire, and on my laptop I nailed up my WiFi to connect only to my WiFi node automatically.  Once you get past this you should be able to update and reload your packages and enjoy the new OS.
 

 Keep in mind that there will always be that one package/program suit that requires re-installation no matter what you saved.  However, since you saved the configuration files it should be easy to re-install and configure.
 


_My “to be saved” configuration file list:_
 

 /etc/passwd
 /etc/group
 /etc/samba/smb.conf
 /opt/nessus  
 /etc/X11/xorg.conf
 /etc/fancontrol
 /etc/sensors.conf
 /etc/network/interfaces
 /etc/smartd.conf
 /etc/exports
 /etc/fstab
 /etc/nsswitch.conf
 /etc/apt/sources.list
 /usr/local/bin
 /etc/udev/rules.d/91-local.rules
 /var/log/bootchart
 

 Hope this helps.
 

 George

---

### Post by amitpokhrel on 2011-02-13
Is the trick behind making a home folder partition is that when the system crashes the partition with os will crash and we can recover everything from the home folder partition??
or is it necessary that I make a backup in my home partition and recover it later..
Please also help me to size partition for home partition and os partition.. mean how much space should i allocate for home partition and os partition

---

### Post by amitpokhrel on 2011-02-13
Is the trick behind making a home folder partition is that when the system crashes the partition with os will crash and we can recover everything from the home folder partition??
or is it necessary that I make a backup in my home partition and recover it later..
Please also help me to size partition for home partition and os partition..

---

### Post by georgemc on 2011-02-13
There are advantages with a separate home folder partition.
 

 Your home folder holds YOUR user and configuration data.  As you customize your desktop, configure  user applications etc., most of the customization data is saved in your home directory.  Many applications default to your home directory when saving data.
 

 You always make backups of your home directories and any of your other data for the case that your home directory partition becomes borked, lets say a HDD failure or pilot error.
 

 If any thing happens with the root partition, and therefor the OS, then your home partition is usually not affected and you need to only recover the root partition.
 

 You  need to look at the different failure scenarios, however, I feel that separating the User data from the OS helps facilitate any system recovery.
 

 As for partition sizing it all depends on how your are using your system and the size of your HDD.  Assuming that the sizes of  the HDDs these days are typical 100GByte and up, I would give root and therefore the OS at least 20-50GBytes of space.  Leaves plenty of room to grow, and plenty of log space.  The remainder of the disk I would allocate to Home directories and data.
 

 Hope this helps.
 George

---

