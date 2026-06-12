---
title: "Make changes to read-only file in text editor (syslinux.cfg)"
date: 2011-02-28
forum: New to Ubuntu
---

### Post by MuleSkinner on 2011-02-28
I'm trying to follow all the steps in [this]("http://ubuntuforums.org/showthread.php?t=1682241") thread and I'm stuck at the following step:

> append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash -- persistent
Rebooted, changes were persistent.Which C.S.Cameron translated for me as the following:

> Press Alt F2 and type "gksu nautilus"
Or you can open terminal and type  "gksu nautilus"
(this opens nautilus as super user).
Now click file system, then double click cdrom, then you right click on syslinux.cfg and open with text editor.I opened syslinux.cfg with text editor and it was a read-only file and I couldn't make any changes to it. Any help would be greatly appreciated as this is the last step of what I'm trying to accomplish.

---

### Post by Kirboosy on 2011-02-28
How much command line experience do you have?


Open a terminal and type in

```
gksudo gedit /path/to/syslinux.cfg
```
If you need further help just tell me where your file is located..

---

### Post by sh4d0w808 on 2011-02-28
Right click on the file, properties, permissions and set up access options to read and write. After then try to open the file again with your editor (I'm not exactly sure that you can do the permission change, but tryx it.)

---

### Post by TechWiz2100 on 2011-02-28
> **sh4d0w808 said:**
> Right click on the file, properties, permissions and set up access options to read and write. After then try to open the file again with your editor (I'm not exactly sure that you can do the permission change, but tryx it.)

DO NOT DO THIS!!

While this is definitely away to circumvent the system its dangerous and not something that should be suggested, especially not to those who have little experience with linux in general.

The best way to edit the file is gksudo or sudo <cli editor> because permissions don't get screwed up causing potential boot issues or what have you later on.

---

### Post by Kirboosy on 2011-02-28
> **TechWiz2100 said:**
> DO NOT DO THIS!!

While this is definitely a way to circumvent the system its dangerous and not something that should be suggested, especially not to those who have little experience with linux in general.

+1

Lets just keep walking the OP through the gksudo way

---

### Post by MuleSkinner on 2011-02-28
> **Caboose885 said:**
> How much command line experience do you have?


Open a terminal and type in

```
gksudo gedit /path/to/syslinux.cfg
```If you need further help just tell me where your file is located..
I did that and it just opens an empty pop-up box. No clue what to do next. BTW, I'm trying to make changes that are on my flash drive so I can make a persistent flash drive.

---

### Post by Kirboosy on 2011-02-28
Ok. What is the path to the file that you used? (my /path/to/syslinux.cfg was an example and not what you are supposed to use.)

Since its a thumb drive it should be something like /media/"thumbdrive"/syslinux.cfg

---

### Post by MuleSkinner on 2011-02-28
I got there by typing in what I pasted earlier:
> Press Alt F2 and type "gksu nautilus"
Or you can open terminal and type  "gksu nautilus"
(this opens nautilus as super user).
Now click file system, then double click cdrom, then you right click on syslinux.cfg and open with text editor.
When I get to cdrom, there is a little grey lock on the icon (not sure if that's meaningful information, but I thought I should mention it).

---

### Post by Kirboosy on 2011-02-28
Well the CDROM drive is readonly since the CD is most likely a CD-R. Unless you copy the files somewhere else you won't be able to modify the files.


Since you are trying to make a persistent thumbdrive why don't you use "Startup Disk Creator"? (System-->Admin-->Startup Disk Creator)

---

### Post by MuleSkinner on 2011-02-28
> **Caboose885 said:**
> 
Since you are trying to make a persistent thumbdrive why don't you use "Startup Disk Creator"? (System-->Admin-->Startup Disk Creator)
I just tried Startup Disk Creator and I'm having the same issue with it that I did attempting various installers- I get hung up on boot up. When I get to where Ubuntu is displayed in the center of the monitor with the five sequentially flashing white to red dots underneath it, that page stays there and the desktop never appears. At least with the method I've been trying to accomplish in this thread, I can successfully boot up, get on the internet, etc.


> Well the CDROM drive is readonly since the CD  is most likely a CD-R. Unless you copy the files somewhere else you  won't be able to modify the files.
There is no more CD-R in the method I've been trying, I'm just booting up with the flash drive.

---

### Post by TechWiz2100 on 2011-02-28
Have you tried UNetbootin? Thats the only one that has given me any positive results so far

---

### Post by MuleSkinner on 2011-02-28
The method I'm trying uses UNetbootin (check out the link in the OP).

---

### Post by Kirboosy on 2011-02-28
So you are using a custom made Ubuntu image? There might be a problem with that image...


Ok....open up Computer....then click "File System" -->/media . What is the name of the thumbdrive?

Then click inside the thumbdrive and tell me what files are there...


run in a terminal ```
sudo fdisk -l
``` and post the output here...

---

### Post by MuleSkinner on 2011-02-28
> **Caboose885 said:**
> So you are using a custom made Ubuntu image? There might be a problem with that image...
I'm using an Ubuntu CD that I burned from ubuntu.com; it's not custom. I'm using it right now and it works fine (I don't have Ubuntu on a hard drive). I've also used others and I get the same results. Please click on the link in the OP so you can get an idea of what I've done and what I'm trying to accomplish. I'll follow your directions below and post the results.


> Ok....open up Computer....then click "File System" -->/media . What is the name of the thumbdrive?EE8A-0A58

> Then click inside the thumbdrive and tell me what files are there...boot  casper  dists  install  pics  poll  preseed  syslinux  autorun.inf  casper-rw  ldlinux.sys  md5sum.txt  README.diskdefines  usbcreator.exe  wubi.exe


> run in a terminal ```
sudo fdisk -l
``` and post the output here...Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd8aed8ae

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60800   488375968+   7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00023bea

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60800   488375968+   7  HPFS/NTFS

Disk /dev/sdc: 7998 MB, 7998537728 bytes
247 heads, 62 sectors/track, 1020 cylinders
Units = cylinders of 15314 * 512 = 7840768 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009722d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1         134     1024000   1b  Hidden W95 FAT32
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 32, 33) logical=(0, 33, 3)
Partition 1 has different physical/logical endings:
     phys=(127, 155, 28) logical=(133, 214, 18)
Partition 1 does not end on cylinder boundary.
/dev/sdc2   *         134         402     2048000    b  W95 FAT32
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(127, 155, 29) logical=(133, 214, 19)
Partition 2 has different physical/logical endings:
     phys=(382, 146, 20) logical=(401, 82, 50)
Partition 2 does not end on cylinder boundary.

---

### Post by Kirboosy on 2011-02-28
I read the OP link. Thats why I was asking if you made a custom CD. The link you gave in that post was discussing creating a custom CD.


ok The command you need to run is...

```
sudo gedit /media/EE8A-0A58/syslinux.cfg
```A file with a bunch of words should pop up if it worked correctly.

Find the line that looks similar to this one...

```
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash
```

and add to it **--persistent** It should now look something like this...
```
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash -- persistent
```

---

### Post by MuleSkinner on 2011-02-28
I shouldn't do the above with what I have on my flash drive now, right? Because my flash drive isn't bootable with with I did using Startup Disk Creator.

Should I start over with what worked or me using UNetbootin and then make the change adding **--persistent?**

---

### Post by TechWiz2100 on 2011-02-28
Yea it's probably best to have a bootable drive before you try and make it persistent

---

### Post by MuleSkinner on 2011-02-28
> **Caboose885 said:**
> I read the OP link. Thats why I was asking if you made a custom CD. The link you gave in that post was discussing creating a custom CD.


ok The command you need to run is...

```
sudo gedit /media/EE8A-0A58/syslinux.cfg
```A file with a bunch of words should pop up if it worked correctly.
An empty box titled 'syslinux.cfg (/media/EE8A-0A58 - gedit' popped up. No bunch of words.

---

### Post by Kirboosy on 2011-02-28
Did you make the drive bootable?

---

### Post by MuleSkinner on 2011-02-28
Yes, following the instructions by **C.S.Cameron** in the thread I linked to in the OP using UNetbootin.

---

### Post by Kirboosy on 2011-03-01
This is coming straight off the Unetbootin Website...
[QUOTE=Unetbootin]
[B]Go to [http://unetbootin.sourceforge.net/diskimg/](http://unetbootin.sourceforge.net/diskimg/) and download one of the files (128mb.zip, 256mb.zip, or 512mb.zip) corresponding to the amount of persistent space you want (make sure the size of the persistent disk image is smaller than the free space you have on your USB drive).

Now extract the file "casper.rw" from the zip file to your USB drive.[/B] 

Now edit D:\syslinux.cfg (assuming D:\ is where your USB drive is) and add in "persistent" at the end of the line that begins with "append", and save the file, so your syslinux.cfg should look something like this:

default unetbootin
label unetbootin
    kernel /ubnkern
    append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash persistent --

For more info see [https://help.ubuntu.com/community/LiveCD/Persistence](https://help.ubuntu.com/community/LiveCD/Persistence)[/QUOTE]

For the non bold section. Run in a terminal ```
gksudo nautilus
```

Then navigate to the drive and open Syslinux to make the changes...

---

### Post by MuleSkinner on 2011-03-01
I followed all of the directions including extracting the the 512mb casper.rw file to the flash drive. The words I changed (I did this in Windows, so I skipped the step about running gksudo nautilus) in the syslinux.cfg ended up looking like this:

> label unetbootindefault
menu label Default
kernel /ubnkern
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash persistent --I booted up Ubuntu using the flash drive and changed Firefox's home page and ran the following command in the terminal:

sudo apt-get install ubuntu-restricted-extras

I rebooted and the changes were gone. :(

Could it be because of the edit tuxcantfly made at the top of post #4 in [this]("http://ubuntuforums.org/showthread.php?t=811397") thread?

---

### Post by Kirboosy on 2011-03-01
Yeah you might have to follow that LiveUsbPendrivePersistent guide. I think its been a while since Unetbootin was updated.

I don't know why the Ubuntu Startup Disk Creator isn't working for you. It even has the option to save changes to it...

---

