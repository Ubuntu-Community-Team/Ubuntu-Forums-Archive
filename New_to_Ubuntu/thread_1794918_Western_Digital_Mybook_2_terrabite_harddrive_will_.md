---
title: "Western Digital Mybook 2 terrabite harddrive will not read"
date: 2011-07-01
forum: New to Ubuntu
---

### Post by Hobbsierox on 2011-07-01
I have a two terrabite mybook that  i have been using for months. Two days ago i let my friend back up his pictures and music on it before he upgraded to 11.04. since then it stopped reading. the only way i can even see it is in terminal with the lsusb command. i have a lot of files on there that i cant access could anyone help me figure out what happened? i am kinda new to ubuntu and linux and i do not have much experience with terminal but i am willing to do what i have to in order to get it working. any advice would be helpful. i'm currently running Ubuntu 10.10 on a hp desktop with an amd 64 x2 processor and two gigs of ram i am willing to give any specs that i missed out on. i just need some help.

---

### Post by wildmanne39 on 2011-07-01
> **Hobbsierox said:**
> I have a two terrabite mybook that  i have been using for months. Two days ago i let my friend back up his pictures and music on it before he upgraded to 11.04. since then it stopped reading. the only way i can even see it is in terminal with the lsusb command. i have a lot of files on there that i cant access could anyone help me figure out what happened? i am kinda new to ubuntu and linux and i do not have much experience with terminal but i am willing to do what i have to in order to get it working. any advice would be helpful. i'm currently running Ubuntu 10.10 on a hp desktop with an amd 64 x2 processor and two gigs of ram i am willing to give any specs that i missed out on. i just need some help.Hi, open disk utility and see if it is listed there, if so make sure it is mounted, if not use disk utility to mount it.

---

### Post by Hobbsierox on 2011-07-01
it doesn't show up in disk manager and i've been trolling forums for the past two days trying all sorts of things to mount it and none have worked

---

### Post by Hobbsierox on 2011-07-01
disk utility**

---

### Post by wildmanne39 on 2011-07-01
Hi, what format is the partition? ntfs or ext3.

---

### Post by Hobbsierox on 2011-07-01
hi, i'm not sure. how would i find out? the only way i even can see the device is with the lsusb command

---

### Post by Hobbsierox on 2011-07-01
at least as far as i can tell the only way the device shows up is lsusb. i still have lots to learn when it comes down to terminal.

---

### Post by wildmanne39 on 2011-07-01
Hi, run this command in a terminal
```
sudo parted -l
```
and post the outcome  here by clicking on new reply and click # and paste the information between the brackets. Make sure you external drive is hooked to your computer and is plugged into the wall.

---

### Post by Hobbsierox on 2011-07-01
i entered it in terminal but still no output how long is it supposed to take?

---

### Post by Hobbsierox on 2011-07-01
not a terminal output but an error message


Unable to mount New Volume
DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

---

### Post by cmcanulty on 2011-07-01
Try this fix I have to do it every so often in Ubuntu with my western digital

```
sudo apt-get install udisks libgdu0 gnome-disk-utility policykit-desktop-privileges --reinstall
```

---

### Post by jtarin on 2011-07-01
Or try this adjustment....I have to do it every so often to mine.A slight tap will do wonders.....careful.....don't over-adjust.:p
[img]http://www.elitesniperteam.co.uk/index.php?app=core&module=attach&section=attach&attach_rel_module=post&attach_id=425[/img]

---

### Post by Hobbsierox on 2011-07-01
hi i restarted my comp and 
```
sudo parted -l
```and this was the output

```
 Model: ATA WDC WD2500JS-60N (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  244GB  244GB   primary   ext4            boot
 2      244GB   250GB  6167MB  extended
 5      244GB   250GB  6167MB  logical   linux-swap(v1)


Model: ATA ST3320620AS (scsi)
Disk /dev/sdb: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      32.3kB  320GB  320GB  primary  ntfs         boot


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label      
```

