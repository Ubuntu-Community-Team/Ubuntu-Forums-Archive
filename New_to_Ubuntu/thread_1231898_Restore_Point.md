---
title: "Restore Point"
date: 2009-08-05
forum: New to Ubuntu
---

### Post by BobJam on 2009-08-05
Us noobs 'speriment a lot to see what works.  Often, those 'speriments screw up the system and the settings we've worked hard to make before we start a new 'speriment.

Consequently, we often want to go back to the way things were before our 'speriment screwed things up.

In Windows, that was a Restore Point.  Is there something like this in Ubuntu?

I've done a Google on this, and the closest I can come to is a thread here on this forum about making a partition image.

Is that the solution for this problem, or is there another method to achieve the same result?

---

### Post by kansasnoob on 2009-08-05
The short answer is no.

Although you can track installation/removal of packages in Synaptic by going to File > History.

And under some circumstances you can boot into recovery mode to restore some configuration files.

---

### Post by ugm6hr on 2009-08-05
> **BobJam said:**
> I've done a Google on this, and the closest I can come to is a thread here on this forum about making a partition image.

This is the best option for this.

---

### Post by expatCM on 2009-08-05
It is REALLY hard to trash Ubuntu.  I have found it possible to dig some rather impressive holes but I have always managed to get out of them.  This forum is a great help when it comes to getting out of trouble ....

---

### Post by lisati on 2009-08-05
Another option is to get your machine configured how you like it, and use [remastersys]("http://www.geekconnection.org/remastersys/remastersystool.html") to create a custom LiveCD. Then when your experiments go haywire, you can pull out your custom LiveCD and put your computer back how it was.

---

### Post by bodhi.zazen on 2009-08-05
Your very best option , by far, is to  'speriment with a virtual machine and a snap shot =)

---

### Post by ubudog on 2009-08-05
> **bodhi.zazen said:**
> Your very best option , by far, is to  'speriment with a virtual machine and a snap shot =)

Yes that is what I do.  I have an installation of 9.04 running in VirtualBox and that's what I use to test everything on before I do it on my main computer.

---

### Post by 3rdalbum on 2009-08-05
System restore points are so difficult to implement properly and reliably. The one in Windows doesn't seem to work very well, and restoring seems to fail about 50% of the time.

Making a partition image is the best solution on any operating system, as far as I can tell. To a great extent, things don't get implemented in Linux distributions until they have a good success rate and they work without hacks.

---

### Post by BobJam on 2009-08-05
From reading through this thread (thanks for all the responses BTW), I have decided to do two things:

[LIST]
[*]Put a Ubuntu in a VM (I already have a VM set up . . . have Windows XP in it . . . so that part will be easy) for my 'speriments.
[/LIST]

[LIST]
[*]Make a partition image so that I can restore from it if it becomes necessary.
[/LIST]
 On the first item above . . . that's pretty straightforward and I don't have any questions.

But on the second item, making a partition image, I have a few questions and comments.[INDENT] 1.  I don't have an external HDD, so I can either put the image in a partition on my internal HDD (the main flaw I see in this is if my HDD goes south on me), or do it to a CD(s?).

2.  Would I use "PartImage" for this?

3.  Would PartImage do a "destination" as CD/DVD's (like "Insert Blank CD #1", etc.), or does it just do images to an HDD?  I didn't see an option for this.  Can it be done, and if so how?

4.  I've read several tutorials, and I read one (damn, I didn't bookmark it so I'll have to look for it again) that seemed to say the program would save an image to a CD/DVD(s).  But none of them were very clear on this, though I could have missed something.  Have to read them over again.

5.  Read a tutorial on "Clonezilla", but it seemed very command line intense.  Being a noob, the simpler the command line stuff the better.  I don't like doing any commands that I don't understand completely, especially when it involves partitioning (will back up my data, no matter what I end up using).  Is similar to what my "rule" was for Windows Registry keys . . . if I didn't understand what the key was for and did, I didn't remove it even if CCleaner recommended removal.

