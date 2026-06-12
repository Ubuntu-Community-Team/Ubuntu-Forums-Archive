---
title: "Wipe hard drive"
date: 2011-09-06
forum: New to Ubuntu
---

### Post by dannylortz on 2011-09-06
Ok i have got the ubuntu 11.04 running in test mmode but i cannot install it because my hard drive is full only 450 mb free. The computer has no othe OS so i have no idead how to format c: Ubuntu doesnt even display the hard drive?? any ideas

---

### Post by yetiman64 on 2011-09-06
If you have no other OSes on the drive instruct the live cd to use the whole drive (select that option and note it has a warning beside it) and it will kindly overwrite anything or any other OS that is there. **Ensure there is nothing you need on that drive first**, it will be lost if you choose that option in the installer. 

You don't need to free up any space first if you don't need what is on the drive by selecting the correct option during install. In fact that particular option has caused some headaches here for Windows dual booters who wrongly selected it and promptly lost their Windows install (overwritten).

---

### Post by ajgreeny on 2011-09-06
> **dannylortz said:**
> Ok i have got the ubuntu 11.04 running in test mmode but i cannot install it because my hard drive is full only 450 mb free. The computer has no othe OS so i have no idead how to format c: Ubuntu doesnt even display the hard drive?? any ideas
You don't say how large your hard drive is, only that it has 450MB free space.  What is on it, and how important is all that data to you?

Assuming you really don't need anything that is already on the disk, I recommend that you follow the link for a separate /home partition shown below.
[Separate home at install.]("http://www.psychocats.net/ubuntu/installseparatehome") 

It is definitely worth doing whenever you need to reinstall the OS, or at distro upgrade time, eg to 11.10, next month.

---

### Post by nipunshakya on 2011-09-06
> **dannylortz said:**
> Ok i have got the ubuntu 11.04 running in test mmode but i cannot install it because my hard drive is full only 450 mb free. The computer has no othe OS so i have no idead how to format c: Ubuntu doesnt even display the hard drive?? any ideas

If you need to see your hard drive then see Disk utility application(simple solution if you haven't tried)

If you are running your ubuntu in your test mode, then you probably need a LiveCD to install ubuntu...
But before doing so, you must backup all your data(if u need them), and then go for fresh installations of ubuntu ...
see these links below....they might help you create healthy and flawless partitions during the installation process.... [http://members.iinet.net/~herman546/index.html]("http://members.iinet.net/%7Eherman546/index.html")
 So far, this is the best guide i found regarding the installations and partitions....good luck

---

### Post by Johnb0y on 2011-09-06
could be busted drive... :o

---

### Post by dannylortz on 2011-09-07
I dont want to dual boot or whatever. And i dont care for any of the **** on the harddrive. In the install wizard thing there is no option it just tells me i need 4.5gb space, connected to power supply and connected to net to continue its that straight forward no other option. wont let me continue until those three things have ticks next to them.

---

### Post by Johnb0y on 2011-09-07
could try using hiren CD??? got lots of tools there for hard drive partitioning...

p.s. quick google of it should be easy to find...

---

### Post by fractalman on 2011-09-07
ok, if you really really are sure you don't need anything that is already on the disk....

I would suggest downloading Dariks Boot and Nuke (DBAN)

[http://www.dban.org/download](http://www.dban.org/download)

burn dban to a disc and then reboot your pc,

enter bios and set your boot priority to boot from a cd first,

then run the program, its quite simple to use and it will totally wipe your drive leaving it blank and pretty much as good as a new one (bar a little wear and tear from already being operational)

once dban has run and finished, reboot and pop your ubuntu disc in, following the on screen guide and install, 

please be aware though that dban can take a while to complete depending on your hardware specs,  my 80g sata2 drive takes about 2 hours to wipe,  my mates 160g took 5 hours. and thats on the lowest method of wiping, if you go for something like a proper deep clean military style then you could be looking at a few days to a week or more depending on hardware.  A basic once through should suffice for a general pc though! :)

you might have to try a few versions of dban, i have found that some versions wont work on one machine but will work on others.

---

### Post by yetiman64 on 2011-09-07
You've already got tools on the live cd to wipe a drive, dd or shred commands in a terminal. No need to download or use any other discs etc.

Here is an example of the shred command from another thread here, note you will have to add a partition table back to the drive with gparted (also available on the live cd)

[http://ubuntuforums.org/showthread.php?p=10685165#post10685165](http://ubuntuforums.org/showthread.php?p=10685165#post10685165) post #2. Post #6 has the alternate dd command.

Ensure you identify the drive correctly using fdisk before issuing the dd or shred command.

Edit: just rechecked that link, leave out the partition number, eg use /dev/sd**a**, to wipe the whole drive with either shred or dd.

---

### Post by YesWeCan on 2011-09-07
> **dannylortz said:**
> Ok i have got the ubuntu 11.04 running in test mmode but i cannot install it because my hard drive is full only 450 mb free. The computer has no othe OS so i have no idead how to format c: Ubuntu doesnt even display the hard drive?? any ideas
Do you want to erase a single partition or the whole disk?

To erase the whole disk:
Boot live Ubuntu CD
Run System/Administration/Disk Utility
select your disk on the left
select "Format Drive"

To erase a specific partition:
Boot live Ubuntu CD
Run System/Administration/Disk Utility
select your disk on the left
click on the partition in the diagram
select "Delete partition"

---

### Post by nipunshakya on 2011-09-07
> **dannylortz said:**
> I dont want to dual boot or whatever. And i dont care for any of the **** on the harddrive. In the install wizard thing there is no option it just tells me i need 4.5gb space, connected to power supply and connected to net to continue its that straight forward no other option. wont let me continue until those three things have ticks next to them.

This forum is all about sending and receiving ideas and putting forward the ones you like the most....dual boot was just an option given to you not a compulsion....and there is no need to get mad or frustrated that u offend someone....
And btw i had already suggested you Disk Utility...you could have given it a try using your LIVECD and then posted your results here instead of being vulgar.

First Use the LiveCD then flush out the entire drive if you don't want anything of your HDD then try the installation....


And no need to offend anyone here. You might be frustrated but u mustn't abuse anyone here...not even your harddrive because it has been serving you.....Love your machine and it will love you.Goodluck

---

