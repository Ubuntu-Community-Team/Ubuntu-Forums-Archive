---
title: "Question about /home directory location."
date: 2009-02-05
forum: New to Ubuntu
---

### Post by Kellemora on 2009-02-05
Hi Gang

I've set up most of my machines with /home on it's own partition AFTER learning this was the best thing to do.

However, I have a few computers that were set up when I first started using Ubuntu that I let the install CD place home in the / (root) partition.

Now I've read things on how to MOVE /home to it's own partition, which I think uses a symlink in the / partition.

WHY could it NOT be done this way, or can it?????

Simply create a new partition for /home and copy the existing /home over to it.  I realize something is pointing to the original location.  But rather than creating symlink to the new location of home.  
Either, enter the new location in fstab OR wipe the root partition and reinstall Ubuntu.  Then copy /usr, /var, /tmp, etc. back to the new install.

Or maybe just copy /home to a new partition and start over from scratch with a new full install with a new /home partition, then copy your old data back to the new /home partition after all is said and done.

Is there something in /home that has to do with where /home is located originally?

In a nutshell, I just wanted to have all my computers set up the same way is all.  And I like /home on it's own partition!  Especially the way computers are dropping like flies around here lately.

TTUL
Gary

---

### Post by cmnorton on 2009-02-05
The reinstalling Ubuntu and wiping the root partition doesn't sound good. 

If home is on a separate drive, you have to mount the drive. I have my /home on a separate drive, but I don't mount the drive as /home. I mount the drive as the whole drive. 

I have a symlink where /home should be:

Here's my fstab entry (from a Fedora system)

/dev/sdb1               /mnt/sdb1               ext3    defaults,errors=remount-
ro 0 1

At root, here's the symlink.

lrwxrwxrwx 1 root root 14 Dec 20  2007 /home -> /mnt/sdb1/home

---

### Post by jocko on 2009-02-05
> **Kellemora said:**
> Hi Gang

I've set up most of my machines with /home on it's own partition AFTER learning this was the best thing to do.

However, I have a few computers that were set up when I first started using Ubuntu that I let the install CD place home in the / (root) partition.

Now I've read things on how to MOVE /home to it's own partition, which I think uses a symlink in the / partition.

WHY could it NOT be done this way, or can it?????

Simply create a new partition for /home and copy the existing /home over to it.  I realize something is pointing to the original location.  But rather than creating symlink to the new location of home.  
Either, enter the new location in fstab OR wipe the root partition and reinstall Ubuntu.  Then copy /usr, /var, /tmp, etc. back to the new install.

Or maybe just copy /home to a new partition and start over from scratch with a new full install with a new /home partition, then copy your old data back to the new /home partition after all is said and done.

Is there something in /home that has to do with where /home is located originally?

In a nutshell, I just wanted to have all my computers set up the same way is all.  And I like /home on it's own partition!  Especially the way computers are dropping like flies around here lately.