6.  What's the difference between "Partition backups" and "Partition images"?  The reason I ask is because there's a thread on this forum titled "Howto: Backup and restore your system!" ( [http://ubuntuforums.org /showthread.php?t=35087]("http://ubuntuforums.org/showthread.php?t=35087")), and then there's a tutorial titled "Using PartImage in Ubuntu" ([http://psychocats.net/ubuntu/partimage](http://psychocats.net/ubuntu/partimage) ).  Both seem to speak to the same thing, so is it just terminology?  But the "Howto: Backup and restore your system!" uses a TAR file as the method, so I'm wondering if it's more than a terminolgy difference.

7.  The "Howto: Backup and restore your system!" thread seems like it would enable you put the zip (TAR?) on a CD, so that seems like what I want, but it's also command line intense.  And how would I test the validity of the file?  I don't want to overwrite my existing system just to see if the file is valid.  Is there another way to do it?

8.  The "Howto: Backup and restore your system!" thread **IS FOUR YEARS OLD FROM WHEN IT WAS FIRST MADE**.  And it's also 95 pages long!  (I haven't read all of it).  So I assume there have been improvements since then (PartImage?)

9.  IMAGE ON A PARTITION WITHIN INTERNAL HDD:[INDENT]a.  As I said before, the main flaw I see in this is if my HDD goes south on me, so would the imaged partition.  That's why I would prefer to do a CD/DVD image.  Or can I send it to a USB stick, and would it be bootable with whatever removable media I used?

b.  I have plenty of room, so making the partition is OK there.

c.  Would I use gparted to make another partition for this image?
[/INDENT]10.  IMAGE ON REMOVABLE MEDIA:[INDENT]a.  This is my preferred method.

b.  Again, would it be bootable?

c.  Any way to make it an .iso?
[/INDENT]11.  I looked at "remastersys" (thanks, lisati), and it seems like it might do what I want (store the image on removable media), plus it says it makes it a "Live CD", which I assume means it's bootable.  Is there any limitation on the total uncompressed size of the files to be imaged?  Is this easier to use than PartImage and does it do the same thing?
[/INDENT]
OK . . . I'll probably have more questions as I go along, but the answers to these will be enough to get me started.

BTW, I'm **not** so worried about Ubuntu itself crashing (Is there an Ubuntu version of the Windows BSOD?  If so, I've not seen it.), but rather my intent is to be able to restore my unique **WORKING** config if I need to.

TIA

---

### Post by mapes12 on 2009-08-05
> **BobJam said:**
> From reading through this thread (thanks for all the responses BTW), I have decided to do two things:

[LIST]
[*]Put a Ubuntu in a VM (I already have a VM set up . . . have Windows XP in it . . . so that part will be easy) for my 'speriments.
[/LIST]

[LIST]
[*]Make a partition image so that I can restore from it if it becomes necessary.
[/LIST]
 On the first item above . . . that's pretty straightforward and I don't have any questions.

But on the second item, making a partition image, I have a few questions and comments.[INDENT] 1.  I don't have an external HDD, so I can either put the image in a partition on my internal HDD (the main flaw I see in this is if my HDD goes south on me), or do it to a CD(s?).

2.  Would I use "PartImage" for this?

3.  Would PartImage do a "destination" as CD/DVD's (like "Insert Blank CD #1", etc.), or does it just do images to an HDD?  I didn't see an option for this.  Can it be done, and if so how?

4.  I've read several tutorials, and I read one (damn, I didn't bookmark it so I'll have to look for it again) that seemed to say the program would save an image to a CD/DVD(s).  But none of them were very clear on this, though I could have missed something.  Have to read them over again.

5.  Read a tutorial on "Clonezilla", but it seemed very command line intense.  Being a noob, the simpler the command line stuff the better.  I don't like doing any commands that I don't understand completely, especially when it involves partitioning (will back up my data, no matter what I end up using).  Is similar to what my "rule" was for Windows Registry keys . . . if I didn't understand what the key was for and did, I didn't remove it even if CCleaner recommended removal.

