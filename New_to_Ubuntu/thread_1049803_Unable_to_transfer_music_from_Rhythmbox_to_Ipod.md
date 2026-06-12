---
title: "Unable to transfer music from Rhythmbox to Ipod"
date: 2009-01-24
forum: New to Ubuntu
---

### Post by Ghost175 on 2009-01-24
Im using Rhythmbox to store and play music, I would have used Amarok but I can't figure out how to have that play mp3's (issue 1), Now with Rhythmbox I am unable to transfer music to my Ipod (nano 3rd gen) (issue 2). I can transfer music from Ipod to computer though... which is odd considering I used to use Itunes which allowed me to put music on my ipod but not add music to my library from my Ipod.

If any of that made sense, please help.
Thanks in advance.

---

### Post by pytheas22 on 2009-01-24
You might have better luck using gtkpod.  Install it by typing:
```

sudo apt-get install gtkpod
```

Then launch it from the Applications>Sound and Video menu.

Also, this could be a permissions issue.  Reboot your computer, and don't plug your iPod in until you've already started gtkpod/Rhythmbox.  This should ensure that the system mounts it with the correct permissions settings.

EDIT: it would also be good if you posted the output of this command (while your iPod is plugged in):

```
lsusb
```

---

### Post by SunnyRabbiera on 2009-01-24
> **Ghost175 said:**
> Im using Rhythmbox to store and play music, I would have used Amarok but I can't figure out how to have that play mp3's (issue 1), Now with Rhythmbox I am unable to transfer music to my Ipod (nano 3rd gen) (issue 2). I can transfer music from Ipod to computer though... which is odd considering I used to use Itunes which allowed me to put music on my ipod but not add music to my library from my Ipod.

If any of that made sense, please help.
Thanks in advance.

Well itunes and rhythmbox are not going to be exactly alike, its the ipod that matters here.
More modern ipods wont work with linux, because apple hates us though steals things from us and rebrands it as their own.
If this is a new ipod, you are not in luck.

---

### Post by Ghost175 on 2009-01-24
@2nd post Im using gtkpod but its giving me a read-only error, so I'm starting to believe that the 3rd post is true, is there no way override this read-only mode? Any update to include newer generation ipods?

---

### Post by SunnyRabbiera on 2009-01-24
> **Ghost175 said:**
> @2nd post Im using gtkpod but its giving me a read-only error, so I'm starting to believe that the 3rd post is true, is there no way override this read-only mode? Any update to include newer generation ipods?

Jailbreaking seems go work for most, but do at your own leisure as we dont really encourage it (though I do, apple deserves a kick in the pants)

Either that or use a mp3 player that you can use with linux, a sansa sandisk is my choice :D

---

### Post by Ghost175 on 2009-01-24
> **SunnyRabbiera said:**
> Jailbreaking seems go work for most, but do at your own leisure as we dont really encourage it (though I do, apple deserves a kick in the pants)

Either that or use a mp3 player that you can use with linux, a sansa sandisk is my choice :D

What's jailbreaking?

---

### Post by MockY on 2009-01-25
Do yourself a favor and install Songbird instead. The only software that works like it should with no extra fuzz.

