---
title: "Backup to a Virtual Machine"
date: 2011-03-23
forum: New to Ubuntu
---

### Post by KratosCrux on 2011-03-23
OK, so I have my netbook in a dual boot, and it has worked perfectly fine for years (upgrading to ubuntu 9.10 was a hassle though!). So one day I decided that I wanted to play some Steam games on my netbook (low graphics games such as Super Meat Boy), and Windoze had about a 7 minute boot time due to the large amount of crap I installed onto it (yeah I know I'm a horrible person) so I decided to re-install. Doing so messed up the partitions quite badly, so I used Testdisk to fix it ([http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)). Having been unable to use my netbook for a while now, I've decided to start fresh, but before I do that I would like to get my current un-bootable Ubuntu 10.10 onto a virtual machine. 

First, [COLOR="Red"]what is the best most reliable method of fixing the MBR and Grub2?[/COLOR]

Second, [COLOR="red"]what is the best way to backup to a virtual machine?[/COLOR]

My ubuntu installation uses Ext3, as I had trouble upgrading to Ext4 when 9.10 came out (or was that 9.04?), and my windows partition is Windows XP Home Edition.


So far, I've successfully backed up all of my data (my netbook has four partitions, [PQService (windows format)] [OS (windows xp)] [Ubuntu_FS] [Data (NTFS formatted data partition)] ) using this tutorial to backup the Ubuntu partition: [http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

I've tried backing up to a virtual machine, and I can get to the point where my data is fully in there, but I can never restore the GRUB2 boot menu / MBR successfully, and this deters me from doing so on my actual hardware. is using the second post in this forum a good idea for backing up? (the one by remmelt): [http://ubuntuforums.org/showthread.php?t=24113&highlight=grub+restore](http://ubuntuforums.org/showthread.php?t=24113&highlight=grub+restore)

if so, how exactly does the HD0,0 part translate? I've backed up and usually my partition is SDA5.

one last thing; when I do fix the grub2 menu on my computer, is booting into PQService to re-install windows XP a good idea? I was thinking that I should re-install windows as the only OS (no data partition either), then fix the windows MBR by booting from an Ubuntu Live CD, then using Lilo as follows:

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr 

using this method I've successfully restored the MBR on my windows 7 machine, is there another safer more reliable method than this?

after windows is fixed I would just use the ubuntu live CD to create 2 new partitions (ubuntu_fs ext4, and data ntfs) using GPartEd, and then when installing ubuntu set the root directory (/) to the EXT4 formatted partition (also another question, I don't quite remember if you need to manually create the extended partition and swap space, as I usually run memory intensive tasks and like to use hibernate, I made my swap space manually and set it to 2GB)

Sorry if this is at all rambling, I know it's quite long and I have a lot of questions to be answered, but I hope you can find the time to answer all of them. If not, the most important question is how to backup to a virtual machine. I'm using VMWare if that makes a difference.

another important point of note, I haven't done anything after I've used Testdisk besides backup my data, as I realize that modifying anything at this point could potentially result in disaster.

Thanks in advance for the help :D

---

### Post by KratosCrux on 2011-04-02
Bump? 

If nobody can answer that, can somebody at least tell me how to restore Grub2? there are an incredible amount of forum posts everywhere and I don't know where to go, or if the method outlined will even work (or if it will fubar any chances I have of recovering my install); all of them have mixed results, so please can somebody point me in the right direction for at LEAST restoring grub2

---

### Post by wolfen69 on 2011-04-02
> **KratosCrux said:**
> 

Second, [COLOR="red"]what is the best way to backup to a virtual machine?[/COLOR]


If you're not using the latest version of Virtualbox, then go to your home folder and do Ctrl-H to show your hidden files. You should see a .virtualbox folder. Just copy that and transfer it over to your new build. If you have a new version of VBox, there is a .virtualbox folder, + a regular folder called VirtualBox VMs. Copy both.

I have to leave now, but I'm sure someone can help with Grub.

---

### Post by Hedgehog1 on 2011-04-02
KratosCrux,

OK if we form a 'game plan' to restore your netbook to operating condition and your data all safe?

The basic flow is this:

1) Boot off a LiveUSB of Ubuntu, either 9.10 or 10.04 (if you want to upgrade since you are going to do a reinstall anyway).

2) Select the 'TRY' from the Live USB, mount you internal storage, and then using nautilus (GUI) copy your data to an external drive (Large USB stick, USB hard drive).  Be sure to copy your 'VirtualBox VMs' folder as part of this you you don't loose your Virtual machines. You can also copy any Windows data you might need. **(I think you have done this step)**

