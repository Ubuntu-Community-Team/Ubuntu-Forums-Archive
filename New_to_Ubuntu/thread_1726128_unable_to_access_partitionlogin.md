---
title: "unable to access partition/login"
date: 2011-04-10
forum: New to Ubuntu
---

### Post by spottsy66 on 2011-04-10
Hi,  

I'm new to Ubuntu and hope you can help with a problem(s).  I'm running  Ubuntu 10.10 on an Acer Aspire 5745.  It's a dual boot with Windows 7.  I  did a normal install of Ubuntu, not Wubi.  

On to the problem.  Last Sunday I was running what I believe was a  system update.  I don't know what was updating, although I do remember  that one of the files was relatively large or at least was taking a  while to download.  At the same time, I was working on a document in  Open Office when everything froze up.  My first mistake was shutting  down the computer manually (with the power switch) instead of letting it  do its thing.  

When I started it up again, I got the grub "minimal BASH-like line  editing" screen (which was cause for much consternation :D).  I couldn't get to the screen where I ordinarily would  be able to choose to run Ubuntu or Windows .  After looking at several  threads, I concluded that there was something wrong with my grub.  I  followed several different batches of instructions most of which  involved booting with a LiveCD and through the terminal was able to  reload/replace the grub.  I can provide links to the threads if that  would be helpful.  I can now get back to the  pick-which-OS-you-want-to-run screen.  Hurray!  I can start Windows  without a problem.  

However, when I choose the Ubuntu option it loads but I get to a screen  with the Ubuntu background and a white box in the middle of the screen  with an Ubuntu logo and that says "Ubunutu 10.10".  If I click in the  box with the mouse, it will switch to my computer's name.  But I can't  log in at all.  The user profile/name I had been using doesn't show up  at all.  Although there is the little on/off logo in the menu bar (now  at the bottom of the screen, it used to be at the top), it won't shut  down or restart if I click it.  

Furthermore, I can't access the  data on my Ubuntu partition.  My biggest concern is recovery of the  data--several chapters of a novel  that I foolishly haven't backed up for quite some time.  I'm willing to  sacrifice all the other data on the disk and/or partition.  I cannot  access this partition from Windows.  I've been at  this for 4 or 5 hours today and I'm about ready to pull out my hair :D 

One other thing I noticed:  On the page where I could choose OSes, the  Ubuntu option used to have a parenthesis with "sda5" following it.   Ubuntu is installed on sda5 (which is dedicated solely to the OS).   There are now three options for loading Ubuntu (there used to be only  one), none of which have the "sda5" following it.  

I'm happy to provide as much more info as I'm able.  

Thanks very, very much in advance.

---

