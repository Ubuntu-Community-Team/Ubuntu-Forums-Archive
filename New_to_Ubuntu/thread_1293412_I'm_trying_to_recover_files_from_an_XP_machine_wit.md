---
title: "I'm trying to recover files from an XP machine with Xubuntu."
date: 2009-10-17
forum: New to Ubuntu
---

### Post by amyers on 2009-10-17
Hi all! Well I never thought I would be attempting to use Ubuntu, but here I am! Here is my situation: I have a windows xp machine that won't boot up and found out that I could use xubuntu(ISO on a burned disc) as a temp OS and attempt to get my files off my computer, onto an external hd. I have xubuntu going, but I cannot find ANY of my files or programs. I saw that I could maybe use Terminal to find them? When I go to Partition editor, I can see a partition (/dev/sda1) and it says (ntfs) under "File System". It shows its size and how much is used. I'm pretty sure this is where my files are, but I don't know how to get to them and transfer to my external HD! Can anyone point me in the right direction? I have NEVER used this before. I messed around with different commands(when searching google) in terminal, but nothing worked for me.

---

### Post by SkyNet2029 on 2009-10-17
Hi! You need to mount the ntfs partition to be able to access the files on it.
IF your Xubuntu has ntfs-3g drivers (it should) you can do this by
 
```
$sudo mount /dev/sda1 /home/user_name/folder_name
```
 
where folder_name is a folder you created in your home directory.
 
since you want to copy them to your usb drive, you would need to mount that
drive as well, under a different folder. Once the two drives are mounted you can copy the files from your old_drive to the new_drive. don't forget to unmount them when done.
 
Hope this helps.

---

### Post by amyers on 2009-10-17
I hate to be stupid about this, but I have no clue what my "user_name" for this would be? I haven't made a user name!
 I tried "sudo mount /dev/sda1 /home/ntfs/files" but that did not work.
("ntfs" is the partition where all my stuff is and "files" is the folder I created on the desktop)

---

### Post by mbeichorn on 2009-10-17
Go to places-->Documents

Look at the address bar, the name before documents should be your user name.

An easier method may be to look at the places menu for somthing called local disk or media, your filesystem could be listed there.

Cheers!

---

### Post by falconindy on 2009-10-17
You'll need to specify the file system type in the mount command (sudo mount -t ntfs ....). Even easier, the drive should show up under Places in the Main Menu just under the 'Computer' item. Enter your password, and it's mounted in /media/.

---

### Post by amyers on 2009-10-17
Thank you for the replys! My external drive should be taken care of. It is automatically Mounted. So I just need to be able to access my files in my ntfs partition. Well when I go into Places->Documents I only see "Documents - File Manager" at the top. I don't see anything that could be a user name.  Ugh! I wish I knew what to do! Again, I hate to be so stupid, but can someone explain to me how putting in "sudo mount /dev/sda1 /home/user_name/folder" lets me access my ntfs partition? Falconindy, it's sounds like you are getting at what I'm asking?

---

### Post by yeats on 2009-10-17
You should also see your computer's internal hard drive in the Places menu... It may have some name like "Volume" or "Disk", but it should definitely be visible.  Don't sweat the manual mounting stuff if you can help it :-).

---

### Post by falconindy on 2009-10-17
Hmm, I suppose I mislead you because I skipped the part about you being on Xubuntu. Gnome gives you something similar to this:
[img]http://i35.tinypic.com/2elxn5k.jpg[/img]

All those koala prefixed drives are from my 9.10 beta install (and unmounted). I could click on any of them and they would be mounted for me under /media.

XFCE isn't my forte.... so, let's do this. Open up a terminal and give us the output of:
```
sudo fdisk -l
```
You'll want to look for an entry that is of type HPFS/NTFS (or something similar). Follow that entry back to the left where it'll say /dev/xxxx. Then, you can use the mount command to get access to the drive. You'll need to make a directory for it first. You can do the following (all from a terminal):
```
mkdir $HOME/windowdrive
sudo mount -t ntfs /dev/xxxx $HOME/windowsdrive
```
Where the xxxx is the same alphanumeric you pulled out of the fdisk results. If you're unsure, post the output and we can help.