6.  What's the difference between "Partition backups" and "Partition images"?  The reason I ask is because there's a thread on this forum titled "Howto: Backup and restore your system!" ( [http://ubuntuforums.org /showthread.php?t=35087]("http://ubuntuforums.org/showthread.php?t=35087")), and then there's a tutorial titled "Using PartImage in Ubuntu" ([http://psychocats.net/ubuntu/partimage](http://psychocats.net/ubuntu/partimage) ).  Both seem to speak to the same thing, so is it just terminology?  But the "Howto: Backup and restore your system!" uses a TAR file as the method, so I'm wondering if it's more than a terminolgy difference.

7.  The "Howto: Backup and restore your system!" thread seems like it would enable you put the zip (TAR?) on a CD, so that seems like what I want, but it's also command line intense.  And how would I test the validity of the file?  I don't want to overwrite my existing system just to see if the file is valid.  Is there another way to do it?

8.  The "Howto: Backup and restore your system!" thread **IS FOUR YEARS OLD FROM WHEN IT WAS FIRST MADE**.  And it's also 95 pages long!  (I haven't read all of it).  So I assume there have been improvements since then (PartImage?)

9.  IMAGE ON A PARTITION WITHIN INTERNAL HDD:[INDENT]a.  As I said before, the main flaw I see in this is if my HDD goes south on me, so would the imaged partition.  That's why I would prefer to do a CD/DVD image.  Or can I send it to a USB stick, and would it be bootable with whatever removable media I used?

b.  I have plenty of room, so making the partition is OK there.

c.  Would I use gparted to make another partition for this image?
[/INDENT]10.  IMAGE ON REMOVABLE MEDIA:[INDENT]a.  This is my preferred method.

b.  Again, would it be bootable?

c.  Any way to make it an .iso?
[/INDENT]11.  I looked at "remastersys" (thanks, lisati), and it seems like it might do what I want (store the image on removable media), plus it says it makes it a "Live CD", which I assume means it's bootable.  Is there any limitation on the total uncompressed size of the files to be imaged?  Is this easier to use than PartImage and does it do the same thing?
[/INDENT]
OK . . . I'll probably have more questions as I go along, but the answers to these will be enough to get me started.

BTW, I'm **not** so worried about Ubuntu itself crashing (Is there an Ubuntu version of the Windows BSOD?  If so, I've not seen it.), but rather my intent is to be able to restore my unique **WORKING** config if I need to.

TIAI've been using Ubu for 2 years and my head was swimming with Backup ideas off the forums. I've tried all the solutions you mention in your post. I found Remastersys not to work. Heliode's tar solution works for me. I recently restored my system from a tar file like this:

> Backup Routine:

Terminal -
sudo mkdir /HDD2
# creates a folder in the filesystem folder called HDD2

sudo mount /dev/sdb1 /HDD2
# mounts the 2nd HDD Linux partition to the file system via the above directory

Backup /home/mark -
sudo tar cvpzf /HDD2/Backup/Home/Mark/bkp-home-mark.tgz /home/mark

Backup /(root) -
sudo tar cvpzf /HDD2/Filesystem/bkp-root.tgz --exclude=/home --exclude=/HDD2 --exclude=/etc/fstab --exclude=/tmp --exclude=/boot --exclude=/proc --exclude=/lost+found --exclude=/media  --exclude=/mnt --exclude=/sys /
# The first two excludes are so that we don't make a second backup of /home and we don't want to backup the second hard drive where we are making the backup to.

SYSTEM DAMAGE!!!!

Reinstall Ubuntu

Then:-

Restore -
Terminal -
sudo mv /HDD2/Backup/Home/bkp-home.tgz /
sudo mv /HDD2/Backup/System/bkp-root.tgz /
# The above will move the tarfiles from the second HDD back into the root file system


sudo su
tar xvpfz bkp-root.tgz -C /
tar xvpfz bkp-home.tgz -C /

Restart the PC.
You will notice that I have more --excludes than Heliode's original post. Much reading on the forums created my approach. It works perfectly.

Another method is to image the partition using Partimage. I found it much easier than Clonezilla. Here's my drill:

> Backup:

   1. Boot from the Partimage System Rescue CD
   2. in Terminal mount a file system on another partition other than the files system. E.g. mount /dev/sda6 /home mounts the /home partition
   3. Back in Partimage select the partition where the filesystem is located to back it up e.g. sda5 
   4. Tab down to the location to make the backup i.e. your mount point and give the backup a file name e.g. /home/mark/partimage/filesystem will create the backup file called filesystem at the path /home/mark/partimage Note - The directory /partimage in the user folder /mark must have been created before running the backup routine
   5. Hit F5 to move to the next screen
   6. Do NOT use any form of compression
   7. Tab down and deselect the description box
   8. Hit F5 to run the backup


Restore:

   1. Boot from the Partimage CD
   2. In Terminal mount the device where the backup is located
   3. On the next screen select the option that places zero's in unused space
   4. Hit F5 to restoreThe trick with this solution is to get familiar with mounting the partition you want to back up too. N.B. Partimage doesn't seem to recognise upper case directory names. Use all lower case you you should be fine. Also, any form of compression (at least for me) and the restore fails. This solution is very very quick - less than 2 minutes to create image file on my test machine the other day.

To be sure you have a safe backup file (either method) you will need to save it on another drive. That of course can be another HDD (as in my tar solution) or DVD's or across a LAN connection (personally, I use SSH - really easy) to another machine.

