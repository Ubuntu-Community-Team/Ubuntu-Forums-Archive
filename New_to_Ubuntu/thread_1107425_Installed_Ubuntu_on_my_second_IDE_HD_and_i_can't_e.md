---
title: "Installed Ubuntu on my second IDE HD and i can't even see him any more from Windows"
date: 2009-03-26
forum: New to Ubuntu
---

### Post by Fauve on 2009-03-26
Hello,

i have two ATA HDs, one 80gb with Windows XP and some files in it, and one 230gb with some music. Yesterday i tried to install Ubuntu Linux at my second HD and partition it through the ubuntu live installation as 50% of it's bandwith for Linux and 50% for Windows XP usage.

 After the installation was complete i restarted my pc in order to log into XP and download some drivers for my Network card. I then noticed that Windows can't even detect my second HD and when i tried running Partition Magic it resulted with an error.

I switched back to linux and also noticed that when i try to access the 2 HDs ( one 80gb which is the Master and one 115gb which is the bandwith i chose for Linux) it says that the drives could not be mounted or something.

Is there a way to fix this or restore my music at least?

Edit: Forgot to say that since i installed linux, each time i start windows they load for like 3-4 minutes till i see the leds of my keyboard and mouse lights up and then the login screen appears.

---

### Post by Michaelg14 on 2009-03-26
How did you partition your second hard drive?  Windows will not recognize an ext3 partition.  Try using gparted from Ubuntu to see if your second hard drive is formated as ext3. gparted is available from synaptic.

---

### Post by Fauve on 2009-03-28
Sorry for my late response, i wasn't able to answer..

I logged to Linux today and was surprised to see that i could open both of my HDs, both my 80gb that holds Windows in and my second 230 (but could see only 115gb as i gave to linux during the installation) In these 115gb i found all the music i had but i don't know if Linux copied them in the ext3 partition or something. 

As for how did i partition my HD, i did it from the Linux installation, i gave 50% of my HD to stay for Windows usage and 50% for Linux installation and stuff. Windows though can't see my second HD yet.

About gparted, i found something in linux system applications or something that has to do with synaptic but i didn't find anything in it called gparted. Downloaded gparted from internet though as an ISO, should i burn it and boot with it or run it from within Linux?

---

### Post by Michaelg14 on 2009-03-30
While in linux click on the System heading in the top panel.  Go down to Administration then to Synaptic Package Manager.  Search on gparted and install it from there.

Having said that you probably don't need it.  Linux can see and read/write to windows files but windows can't see linux files.  

It sounds like you may have an unformatted partition on your second (230) hard drive.  It would not show up in either system but will be available for formating under gparted.  If you want if for windows use I would use something like partition magic from windows.  As far as I know there is no way for windows to see a linux partition but I am no expert.

---

### Post by Fauve on 2009-03-30
I found an application named parted on synaptic as you said and it's already installed but being a complete newb at linux i did not know how to start it :S . 

I already have PartitionMagic 8.0 but as i said in my first post but when it start running it pops up a message "Init Error <number>" and disappears. (This might be off but when i bought the 230gb HD i had problems formating it using PartitionMagic, it would just stick to 3% resulting with an error or something, so i formated it using a Windows XP disc).

At least from within linux i could find the music i had stored in my 230gb HD and copied it in my 80gb one so i thought formating the second HD from scratch to ntfs and then do Ubuntu installation again. But won't try that till i try out all other solutions because i don't have a windows XP CD currently available.

Edit: I managed to squeeze some information about my 230gb HD from Partition Info tool from PartitionMagic 8.0 subtools. I will copy paste it here.

Partition Information for Disk 2:    238,472.7 Megabytes
Volume         PartType    Status    Size MB    PartSect  #   StartSect  TotalSects
===========================================================================================================
               NTFS        Pri,Boot 114,212.1           0  0          63 233,906,337
               Extended    Pri      124,260.6           0  1 233,906,400 254,485,665
               EPBR        Log      121,311.1        None -- 233,906,400 248,445,225
               Linux Ext3  Log      121,311.1 233,906,400  0 233,906,463 248,445,162
               EPBR        Log       2,949.4 233,906,400  1 482,351,625   6,040,440
Warning: EPBR partition starting at 482351625 is without logical partition.
               Unallocated Log       2,949.4        None -- 482,351,625   6,040,440

You might make more out of it than i can.

---

### Post by Michaelg14 on 2009-03-30
you can start gparted from a terminal window, just type in

```
sudo gparted
```

I think you have an extended partition on your second drive, you need to install a logical partition inside the extended partition to use that space. You are only allowed to have four partitions on a drive but if one is extended you may install as many logical partitions in it as you want.  There is probably some limit but I don't know what it is.  I have seven on my hard disk but four of those are in an extended partition.

Linux will not work in a windows partition.  Linux requires its own partition.  

gparted is much easier to work with, the g indicates a graphical interface and works well with gnome.

---

### Post by briansvgs on 2009-03-30
If you are trying to read files on your linux partition from within windows, I suggest using a utility such as [ext2ifs]("http://www.fs-driver.org/").This will add an ext3 driver to your windows system, allowing windows to read the partition (assuming that it is an ext3 of course).

---