### Post by Quackers on 2011-04-10
Welcome to UF.
From the live desktop, making sure you have an internet connection and being sure that sda5 is indeed your Ubuntu root partition (and that you don't have a separate Ubuntu /boot partition) please open up a terminal and copy/paste each of these lines into the terminal, one line at a time, pressing enter after each line.
```
sudo mkdir /mnt/temp
sudo mount /dev/sda5 /mnt/temp
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/temp$i;  done
sudo cp /etc/resolv.conf /mnt/temp/etc/resolv.conf
sudo chroot /mnt/temp
```
At this point your terminal prompt should change from ubuntu@ubuntu
to root@ubuntu
If it hasn't you need to start again.
Now please run these lines one at a time, pressing enter after each line.
```
apt-get update
dpkg --configure -a
```
the first command may scroll many lines of text and may even give errors.
Please run the second line when your root prompt returns and report anything that happens.

---

### Post by spottsy66 on 2011-04-10
Hi Quackers,

Thanks for replying so quickly.  I ran the commands in your post.  Everything ran fine, and I was able to access the root prompt.  After running the first command with the root prompt, a long list of URLs was displayed.  After running the second command under the root prompt, I was returned to the root prompt; no other text was displayed.  What's next?

---

### Post by Quackers on 2011-04-10
The second command gave no output then?

---

### Post by spottsy66 on 2011-04-10
Nope.  Should I run it again?

---

### Post by Quackers on 2011-04-10
No, that's unexpected, but ok.
While we are chrooted into your system we can make sure that grub is installed and working correctly.
Please enter the following commands into the terminal
```
apt-get purge grub grub-pc grub-common
```
You will get a warning about making the system unbootable. That's ok, just tab to the "YES" and press enter
Then run ```
apt-get install grub-common grub-pc
```
During this command you will get a white box popping up asking about kernel additions. Tab to "OK" and press enter.
Then it will give details of the installation notes. Tab to "OK" and press enter.
It will then give details of the device options.
The top item should be /dev/sda and it should be highlighted. That is where you want to install grub. To select /dev/sda, while it is highlighted press the space bar and you should see a * appear in the box.
Tab to "OK" and press enter.
When that has finished, reporting no errors, run ```
 update-grub
```
When that has run please run ```
exit
```
then
```
for i in /dev/pts /dev /proc /sys; do sudo umount /mnt/temp$i ; done
```
At this point your terminal prompt should be back at ubuntu@ubuntu.
Please then go to the places menu and see if your Ubuntu partition is named. If it is open it and view your files. Back them up if you want to.
When all is done please reboot and see if Ubuntu then boots.

---

### Post by spottsy66 on 2011-04-10
I followed your instructions.  Under the "Places" menu, it is called "Home".  I was able to access my files, except for the folder I need to--with the chapters I'm trying to salvage.  The folder icon has an "X" in the corner.  When I tried to open the folder I was told "The folder contents could not be displayed.  You do not have the permission necessary to view the contents of [folder name]."  Would it matter that I had files from this folder open when I shut down last Sunday?

When I rebooted, I got the same thing as I had been getting--the Ubuntu  background with the white box with the logo.  I'm still not able to log  in.  So I rebooted again with the LiveCD.  Any other ideas (fingers crossed :D)

---

### Post by Quackers on 2011-04-10
Is the file system encrypted?

---

### Post by spottsy66 on 2011-04-10
No.

---

### Post by spottsy66 on 2011-04-10
FWIW, I just noticed that the "Lost and Found" folder icon has the same "X" mark on the lower right hand corner, and it gives the same error message ("The folder contents could not be displayed....")

---

### Post by oldfred on 2011-04-10
Becuase of the abnormal shutdown you may have file corruption.

From liveCD so everything is unmounted,swap off if necessary, change sdb1 to your partition(s)
e2fsck is used to check the ext2/ext3/ext4 family of file systems.
sudo e2fsck -C0 -p -f -v /dev/sdb1
if errors:
sudo e2fsck -f -y -v /dev/sdb1

If you were working on an openoffice file it may be corrupted or part of the source of the  corruption.

When I use some software like Tux Commander I find two files.
backupscript.txt
backupscript.txt~

I believe the second is the older copy and some software may easily recover it without the full photorec or testdisk. You may be able to open it directly with openoffice.

---

### Post by Quackers on 2011-04-10
And is that the file that was being worked on when the problems arose?

EDIT
Please see oldfred's post above.

---

### Post by spottsy66 on 2011-04-11
[COLOR=black][FONT=Georgia][SIZE=3]Oldfred, my apologies, but I’m afraid I don’t understand the beginning of your post: [/SIZE][/FONT][/COLOR]
[FONT=Arial][SIZE=2][COLOR=black]From liveCD so everything is unmounted,swap off if necessary, change sdb1 to your partition(s)[/COLOR][/SIZE][/FONT]
[FONT=Arial][SIZE=2][COLOR=black]e2fsck is used to check the ext2/ext3/ext4 family of file systems.[/COLOR][/SIZE][/FONT]
 
[FONT=Georgia][SIZE=3][COLOR=black](My apologies for any breach of decorum--I know there's a way to copy from another post but either I'm overlooking it or the computer I'm on now (at work) has something disabled).[/COLOR][/SIZE][/FONT]
 
[FONT=Georgia][SIZE=3][COLOR=black]Am I to open the terminal in LiveCD and enter[/COLOR]:[/SIZE][/FONT]
 
[COLOR=black][FONT=Georgia][SIZE=3]sudo e2fsck -C0 -p -f -v /dev/sdb1[/SIZE][/FONT][/COLOR]
[FONT=Georgia][SIZE=3][COLOR=black]if errors:[/COLOR][/SIZE][/FONT]
[FONT=Georgia][SIZE=3][COLOR=black]sudo e2fsck -f -y -v /dev/sdb1[/COLOR][/SIZE][/FONT]
 
[COLOR=black][FONT=Georgia][SIZE=3]What am I hoping to accomplish with those commands? [/SIZE][/FONT][/COLOR]
 
[COLOR=black][FONT=Georgia][SIZE=3]To answer Quacker’s question, yes, the folder I can’t open is the folder I was working on when I shut down the computer last weekend. I didn’t think to try to open it with Open Office. I’ll try that this evening when I’m home. [/SIZE][/FONT][/COLOR]
 
[COLOR=black][FONT=Georgia][SIZE=3]If I can’t get to it that way, would I use a recovery tool of some kind? Also, what about logging into a profile without LiveCD?[/SIZE][/FONT][/COLOR]
 
[COLOR=black][FONT=Georgia][SIZE=3]Thanks again![/SIZE][/FONT][/COLOR]

---

### Post by oldfred on 2011-04-11
Sorry, those are terminal commands to run the file checks on any of the ext Linux file systems, just like chkdsk is a command for NTFS windows partitions. You have to make sure the partition is unmount to prevent futher damage.

In the command I posted it is for sdb1, but I do not know which partition is yours so you have to change the sdb1 to sda1 or sda2, etc. If you have more than one ext3 or ext4 partition, you have to run them both once for each.

---

### Post by spottsy66 on 2011-04-11
Thanks for the clarification Oldfred.  I'll run those commands this evening and will report back with the results.

---

### Post by spottsy66 on 2011-04-11
Good evening,

I tried to open the Open Office folder that I want to save and was told that I don't have access.  

This is the result I got from the first test on sda5 (which is ext2 and is my dedicated Ubuntu partition, i.e., the only thing on the partition is Ubuntu)


218879 inodes used (17.08%)
    1302 non-contiguous files (0.6%)
     294 non-contiguous directories (0.1%)
         # of inodes with ind/dind/tind blocks: 6496/77/0
  924898 blocks used (36.13%)
       0 bad blocks
       0 large files

  156973 regular files
   26108 directories
      59 character device files
      26 block device files
       0 fifos
     390 links
   35701 symbolic links (29644 fast symbolic links)
       3 sockets

I did not run the second test for this partition.

When I ran the both tests for sda6 (swap) I got this:

/dev/sda6 is mounted.  

WARNING!!!  The filesystem is mounted.   If you continue you ***WILL***
cause ***SEVERE*** filesystem damage.

Do you really want to continue (y/n)? no

check aborted.

I got the same result when I ran the first test on sda7 (which is an ext4 file system and is my Home partition where the files I want to save are stored).  I did not run the second test.

Other info that might be helpful:  sda1, 2 and 3 are for Windows and are ntfs.  sda4 is an extended partition.  sda5, 6 and 7 are logical partitions.

---

### Post by oldfred on 2011-04-11
Swap is not formated so e2fsck will not work  on swap partition. Is the file/folder you want in /home? Or in one of the NTFS partitions?

You have to umount swap (swapoff in gparted) in the extended partition to in effect unmount the entire extended partition and all partitions in it. LiveCDs usually mount swap to speed things up.

---

### Post by jtarin on 2011-04-11
Did you try accessing your file while in Live CD mode and as root? If not I would try that as a last ditch attempt for file recovery.

---

### Post by sirgogo on 2011-04-11
Boot into Ubuntu like you did before, except when you get the screen where you cannot login (GDM screen), hit CTRL + ALT + F1 - F5, until you get a console screen. Log in. You can use some of the commands Quackers provided to update (try with a wired connection to avoid utility confusion if updating with wifi connection doesn't work). Reboot. If it still doesn't work, use the method stated to access the console again and reconfigure the X server manually (or auto) via the terminal using

```
sudo dpkg-reconfigure xserver-xorg
```

This should work, unless your error is not related to updates or the x-server.

---

### Post by spottsy66 on 2011-04-11
Thanks everyone for your replies.  The files I want to recover are on /home.  I believe I have access to the ntfs partitions through Windows.

I have not tried to get to the files from the LiveCD using root.  While I think I know what that means, I don't know how to do it (being quite the noob :p)

Sirgogo, I can follow you until you get to "some of the commands Quackers provided".  Which commands in particular?

I'm about to sign off for tonight and may not have much time to devote to this tomorrow, but I'll happily follow whatever advice you provide when I get the chance.  

Thanks again!

---

### Post by jtarin on 2011-04-12
> **spottsy66 said:**
> 
I have not tried to get to the files from the LiveCD using root.  While I think I know what that means, I don't know how to do it (being quite the noob :p)
You were given instructions earlier on how to run the LiveCD and then change to root.....use those instructions to gain root access to your files.
It could be as simple as launching Nautilus file manager to access your files as root. Then it could also mean mounting the partition before you can get there with Nautilus.Try and see.

---

### Post by spottsy66 on 2011-04-12
[SIZE=3][FONT=Georgia]OK, I’m confused.  Oldfred says I need to “unmount the entire extended partition and all the partitions in it”.  Jtarin says I need to mount the partition.  Which is it?  Regardless, telling me to mount a partition isn’t helpful because I don’t know how to do it.  I’ll follow Sirgogo’s suggestions as far as I understand them.  I’ll try getting to the files through root.  I’ll try Nautilus.  After that I’m seriously tempted to go back to my typewriter (you’ll note the absence of a smiley).  [/FONT][/SIZE]
[FONT=Georgia][SIZE=3] [/SIZE][/FONT]
[FONT=Georgia][SIZE=3]The reason I started this thread is because I’m clearly out of my depth.  I need step by step instructions, spelled out clearly.  I’d love to understand what those instructions are doing so in the future maybe I can fix stuff on my own.  Between prepping for the initial install and this current problem, I’ve spent almost a month just trying to get Ubuntu to work.  I like Ubuntu.  I like the philosophy behind it and I like how it feels.  Help me out guys, please.  I want this to work.  But it’s becoming untenable.[/SIZE][/FONT]

---

### Post by oldfred on 2011-04-12
You have to mount the partition to see the files even with Nautilus. With Nautilus you just click on the partition in left panel & it automounts. (if it is ok).

To run the e2fsck file checks (if it is not ok) you have to unmount the partition and if it is in the extended partition all partitions in the extended including any swap must also be unmounted.

If unsure how to unmount a partition manually, one of the easiest ways is to use gparted. It will show little key symbols on mounted partitions. You can click on each and unmount or swapoff to unmount any mounted partitions.

---

### Post by jtarin on 2011-04-12
If you will read my first post you will see I was only giving instructions to rescue your files....not rescue your system as Oldfred was doing. Sorry for not being clearer. I will step back and let others advise.

---

### Post by spottsy66 on 2011-04-12
Jtarin, my apologies for being harsh this morning.  This whole thing is seriously frustrating and I was a little hot under the collar.  Thanks for writing back and clarifying.  I followed your advice--trying to access my files as root.  No luck.  I was told I don't have access.

Using gparted I swapoff-ed my swap partition (sda6) and unmounted my /home partition (sda7).  When I tried to unmount sda5 (Ubuntu), I got the error message "Could not unmount /dev/sda5  umount: /mnt/temp: device is busy.  (In some cases useful info about processes that use the device is found by lsof(8) or fuser(1))."  In gparted I see in the "Mount Point" column that sda5 is "/mnt/temp".  I am also not able to unmount sda4, which is the extended partition in which sda5, 6 and 7 are located.  

I'm going to try Sirgogo's advice now.  I'll report back how that works out.

Thanks again everybody!

---

### Post by spottsy66 on 2011-04-12
I tried Sirgogo's advice and ran the reconfigure X server script.  When I rebooted (without the LiveCD), I noticed that on the GDM screen in the white box it doesn't toggle back and forth between my computer's name and "Ubuntu 10.10" any more.

---

### Post by jtarin on 2011-04-12
> Jtarin, my apologies for being harsh this morning. This whole thing is seriously frustrating and I was a little hot under the collar. Thanks for writing back and clarifying. I followed your advice--trying to access my files as root. No luck. I was told I don't have access.No problem....you didn't come across as such. 
There is a method using the Live CD called "chroot" (change root) that I use for re-installing Grub2 which might work to be able to access your files for recovery. Here's the[ link]("https://help.ubuntu.com/community/Grub2#METHOD%203%20-%20CHROOT"). Skip steps 8,9,10 (relating to Grub2). In this environment you should be able to mount the partition your files are on for recovery. Any error messages post them in detail if possible.

---

### Post by oldfred on 2011-04-12
You have to be the third or fourth user with partition problems that continue to say file in use. Several have fixed it by download Slitaz and running the e2fsck commands from it:

Try this, is sure swapoff completed:
root@ubuntu# fuser -vam /dev/sda5
root@ubuntu# lsof /dev/sda5
Terminate with "kill [pid]" or "kill -9 [pid]
If not:
Problem running e2fsck apparently in use by the system,  Use Slitaz
[http://ubuntuforums.org/showthread.php?t=1713946](http://ubuntuforums.org/showthread.php?t=1713946)
SATA will use sda1 and IDE devices use hda1 in Slitaz

---

### Post by spottsy66 on 2011-04-18
[FONT=Georgia]Hello again, 

This is the first time I've had a chance to try the advice given.  I took another look at gparted and was able (for whatever reason) to unmount sda5 (/boot) and sda7(/home).  I ran the e2fsck test Oldfred suggested last week.  These are the results:[/FONT]

ubuntu@ubuntu:~$ sudo e2fsck -C0 -p -f -v /dev/sda5
                                                                               
  218955 inodes used (17.08%)
    1387 non-contiguous files (0.6%)
     353 non-contiguous directories (0.2%)
         # of inodes with ind/dind/tind blocks: 6553/79/0
  942629 blocks used (36.82%)
       0 bad blocks
       0 large files

  157047 regular files
   26110 directories
      59 character device files
      26 block device files
       0 fifos
     390 links
   35701 symbolic links (29644 fast symbolic links)
       3 sockets
--------
  219336 files
ubuntu@ubuntu:~$ 


[FONT=Georgia]Then I ran the second check on sda5:[/FONT]

ubuntu@ubuntu:~$ sudo e2fsck -f -y -v /dev/sda5
e2fsck 1.41.12 (17-May-2010)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

  218955 inodes used (17.08%)
    1387 non-contiguous files (0.6%)
     353 non-contiguous directories (0.2%)
         # of inodes with ind/dind/tind blocks: 6553/79/0
  942629 blocks used (36.82%)
       0 bad blocks
       0 large files

  157047 regular files
   26110 directories
      59 character device files
      26 block device files
       0 fifos
     390 links
   35701 symbolic links (29644 fast symbolic links)
       3 sockets
--------
  219336 files

[FONT=Georgia]Then I did the same thing for sda7 (/home):[/FONT]

ubuntu@ubuntu:~$ sudo e2fsck -C0 -p -f -v /dev/sda7
                                                                               
   49480 inodes used (0.29%)
    1022 non-contiguous files (2.1%)
      20 non-contiguous directories (0.0%)
         # of inodes with ind/dind/tind blocks: 0/0/0
         Extent depth histogram: 49420/42
 3985547 blocks used (5.78%)
       0 bad blocks
       1 large file

   48381 regular files
    1081 directories
       0 character device files
       0 block device files
       0 fifos
       0 links
       9 symbolic links (8 fast symbolic links)
       0 sockets
--------
   49471 files

[FONT=Georgia]Results from second test on sda7:[/FONT]

ubuntu@ubuntu:~$ sudo e2fsck -f -y -v /dev/sda7
e2fsck 1.41.12 (17-May-2010)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

   49480 inodes used (0.29%)
    1022 non-contiguous files (2.1%)
      20 non-contiguous directories (0.0%)
         # of inodes with ind/dind/tind blocks: 0/0/0
         Extent depth histogram: 49420/42
 3985547 blocks used (5.78%)
       0 bad blocks
       1 large file

   48381 regular files
    1081 directories
       0 character device files
       0 block device files
       0 fifos
       0 links
       9 symbolic links (8 fast symbolic links)
       0 sockets
--------
   49471 files


[FONT=Georgia]Then I tried Jtarin's suggestion to go in through chroot following the directions from the link you provided and got:[/FONT]

ubuntu@ubuntu:~$ sudo mount /dev/sda7 /mnt
ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt/boot
mount: mount point /mnt/boot does not exist
[FONT=Georgia]
Bypassing instruction #5, I got this:[/FONT]
ubuntu@ubuntu:~$ sudo mount /dev/sda7 /mnt
ubuntu@ubuntu:~$ sudo mount --bind /dev /mnt/dev
mount: mount point /mnt/dev does not exist


[FONT=Georgia]Thoughts?[/FONT]

---

### Post by oldfred on 2011-04-18
If you browse your sda7 partition does it have the folders you normally have in / (root)? You may or may not have /boot as the real /boot is in your other partition.

---

### Post by spottsy66 on 2011-04-19
I remember seeing at least some of those folders in my travels, but I don't remember if I saw them in / or in /home.  I'll look this evening. 
 
On another note, I realized last evening that I no longer see any of my document folders, including the one I was hoping to save.  I'll do a more thorough search this evening using the terminal.  If they're gone for good... that would stink but so it goes.  Turns out I had backed up more than I thought I did, and the stuff that is/might be gone can be chalked up to lessons learned.  If in fact my files aren't there, would it make sense to deinstall Ubuntu and start over from scratch?  Thinking out loud, it might make sense to do this anyway now that I understand how all this works a little better than when I did the original install.  
 
I'll let you know what I find this evening.  Thanks again!

---

### Post by oldfred on 2011-04-19
If your files in /home are ok then the reinstall is a bit easier. All your files & configurations for all your programs are in /home. Just be sure to not reformat, but include the existing /home in your reinstall.

But I generally recommend you backup a list of installed applications and any system wide configuration changes you have made that would be in /etc. I do not recommend reusing /etc for a new version as many system setting may change, but if you had to manually configure something is is nice to know what the setting was rather than start from scratch. 

If you do get it working include this list in your backups.
from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)

#Make list:
dpkg --get-selections > ~/my-packages
#Restore list of applications to new install
sudo dpkg --set-selections < my-packages && sudo apt-get dselect-upgrade

---

### Post by spottsy66 on 2011-04-19
Oldfred,

I have all the files you had in your screen shot in /  (the path in Nautilus is:  File System/media/home/[username]/documents).  There are some files on your screen shot that I do NOT have:

grub12
lib 32
lib 64
lost+found

There are also two files, one called initrd.img and vmlinuz that when I look in Properties say

Type:  Link (broken) (inode/symlink)

For whatever reason I can now see all my folder and files in /home again.  So I guess they're not lost after all.  But I still can't open the folder I really want to save.  Any ideas on how we can save that folder?

FWIW, in Nautilus in the bar on the left where you can select what folder and/or file system you want to open, there is a Home that opens up to show my files, and one that doesn't do anything.  

I won't have time this evening to follow your advice on backing up.  

Thanks again for all your help and patience.

P.s.  In gparted, sda7's mountpoint is /media/Home.  I mention this because I don't remember seeing this before.

---

### Post by oldfred on 2011-04-19
The grub12 must have been a typo, it has nothing in it . Do not think lost & found is essential, but the lib32 & lib64 are. Perhaps you might not have them if you only have the 32 bit install? Not sure as I have 64 bit.

The broken link says a kernel update did not work. If booting from a liveCD you may see the /home partition in /media because it is not mounted as /home. In your normal install you mount the other partition in fstab. So that is ok.

If you do this then do you have permissions to see your files. Becareful because you are at root and can move or delete system files.

gksu Nautilus

#chroot from liveCD into your install to repair it
sudo -i
mount /dev/sda7 /mnt
#if /boot
mount /dev/sda5 /mnt/boot

for i in dev proc sys usr; do mount --bind /$i /mnt/$i; done
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf #(may or may not be necessary to establish an internet connection)
sudo chroot  /mnt

apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a

reinstall kernel:
sudo apt-get update
sudo apt-get install linux-image
sudo update-grub

---