Hope this helps.

All the best.

Mark :D

---

### Post by Mark Phelps on 2009-08-05
If you're still interested in using Partimage but don't want to deal directly with it, check out Partimage Is Not Ghost (P.I.N.G) -- a front-end to Partimage that the ping.windowsdream.com folk provide for free.

---

### Post by Trent T on 2009-09-06
Hi BobJam--

I migrated to Ubuntu Linux about 2 years ago and never had a problem-- Until last week, when I thought my hard drive seized!  This got me thinking about how to backup my entire work and play environment to a different physical drive, in case the drive seizes for real the next time!  Here's what I did:

I got a 2nd hard drive from TigerDirect, and installed it:

Get gparted using the Synaptic utility.  
Follow gparted directions to get the drive formatted, then
Create a mountpoint directory for your new drive from within 'terminal.' For example,
typing the commands

sudo mkdir /home/myusername/backupdrive
sudo mount /dev/sdc1 /home/myusername/backupdrive

will define a new directory called 'backupdrive,' 
and then will mount your new hard drive that system calls 'sdc1' as ...backupdrive.

The next time you look in your home/myusername/ directory, you will see a new subdirectory called 'backupdrive.'  You can read and write files to it just as if it was any other subdirectory on your original harddrive.

BACKING UP--

This is done from 'terminal,' once again.

sudo su                            <-- Makes you the superuser.
cd /home/myusername/backupdrive    <-- changes you to the backupdrive directory

tar cvpf backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/home/myusername/backupdrive/backup.tgz --exclude=/mnt --exclude=/sys /

This long command (all on a single line) creates an archive backup named 'backup.tgz' within the backupdrive directory.  You can compress the files as well by starting it out as;

tar cvpzf backup.tgz....
 
The exclusions are there to prevent backup of files and directories that you don't need, or that would be recursive.

Next Step: Make A Bash Script

It was a great relief to find a way to backup my hard drive.  
I don't like all the fiddly typing though, so I am cobbling together a bash script that I can run at the end of every day.  If I get it to work, I will try to post it in case anyone is interested in adapting it to their own system.

--Trent T

Disclaimers--
Most of this info was plagiarized from;
Heliode - Howto: Backup and restore your system! on ubuntuforums.org

I am also stealing as many ideas as possible from;

Online book 'Advanced Bash Scripting Guide' by Mendel Cooper - [email]thegrendel.abs@gmail.com[/email] - [http://tldp.org/LDP/abs/html/index.html](http://tldp.org/LDP/abs/html/index.html)

---

### Post by mapes12 on 2009-09-07
FSArchiver is relatively new and looks to automate the whole tar thing. I've not had chance to give it a go but would like to hear from anyone that has. I believe it's written by the Partimage guys so good news there.

[http://www.fsarchiver.org/Main_Page](http://www.fsarchiver.org/Main_Page)

---

### Post by Trent T on 2009-09-11
Thanks mapes12!!

I may try backing up and restoring my Ubuntu 8.0.4 hard-drive with FSArchiver, if I can resurrect it one more time...

---

### Post by LewRockwell on 2009-09-11
very good thread

very good posts

very good information

we use clonezilla(mostly because it's the hammer in the toolbox...and will get the job done no matter what operating system/file system you're utilizing at that period of time)

NEVER trust Windows and/or supposed Restore Points

as always, your mileage may vary

we now return you to your regularily scheduled programming

.

---

### Post by mapes12 on 2009-09-11
> **LewRockwell said:**
> very good thread

very good posts

very good information

we use clonezilla(mostly because it's the hammer in the toolbox...and will get the job done no matter what operating system/file system you're utilizing at that period of time)

NEVER trust Windows and/or supposed Restore Points

as always, your mileage may vary

we now return you to your regularily scheduled programming

.+1 for Clonezilla. Works for me as well.

If you're new to Linux just get your head around the concept of mounting virtual (in memory not on HDD) directories and Clonezilla is then a breeze. If you have no idea what I'm rambling on about then please post back.

Mark

---

### Post by nhasian on 2009-09-11
+1 for Clonezilla

you cannot use Clonezilla from within Ubuntu because you cannot backup a partition while its in use.  You must download and burn the Clonezilla ISO to a CD and boot from it to backup or restore individual partitions or entire devices.

I like to play with the development version of Ubuntu which thus far is Karmic Koala.  before doing a risky dist-upgrade I like to backup my root partition with Clonezilla.  It's saved my butt several times.

---