---

### Post by amyers on 2009-10-17
Thanks so much for being patient with me guys! Ok, the easiest thing for me to do is post the results of "sudo fdisk -1" which is:
```
fdisk: invalid option -- '1'

Usage: fdisk [-b SSZ] [- u] DISK       Change partition table
           fdisk -l  [-b SSZ] [-u] DISK    List partition table(s)
           fdisk -s PARTITION                Give partition size(s) in blocks
           fdisk -v                                 Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u:  give Start and End in sector (instead of cylinder) units
-b  2048:  (for certain MO disks) use 2048-byte sectors

```

Ok, this doesn't sound like what you need though, is it? This sounds like some kind of explanatory note or something.

Chrissharp: Yes, I can go into APPLICATIONS->SYSTEM->PARTITION EDITOR and it will load up a few seconds and then I can see my fat32 recovery partition and my ntfs partition which is the one I need access to, but am completely clueless on doing so, haha! I mean Im still lost on how doing these "mount" commands in Terminal lets me access that partition. Again, I REALLY appreciate you guys taking the time to help!

---

### Post by kilowattradio on 2009-10-17
> **amyers said:**
> Hi all! Well I never thought I would be attempting to use Ubuntu, but here I am! Here is my situation: I have a windows xp machine that won't boot up and found out that I could use xubuntu(ISO on a burned disc) as a temp OS and attempt to get my files off my computer, onto an external hd. I have xubuntu going, but I cannot find ANY of my files or programs. I saw that I could maybe use Terminal to find them? When I go to Partition editor, I can see a partition (/dev/sda1) and it says (ntfs) under "File System". It shows its size and how much is used. I'm pretty sure this is where my files are, but I don't know how to get to them and transfer to my external HD! Can anyone point me in the right direction? I have NEVER used this before. I messed around with different commands(when searching google) in terminal, but nothing worked for me.

Your best bet is to buy a USB HD enclosure for HD, it will either be a SATA, eSATA or IDE (ATA) drive you have in your computer, then remove the HD from your computer placing it the USB enclosure and running Windows XP. That way you can attempt to copy the contents of the HD and attempt to fix it with the command chkdsk and the windows de-fragmentation program.

---

### Post by golanbatrac on 2009-10-17
> **amyers said:**
> Thanks so much for being patient with me guys! Ok, the easiest thing for me to do is post the results of &quot;sudo fdisk -1&quot; which is:
```
fdisk: invalid option -- '1'

Usage: fdisk [-b SSZ] [- u] DISK       Change partition table
           fdisk -l  [-b SSZ] [-u] DISK    List partition table(s)
           fdisk -s PARTITION                Give partition size(s) in blocks
           fdisk -v                                 Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u:  give Start and End in sector (instead of cylinder) units
-b  2048:  (for certain MO disks) use 2048-byte sectors

```Ok, this doesn't sound like what you need though, is it? This sounds like some kind of explanatory note or something.

Chrissharp: Yes, I can go into APPLICATIONS->SYSTEM->PARTITION EDITOR and it will load up a few seconds and then I can see my fat32 recovery partition and my ntfs partition which is the one I need access to, but am completely clueless on doing so, haha! I mean Im still lost on how doing these &quot;mount&quot; commands in Terminal lets me access that partition. Again, I REALLY appreciate you guys taking the time to help!

-l (as in Llama), not -1.

---

### Post by yeats on 2009-10-17
> Chrissharp: Yes, I can go into APPLICATIONS->SYSTEM->PARTITION EDITOR and it will load up a few seconds and then I can see my fat32 recovery partition and my ntfs partition which is the one I need access to, but am completely clueless on doing so, haha! I mean Im still lost on how doing these &quot;mount&quot; commands in Terminal lets me access that partition. Again, I REALLY appreciate you guys taking the time to help!