3) Make sure a 2nd time you have copied everything you need.

4) Install XP again (I think it is a BIOS option in most netbooks?); let it overwrite the disk.  This step updated the MBR with the 'Windows only' one.

5) Once XP is tested and running (and finished it updates) defrag it and then install Ubuntu 9.10 (or 10.04) as a side-by-side/dual boot from the LiveUSB. This also updates the MBR with Grub.

6) Copy your data back to XP and Ubuntu parititons from your external USB Stick/USB Drive.


***The Hedge***

:KS

---

### Post by KratosCrux on 2011-04-02
> **Hedgehog1 said:**
> KratosCrux,

OK if we form a 'game plan' to restore your netbook to operating condition and your data all safe?

The basic flow is this:

1) Boot off a LiveUSB of Ubuntu, either 9.10 or 10.04 (if you want to upgrade since you are going to do a reinstall anyway).

2) Select the 'TRY' from the Live USB, mount you internal storage, and then using nautilus (GUI) copy your data to an external drive (Large USB stick, USB hard drive).  Be sure to copy your 'VirtualBox VMs' folder as part of this you you don't loose your Virtual machines. You can also copy any Windows data you might need. **(I think you have done this step)**

3) Make sure a 2nd time you have copied everything you need.

4) Install XP again (I think it is a BIOS option in most netbooks?); let it overwrite the disk.  This step updated the MBR with the 'Windows only' one.

5) Once XP is tested and running (and finished it updates) defrag it and then install Ubuntu 9.10 (or 10.04) as a side-by-side/dual boot from the LiveUSB. This also updates the MBR with Grub.

6) Copy your data back to XP and Ubuntu parititons from your external USB Stick/USB Drive.


***The Hedge***

:KS