---

### Post by wildmanne39 on 2011-07-01
Model: ATA ST3320620AS (scsi)
Disk /dev/sdb: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      32.3kB  320GB  320GB  primary  ntfs         boot

Hi, I am not an expert but this drive is showing as a boot drive now with the partition format ntfs for windows, I am going to give you a link to mount window file systems but it is possible since it is a boot partition that your files have been over written by what your friend did.
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

---

### Post by Hobbsierox on 2011-07-01
hey all still no luck any other suggestions?

---

### Post by jtarin on 2011-07-01
```
Error: /dev/sr0: unrecognised disk label
```That's your CD/DVD drive.
In a terminal issue the command ```
cat /etc/fstab
``` copy and post the results.

Do you have any reason to have a bootable ntfs drive?

---

### Post by ClientAlive on 2011-07-01
> **jtarin said:**
> Or try this adjustment....I have to do it every so often to mine.A slight tap will do wonders.....careful.....don't over-adjust.:p
[img]http://www.elitesniperteam.co.uk/index.php?app=core&module=attach&section=attach&attach_rel_module=post&attach_id=425[/img]


:D

your crazy

lmao

---

### Post by Eiji Takanaka on 2011-07-01
I had issues with a western digital external harddrive. Came down to file partition type as i vaguely recall.

Think i used fdisk to reformat.

---

### Post by ClientAlive on 2011-07-01
> **Hobbsierox said:**
> hi i restarted my comp and 
```
sudo parted -l
```and this was the output

```
 Model: ATA WDC WD2500JS-60N (scsi)
Disk /dev/sda: **250GB**
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  244GB  244GB   primary   ext4            boot
 2      244GB   250GB  6167MB  extended
 5      244GB   250GB  6167MB  logical   linux-swap(v1)


Model: ATA ST3320620AS (scsi)
Disk /dev/sdb: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      32.3kB  320GB  320GB  primary  ntfs         boot


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label      
```

It's also showing as much less than 2 terrabytes in size. Is that top listing really the drive in question? Does he have 2 drives in the computer where one is a western digital and the other is (whatever the second listing here says), while the 2 terrabyte external, my book drive is not showing at all?


> **wildmanne39 said:**
> Hi, I am not an expert but this drive is showing as a boot drive now with the partition format ntfs for windows, I am going to give you a link to mount window file systems but it is possible since it is a boot partition that your files have been over written by what your friend did.
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)


One of the first things people say is if you think the drive may have been corrupted or is damaged, don't do anything invasive as it could cause further damage. Invasive in the case of a drive with no physical damage means things like writing to the drive or altering partitions, etc. Invasive in the case of a physically damaged drive means anything at all that causes mechanical movement within the drive.
----------------

Edit:

In the output quoted above each disk is listed as

> 
/dev/sda


And

> 
/dev/sdb


Isn't it that " . . ./sda" is an internal drive, while " . . ./sdb" is an external drive? But neither of those drives listed is anywhere close to 2 terrabytes.

---

### Post by Eiji Takanaka on 2011-07-01
Do you always mount/unmount properly as well? 

This severely messed up one of my external harddrives in my early ubuntu days, well it didn't mess it up, it just took a fair bit of research to get working again ;)

---

### Post by jtarin on 2011-07-01
> **ClientAlive said:**
> :D

your crazy

lmaoMy wife and friends agree!:P

---

### Post by Eiji Takanaka on 2011-07-01
try "sudo fdisk -l"

dude. Thats a small L by the way ;)

As was aformentioned /sdb usually is the external drive /sda is internal. This can vary though.

If no /sdb's are showing up then its probably not recognizing the drive for some reason.

---

### Post by ClientAlive on 2011-07-01
> **Hobbsierox said:**
> hey all still no luck any other suggestions?


Relax. Take a deep breath. It will be ok.