You need the ntfs partition, but the partition editor is not what you want to use - that is for resizing and reformatting partitions (which would destroy data, not save it :-) ).  Open a file manager (any menu item in Places will do this), and try to navigate to the ntfs partition from there.  That *should* work.

---

### Post by amyers on 2009-10-17
kilowatt: thank you, but I don't think I will go that route. I plan on just doing a fresh, new xp install once I get my programs off. I think I can do it, I just need some really clear direction for dummies, haha

---

### Post by amyers on 2009-10-17
That should be an L as in llama, yes

---

### Post by amyers on 2009-10-17
Ok Chris, If I manage to find ntfs by going through "PLACES" what exactly do I do then? because I can't just start clicking and dragging files into my external HD right? What exactly is the point of me making a new folder on the desktop? Aren't I trying to get my ntfs files and programs into that folder and then I transfer to external HD? Which seems like an extra un-needed step, but what do i know.

---

### Post by yeats on 2009-10-17
> Ok Chris, If I manage to find ntfs by going through "PLACES" what exactly do I do then? because I can't just start clicking and dragging files into my external HD right?

Actually, if you have them open, one per window, you can do *exactly* that.  At least that's what I'm thinking will be the most straightforward way to do what you're trying to do...  Can you try that?

---

### Post by amyers on 2009-10-18
eh, I don't think it's gonna work man. That would be too easy! I have gone through everything pretty much and it looks like all the folders and files are all having to do with the xubuntu, nothing that is on my actual computer's hard drive. I went through PLACES->FILE SYSTEM hoping that I could access my real files. It's all the files that are part of the ISO xubuntu disc that I'm using. This is crazy! There has to be another way for me to get into that ntfs partition!

---

### Post by amyers on 2009-10-18
I found these instructions: [http://www.cyberciti.biz/faq/mounting-windows-partition-onto-ubuntu-linux/](http://www.cyberciti.biz/faq/mounting-windows-partition-onto-ubuntu-linux/)   but when I try # sudo fdisk -1 I get "command not found"!
These instructions make it sound so easy, yet nothing is working for me. So frustrating!  IF for some reason I do get far enough where I need to make a directory  (First you need to create directory where you can attach windows partition using mount command (for example /media/c for C:):# sudo mkdir -p /media/c) is it possible for me to make a directory right on the desktop? Or where should I make it at?

---

### Post by amyers on 2009-10-18
ok guys, sorry to keep posting with change, but here is where I am now:
I was able to make a new directory within /media ( I have no clue why there, but that is the directions that I'm seeing when looking up  ways to mount the partition. So I've got the directory and now I'm trying to mount ntfs to that directory within Terminal and the commands won't work! Here is what I'm getting:```
mount: can't find /dev/sda1/media/windows in /etc/fstab or /etc/mtab
``` I've physically gone to /media/ and verified that "WINDOWS" directory is there, but I'm getting that error. I think I'm getting closer!

---

### Post by Baelus on 2009-10-18
Hi there,

Copy this and paste it into your terminal window:

```
sudo mount -t ntfs-3g /dev/sda1 /media/windows
```

That should get you a folder called "windows" on your desktop.

Let us know how it goes.:)

---

### Post by amyers on 2009-10-18
I want to say thank you to everyone who took the time to respond! I was able to create the directory and mount the ntfs partition. Currently transferring files to external HD as I type this! Thanks again! I will be looking into this ubuntu thing even more now!

---

### Post by yeats on 2009-10-18
> I want to say thank you to everyone who took the time to respond! I was able to create the directory and mount the ntfs partition. Currently transferring files to external HD as I type this! Thanks again! I will be looking into this ubuntu thing even more now!

Glad you got it worked out.  Ubuntu is a great alternative, despite the difficulties getting this task done, and I hope you give it a shot some time :-).

---

### Post by stinger30au on 2009-10-18
ultimate boot cd for windows will do what you want

[http://www.ubcd4win.com/](http://www.ubcd4win.com/)

theres plenty round like this

---

