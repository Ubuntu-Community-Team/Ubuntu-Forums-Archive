---
title: "Moving wubi install to a different dual partition?"
date: 2011-07-25
forum: New to Ubuntu
---

### Post by Lucypie on 2011-07-25
Okay, I'm not a complete beginner. I know how to do a good bit of whathaveyou, but I still sometimes get lost, which is why I am making my own post. I saw a few similar to this question, but none were understandable by me. 

I'll start by giving you a good list of information.

Ubuntu Version: 11.04 (but using the ubuntu classic theme until I can figure out how to edit the top bar & have menus)
Installation process: I installed it via Windows 7 using a Ubuntu 10.04 wubi installation. I then upgraded it to 11.04
I have a 320 GB hard drive
I have 4 gigs of RAM
Ubuntu is installed on a 20GB partition.

I wish to keep all my programs and settings without having to reinstall all of them and re-set-them up. I have a XAMPP server and a bunch of custom scripts installed for many purposes.

This is what I want to do:

I want to resize my windows partition to a very small size (whatever the most I can resize it) and make a fresh partition for UBUNTU. I wouldn't mind reinstalling ubuntu and stuff, but I need help making sure I have my programs and such. How can I go about doing this without losing stuff?

I do have a 40GB External HDD and a 120 GB laptop drive (to the side) that I could use if need be, for program storage, but I still want those scripts and such.

---

### Post by oldfred on 2011-07-25
I do new clean installs and my backup procedure is to make sure I have copies of what I need.

HOWTO: migrate wubi install to partition - bcbc 
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

Originally Posted by MountainX View Post #20 also other backup apps
[http://ubuntuforums.org/showthread.php?t=868244&highlight=backup](http://ubuntuforums.org/showthread.php?t=868244&highlight=backup)
Sample rsync file, use a text editor and paste into a file & name it mybackup.sh

Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
backup the following:

1. /home (Users' personal files and settings)
2. /etc (System-wide configuration settings)
3. /var/spool/cron/crontabs (Commands which run automatically)
4. The script to generate the backup
5. list of installed applications 

I include these also:
cp /etc/apt/sources.list ~/sources.list.backup
apt-key exportall > ~/repositories.key
Various hardware listings/configurations
dpkg --get-selections > ubuntu-files
bash ~/Documents/LinuxDocs/CurrentSys/boot_info_script055.sh
lshw -html > ~/hardware_info.html
udevadm info --export-db > file.txt
dmidecode > bios.txt

Other applications if data not separate
apache, any sqldb, tomcat 
Document system backup or for multiple install:
[http://users.telenet.be/mydotcom/howto/linux/autoinventory.htm](http://users.telenet.be/mydotcom/howto/linux/autoinventory.htm)

If you have room leave wubi installed untill after you know you have copied everything over. Windows does want 30% free space to work well but you will add space after you delete wubi.

If still using windows I also suggest a shared NTFS partition for any data you want in both.

---

### Post by Lucypie on 2011-07-25
My goodness! Thank you so much for the quick response and very helpful information!! 
I will get to work right away and within 3 hours edit this post with my results. I thank you so very much.

--EDIT:::

We have a problem. Somehow my ubuntu partitions are ... Combined with windows? I don't  bloody know. It's not showing an ubuntu partition on Gparted or windows partition deal. I'm going to install 11.04 and start fresh but put my files and crap on it. If my settings are easily backed up, I will do the same on my fathers computer. he also wants his partition moved.

---

### Post by anewguy on 2011-07-25
+1.  Also, I'd move away from a wubi install (that's normally used just to try it out a little) and go with a dual-boot system, where Ubuntu is installed in it's own partition and you get the grub menu at boot.  I also wouldn't worry too much about shrinking your Windows down so much.  With a 320gb drive, you should have more than plenty of room for both.

So, with that in mind, this is what I would do if it was me (just my opinion):
[LIST]
[*]Boot into Windows and defrag the disk twice.  Yep, twice.  Don't do anything else on the PC.  The idea is to get rid of fragmented files and leave the disk as clean as possible
[*]Backup anything you want to keep from your Windows install, "just in case"
[*]Using the LiveCD, boot and click on install
[*]When prompted about disk usage, select manual
[*]Set the size of your Windows partition down by say 100gb max - that will give you a *heck* of a lot of room in Linux
[*]Create a partition for swap - if a laptop and you plan to hibernate, make the swap just a little over twice the size of the amount of ram memory you have.  Some would contradict that, I just know that for me personally it has always had one problem or another until I just did that.
[*]Create partition of 20gb and set it's mount point to "/"
[*]Create a partition using the rest of the disk and set it's mount point to "/home"
[*]Continue with the installation.
[/LIST]
I'm not saying it's the best or only way to do it, just what I would do.  Others will post here as well with their opinions.

Good Luck!

---

### Post by Lucypie on 2011-07-25
I will be printing your answer and doing that. I already defragged it (one and a ... half? times) but I will do it another two times. As soon as I finish downloading 11.04 iso that is. I'm going to burn a fresh disk to insure that I get the *absolute* best chance at this working. I've had some errors with my old disk, which is another reason I'm making a new one. I tried the merging wubi into a new one,  but I get several errors. One being about how I have no extra size (even though I have 100G+ unallocated.) and another about how I can make only a max of 32G, but I want about 100G. So I think I will be doing a fresh install and trying to just reupload my settings and files. hopefully, it will all work. 


Once more, I wish to thank you all for answers, so much.

---