Try to check things out before you try them. Be careful. That's always a good idea. Think about the clues you see, the answer will be revealed. 

:)

---

### Post by ClientAlive on 2011-07-01
> **Eiji Takanaka said:**
> try "sudo fdisk -l"

dude. Thats a small L by the way ;)


What that command does is list information about the drives in or attached to the computer.

To get information on any command you can type "man" then a space then the name of the command - into the terminal and press enter. To exit the man page press Q. To move up and down use the arrow key or the page up/ page down keys.

Here's the beginning of the man page for the fdisk command.

By entering . . .

```

man fdisk

```

I get a page that starts with . . .

```

NAME
       fdisk - Partition table manipulator for Linux

```

HTH

---

### Post by jtarin on 2011-07-01
If I unplug mine and then plug it back in.....I need to reboot before it will show.

---

### Post by ExileAmongYou on 2011-07-01
If you have a spare USB cable lying around, swapping the cables is always worth a try.

---

### Post by Eiji Takanaka on 2011-07-01
Anything showing up in "System - Administration - Disk Utility"?

Its starting to come back to me a bit actually, i definately had major issues when switching between windows and ubuntu with a WD external harddrive. I could swear it was something to do with the file-type.....

Maybe something to do with a forced mount/umount......

Apologies my memory isn't too great ;)

---

### Post by jtarin on 2011-07-01
> **Eiji Takanaka said:**
> Anything showing up in "System - Administration - Disk Utility"?

Its starting to come back to me a bit actually, i definately had major issues when switching between windows and ubuntu with a WD external harddrive. I'm could swear it was something to do with the file-type.....
Ok...let's try hypnosis.;)

---

### Post by Eiji Takanaka on 2011-07-01
Haha jtarin might not be a bad idea man! ;)

---

