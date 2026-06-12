---
title: "Pulling My Hair Out Trying To Upgrade!!!"
date: 2010-12-05
forum: New to Ubuntu
---

### Post by ozark_hillbilly on 2010-12-05
I need some help. 
I like the stability of Linux and want to upgrade from Jaunty to Lucid to keep things updated. I have both now installed and can select which to boot up. The problem is during the Lucid install no user data was transferred from Jaunty as I directed during the install process.
I now want to get my files put on the Lucid install. File permissions are getting in the way. Is there a way I can disable file permissions or make it so that I can ALWAYS transfer ANY file I want? When I went into Root Terminal and used nautilus the files I put on the Lucid partition have a padlock icon on them. Evidently Root has control of them now. 
Upgrading is turning into a huge PITA. I would like to see Linux more widely used by computer users but the learning curve is a huge stumbling block.

Am I looking at much money to have someone locally do this for me?

Ed

---

### Post by lbarnes on 2010-12-05
Can't help ya but GO HOGS!!!

---

### Post by lindsay7 on 2010-12-05
This is what I would do to set things up for the future.  Back up what you need first of all.  Then repartition you drive so that you have a / partition for 10.4 and a "home patition" which you will store all of your user info and other data. Set up a partition where you can install new versions of Ubuntu (10.10 for example), and you will need a swap partion.  So at the minimum you would have something like this

sda1 "/"  for 10.4
sda2 "home"  this is to share
sda3 "/" for 10.10 or newer
sda4 "swap"

This would be a bare bone set up, you could also partition with a extended partition to accommodate the "home" share partition and other partitions if you would like.

This way when you want to install a new version of Ubuntu you would only install it to the "/" partition and leave the other partitions alone and unchanged.

---

### Post by ozark_hillbilly on 2010-12-05
I appreciate the help but what do I do if I don't understand all the /sda1 partition stuff? This is Greek to me. And herein is where I feel the complexities of Linux will never allow it to be as widely accepted as MSDOS.
I don't like Microsoft but don't like the learning curve of 
linux either. 
I have a separate hard drive that backs up my Jaunty data every week. That much i figured out. I am loathe to go creating more partitions etc for fear of screwing up what works now. I just need a clean way of transferring my user files from one Linux distrubution to another. Without having to try and change all the user permissions for the files.
Dazed and Confused,

Ed

---

### Post by colin.p on 2010-12-05
> **ozark_hillbilly said:**
> I need some help. 
I like the stability of Linux and want to upgrade from Jaunty to Lucid to keep things updated. I have both now installed and can select which to boot up. The problem is during the Lucid install no user data was transferred from Jaunty as I directed during the install process.
I now want to get my files put on the Lucid install. File permissions are getting in the way. Is there a way I can disable file permissions or make it so that I can ALWAYS transfer ANY file I want? When I went into Root Terminal and used nautilus the files I put on the Lucid partition have a padlock icon on them. Evidently Root has control of them now. 
Upgrading is turning into a huge PITA. I would like to see Linux more widely used by computer users but the learning curve is a huge stumbling block.

Am I looking at much money to have someone locally do this for me?

Ed

If all you want is to copy over your user data from jaunty, then why don't you do a backup (grsync or luckybackup) of your jaunty home directory onto an external drive (a USB jump drive for instance) and then when you are booted into lucid, just copy and paste from the backup.
I did that when I did a clean install of lucid from karmic and I didn't lose a darn thing. I didn't encounter any permission issues whatsoever either.

---

### Post by Old_Grey_Wolf on 2010-12-05
Boot into Lucid. Then open a terminal and type without the quotes "gksudo nautilus". Enter your password. Enable show hidden files in nautilus by pressing Ctrl+h. Find the /home directory in Jaunty and copy it to the Lucid /home directory.

If you need to change permissions, right click on a folder after it is copied, select Properties, then select the Permissions tab, change the permissions, and click the Apply Permissions to Enclosed Folders button

---

### Post by tgm4883 on 2010-12-05
> **ozark_hillbilly said:**
> I appreciate the help but what do I do if I don't understand all the /sda1 partition stuff? This is Greek to me. **And herein is where I feel the complexities of Linux will never allow it to be as widely accepted as MSDOS.**
I don't like Microsoft but don't like the learning curve of 
linux either. 
I have a separate hard drive that backs up my Jaunty data every week. That much i figured out. I am loathe to go creating more partitions etc for fear of screwing up what works now. I just need a clean way of transferring my user files from one Linux distrubution to another. Without having to try and change all the user permissions for the files.
Dazed and Confused,

Ed

Lets just clarify one thing. You are adding the complexities here, not Linux. You want to multiboot and share your home directory between them. That isn't something that dos/windows does easily either.

---

### Post by ozark_hillbilly on 2010-12-05
> **tgm4883 said:**
> Lets just clarify one thing. You are adding the complexities here, not Linux. You want to multiboot and share your home directory between them. That isn't something that dos/windows does easily either.

No, I am not wanting to share my home directory. I wanted to simply upgrade my Linux OS and the install process decided to not copy my user data. If the install of Lucid had transferred my files I wouldn't be in the current pickle I'm in.

---

### Post by ozark_hillbilly on 2010-12-05
> **Old_Gray_Wolf said:**
> Boot into Lucid. Then open a terminal and type without the quotes "gksudo nautilus". Enter your password. Enable show hidden files in nautilus by pressing Ctrl+h. Find the /home directory in Jaunty and copy it to the Lucid /home directory.

If you need to change permissions, right click on a folder after it is copied, select Properties, then select the Permissions tab, change the permissions, and click the Apply Permissions to Enclosed Folders button

This sounds straightforward enough. This is gonna sound stupid but I don't care right now. How do I find the the Jaunty and Lucid home directories? Is the \Home directory considered Jaunty and \Media\Disk\Home considered Lucid?

Ed

---

### Post by Old_Grey_Wolf on 2010-12-05
> **ozark_hillbilly said:**
> No, I am not wanting to share my home directory. I wanted to simply upgrade my Linux OS and the install process decided to not copy my user data. If the install of Lucid had transferred my files I wouldn't be in the current pickle I'm in.

I don't recall 10.04 Lucid ever asking if I wanted my user data to be copied when doing a fresh install. I've only installed it on 5 computers though.

---

### Post by Old_Grey_Wolf on 2010-12-05
> **ozark_hillbilly said:**
> This sounds straightforward enough. This is gonna sound stupid but I don't care right now. How do I find the the Jaunty and Lucid home directories? Is the \Home directory considered Jaunty and \Media\Disk\Home considered Lucid?

Ed

Yes, it should be. You can explore the contents of /Media/Disk/Home to be sure. You could boot Jaunty and save a file called Test_Something then check that it shows up in the /Media/Disk/Home directory after booting to Lucid.

Edit: The use of "\" is Windows while "/" is Linux. ;)

---