[http://www.getdeb.net/release.php?id=3519](http://www.getdeb.net/release.php?id=3519)

---

### Post by pytheas22 on 2009-01-25
> @2nd post Im using gtkpod but its giving me a read-only error, so I'm starting to believe that the 3rd post is true, is there no way override this read-only mode? Any update to include newer generation ipods?

What's the output of the commands:
```

lsusb
ls -l /media
```

while your iPod is plugged in?  With that information, we can google to see if other users have had issues with it.

Also, what exactly does gtkpod say regarding the read-only error?  And does the error still occur if you open gtkpod as root by typing in a terminal:
```

sudo gtkpod
```

If that also fails, it will rule out permissions as the source of your problem, so that we can be confident in attributing it to Apple's fascism.  But for now it's still possible that the issue is caused by Ubuntu mounting your iPod in such a way that only root can write to it.

---

### Post by Ghost175 on 2009-01-25
Could not open "(null)" for reading extended info.
Extended info will not be used.
Error reading iPod photo database (Photos directory not found: '/media/disk/iPod_Control/Photos' (or similar).).

was the error I recieve when I tell gtkpod what model Ipod I have 

when i actually attempt to add a song it goes alittle more like:

Transfer of 'C'Mon C'Mon' failed. Error opening '/media/disk/iPod_Control/Music/F12/gtkpod477998.mp3' for writing (Read-only file system).


Song Bird downloaded and says I need to format my ipod for windows, orr turn off journaling for the Ipod using MAc's Disk Utility app... but im only running linux so if nothing else works ill tkae it to a mac or pc and see if i can do either of those

---

### Post by pytheas22 on 2009-01-25
Yeah, formatting the iPod for Windows often helps.  If that doesn't work, it would still be good to see the output of:
```

lsusb
ls -l /media
```

Also, as a last resort you could run Windows in a virtual machine and access the device that way by giving it direct access to the iPod.  VirtualBox makes this easy.  But only do that if all else fails...

---

### Post by Ghost175 on 2009-01-25
was this it,and I thought I used disk utility to change the setup for the ipod to windows but now it doesn't show up in disk utility or when i connect it to Linux o_0 

also is this the output you were looking for?
colin@colin-laptop:~$ ls
colin@colin-laptop:~$ lsusb
Bus 008 Device 005: ID 05ac:1263 Apple, Inc. 
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 004 Device 003: ID 05ca:180a Ricoh Co., Ltd 
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by Ghost175 on 2009-01-25
Im also trying this method but have run into an issue here as well...
[http://ubuntuforums.org/showthread.php?p=6613084#post6613084](http://ubuntuforums.org/showthread.php?p=6613084#post6613084)

whats gcc?
how do i compile?

---

### Post by pytheas22 on 2009-01-25
> was this it,and I thought I used disk utility to change the setup for the ipod to windows but now it doesn't show up in disk utility or when i connect it to Linux o_0

What do you mean?  Did you bring the iPod to a Windows box and try to reformat it for Windows?  Or did you do something else?  What is 'disk utility'?
> 
Im also trying this method but have run into an issue here as well...
[http://ubuntuforums.org/showthread.p...84#post6613084](http://ubuntuforums.org/showthread.p...84#post6613084)

whats gcc?
how do i compile? 

If you want to install gcc, type:
```

sudo apt-get install build-essential
```

But the instructions in that thread you linked to are quite old, and I'd assume that whatever added functionality they provide has been merged into the mainstream build of Amarok by now.  It can't hurt to try, however.  Also, did you say that you CAN transfer files to your iPod using Amarok, but just can't play mp3s in Amarok?  Because if so, it would probably be easy to figure out how to make Amarok play mp3s, and then your problem would be solved.
> 
also is this the output you were looking for?
colin@colin-laptop:~$ ls
colin@colin-laptop:~$ lsusb
Bus 008 Device 005: ID 05ac:1263 Apple, Inc. 

Yes, thanks for that.  Unfortunately I googled for your iPod PCI ID (05ac:1263) and it seems that very few people have used this model on Linux.  The only thread I could find was [one in French]("http://forums.fedora-fr.org/viewtopic.php?id=38036") where the poster ended up using a virtual machine running Windows.  This doesn't mean your device won't work with gtkpod/Rhythmbox/Amarok, it just means that unfortunately no one has figured this out yet.

I think that at this point, your best bet is to bring the iPod to a Windows machine and format it for Windows using iTunes or whichever other software Apple gives you for doing that.  I suspect that it would work then.

---

### Post by Ghost175 on 2009-01-25
What do you mean? Did you bring the iPod to a Windows box and try to reformat it for Windows? Or did you do something else? What is 'disk utility'?

Sorry I mean to say I brought it to a Mac. When I hooked it up to gtkpod it said i had to turn journaling off with disk utility for mac. There is an option to change the formating from Mac OS X Extended (journaled) to Mac OS X Extended but theres no way it seems to make the change permanent. I tried changing the format to what I believed was windows but now it doesnt show up as an ipod on macs or linux. I'm going to try bringing the ipod to a windows pc and formatting it for that but it would be monday until i have acess to a pc. Disk utility is a program to change the settings on connected devices on a mac, although most of the time i dont know what its talking about.

*update* just spent half an hour w/ apple support the Ipod is no being recognized by my MAc and Linux laptops

But the instructions in that thread you linked to are quite old, and I'd assume that whatever added functionality they provide has been merged into the mainstream build of Amarok by now. It can't hurt to try, however. Also, did you say that you CAN transfer files to your iPod using Amarok, but just can't play mp3s in Amarok? Because if so, it would probably be easy to figure out how to make Amarok play mp3s, and then your problem would be solved.

Amarok is unable to read my ipod however, im going ot format it for windows and see if it does.

Also, if anone knows how to have amarok play mp3 that would be useful

Thanks for your help so far I feel like im making progress

---

### Post by Stefanum on 2009-01-26
different from original poster...
have ipod, model a1285 (newest nano version).
music will not move from rythmbox to ipod.  
downloaded gtkpod and asks me to create /media/ipod and initialize ipod, but this ipod version is not one of the options.  
lsusb:
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 005: ID 046d:c70c Logitech, Inc. BT Mini-Receiver (HID proxy mode)
Bus 002 Device 004: ID 046d:c70b Logitech, Inc. BT Mini-Receiver (HID proxy mode)
Bus 002 Device 003: ID 046d:0b02 Logitech, Inc. BT Mini-Receiver (HID proxy mode)
Bus 002 Device 002: ID 413c:8000 Dell Computer Corp. BC02 Bluetooth USB Adapter
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 007: ID 05ac:1263 Apple, Inc. 
Bus 001 Device 005: ID 03f0:3711 Hewlett-Packard PSC 2500
Bus 001 Device 004: ID 0bc2:3001 Seagate RSS LLC 
Bus 001 Device 003: ID 04cc:1521 Philips Semiconductors USB 2.0 Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
ls -l /media:

lrwxrwxrwx 1 root    root     6 2009-01-19 17:18 cdrom -> cdrom0
dr-xr-xr-x 1 root    root  2048 2007-09-22 09:03 cdrom0
drwxrwxrwx 1 root    root  4096 2009-01-22 18:53 FreeAgent Drive
drwx------ 7 stefano root 16384 1969-12-31 19:00 IPOD
drwxr-xr-x 2 root    root  4096 2009-01-24 16:38 usb_hd

Q how to fix?

---

### Post by pytheas22 on 2009-01-26
Stefanum: according to [this page]("http://forums.myspace.com/t/4364132.aspx?fuseaction=forums.viewthread"), that model should work in Songbird, which you can download [here]("http://www.getdeb.net/search.php?keywords=songbird") (for 32-bit Ubuntu)--just save the .deb file to your desktop and double-click to install.

Let us know if that works and is an acceptable solution for you.

Ghost175: have you made any progress?

---

### Post by Ghost175 on 2009-01-27
I was able to format the ipod for windows and it appears on songbird, I am able to put songs on it, but when i remove it resets (gives me the apple logo and asks me to select a lanuage) at this point i might keep passively searching for solutions, hassle apple tech support and if all else fails try to dual boot mac and linux : /

Same Response from Rhythmbox and I can't seem to get it to register in AmaroK. GTKPod had my hopes up but same thing every time it just resets.

---

### Post by pytheas22 on 2009-01-27
Are you unmounting the device before removing it?  You should be able to unmount it through Songbird, gtkpod or Rhythmbox (I believe each of them has an option under a menu somewhere to unmount the device), or through Gnome by right-clicking on the iPod's icon (should be on your desktop) and selecting 'Unmount Volume'.  You can also open a Nautilus folder (for example, your /home folder) and in the left pane of the window, you should see an entry for your iPod.  Click on the triangle to unmount it.

Does unmounting the device first make a difference?

---

### Post by Ghost175 on 2009-02-03
Whether I eject or unmount the ipod still say "connected Eject before disconnecting" then when I do disconnect it, it resets...

---

### Post by pytheas22 on 2009-02-03
I googled an unfortunately couldn't find any more suggestions regarding a solution to this problem.  Is it interfering with your use of the iPod, or is it just annoying but not a serious impediment?

---

### Post by Ghost175 on 2009-02-06
Unfortunately at this point I cant use the ipod at all, that is I can use, as long as there is no data on it. It wipes all the supposed data by resetting the ipod upon disconnect. I can charge my ipod, but thats as for as linux (or should I say apple) functionality will carry the issue. Im going to call apple and at least hassle the customer service rep as to possible solution, im also trying to dual boot windows which should be.. interesting.

---

### Post by pytheas22 on 2009-02-06
Sorry there's not a better solution.  I'm glad that you're going at least to complain to Apple about its refusal to support Linux (which is especially nasty given that so much of OS X was jacked from free-software projects). 

Also keep in mind that you could install Windows inside VirtualBox and configure it for direct access to USB devices--this would allow you to install iTunes in your virtualized Windows system and access the iPod that way.  There are instructions [here]("http://www.ubuntu-unleashed.com/2008/04/howto-install-virtualbox-in-hardy-heron.html") on getting all that set up (they're for Ubuntu 8.04 but should work on 8.10).

---

### Post by Ymse on 2009-04-08
I downloaded and installed Songbird 1.0.0, Build 860 (20081124135530 to my Ubuntu Intrepid, added the add-on for iPods, and everything works! I Just uploaded an album, unplugged the iPod and switched it on, and the music was there, and it played. Didn't have any albumcoverpics though, but that could be my music library, songbird or the plug-in - and it's reallt not that important (at least, not for me).

My iPod Nano is one of the newer (A1285, same as Stefanum), so hopefully it works for older versions too.

I just plugged it right in without doing anything with it beforehand.

*happymonkey*

---

### Post by Glucklich on 2009-05-08
The craziest thing happened to me today. I have a 2º Generation iPod Nano as you can see from the lsub:
> Bus 001 Device 009: ID 05ac:1260 Apple, Inc. iPod Nano 2.Gen

And here's the funny thing about it. I first installed Ubuntu about the same time I joined the forums. After solving my sound problems, one of the first things I wanted to try was the iPod (for obvious reasons). Clicked on Rhythmbox and it was love at first sight. Everything worked perfectly. Now, I just installed the 9.10 version and apparently I cannot transfer songs to the iPod. I already tried gtkpod and it also doesn't work. On Rhythmbox, when I try to transfer a song it says: "Error creating directory: Permission denied." I will try songbird as previously presented as a solution but I wanted to know what caused the malfunction between versions. This one, seems like a Rhythmbox error to me.

Edit: Yep. Songbird works great and looks pretty cool. Rhythmbox just took a step behind for me, until they fix their iPod transfer issue. I hate when they touch on stuff that was already working.

---

### Post by culturejam on 2009-07-31
I ran into the same issue with an older iPod Photo. I tired RhythmBox and Gtkpod with no joy. I installed SongBird, and it alerted me that the problem is that the iPod was formatted for the MacOS filesystem with journaling turned on. It also said that I would need to turn journaling off (or reformat for Windows) to make it work with SongBird.

---

### Post by budbaker44 on 2009-08-01
I don't know if this will help or if you fixed your problem but I have the 2nd gen iPod nano and I installed Banshee music player and plug my iPod right in and it synced right away after the window prompt asking me what I wanted to open my iPod in. Have had no problem sycning or adding or removing playlists or anything. Hope I helped you.

---

### Post by FoolishStar on 2009-12-15
I have the same problem, I think it's because when Ubuntu mounts the device it mounts it with the owner as root and the group root so normal users cannot write to it;

james@orion:~$ ls -al /media/
total 44
drwxr-xr-x  7 root  root   4096 2009-12-15 07:45 .
drwxr-xr-x 21 root  root   4096 2009-12-05 14:12 ..
lrwxrwxrwx  1 root  root      6 2009-12-04 22:03 cdrom -> cdrom0
drwxr-xr-x  2 root  root   4096 2009-12-04 22:03 cdrom0
drwxr-xr-x  2 root  root   4096 2009-12-04 22:03 cdrom1
drwxrwxrwx  1 root  root   8192 2009-12-13 18:44 hdd0
drwxr-xr-x  8 root  root  16384 1970-01-01 01:00 ORION
drwx------  1 james james  4096 2009-12-13 18:44 usb_disk

My Ipod is call 'ORION', if you look at my other usb disk 'usb_disk' you will see that the owner of that is james.james.

I mount my usb_disk the old fashioned way using FSTAB.  Not had chance to try this yet but I'll mount it with FSTAB later and post back here if it allows a normal user to write to it.  

I firmly think it's nothing to do with using another application or GCC, it's just permissions, same as my problem with Ubuntu 9.10

---

### Post by FoolishStar on 2009-12-15
Aye it was added it in fstab and behold!

> james@orion:~$ ls -al /media/
total 44
drwxr-xr-x  7 root  root   4096 2009-12-15 08:16 .
drwxr-xr-x 21 root  root   4096 2009-12-05 14:12 ..
lrwxrwxrwx  1 root  root      6 2009-12-04 22:03 cdrom -> cdrom0
drwxr-xr-x  2 root  root   4096 2009-12-04 22:03 cdrom0
drwxr-xr-x  2 root  root   4096 2009-12-04 22:03 cdrom1
drwxrwxrwx  1 root  root   8192 2009-12-13 18:44 hdd0
drwx------  8 james james 16384 1970-01-01 01:00 ORION
drwx------  1 james james  4096 2009-12-13 18:44 usb_disk

> james@orion:~$ cat /etc/fstab 
# /etc/fstab
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=544c9c60-19dc-4365-ab87-3d68cc1923a8 /               ext4    errors=remount-ro 0       1
/dev/sdb5       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda2       /media/hdd0     ntfs-3g defaults,en_GB.UTF-8    0       0
/dev/sdh1       /media/usb_disk	ntfs-3g defaults,en_GB.UTF-8	0	0
/dev/sdj2       /media/ORION	ntfs-3g defaults,en_GB.UTF-8	0	0

I did this by firstly plugging in my ipod.  Then I ran 'dmesg | tail' from a terminal, that outputted;

> james@orion:~$ dmesg | tail
[49638.093431] sd 7:0:0:0: [sdj] Mode Sense: 68 00 00 08
[49638.093434] sd 7:0:0:0: [sdj] Assuming drive cache: write through
[49638.094925] sd 7:0:0:0: [sdj] 14651280 2048-byte logical blocks: (30.0 GB/27.9 GiB)
[49638.096049] sd 7:0:0:0: [sdj] Assuming drive cache: write through
[49638.096053]  sdj: sdj1 sdj2
[49638.139126] sd 7:0:0:0: [sdj] 14651280 2048-byte logical blocks: (30.0 GB/27.9 GiB)
[49638.141679] sd 7:0:0:0: [sdj] Assuming drive cache: write through
[49638.141687] sd 7:0:0:0: [sdj] Attached SCSI removable disk
[49639.452828] FAT: invalid media value (0x2f)
[49639.452835] VFS: Can't find a valid FAT filesystem on dev sdj1.

Which gave me the clue that the actual device was from '/dev/sdj' so I was looking for that from the next command;

> james@orion:~$ mount
/dev/sdb1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/sda2 on /media/hdd0 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/james/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=james)
/dev/sdc1 on /media/usb_disk type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
**/dev/sdj2 on /media/ORION type vfat **(rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)

As you can see, Ubuntu mounted /dev/sda2 on /media/ORION so I added the following to my FSTAB file in /etc

> /dev/sdj2       /media/ORION	ntfs-3g defaults,en_GB.UTF-8	0	0

---

### Post by dentman on 2010-03-31
Dude
 Sudo Rhythmbox

It opens and you can copy files to your crappy Apple mp3 player.

---

### Post by andy1964 on 2010-03-31
I have a 3rd generation iPod (30GB x8484 model) and had this exact problem with mine when I switched to 9.10 Karmic six weeks ago.
Here's how I fixed it:-
 
1, go back to iTunes on a windows OS (either your own or anyone else with it on their windoze machine. 
2, On the options screen for the iPod, click 'Manual data usage' on the main option for the iPod.
3, Close iTunes and remove you iPod. Destroy the windoze box (only joking....)
4, Go back to your Linux machine.
5, Launch Rhythmbox (should do this automatically as soon as your iPod mounts onto the desktop ).
6, Import the music file into Rhythmbox (File >>> Import).
7, Go to the music folder in the LHS bar of Rhythmbox. You should now see the music file you've just imported.
8, Drag and drop this onto the iPod folder on the LHS screen of Rhythmbox. If you're eagle-eyed, you may even see the transfer bar flash up on the bottom RHS of Rhythmbox).
9, Eject the iPod. (File >>> Eject)
10, You should have the track on you iPod now.
 
I've done similar operations with podcasts.
Haven't been able to work out syncing yet so am manually manage this. I find it not a great problem, however, as I tend to only add music to the iPod and add/subtract podcasts.
 
Hope it works
Cheers
Andy

---

### Post by yichuan on 2010-04-11
Above method doesn't work for me. That exactly what I used to do. But now, after I unintalled pulse and installed gnome-alsamixer, I got "permission denied" when dragging files in my rythmbox lib to ipod.

Also, banshee and pod-gtk doesn't work, they will not detect my ipod device(old version maybe?).

sudo rhythmbox doesn't work,ipod will not be detected in sudo mode of rhythmbox, but it shows in normal connection as mentioned above.

Songbird doesn't work, it will no longer provide pod device service for now. Some one replied me with that.

FoolishStar's post is similar to the problem I have, I don't want to try his solution since I don't think I'm good enough to mess around os files...

Any additional advice will be helpful.

---

### Post by pytheas22 on 2010-04-11
> Above method doesn't work for me. That exactly what I used to do. But now, after I unintalled pulse and installed gnome-alsamixer, I got "permission denied" when dragging files in my rythmbox lib to ipod.

Also, banshee and pod-gtk doesn't work, they will not detect my ipod device(old version maybe?).

sudo rhythmbox doesn't work,ipod will not be detected in sudo mode of rhythmbox, but it shows in normal connection as mentioned above.

Songbird doesn't work, it will no longer provide pod device service for now. Some one replied me with that.

FoolishStar's post is similar to the problem I have, I don't want to try his solution since I don't think I'm good enough to mess around os files...

Any additional advice will be helpful.

What's the device ID for your iPod?  If you don't know, post the output of this command (with the iPod plugged into the computer):
```

lsusb
```

With the device ID, we can google to see if others have experienced trouble with this particular model on Ubuntu.

---

### Post by yichuan on 2010-04-12
here is the output:
Bus 002 Device 004: ID 05ac:120a Apple, Inc. iPod Nano


and I think I get rhythm box working...
1) eject ipod from rhythmbox (it should auto detect ipod when plugin)
2) reinsert ipod. My rhythm box will crash with no alert msg.
3) try open rhytmbox again. Now file transmission works, no permission error.

and sadly, everytime transfer a music will be painful process.

---

### Post by pytheas22 on 2010-04-12
Please post the output of these commands when you plug the iPod in the first time (i.e., when it is NOT working with Rhythmbox):
```

mount
ls -lhR /media
dmesg | tail -30
```

Then, unplug and replug the iPod, as you need to do to get it working with Rhythmbox, and then please run those commands a second time and post the output.

That should help figure out what's changing with the permissions.

Also, you could try using Songbird, another music player that sometimes works better with iPods.  You can install it using the instructions at [https://help.ubuntu.com/community/Songbird](https://help.ubuntu.com/community/Songbird).

---

### Post by lunallena on 2010-05-05
Hi Guys...I can now transfer music from Rhythmbox to my iPod.

These post are pretty old for the most part but I was having problems transferring my mp3s to my new iPod (Classic 160gb) within Rhythmbox so I came to check them out.  I kept getting the classic "Read-only file system" error every time I tried moving music to my iPod.  I WAS however able to transfer a few podcasts from my iPod to my computer (I had previously placed those podcasts in my iPod from a friend's Mac).  

In the end, I decided to take my iPod to a friend's PC.  I restored my iPod to fit Windows iTunes through his PC and had him load some music onto my iPod.  When I came home to my Linux laptop and loaded my iPod on Rhythmbox not only did I see the songs my friend had transfered over into my iPod, but I could successfully transfer songs from my computer to my iPod and vice-versa.  (I haven't ejected the iPod yet, so I haven't checked to see if I'll be able to listen to the songs but everything seems promising so far).  

Moral of the story, use a friend's Windows PC to restore your iPod and, after that, you should be able to transfer songs from your computer to your iPod within Rhythmbox..AND Vice-versa, not like in fascist iTunes! :) 

En español- Si estas teniendo problemas en transferir musica de Rhythmbox a tu iPod, mi solucion fue la siguiente:  por medio de una PC (Windows) que tenga iTunes restaura tu iPod y transfiere un par de canciones (o todas las que gustes); despues de esta accion, monta tu iPod al Rhythmbox y veras que podras transferir musica de Rhythmbox a tu iPod.  ¡Suerte!     ):P

---

### Post by TheHitman2010 on 2010-05-05
"Well itunes and rhythmbox are not going to be exactly alike, its the  ipod that matters here.
More modern ipods wont work with linux, because apple hates us though  steals things from us and rebrands it as their own.
If this is a new ipod, you are not in luck."

Which is funny - they'd rather Windows have access to their software? Weird.

---

### Post by notbitmonk on 2010-06-17
I found old ipod (2nd gen I think) which I gave to my daughter.  I was able to read and then delete the music in it.  I tried adding files to it with no luck.  My music files are all FLAC that I rip from my Cds.  I bought the Fluendo codecs and then installed LAME.  That means that I didn't install the Ubuntu restricted extras.  I have noticed that for several versions of Ubuntu, Rhythmbox will not let you select mp3 as a rippable format if the restricted extras are not installed.  I have done this over 20 times and the result is always the same.  I can install LAME but to actually have mp3 encoding support in Rhythmbox, you have to install the restricted extras.  I do not want to install the restricted extras.  Does anyone know what happens during the restricted extras installation that makes Rhythmbox encode to mp3?

---

### Post by pytheas22 on 2010-06-17
notbitmonk: I wish I could help but I have no expertise in that area.  Are you sure the codecs from Fluendo actually support encoding mp3s as well as decoding?  Could you maybe use another application for this purpose, such as Avidemux?

In any case, you'd probably find a better informed answer in the Multimedia & Video subforum.

---

### Post by notbitmonk on 2010-06-18
Fluendo codecs do not encode. Since I have the Fluendo codecs to decode I did not need the restricted extras to perform anything.  The main digital music player was a Sansa Clip and that one is able to play FLAC and ogg so the need to transfer mp3s to a player was not there.  I installed LAME to use with Audacity in converting some of the songs in ringtones for my phone.  I just find Rhythbox behavior a bit odd.  I'll do as you say and ask in Multimedia section.

---

### Post by aurisel on 2010-06-24
> **notbitmonk said:**
> [...] I have noticed that for several versions of Ubuntu, Rhythmbox will not let you select mp3 as a rippable format if the restricted extras are not installed. [...] I do not want to install the restricted extras.  Does anyone know what happens during the restricted extras installation that makes Rhythmbox encode to mp3?
I found myself in this exact situation today. I believe that the required package is this:

gstreamer0.10-plugins-ugly-multiverse

This is one of the packages included in ubuntu-restricted-extras. After installing it, closing Rhythmbox, and reopening Rhythmbox, I was able to select MP3 in order to CD tracks to an iPod Photo. (Sonic Adventure 2 Birthday Pack Extra Sound CD; Happy 19th, Sonic! :KS)

Certainly, installing ubuntu-restricted-extras would make practically anything I wanted to work, work. It's just that I want to keep tabs on what's in my system, and for example, I already have Flash installed in ~/.mozilla/plugins/ -- I don't want to install whatever is in the repositories, system-wide.

I kind of don't like how gstreamer0.10-plugins-ugly-multiverse installs libx264, but, it doesn't mean that I need to use it. Viva la WebM? :p

I hope this helps someone.

---

### Post by maghreb on 2010-08-17
Sorry to revive an old thread, but after looking on google for some time and reading what was said here (no answer really), i found an answer to my "error transferring track: permission denied" problem while copying tracks to ipod.

FoolishStar page #3 post #27-#28 nailed it down, but code to add to /etc/fstab was.. well... incorrect. ;)

I found a working (for me) answer here:

[http://davesource.com/Solutions/20080225.iPod-linux-read-only.html](http://davesource.com/Solutions/20080225.iPod-linux-read-only.html)

For the lazy or in case of link failure, I'll write it here.

After finding how to get UUID of ipod (on Karmic) 
```
ls -l /dev/disk/by-uuid
```I added an entry to /etc/fstab:

```
UUID=DEVICE_UUID_HERE      /media/iPod     auto  rw,user,noauto  0   0
```

*You want to use UUID because /dev/sdX is not constant and may change when pluging other devices.

Then created the mount point:
```
mkdir /media/iPod
```Safely removing ipod the reconnecting it and Voilà!

hope it helps!

mag

---

### Post by chslaxcoach on 2010-11-27
After reading this thread and quite a few others, this link saved the day.  I was getting in my dmesg


[HTML]
<code>hfs: write access to a journaled filesystem is not supported, use the force option at your own risk, mounting read-only.
</code>
[/HTML]
Connect your iPod up to a Mac (if you have one), open a terminal, and do:

[HTML]
<code>
$diskutil disableJournal /Volumes/NAME_OF_IPOD
</code>
[/HTML]


This saved me and a few others.  Check out this
[https://bbs.archlinux.org/viewtopic.php?id=92977](https://bbs.archlinux.org/viewtopic.php?id=92977)

---