### Post by ClientAlive on 2011-07-01
[http://www.googlubuntu.com/](http://www.googlubuntu.com/)

---

### Post by ClientAlive on 2011-07-01
[http://ubuntuforums.org/showthread.php?t=207636](http://ubuntuforums.org/showthread.php?t=207636)

#'s 5, 6 and 10 (maybe other's further on in)

[http://ubuntuforums.org/showthread.php?t=961104](http://ubuntuforums.org/showthread.php?t=961104)

#8

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=problem+with+western+digital+my+book&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=problem+with+western+digital+my+book&as_qdr=all&sa=Google+Search&lang=en)

---

### Post by Hobbsierox on 2011-07-03
> **wildmanne39 said:**
> Hi, run this command in a terminal
```
sudo parted -l
```and post the outcome  here by clicking on new reply and click # and paste the information between the brackets. Make sure you external drive is hooked to your computer and is plugged into the wall.

Hi i still am not having any luck getting it to read/mount i've even gone so far as to take the my book apart and hardwire it into the motherboard like a regular internal drive and it still does not read. i'm not sure what to do. any advice would be greatly appreciated as i previously stated i've barely any experience with terminal but am willing to learn. i dont know what to try next and i really need to get this back up and running. if you have any other ideas please send them my way.

---

### Post by jtarin on 2011-07-03
Is it being recognized in the bios?

---

### Post by Hobbsierox on 2011-07-03
When i reboot with it plugged in my comp wont boot up at all. it stays at the hp blue screen and none of the buttons to enter bios or setup or boot order work

---

### Post by ClientAlive on 2011-07-03
> **jtarin said:**
> Is it being recognized in the bios?


ouch!

---

### Post by jtarin on 2011-07-03
> **Hobbsierox said:**
> Hi i still am not having any luck getting it to read/mount i've even gone so far as to take the my book apart and hardwire it into the motherboard like a regular internal drive and it still does not read.Give a detailed account of how you "wired" this setup.

---

### Post by Hobbsierox on 2011-07-03
i took apart the mybook and used  my sata cable and the power cable to wire them into the mother board like any harddrive.

---

### Post by jtarin on 2011-07-03
All I can say at this point is to try another computer to see if it can be read.

---

### Post by Hobbsierox on 2011-07-03
i have hooked this thing up to multiple different laptops and so far none of them will read the device when i 
```
lsusb
```
this is my output
```
Bus 002 Device 005: ID 046d:c318 Logitech, Inc. Illuminated Keyboard
Bus 002 Device 004: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
Bus 002 Device 002: ID 046d:c016 Logitech, Inc. Optical Wheel Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 009: ID 1058:1130 Western Digital Technologies, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

any idea how i could mount it with this information being as it is not showing up anywhere else with any command i try?

---

### Post by wildmanne39 on 2011-07-04
> **Hobbsierox said:**
> i have hooked this thing up to multiple different laptops and so far none of them will read the device when i 
```
lsusb
```
this is my output
```
Bus 002 Device 005: ID 046d:c318 Logitech, Inc. Illuminated Keyboard
Bus 002 Device 004: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
Bus 002 Device 002: ID 046d:c016 Logitech, Inc. Optical Wheel Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 009: ID 1058:1130 Western Digital Technologies, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

any idea how i could mount it with this information being as it is not showing up anywhere else with any command i try?Hi, here is a guide for mounting window partitions, but I do not know if it will work.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

---

### Post by jtarin on 2011-07-04
Let's have the model name and number of this thing.

---

### Post by jtarin on 2011-07-04
[FAQ: External hard drive no longer shows up in My Computer and data can no longer be accessed]("http://community.wdc.com/t5/My-Book-for-PC/FAQ-External-hard-drive-no-longer-shows-up-in-My-Computer-and/td-p/133426")

---

### Post by wildmanne39 on 2011-07-04
Hi jtarin, it does not look good does It?

---

### Post by jtarin on 2011-07-04
Looks like an RMA.

---

### Post by Hobbsierox on 2011-07-04
so i think as a possibility that my harddrive got fried because i took the case off and there was black scorch looking marks on the circuit board

---

### Post by jtarin on 2011-07-04
> **Hobbsierox said:**
> so i think as a possibility that my harddrive got fried because i took the case off and there was black scorch looking marks on the circuit boardThat should have been your opening post, but thanks for stopping us after 5 pages.:p 

Mark this thread as solved if you will.

---

### Post by Hobbsierox on 2011-07-04
sorry for any inconvenience i didnt notice it right off the bat because it was still being read with lsusb  and i was so focused on trying to fix it being as it still showed up. i apologize for wastin time with a hardware issue that i thought had to do with the file system partitions and such

---

### Post by Hobbsierox on 2011-07-04
[COLOR=Black]i want to thank everyone for helping me out even though i am still a noob i appreciate it all. i had the opportunity to learn some things which i am very grateful for. big thanks [jtarin]("http://ubuntuforums.org/member.php?u=738123"), [Eiji Takanaka, and ]("http://ubuntuforums.org/member.php?u=1151216")[/COLOR][URL="http://ubuntuforums.org/member.php?u=508533"][COLOR=Black]_wildmanne39 for the help_[/COLOR]
[/URL]

---

### Post by jtarin on 2011-07-04
Not a problem really...that's why we're here,:pbut next time post in the "Breakfast" section under "Toast" for hardware problems like this.:lolflag:  .....Good Luck.

---

### Post by wildmanne39 on 2011-07-04
Hi, your welcome any time we can help just start a thread.

---

### Post by jtarin on 2011-07-04
> **Hobbsierox said:**
>  i had the opportunity to learn some things which i am very grateful for.I had the opportunity too.....just learned about these type of HD's and how I might stay away. Thanks to you.

---

### Post by cmcanulty on 2011-07-04
Also try reaching it with a knoppix or puppy live CD both have seen drives for me sometimes when it won't show in Ubuntu

---

### Post by mister_p_1998 on 2011-07-04
Try plugging it into an XP machine, if its been improperly unmounted, it wont mount in linux.

---