So, maybe you misunderstood or something, but I don't wish to backup my virtual machines (my system didn't have virtualbox or VMWare installed). What I want to do is take my backup that I made (it's in a tar.gz zip folder) and restore it to a virtual machine on my other computer (other PC runs Windows 7 x64).

I have backed up the data on my Data partition, and as I mentioned before, I've used tar to back up my operating system

as for re-installing windows XP, the option is in grub, so that's basically the reason I want to restore grub on my hardware.

If that same command is in the boot menu then restoring grub might not be necissary... although I do want to get my OS working as it was before, so restoring the grub on my hardware might not be the best idea until I can restore it in a virtual machine

I've come across another issue with restoring my TAR backup to a virtual machine though, maybe it's because I'm completely unskilled in this particular area, but I backed up from a live CD so now inside the tar.gz file there are 2 folders, "/media/sda5", and when I try restoring it keeps trying to make an SDA5 folder under media instead of backing up to the partition I specify with -C... I'll post the command I've been using when I can.

---

### Post by KratosCrux on 2011-04-03
So, just to clarify:

I have a netbook, I backed up the Ubuntu partition (ext3 10.10) onto an external harddrive using this tutorial ([http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)) and now have a directory on that hard drive as follows:

/Bac_201/KC201_Bac.tar.gz

I backed up from a live CD, so now inside of this tar.gz archive there are two folders, media and sda5, sda5 ofcourse containing my operating system.


On my virtual machine I created an Extended partition, made a 2GB swap space and the rest is ext3 (ext3 space is mounted as sda1)

here is what I've tried to do inside the virtual machine to restore:

```
sudo -s
mkdir /media/FROM/
mkdir /media/TO/

mount /dev/sdb1 /media/FROM/
(sdb1 is the drive that has the tar file on it)

mount /dev/sda1 /media/TO/
(sda1 is the new ubuntu filesystem in the VM)

cd /

tar -xvpzf /media/FROM/Bac_201/KC201_Bac.tar.gz media/sda5/ -C /media/TO/
```

this is apparently supposed to extract the contents of /media/sda5 (a folder inside the tar file) from the tar file named KC201_Bac to sda1 (the virtual hard drive)

but instead it just creates the directory sda5 under media of the live ubuntu cd, how do I extract to sda1?

---

### Post by KratosCrux on 2011-04-08
Bump? 

I haven't been able to try anything really in the past few days so I'm going to try backing up again to a new tar file and post the results... see if starting over again will help this.

---

### Post by Learning Linux 2011 on 2011-04-08
> **KratosCrux said:**
> Bump? 

I haven't been able to try anything really in the past few days so I'm going to try backing up again to a new tar file and post the results... see if starting over again will help this.


It's ironic that your signature reads: [COLOR=DimGray]Some people might not know what you are talking about. Plz; Break it Down

[/COLOR]I think that is exactly what you need to do in this case.  You are talking about too much at one time.

---

### Post by Learning Linux 2011 on 2011-04-08
> **KratosCrux said:**
> Bump? 

I haven't been able to try anything really in the past few days so I'm going to try backing up again to a new tar file and post the results... see if starting over again will help this.


It's ironic that your signature reads: [COLOR=DimGray]Some people might not know what you are talking about. Plz; Break it Down

[/COLOR]

---

### Post by KratosCrux on 2011-04-08
yeah... did you see post number six (6)
personally I think that is quite broken down
this is a complicated matter as I'm sure most things are on these forums

your helpfulness - 1/10 

sorry I'm just trying to get help here, I'm sure you know how this feels.
also, I'm looking for people's opinions on what I should be doing to help this situation, not commentary on my signature, thank you very much.

---

### Post by Learning Linux 2011 on 2011-04-08
> **KratosCrux said:**
> yeah... did you see post number six (6)
personally I think that is quite broken down
this is a complicated matter as I'm sure most things are on these forums

your helpfulness - 1/10 

sorry I'm just trying to get help here, I'm sure you know how this feels.
also, I'm looking for people's opinions on what I should be doing to help this situation, not commentary on my signature, thank you very much.

My point was that YOU need to do exactly what your signature reads.

This is the Absolute Beginner section.  

(#1) You are asking too much for this section
(#2) You are asking too much in one thread.
(#3) What you are asking isn't very clear to the average person.

If your post has gone that long without a response, it is because it is either in the wrong category (which it is) or it is asking too much at one time (which it also is).

People don't know what you are talking about.  If you want help, break it down.  Follow your own advice.

---

### Post by KratosCrux on 2011-04-09
> **Learning Linux 2011 said:**
> My point was that YOU need to do exactly what your signature reads.

This is the Absolute Beginner section.  

(#1) You are asking too much for this section
(#2) You are asking too much in one thread.
(#3) What you are asking isn't very clear to the average person.

If your post has gone that long without a response, it is because it is either in the wrong category (which it is) or it is asking too much at one time (which it also is).

People don't know what you are talking about.  If you want help, break it down.  Follow your own advice.

Thank you, I realize this is the absolute beginner's section, and you're right :D. Sorry I don't know this site too well. I've made a new forum post in the General section, the only reason I created it here was because I consider myself a total noob Q.Q

If you or anybody else has anything further to ask me please e-mail me, [email]kratos_crux@googlemail.com[/email]




Here is a link to the newest forum about this subject:
[http://ubuntuforums.org/showthread.php?p=10655492#post10655492](http://ubuntuforums.org/showthread.php?p=10655492#post10655492)

---

