---
title: "Automatic mounting of drives?"
date: 2010-07-18
forum: New to Ubuntu
---

### Post by djk21108 on 2010-07-18
Hi forum members!

I'm hoping you all have some insight into this issue. I have a 134 GB file system as one of the options under places. This is where all the data from my Windows OS is held. My pictures movies and documents are all there. This is great, and I can access all this pretty well.

I put a shortcut on my desktop as a link to the folders where all these great pieces of data are held.

Only problem is, until that file system is "mounted" in Ubuntu, I can't access that folder.

Is there any way to auto-mount that drive or keep it forever mounted or whatever?

Thanks in advance!

---

### Post by Zorgoth on 2010-07-18
There is a text file called /etc/fstab you could edit as administrator ("sudo").  Be careful when doing this and back up your old fstab; it isn't too dangerous but you could mess things up if you don't know what you're doing.  If you do mess things up, use the live CD to access your hard drive and restore the backup.

Basically you would do something like this:

Add the line

```

windows_device /media/OS ntfs-3g defaults,mode=777 0 0

```

windows_device is not literal; I mean something like /dev/sda1 or /dev/hda2, or whatever.

To find out the name of your windows partition, type 
"sudo fdisk -l" and find the appropriate partition in the output.

if your drive is ntfs (Vista or later, sometimes on XP), something similar
with FAT32.  I am not sure if it is ntfs-3g or just ntfs.

---

### Post by djk21108 on 2010-07-18
Alright so it appears /dev/sda2 is my windows_device in this case, I'm a pretty big beginner, so I'm just curious how to open up fstab and edit it. I realize it's something with gedit, but I'm just so new hehe.

---

### Post by djyoung4 on 2010-07-18
> **djk21108 said:**
> Alright so it appears /dev/sda2 is my windows_device in this case, I'm a pretty big beginner, so I'm just curious how to open up fstab and edit it. I realize it's something with gedit, but I'm just so new hehe.

try pysdm
```
sudo apt-get install pysdm
```
its a gui for editing your fstab file

---

### Post by djk21108 on 2010-07-18
Sorry to be a noob, I installed pysdm, but how do I run it?

/Windows user.

---

### Post by MooPi on 2010-07-18
You can edit fsatb in any editor of your choosing, but gedit will do nicely. Open a terminal and type ```
gksu /etc/fstab
```You will be asked to enter your password, then fstab will open. This is what mine looks like. Notice my WindowsXP drive.

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=b3ce4e2a-f862-4f38-9402-00301e1f52a1 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=9b447b24-4a29-425c-87c5-4068e5ea50e4 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
# BigBin /dev/sda3
UUID=819005e9-fd37-4f2a-91ef-162b7fe9e400 /media/BigBin   ext3     user,auto   0     0
# WindowsXP /dev/sda2
UUID=7EBC9389BC933A9B /media/WindowsXP ntfs defaults 0 0
```
Before you edit fstab you'll need to find out your drives UUID. So in terminal again type ```
sudo blkid
``` This will give your drives UUID designation.

---

### Post by djk21108 on 2010-07-18
Awesome, Fstab is open, the UUID of sda2 is 

/dev/sda2: UUID="7C9A394D9A3904E4" TYPE="ntfs" 


Thanks so much already, so where do I go from here?

---

### Post by MooPi on 2010-07-18
Plug in your UUID minus the quotation. This could be a sample, just make changes as you desire. I like to use "defaults' for the options. It's always a good idea to make directory in media ```
sudo mkdir /media/your-drive-name-here
```
```
#/dev/sda2 Windows 
UUID=7C9A394D9A3904E4 /media/drive ntfs defaults 0 0
```
Make certain of your entry as if its way off it could hang your boot.Be ready to use your Live CD if things go bad.

---

### Post by djyoung4 on 2010-07-18
> **djk21108 said:**
> Awesome, Fstab is open, the UUID of sda2 is 

/dev/sda2: UUID="7C9A394D9A3904E4" TYPE="ntfs" 


Thanks so much already, so where do I go from here?

kinda copy MooPi's.  add on the new line
```
UUID=7C9A394D9A3904E4 /path/to/windows ntfs defaults 0 0
```

---

### Post by djk21108 on 2010-07-18
Thank you guys so much! I apprecate the support you users give!

---

### Post by djk21108 on 2010-07-18
Well I do believe it was mounted on the restart of Ubuntu.

Now I can access the hell out of the file system, but for some odd reason Banshee has stopped being able to play music from my Windows drive.

---

### Post by Zorgoth on 2010-07-18
What are the permissions?

Maybe it was storing a different path to the windows drive?  Have you tried relocating the music?

---

### Post by djk21108 on 2010-07-18
Haha, I'm such a dummy. Reimported, and now everything is great.

Thanks again everyone!

---

### Post by Zorgoth on 2010-07-18
Mark as solved please :)

---

### Post by djk21108 on 2010-07-18
> **Zorgoth said:**
> Mark as solved please :)

Eeeek Sorry!!! But...how

/ducks for cover

---

### Post by Zorgoth on 2010-07-18
Click the arrow next to "Thread Tools" and select the option "Mark as Solved."

---

