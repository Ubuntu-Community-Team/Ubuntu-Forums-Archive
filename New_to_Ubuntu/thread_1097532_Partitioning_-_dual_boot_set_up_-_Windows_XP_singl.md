---
title: "Partitioning - dual boot set up - Windows XP single partition present"
date: 2009-03-16
forum: New to Ubuntu
---

### Post by Eagle Nest on 2009-03-16
Question: Can I use the Ubuntu Desktop installation process to do ALL the partitioning ... from the current state of ONE partition for Windows XP to my goal of 4 (or more) partitions? Perhaps I am overlooking the obvious. I am working with 8.10 and have reached the partition window.

Supplemental: I have an 80 GB HDD under ntfs for the Windows XP O/S. I was led to believe that I could use the Ubuntu install process to change the size of the Windows partition, but it is not clear to me if this is possible.

---

### Post by Andreas1 on 2009-03-16
when the graphical installation assistant reaches the point where it offers some options like "make drive smaller and use rest of space for ubuntu" or "use entire harddisk", there should also be one last option to do everything manually. choose that. just make sure you create an ubuntu partition formatted with ext3 mounted as "/" and a swap partition about the size of your ram (or more if you want to use suspend to disk aka hibernate).

alternatively you can just boot the live cd choosing "try ubuntu out" instead of "install ubuntu" and then run System>Administration>Partiton Editor (or run gksudo gparted).

---

### Post by Eagle Nest on 2009-03-16
I'm just not getting anything, even with "manual" that seems to allow me to change the size of the part of the HDD devoted to Windows. The sliding bar does not appear at all. It's weird. 

I tried all this with the "Install Ubuntu" option from the LIVE CD; I think I will try "Try Ubuntu without making any changes" and then click on the "install" icon on the desktop. Perhaps that sequence will give me what I want; I will post my results. argg. Frustrating.

---

### Post by Andreas1 on 2009-03-16
> **Eagle Nest said:**
> I'm just not getting anything, even with "manual" that seems to allow me to change the size of the part of the HDD devoted to Windows. The sliding bar does not appear at all. It's weird.

can you describe what you see after choosing "manual"? as far as i remember there should not be a slider, there should be a list of your partitions where you can right click on them to edit.

Edit: something like this:
[IMG]http://blog.dreamdevil.com/media/2008/11/05-ubuntu-8_10-prepare-partition-good.jpg[/IMG]

---

### Post by ivanvajar on 2009-03-16
Boot from LiveCD and run System>Administration>Partiton Editor

Right-click on your Windows partition, then Resize. Move slider to make Partition smaller and on new unallocated space => right-click/create. You use this method to create any partition type from egzisting partition.

---

### Post by Eagle Nest on 2009-03-16
Thanks for advice from Andreas1 and ivanvajar. I have gone into System-Administration-Partition Editor but still have problems. 

The range of sizes is listed as from 71309 MiB (min) to 76317 MiB (max). It looks like I have 8 MiB to play with, if that. However, I went further into things and got a message as follows:

noted in a message that the filesystem was ntfs
size 74.52 GiB
warning of at least 2 bad sectors
recommended a full backup (I've already saved everything that needs saving) and run chkdsk/f/r on Windows and reboot Twice ... after which I can resize NTFS safely by additionally using the bad sectors options of ntfs resize.

It is very late for me so I will take a break shortly. Of course I ran defrag before trying any of this, but did not run chkdisk at the time. Could this really be the problem?

---

### Post by Andreas1 on 2009-03-16
ubuntu cautiously refuses to touch ntfs if it finds it damaged and hence unsafe to resize. chkdsk might be worth trying.

---

### Post by presence1960 on 2009-03-16
> **Eagle Nest said:**
> Question: Can I use the Ubuntu Desktop installation process to do ALL the partitioning ... from the current state of ONE partition for Windows XP to my goal of 4 (or more) partitions? Perhaps I am overlooking the obvious. I am working with 8.10 and have reached the partition window.

Supplemental: I have an 80 GB HDD under ntfs for the Windows XP O/S. I was led to believe that I could use the Ubuntu install process to change the size of the Windows partition, but it is not clear to me if this is possible.

Someone already told you to choose "use ubuntu without any changes" when you boot Live CD. Then use partition editor- you'll find it under administration. Right click on the XP partition and choose resize. Make the partition smaller to the point you have enough space you desire for new partition(s). Then right click the unallocated space and choose "New" to create your new partition(s).

---

### Post by Eagle Nest on 2009-03-16
I've run chkdisk on the Windows XP system. I'm still not able to get either the install program or the partition editor to make the ntfs partition smaller so I can get on with setting up Linux on my PC. This is very frustrating. The online screen shots that I am able to call up/look at do not show what I see. That is very unhelpful.

---

### Post by Andreas1 on 2009-03-16
> **Eagle Nest said:**
> The online screen shots that I am able to call up/look at do not show what I see. That is very unhelpful.

So what do you see? Can you post a screenshot of your gparted (Partition Editor), maybe with the edit partition dialog window or the error message?

---

### Post by Eagle Nest on 2009-03-16
OK, I will try to do so.

---

### Post by Eagle Nest on 2009-03-16
It's my understanding that the partition of my hard drive on which Windows XP sits has to be made smaller before I can add root, home and swap partitions for Linux. At least no one here with advice has contradicted that assumption. But making the Windows partition smaller just never comes up, either in Linux install procedure, or in the partition software as it is run from the Live CD. I cannot even get to first base here. There is no slider, and there's no drop down menu to change the size downward. It really seems to me that people are giving me advice based on older Linux installs and haven't looked at 8.10 at all themselves.  

Is there some way to shrink the windows partition either FROM windows and/or with some readily available software? I've had it with this nonsense.  

Just to be clear, to respond to Andreas1, I have ONE ntfs partition for windows with a mere 8 MB of the roughly 80 GiG hard drive "free". When I go through the manual choice there is no point where I am given the choice to change the size of the partition to make it smaller. As I've already noted, there's reference to a 8 MB change. That's it. I can't be any clearer than that.  

Andreas1: "Can you post a screenshot of your gparted (Partition Editor), maybe with the edit partition dialog window or the error message?"

I have no idea how to save a screenshot when I'm using the Live CD. If you think this is important how about sharing the shortcut?

---

### Post by orethrius on 2009-03-16
I notice nobody bothered to ask what seems to be the obvious question here.

In Windows, how much space is available on that 80-gig drive? GParted can resize *free space*, but it cannot magically make it appear (you will need to either compress the drive in Windows, or remove some files first).  If it makes a difference, I made that mistake the first time I handled GParted, too.  :-D

---

### Post by Eagle Nest on 2009-03-16
Well I've messed around and messed around ... and I must have changed SOMETHING, becuase GParted now reads as follows ...

Partition     Filesystem    Mountpoint Size         used   unused flags

/dev/sda1     ntfs          /media/disk  74.52 GiB  7.24   67.28   boot
unallocated   unallocated                 7.84 MiB    --    --  

I don't recall having that mountpoint before. Gparted doesn't seem to be much good with the above changes ... I can't seem to do anything now. 

I will try to go through the install procedure but this is really getting annoying.

---

### Post by Andreas1 on 2009-03-17
> **Eagle Nest said:**
> It really seems to me that people are giving me advice based on older Linux installs and haven't looked at 8.10 at all themselves.
I am running 8.10 and i just checked. In gparted, when i right click on a partition there is an entry in the context menu that says "resize/move"

> **Eagle Nest said:**
> Just to be clear, to respond to Andreas1, I have ONE ntfs partition for windows with a mere 8 MB of the roughly 80 GiG hard drive "free". When I go through the manual choice there is no point where I am given the choice to change the size of the partition to make it smaller. As I've already noted, there's reference to a 8 MB change. That's it. I can't be any clearer than that.

what do you mean by "no choice but *reference to a change*"?
anyway, as orethrius pointed out, you obviously can't make a partition smaller than the data contained by it, so how much space inside the partition is free? (i take it that the 8mb are unallocated space outside the partition)
EDIT: From your last post i can see there is enough space free. So, what exactly happens when you right click on that partition and choose "resize/move"? is the option grayed out or something?


> **Eagle Nest said:**
> Well I've messed around and messed around ... and I must have changed SOMETHING, becuase GParted now reads as follows ...

Partition     Filesystem    Mountpoint Size         used   unused flags

/dev/sda1     ntfs          /media/disk  74.52 GiB  7.24   67.28   boot
unallocated   unallocated                 7.84 MiB    --    --  

I don't recall having that mountpoint before. Gparted doesn't seem to be much good with the above changes ... I can't seem to do anything now. 

I will try to go through the install procedure but this is really getting annoying.

maybe you mounted the drive by opening it with the file browser. try the eject button next to the drive in the side pane of the file browser


EDIT: as for the screenshot, hit the print key, and save it either to an usb storage device if you have one or just temporarily mount the ntfs drive (as you apparently did accidentally) and save it there. i was only suggesting a screenshot because we don't seem to be communicating so well;)

---

### Post by Eagle Nest on 2009-03-17
Here are 2 examples of the resize window I see in GParted ...

[IMG]http://i614.photobucket.com/albums/tt227/Eagle_Nest/ResizeScreenshot.png[/IMG]

[IMG]http://i614.photobucket.com/albums/tt227/Eagle_Nest/1b-Screenshot.png[IMG]

Here is the prepare disk space window ...

[IMG]http://i614.photobucket.com/albums/tt227/Eagle_Nest/preparediskspaceScreenshot.png[/IMG]

Here is the Prepare Partitions window ...

[IMG]http://i614.photobucket.com/albums/tt227/Eagle_Nest/preparepartitions1Screenshot.png[/IMG]

and here is the Edit a Partition window...

[IMG]http://i614.photobucket.com/albums/tt227/Eagle_Nest/preparepartitions2Screenshot.png[/IMG]

and here I reach a dead end ...

[IMG]http://i614.photobucket.com/albums/tt227/Eagle_Nest/preparepartitions4Screenshot.png[/IMG]

OK. I hope that makes my difficulties more clear. Thanks for being patient Linux users.

---

### Post by Eagle Nest on 2009-03-18
If someone could suggest a quick way for me to reduce the size of the above images then I would appreciate that. I've done such resizes in the past but I can't access the discussion board there anymore. thx.

---

### Post by Andreas1 on 2009-03-18
There's that orange warning triangle next to "/dev/sda1" and the "unknown" entry in the "used" column. If you right-click on the partition and choose "information" i think it will tell you that something is wrong with the ntfs partition and its content could not be read, hence could not be resized.
I've had that several times. Sometimes running chkdsk under windows fixed it. (in windows, right click on the drive, properties, tools > error checking > check now. Be sure to check "Automatically fix file sytem errors") Some might also suggest running the Defragmentation on that drive.

In short: you have to fix the partition from windows and only if that orange warning triangle is no longer there and gparted displays correctly how much space is free you can resize it. The weird thing is, as i recall, one time this (first chkdsk, then gparted) would spontaneously work and another time it wouln't.

[SIZE="3"]does anyone know if resizing the ntfs partition can also be done from windows?[/SIZE]

---

### Post by Eagle Nest on 2009-03-18
OK. I will let you know how it goes. thx again.

---

### Post by muteXe on 2009-03-18
When you get all this working, make sure you defrag your windows a couple of times too before installing ubuntu.

---

### Post by Eagle Nest on 2009-03-18
I've run chkdisk several times, defrag one more time, and I'm still getting the same messages. I will print screen what I'm getting, then defrag one more time, and then come back here. Damn, this is annoying.

Here's what I get from GParted after checking "information" ...

[IMG]http://i614.photobucket.com/albums/tt227/Eagle_Nest/resizenotesfromGParted.png[/IMG]

---

### Post by kansasnoob on 2009-03-18
When you defrag XP what does it show for amount of disk used and free?

---

### Post by Andreas1 on 2009-03-18
i would follow all of those suggestions, also (especially) the one about making a backup. and do the backup before running 'chkdsk/f/r'.
when my ntfs partition caused trouble the error message was somewhat similar but it did not involve *physical* damage. if gparted is right about this it would be time to get a new harddrive, but the question is if this information is reliable.

ideas anyone?

EDIT: 'chkdsk/f/r' is equivalent to checking both "Automatically fix file system errors" and "Scan for and attempt recovery of bad sectors". THIS MAY TAKE SOME TIME.

---

### Post by kansasnoob on 2009-03-18
Well, if there is enough free space, the answer is to use ntfsprogs.

So with the Live CD booted go to terminal and run:

```
sudo apt-get install ntfsprogs
```

If it installs (I say *if* because the Live CD runs in system RAM so there are definite limitations) you should then be able to resize the ntfs partition once you reopen gparted (partition editor).

More about ntfsprogs here:

[http://www.linux-ntfs.org/doku.php](http://www.linux-ntfs.org/doku.php)

An alternative would be downloading and burning an actual gparted live CD:

[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

Of course there is no absolute guarantee that data won't be lost or that the Windows install will still perform properly (or even boot).

---

### Post by Eagle Nest on 2009-03-18
> **kansasnoob said:**
> When you defrag XP what does it show for amount of disk used and free?

C: 
NTFS file system
74.52 GB capacity
67.25 GB free
90% free

I've now run defrag and chkdisk about a zillion times. 

Is ntfsprogs something that a Linux newbie like myself could reasonably be expected to run successfully? A one day intro to Linux and this (frustrating) thread is it for me.

---

### Post by Eagle Nest on 2009-03-20
Here is an image ...

[IMG]http://i614.photobucket.com/albums/tt227/Eagle_Nest/preparepartitionswontfs.png[/IMG]

I set up some partitions. However, my original SINGLE ntfs partition is nowhere to be seen here. I don know if, going forward with this set of partitions, I would wind up deleting the Windows ntfs partition altogether. In which case, I might as well just install Linux and wipe out the Windows altogether. But thats something I want to avoid, if possible. 

So, here I sit. !!! Help!!!

---

### Post by Andreas1 on 2009-03-20
> **Eagle Nest said:**
> I don know if, going forward with this set of partitions, I would wind up deleting the Windows ntfs partition altogether. In which case, I might as well just install Linux and wipe out the Windows altogether. But thats something I want to avoid, if possible.

Yes, of course it would delete the Windows partition.

Just an idea: You could repartition the hard drive, create a new ntfs (or FAT) partition (sda1) with gparted, then reinstall windows, then install ubuntu.

By the way, did chkdsk say anything about bad sectors?

---

### Post by Eagle Nest on 2009-03-21
> **Andreas1 said:**
> Yes, of course it would delete the Windows partition. 

OK, thanks for confirming that. 

> Just an idea: You could repartition the hard drive, create a new ntfs (or FAT) partition (sda1) with gparted, then reinstall windows, then install ubuntu. 

Could you outline this a bit more? If such partitions were created, would the PC then read the Windows install CD without having to install some drivers or something? 



> By the way, did chkdsk say anything about bad sectors?

No, nothing at all. It ran OK. But I'm getting paranoid so I will run it again, OK?

I should mention that the CD provided by my instructor didn't work, as a result of which I went back to one that I had already. I'm going to post my current difficulties on a local bulletin board and see if I get any bites. Maybe someone local can look at my problems.

---

### Post by Eagle Nest on 2009-10-22
OK, I've disposed of my PC and therefore the questions raised here aren't relevant to me anymore. I've got myself a new laptop and I've been able to install Ubuntu 8.10 alongside Windows Vista using WUBI. I'm happy with this arrangement as I can gradually get more and more skillful with Linux until the Windows OS and related applications are reduced to whatever cannot be run using Linux ... which shouldn't be very much at all. 

Great so far. However, I'm not able to connect to the wireless. So I will be posting over there, probably, just as soon as I get the information as outlined over here ... 

[How to Post a Wireless Issue. ]("http://ubuntuforums.org/showthread.php?p=6183681")

Thanks to those of you who offered assistance on my previous machine.

---

### Post by HarrisonNapper on 2009-10-22
A couple of things for the benefit of google searchers out there:

When you have a hard-drive running 100% Windows, it's usually a good idea to resize the Windows partition from within Windows itself. It comes with utilities to help you do just that.

Once you have resized the partition, done a check disk, and defragmentation (try for the lowest level of fragmentation you can). You should use GParted on the Ubuntu Live CD/USB or a GParted Live CD/USB to format the empty partition for linux. There are lots of guides on how to do all of these things in the Ubuntu Documentation, psychocats, et cetera. Or you can just use the installer to partition, but you will have to manually specify the linux partition for installing Ubuntu.

Note that even if Windows reports you have a total of xGB space with xGB free, it is still on the Windows partition and on an ntfs partition. That's why it's important to resize the partition within windows first to create free space for Ubuntu.

---