TTUL
Gary
I think you are trying to do things more complicated than they are.
This is how to move /home to it's own partition (probably safest to do from a live cd):
1. Make a new, empty partition (with ext3 or any other linux filesystem).
2. Copy everything (including hidden files and folders) from your current /home folder to the root of the new partition (but don't put the actual /home folder there, just it's contents).
3. Make a line in /etc/fstab for mounting the new partition, **set the mount point to /home**, don't symlink.
4. Rename the old /home folder (just keep as a backup until you know it's safe to remove).
5. Make a new, empty /home folder in your / to be used as mount point for the new partition.
6. Reboot.

And: If you would need to reinstall ubuntu in the future (or install another distro), just remember to tell the partitioner to use your /home partition as /home and don't format it. That will keep all your settings.

---

### Post by Kellemora on 2009-02-05
Hi CMN and Jocko

For CMN, I have 500 gigs to use for nothing except Ubuntu and it's programs, NO user DATA will be stored here, it's located on a Data File Server.  For this reason I don't need a separate HD for Home.

For Jocko

Maybe I don't understand something correctly, and that is why I'm confused here.

I have /home on a separate partition on most of my computers already.  When I OPEN the FILESYSTEM I see a Folder named HOME.
If I check the PROPERTIES of this folder it shows the SIZE of the available space 300+ gigs, which is expected.
If I open ANY OTHER FOLDER it shows Properties for available space as 30 gigs, which is expected.  Because I only allocated 40 gigs for root and 350 gigs for /home on a separate partition.

What I don't understand is simply this.  Does ROOT SEE the /home on it's separate partition OR is their a LINK from Roots Home Folder to the /home on a separate partition?????

For further clarification, when I used Gparted to format the drive and set up the partitions, I set the following:
sda1 / 50 gigs (root)(boot)
sda2 Extended
sda5 swap 4 gigs
sda6 /home 350 gigs
Unallocated 100 gigs

THEN I installed Ubuntu Hardy on sda1.

I am assuming that if I set up another computer the same way, I can simply COPY what is in my HOME folder to the new computers /home partition AFTER Ubuntu is installed and set up.
That ONLY personal settings are stored in the /home folder and system settings are in places like /usr, /var, /tmp, etc.

IF NOT, then what is the purpose of backing up HOME, if it contains no User Data, only User Set-Up info?????

Then my next question would be, does Ubuntu LOOK FOR HOME on Boot UP or is HOME established during the install?  Meaning, if I place HOME on a separate partition THEN delete HOME that resides on ROOT, then REBOOT so HOME will once again be found under FILESYSTEM after the Reboot.

I do have a test machine I CAN try this on to see just what happens in real life, but I'd rather not, since I'm using it almost daily now too.

Maybe I should though, just so I know I can mess things up royally and learn how to untangle myself better, hi hi........

TTUL
Gary

---

### Post by jocko on 2009-02-08
> **Kellemora said:**
> For Jocko

Maybe I don't understand something correctly, and that is why I'm confused here.

I have /home on a separate partition on most of my computers already. When I OPEN the FILESYSTEM I see a Folder named HOME.
If I check the PROPERTIES of this folder it shows the SIZE of the available space 300+ gigs, which is expected.
If I open ANY OTHER FOLDER it shows Properties for available space as 30 gigs, which is expected. Because I only allocated 40 gigs for root and 350 gigs for /home on a separate partition.

What I don't understand is simply this. Does ROOT SEE the /home on it's separate partition OR is their a LINK from Roots Home Folder to the /home on a separate partition?????

Not sure what you mean here. Either you have home as just a simple folder in your '/' partition, or you use the simple folder /home as mount point for another partition.
Either way, /home is a folder in your filesystem, and will always be where it is.
There are no links involved, with linux you can mount a partition in (almost) any folder in your filesystem, and when you do so, the data on that partition will appear as data in that folder. Linux is not like windows, where you see separate partitions as separate filesystems (C:\, D:\ and so on).
> **Kellemora said:**
> For further clarification, when I used Gparted to format the drive and set up the partitions, I set the following:
sda1 / 50 gigs (root)(boot)
sda2 Extended
sda5 swap 4 gigs
sda6 /home 350 gigs
Unallocated 100 gigs

THEN I installed Ubuntu Hardy on sda1.

I am assuming that if I set up another computer the same way, I can simply COPY what is in my HOME folder to the new computers /home partition AFTER Ubuntu is installed and set up.
That ONLY personal settings are stored in the /home folder and system settings are in places like /usr, /var, /tmp, etc.

IF NOT, then what is the purpose of backing up HOME, if it contains no User Data, only User Set-Up info?????
Yes, you can just copy what's in the /home of one install to the /home of another install. All your personal settings are stored in hidden files and folders in your /home (file names starting with a "."). System-wide settings are stored in /etc.
> **Kellemora said:**
> Then my next question would be, does Ubuntu LOOK FOR HOME on Boot UP or is HOME established during the install? Meaning, if I place HOME on a separate partition THEN delete HOME that resides on ROOT, then REBOOT so HOME will once again be found under FILESYSTEM after the Reboot.
Ubuntu doesn't "look" for /home. As I said, the folder /home is ALWAYS a folder on the root (/) of your filesystem.
If you want to use a separate partition as /home, you still need to have a /home folder on your / partition, but instead of using it as a container for data which is located on your / partition, you use it as a container for an entire partition.
If there is a line in /etc/fstab that specifies a particular partition to be mounted in /home, data on that partition will be accessed through the /home folder.
If there is no line in /etc/fstab for mounting anything in /home, the contents of the /home folder will be on your / partition...
So, to make an already installed ubuntu system to use a separate partition as /home, you need to:
1. Have a partition with a linux file system.
2. Copy your data from the /home folder (either from the same computer or, if you wish, from a different computer where you have a user with the same username) to this partition. So directly on the root of this partition you should see your users home folder (not the actual /home folder, just the folder with your username).
3. Make sure there is an empty /home folder on your / partition that can be used as mount point for the partition.
4. Set up a proper line in /etc/fstab to mount this partition as /home. Also make sure the same partition is not set to mount somewhere else.

If you want to install a fresh ubuntu system it's easier:
1. Have a partition with a linux file system.
2. Copy your data from the /home folder to this partition.
3. Install ubuntu. When you get to the partitioning part, use the "advanced" option and set up your partitions yourself, set one partition to be mounted as / and format this partition to a linux filesystem (such as ext3), and set your home partition to be mounted as /home, but do NOT format this partition. Make sure you use the same username for this install as you did on the install you copied the /home from.

---

### Post by hyper_ch on 2009-02-08
[http://www.psychocats.net](http://www.psychocats.net)

Go to the tutorials and you'll find an entry about moving home to an own partition. Very simple.

---

### Post by Kellemora on 2009-02-08
Thanks Jocko

That clarifies a LOT for me!

I've tried MOVING /home to a new partition following all the directions and messed up twice in the past.

As I set up each NEW INSTALL on a computer I made a separate /home partition and the install went just fine and Data is stored in the separate /home partition as expected.  And yes /home appears in the / directory as well.  But if you right click on it and check Properties it gives the size of the /Home partition, NOT the / partition which is exponentially smaller.

What happened a couple of times when I simply tried to MOVE /home to it's own partition was Data was still being stored on the same partition as / and not on the larger partition.

Rsync did this to me once also!  Created a file under /media/sdc/backup and stored all the data into the / partition instead of onto the sdc drive as it should have.  I've still never figured out why this happened either!  It works OK now though and I've changed nothing in the script at all.  My only thoughts are that the drive was not mounted so Rsync just wrote the data to the / of the sda drive instead, but inside the /media/sdc/backup folder of that name, not to the sdc drive itself.

I think I will take the For Sure way and wipe the disk, create the /, /home and swap partitions using Gparted, then install Ubuntu telling it where /home is located as I did on my latest installs which have all worked out perfectly.

When I first started, I was making partitions for all of the folders, like /usr, /tmp, /etc, etc. so I could back them up easier.  Then I learned no need to do that, just leave them inside of / and all will be OK.  But I DO want /home on it's own partition for sure!

TTUL
Gary

---

### Post by bayvista on 2009-04-26
I have my /home folder in a separate partition. It is defined in fstab as:

/dev/sdb2   /home     ext3    defaults   0   2

All my data is stored correctly in this folder. However, each folder in /home appears as an icon on my desktop. which I don't want. How can I stop this?

---

### Post by bayvista on 2009-05-25
Bump

---

### Post by mike555 on 2009-05-25
I believe you are misinformed , putting /home on a separate partition is not good for your hard drive, because it has to bounce the reading arm back and forth too much between your operating system and your home partition  ....... it would be better just to have a separate partition for backing up your home folder and let your regular home folder be with your operating system (same partition ......... my 2 cents worth.

---

### Post by Seq on 2009-05-25
> **mike555 said:**
> I believe you are misinformed , putting /home on a separate partition is not good for your hard drive, because it has to bounce the reading arm back and forth too much between your operating system and your home partition  ....... it would be better just to have a separate partition for backing up your home folder and let your regular home folder be with your operating system (same partition ......... my 2 cents worth.

This does not make any sense. Whether you're seeking within one partition or two, you are seeking regardless.

Also, I'd never recommend a backup partition on the same drive. Ever. Even if you say "Don't rely on it", somebody will rely on it.

Regarding the original issue, I think you've made it far more complex than it needs to be. Drop to console (kde/gnome may write files to your no-longer-used /home directory on root partition. mount new-home somewhere. mv /home/* /new-home (or wherever you've put it). update fstab. umount /new-home and mount /home. Done. Total time depends largely on how much data you have.

You don't even have to reboot, assuming you were not logged into X (in that case, log out and back in or you may have some odd issues with already open files).

---

### Post by tom56 on 2009-05-25
> **Seq said:**
> Also, I'd never recommend a backup partition on the same drive. Ever. Even if you say "Don't rely on it", somebody will rely on it.

This is precisely why having /home on a separate partition is completely pointless. Why not just backup the home folder to so an external drive then restore it from there if you need to. No need for it to be on a different partition.

---

### Post by Seq on 2009-05-25
> **tom56 said:**
> This is precisely why having /home on a separate partition is completely pointless. Why not just backup the home folder to so an external drive then restore it from there if you need to. No need for it to be on a different partition.

/home on a separate partition is not completely pointless. It makes fresh installs easier (if you do that sort of thing). It can make certain backup tools easier to use. You can set different mount options (eg. noatime on /, relatime on /home).

Personally I think everybody should be using separate partitions with lvm and backup utilities should automatically use snapshots while running to ensure consistency. But hey, that's just me :)

---

### Post by tom56 on 2009-05-25
> **Seq said:**
> /home on a separate partition is not completely pointless. It makes fresh installs easier (if you do that sort of thing). It can make certain backup tools easier to use. You can set different mount options (eg. noatime on /, relatime on /home).

It doesn't make fresh installs any easier. Simply, do the install then restore /home from your backup drive. I'm not sure what you mean about making backup tools easier to use, I guess you mean partition imagers, but personally I find rsync quicker and more useful (since you can restore individual files).

I have to admit though, I hadn't thought about different mount options. But that's kind of an unusual use case.

I have nothing against people using a separate /home if it fits their circumstances, what worries me is the way people recommend it to newbies regardless, especially when they imply it is some sort of replacement for doing regular backups. As evidenced by the first post in this thread:

> I've set up most of my machines with /home on it's own partition AFTER learning this was the best thing to do.
> I like /home on it's own partition! Especially the way computers are dropping like flies around here lately.

---

### Post by mike555 on 2009-05-25
If you install your operating system on partition 1 ,lets say the inside rings of your hard disc .... and your home on partition 5 , the outside of your hard disc , your hard drive reading arm has to bounce back and forth all the time when checking preferences etc from your home folder .... 


> **Seq said:**
> This does not make any sense. Whether you're seeking within one partition or two, you are seeking regardless.



---

### Post by bayvista on 2009-05-30
Seq - I like your suggestion. Could you spell it out in detail steps with Terminal commands please? I have created a mount point in the mnt folder called new-home. What's next?

---

### Post by Seq on 2009-05-30
> **bayvista said:**
> Seq - I like your suggestion. Could you spell it out in detail steps with Terminal commands please? I have created a mount point in the mnt folder called new-home. What's next?

[Here is a quick tutorial.]("http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/") I found it with [this Google Search]("http://www.google.ca/search?q=move+home+to+new+partition"). (Personally I would do `sudo cp -a /home/* /mnt/newhome/` instead of the cpio stuff, but that is just me).

The important thing to remember is that after you cp your files to your new partition, you have two sets of your data -- one on the root partition, and one on your new /home partition. You'll only see one set though since it would be mounted over the other. I'd suggest NOT removing the root partition version until you're sure everything copied over properly.

Also: Do a backup first. You should do them anyway, but especially before you start changing your disk.

---

### Post by blueridgedog on 2009-05-30
> **bayvista said:**
> 
All my data is stored correctly in this folder. However, each folder in /home appears as an icon on my desktop. which I don't want. How can I stop this?

You need to change your desktop to a folder in your home directory, typically called Desktop.  This thread will give you some ideas:

[http://ubuntuforums.org/showthread.php?t=341607](http://ubuntuforums.org/showthread.php?t=341607)

I _THINK_ you need to make a directory in your home directory called Desktop, then run gconf-editor, to to /apps/nautilus/preferences and remove the check in the desktop_is_home_dir box.

---

### Post by bayvista on 2009-06-03
I tried gconf-editor as suggested. the 'desktop_is_home_dir' box is not ticked.
I have:

created a new partition on another drive
copied my existing /home directory to the new partition.
updated fstab to point to the new partition
rebooted.

It all works except every folder in /home appears as an icon on my desktop. Very annoying.

I ended up moving all these folders to /desktop and that removed them from my Desktop. Very strange???
:( :( :(

---

### Post by Seq on 2009-06-03
> **bayvista said:**
> I tried gconf-editor as suggested. the 'desktop_is_home_dir' box is not ticked.
I have:

created a new partition on another drive
copied my existing /home directory to the new partition.
updated fstab to point to the new partition
rebooted.

It all works except every folder in /home appears as an icon on my desktop. Very annoying.

I ended up moving all these folders to /desktop and that removed them from my Desktop. Very strange???
:( :( :(
Check the contents of the file ".config/user-dirs.dirs". It stores the XDG paths. It may have made XDG_DESKTOP_DIR to be $HOME, which would cause the issue you are experiencing.

---

### Post by bayvista on 2009-06-04
Thanks, SEQ. You were spot on. By changing the location of my Desktop folder from $home/ to $home/Desktop, i removed all the Folders from my Desktop. They are now in /home where they belong. It seems that this is a trap for people who want their /home directory on a separate partition.
Anyhow, it is exactly how I want it now.  Thanks again

:p :p :p

---

### Post by calibre97 on 2009-06-14
Mike,
I'm beginning to think there's no real upside to simply having /home in a separate partition on the same drive, too. My problem is I'd like to move /home BACK to within / but I'm not sure how to go about it. I keep 3 different distros on my laptop and having to mount and rsync 6 partitions gets tiresome. I'd like to just have 3 full partitions for everything. I stupidly tried booting into Mint7 to deal with Mint6, but to move my user folder from Mint6's /home partition (sda10) into Mint6's root partition (sda11) I had to open /media/Mint6root as root (in Mint7). I removed the line about home in Mint6's /etc/fstab, but still, when I booted into Mint6, there were all kinds of errors. I attribute that to Mint7's root owning files because of the move.

What are the instructions for moving /home back into root? Do I need to be booted into Mint6 to do this to maintain permissions? And what would the sequence of events be? For example, umount /home? Then copy /Mint6home/userfolder to /? Or what? Any help would be greatly appreciated.

Once I'm able to shrink everything to just 3 partitions for the OSes, I can easily do tar backups of things like /home and /etc to a data partition and rsync the whole OS partition to a USB drive (booted into RescueCD of course).

---

### Post by camper365 on 2009-06-14
When you mount a flash drive with:

```
sudo mount /dev/sdb1 /media/disk
```

The filesystem accesses the flash drive as /media/disk.
The same if you type:
```
sudo mount /dev/sda2 /home
```
There is no symlink involved, it is simply mounted there.

---

### Post by blueridgedog on 2009-06-14
> **calibre97 said:**
> 
What are the instructions for moving /home back into root? Do I need to be booted into Mint6 to do this to maintain permissions? And what would the sequence of events be? For example, umount /home? Then copy /Mint6home/userfolder to /? Or what? Any help would be greatly appreciated.


Boot off of a liveCD (as you will have /home files in use otherwise), mount your current home partition as something else such as /mnt/disk and your current / partition as something else as well, such as /mnt/disk2 then simply copy everything:

```
sudo rsync /mnt/disk /mnt/disk2/home -av
```

At this point you will have a disk that is an archive of /home, and you can backup home in the future by reversing the rsync (and adding --delete so that things you delete in /home are deleted from your drive).

As ever, backup before you mess up!

---

### Post by calibre97 on 2009-06-14
Oh sonofabitch. 
First, thank you.
Second, I'm an idiot. rsync. Of course.
And yeah, probably smarter to do it from RescueCD than in another distro and mounting things.

Off to do it now. Thanks again.

---

### Post by raymondh on 2009-06-14
> **calibre97 said:**
> Mike,
I'm beginning to think there's no real upside to simply having /home in a separate partition on the same drive, too. My problem is I'd like to move /home BACK to within / but I'm not sure how to go about it. I keep 3 different distros on my laptop and having to mount and rsync 6 partitions gets tiresome. I'd like to just have 3 full partitions for everything. I stupidly tried booting into Mint7 to deal with Mint6, but to move my user folder from Mint6's /home partition (sda10) into Mint6's root partition (sda11) I had to open /media/Mint6root as root (in Mint7). I removed the line about home in Mint6's /etc/fstab, but still, when I booted into Mint6, there were all kinds of errors. I attribute that to Mint7's root owning files because of the move.

First off, great job on the rsync :)

With regard to the above quote ...(and I do apologize if this may be off-topic).... I once read a HOW-TO by Bodhi.Zazen about basic partitioning.  On that how-to, what caught my interest was his preference to use /data instead of /home.  Here's the excerpt from his HOW-TO:

[I]Options.

/home: This is helpful if you need to re-install Ubuntu. /home stores user data and user configuration files.

Limitations:

   1. /home does not save all of the installed applications you have installed or removed beyond the base install.
   2. If you boot multiple distros those user config files can conflict.


/data: This is helpful and I use this in favor of /home.

Why?

   1. First, I boot multiple distros and user configuration files in /home can conflict as above.
   2. Those user config files are not "mission critical" to back up. They will be regenerated if deleted, although you will loose your application preferences.
   3. Backup /home to /data and you can restore /home.
   4. Data partition can be shared with other OS (Windows or other distro's) easier then /home.


You can, of course, mount your data partition as any name (mount point) you like.[/I]


I, myself, use /home.  But, with multiple distros (with its' own configuration files, etc) as well as  multiple users in my household, am now considering /data for all our computers with the hopes of minimizing those "challenges". 

Good luck.

---

### Post by calibre97 on 2009-06-14
Back to that rsync example, I think there should be trailing slashes, as in:

rsync -av /mnt/disk/ /mnt/disk2/home/

Otherwise the system will think you want disk into a file called "home".

As for data, yes, I already do that. I have 2 data partitions at the beginning of the extended partition. I've recently configured Thunderbird to use a config on one of them so I don't have to worry about checking mail. I also store VMs for Virtualbox there, too. It's a smart idea. I'm currently working on creating a global /boot partition - mainly because of the multiple distros I have going on.

---

### Post by blueridgedog on 2009-06-14
> **calibre97 said:**
> Back to that rsync example, I think there should be trailing slashes, as in:

rsync -av /mnt/disk/ /mnt/disk2/home/

Correct...my bad.  Note that you are in deep water here so to speak and you need to keep straight in your mind where you have mounted your / and where you have mounted you old /home...it is pretty easy, but unforgiving.  The worst case scenario is you end up with a copy of something someplace that you did not intend, as the rsync command in the above incarnation is non-destructive.

---

### Post by blueridgedog on 2009-06-14
As a twist on this thread...I generally keep /home inside of /, but keep a partition for my files (1/2 T at this point).  I mount that partition as /home/myuser/Documents, with symlinks back to the usual ~/pictures, ~/music and the like so /home stays pretty small and is easy to dump to a backup if needed.

---

### Post by calibre97 on 2009-06-14
And a final note, whilst freeing up space and renumbering partitions - um, thou shalt remember to update GRUB with thine new sda numbers! Um, yeah, I'm going to have to ask you to go ahead and come in on Sunday and make sure those later partition distros actually, um, boot...yeah. Ok? Thanks peter!

---

### Post by theozzlives on 2009-06-14
Why a Hard Drive that's such a mess, and why 3 distros? Do you get work done or play with partitions all day? Sorry, I just like things simple and your /home partition should stay or next time you install a new version, you'll lose everything.

---

### Post by blueridgedog on 2009-06-14
On my last system rebuild, I juggled the drives around and really got things goofed up, but was able to boot on a liveCD and install grub to the disk of my choosing with the standard grub commands (which I can post if you need them) and you can always mount the partition with / on it and edit the menu while on the livecd.

I have been playing with Fedora 11 on a USB stick this weekend (while not building a chair to use with a telescope).

---

### Post by calibre97 on 2009-06-14
Ozzlives,
Um, wow, thanks for uh, sharing.

Blueridge,
Thanks but I'm cool. I've got System Rescue CD and supergrubdisc so I can get myself out of any trouble that might come my way. So far so good.

I'm going to get that universal boot partition going and then throw Fedora 11 on, where Mint 6 was.

Back to ozzlives: That'd be for shitz-n-giggles. I get plenty of 'work' done on my Mac Mini (Win 7 in Virtualbox) and Dell from work (running XP). Dontcha worry none bout my partitions. I'm leaving my Mint 7 split because that's my main boot-up. XP is for the occasional game, and Fedora and Kubuntu are for funnin' around.

---

