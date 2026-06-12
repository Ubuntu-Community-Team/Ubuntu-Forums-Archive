---
title: "How do you open an iMac floppy in Ubuntu?.."
date: 2009-03-03
forum: New to Ubuntu
---

### Post by DonaldJ on 2009-03-03
I'm trying to open a floppy...

I tried the codes in thread:   [http://ubuntuforums.org/showthread.php?t=1079745&highlight=open+floppy+ubuntu](http://ubuntuforums.org/showthread.php?t=1079745&highlight=open+floppy+ubuntu)


floppy is /dev/fd0 on my computer. The way I had to get mine to work was go to the /media folder and create a folder floppy0

Code:

cd /media
sudo mkdir floppy0

then I edited my fstab

Code:

sudo gedit /etc/fstab

and added this at the end

Code:

/dev/fd0 	/media/floppy0	auto	rw,auto,user,exec,sync	0	0

after that, you should be able to mount it like any other drive.

Code:

sudo mount /dev/fd0

_____________________


It got "floppy0" into the media file..  but floppy no work...


_____________________________________________________________________________



I tried the codes in:  [http://ubuntuforums.org/showthread.php?t=1066394&highlight=open+floppy+ubuntu](http://ubuntuforums.org/showthread.php?t=1066394&highlight=open+floppy+ubuntu)


You need to check a few things... open Applications --> Accessories --> Terminal and then type the following:
Code:

ls /media

If there is a directory listing for "floppy0" then you should be all set, otherwise, execute the following command:
Code:

sudo mkdir /media/floppy0

Next, you need to execute the following command:
Code:

gksudo gedit /etc/fstab

See if there is an entry for your floppy drive. I'm pretty sure that there is not. If there IS, edit it to look like the following line. If it is not there at all, add the following line to the end of the file:
Code:

# Floppy Drive
/dev/fd0     /media/floppy0     auto     rw,user,noauto,exec,utf8    0  0

You shouldn't have to do anything else. You should now be able to use your floppy.

_______________________________________________________


Still floppy no work...

_______________________________________________________


Don't think I'll try this one yet:
  [http://ubuntuforums.org/showthread.php?t=1075648&highlight=open+floppy+ubuntu](http://ubuntuforums.org/showthread.php?t=1075648&highlight=open+floppy+ubuntu)

_______________________________________________________


How do you get a floppy to work in Ubuntu..?
I know they are obsolete, and inefficient, and not worth the effort.. but we need to get out of them what's in hundreds of them...  They were done with an iMac...

---

### Post by handy on 2009-03-03
I'm not sure how successfully Linux can read Apple's HFS & HFS+ file systems. 

If you find you can't get at the floppy's, try transferring the data onto a USB key, or emailing the data to yourself.

---

### Post by RealG187 on 2009-03-03
I have a program that reads Mac Disks, but it's for Windows. Not sure if Wine could access a floppy at file system level, although I did use Wine to access my DVD Burner at the hardware level by using the autodetect option in the drives tab of Winecfg...

---

### Post by ashwinhgtx on 2009-03-03
Try installing the hfsplus and hfsutils packages through Synaptic. They should provide you read write access to HFS formatted volumes.

---

### Post by DonaldJ on 2009-03-03
That makes some sense...  "Wine, and a floppy software, and a mac to windows converter"...

Does Wine work with Mac?.. or is there a Mac-OS go-between, like Wine is for Windows..?

Ummm..  Wine for Windows... "Mine for Mac"..?  

["W-in-ebuntu.. M-in-ebuntu.."]

---

### Post by DonaldJ on 2009-03-03
I tried "hfsplus and hfsutils", but no success, yet...

Maybe I should reboot, and try some of the codes I found in the other threads to open a floppy, now that I've got floppy files..?

---

### Post by yther on 2009-03-03
Linux can read HFS floppies just fine.  The trick is in telling it what to expect.  Assuming /media/floppy0 exists, have you tried this?

```
mount -t hfs /dev/fd0 /media/floppy0
```

The "hfs" kernel module (the bit that handles the Mac filesystem) is installed on my system, and I didn't go out of my way to get it, so it must be part of the default set.  (Type "locate hfs | grep ko" to see; you should have **hfs** and **hfsplus** modules somewhere.)  Given that, no extra tools should be necessary to read and write Mac floppies (or hard drives).

The **hfstools** and utilities would be useful if you need to *create* Mac filesystems, such as making a new Mac disk.

Using the above, I have retrieved Mac files from lots of disks, although I no longer have any around.  You will probably lose the "Mac magic" ("resource fork" in Mac speak) that tells it what kind of files they are, but you will find a similar magic on Linux.  ;)

If the mount line above works, then you can add a line in **fstab** with "hfs" as the type, for auto-mounting.  If it doesn't work, try "hfsplus" as the type instead.

---

### Post by handy on 2009-03-03
Thanks for your valuable post yther.

---

### Post by DonaldJ on 2009-03-03
> **yther said:**
> Linux can read HFS floppies just fine.  The trick is in telling it what to expect.  Assuming /media/floppy0 exists, have you tried this?

```
mount -t hfs /dev/fd0 /media/floppy0
```

The "hfs" kernel module (the bit that handles the Mac filesystem) is installed on my system, and I didn't go out of my way to get it, so it must be part of the default set.  (Type "locate hfs | grep ko" to see; you should have **hfs** and **hfsplus** modules somewhere.)  Given that, no extra tools should be necessary to read and write Mac floppies (or hard drives).

The **hfstools** and utilities would be useful if you need to *create* Mac filesystems, such as making a new Mac disk.

Using the above, I have retrieved Mac files from lots of disks, although I no longer have any around.  You will probably lose the "Mac magic" ("resource fork" in Mac speak) that tells it what kind of files they are, but you will find a similar magic on Linux.  ;)

If the mount line above works, then you can add a line in **fstab** with "hfs" as the type, for auto-mounting.  If it doesn't work, try "hfsplus" as the type instead.



Thanks

I can't find where to place that code..?  
I've been running Ubuntu almost a month...  
When I place it in Terminal, it says "only root can do that", or "command not found"...  When I go to user and "change to root", I still can't make that code do anything.. if I actually did change to root, which I doubt..?  How do you run that code/command?..

---

### Post by egalvan on 2009-03-03
> **DonaldJ said:**
>   
When I place it in Terminal, it says "only root can do that", or "command not found"...  When I go to user and "change to root", I still can't make that code do anything.. if I actually did change to root, which I doubt..?  How do you run that code/command?..

To run a terminal command as "root", put  "sudo" in front of it...

```
sudo mount -t hfs /dev/fd0 /media/floppy0
```

it will ask for the password...
type in your password (the one you use to log in with)
note that nothing will show, not  *** or ### or anything to indicate you are typing... I guess this is to keep folks from counting the characters...

use 'gksudo' to run graphical programs, such as 'gedit'

```
gksudo gedit /boot/grub/menu.lst
```

Good luck

And no, Ubuntu does not easily allow a root log-in...
if you need to ask how, you probably should not be using it.
sudo will do (almost) all you need.

---

### Post by DonaldJ on 2009-03-03
After:  "sudo mount -t hfs /dev/fd0 /media/floppy0"

I get:  "mount: special device /dev/fd0 does not exist"

But I do have "Floppy0" in Media File..  but it's empty...

And in Mnt File I have "Floppy".. it's empty too...

---

### Post by yther on 2009-03-03
> mount: special device /dev/fd0 [COLOR="Red"]does not exist[/COLOR]

Now we're getting somewhere... no /dev/fd0 means your system doesn't recognize that you have a floppy drive... or (remotely possibly) it's calling the floppy drive something else.  I don't even *have* a floppy drive on my machines here, so it'd be hard to test.  :(

I was unable to tell from your first post (due to lack of quoting, or other means of separating your words from the words of others) if you ever got your drive to work.  Just for kicks, if you do "ls /dev/fd*" does anything come back?

Is your floppy drive built into your box, or external, such as a USB device?  If it's built in, have you checked the physical connections inside&#8212;ribbon cable and power?  Is the drive enabled in your BIOS?  When you insert a disk, it should make a few sounds as it recognizes the disk, and if your drive has a light, it may come on briefly.  Does any of that happen?  (If it's USB, basically the same questions, though it's much less of a pain to check the physical connections in that case.)

Normally, the device subsystem should create a "node" in /dev/ for the floppy drive, if it detects that you have one.  For internal drives, this happens during boot.  For external drives, it should be created when you plug the device in.  If it's not there, that indicates some other problem.

Another question (just in case):  Are you running the stock Ubuntu kernel, or did you compile your own?

---

### Post by DonaldJ on 2009-03-03
Ran:  "ls /dev/fd"

I get: bright baby-blue numbers: "0 1 2 3"

_________________


Floppy is built into the tower: Compaq Presario, P3, 500 RAM, 80-gig...

Connections are good..  it installed W2000 boot floppies from it, last time I ran windows...  And should I reboot Ubuntu with a floppy, it asks to remove it and hit any key...

Nothing happens when I push in a floppy...

It's stock Ubuntu...  No changes...  I wouldn't know how to change it...

---

### Post by yther on 2009-03-03
OK, I checked my /dev and it in fact has a directory called "fd" just like you do.  Rummaging in my closet, I found an old USB floppy/SuperDisk drive and plugged it in... unfortunately, it is recognized as a mass storage device and therefore became /dev/sde.  No help there.

What happens if you do "sudo modprobe floppy"?

***EDIT***

If you suddenly have a /dev/fd0 after that, you can edit /etc/modules (using sudo of course) and add "floppy" on a line by itself, so that the module will be automatically loaded when you start up.  I don't know why it's not there to begin with, but this seems to be a common problem [dating back a couple of years]("http://www.google.com/search?q=ubuntu+dev+floppy").

---

### Post by RealG187 on 2009-03-03
> **DonaldJ said:**
> Does Wine work with Mac?.. or is there a Mac-OS go-between, like Wine is for Windows..?
["W-in-ebuntu.. M-in-ebuntu.."]

I think there is a program called DarWine...

---

### Post by DonaldJ on 2009-03-04
> **yther said:**
> OK, I checked my /dev and it in fact has a directory called "fd" just like you do.  Rummaging in my closet, I found an old USB floppy/SuperDisk drive and plugged it in... unfortunately, it is recognized as a mass storage device and therefore became /dev/sde.  No help there.

What happens if you do "sudo modprobe floppy"?




Nothing...

I'm guessing I need to place something into the "Floppy0" file...  Maybe a driver, or a something or other..?

Can I set the flash drive mount to see the floppy?..

I'm gonna look-see if DarWine is available... and try everything till I gets it working...

________________________

Ohhh  this is a weird one!..

I figured I'd try your suggestion again, and I copied ""sudo modprobe floppy" ..  but I hadn't noticed that I had failed to highlight the "S"..  I ran "udo modprobe floppy", and it installed "udo"..  then I clicked Floppy, and it read through the floppy, but I got a pop-up that said it couldn't mount..  but now I've got a floppy icon in the Media file...
computer:///Floppy%20Drive.drive
computer:///CD-RW%5CDVD%C2%B1RW%20Drive.drive
computer:///root.link

It's getting closer...

---

### Post by DonaldJ on 2009-03-04
sudo modprobe floppy
[sudo] password for x:
sudo mount -t hfs /dev/fd0 /media/floppy0
mount: /dev/fd0 already mounted or /media/floppy0 busy
mount: according to mtab, /dev/fd0 is already mounted on /media/floppy0


Holy geepers!  it worked!..  and it's an iMac floppy yet...

/media/floppy0/!introto.pla/resource.frk
/media/floppy0/!introto.pla/!angels&.pla
/media/floppy0/!introto.pla/finder.dat
/media/floppy0/!introto.pla/!gabriel.&mi
/media/floppy0/!introto.pla/!insidep.la0
/media/floppy0/!introto.pla/!insidep.lat
/media/floppy0/!introto.pla/!introdu.cti
/media/floppy0/!introto.pla/!platoni.cs0
/media/floppy0/!introto.pla/!platoni.cso
/media/floppy0/!introto.pla/!plato's.sub

But I can't read most of it, yet..  and now I can't get it to open another floppy, a window's floppy...
I suppose I need to delete the last floppy data from the OS..?

---

### Post by yther on 2009-03-04
> **DonaldJ said:**
> Holy geepers!  it worked!..  and it's an iMac floppy yet...

/media/floppy0/!introto.pla/resource.frk
...[snip]...

But I can't read most of it, yet..  and now I can't get it to open another floppy, a window's floppy...
I suppose I need to delete the last floppy data from the OS..?

You shouldn't need to delete anything.  Do "sudo umount /media/floppy0" to safely remove the disk... or, if some icon for the disk appears on your desktop or file manager (it's in /media, so that might happen), you can use point-and-click methods to unmount it.  (Note that the terminal command is "**u**mount"&#8212;no letter N&#8212;and not "unmount".)

BTW, I'm guessing you got that "already mounted" message due to some automatic process helpfully mounting the disk for you, but I'm not sure.

If you put a line in /etc/fstab like the following, it *should* allow you to mount/umount without resorting to **sudo**.

```
/dev/fd0  /media/floppy0  hfs,users,noauto  0 0
```

It may be a chore going through those Mac disks and trying to recover your old files, but&#8212;assuming you know what created them in the first place&#8212;it shouldn't be that tough unless they are in weird formats.  (Your listing there looks about like what I remember from the few Mac floppies I had to deal with.)

Good luck!  :KS

---

### Post by DonaldJ on 2009-03-04
/dev/fd0  /media/floppy0  hfs,users,noauto  0 0bash: /dev/fd0: Permission denied

_________________


Click the floppy icon in the side panel, and the floppy mounts, both iMac and Windows floppies...
Rght-click>unmount, unmounts it...  but it can't read most of the files...  I suppose I need a bunch of commands to open various breeds of files...

---

### Post by yther on 2009-03-04
> **DonaldJ said:**
> /dev/fd0  /media/floppy0  hfs,users,noauto  0 0
bash: /dev/fd0: Permission denied

_________________


Click the floppy icon in the side panel, and the floppy mounts, both iMac and Windows floppies...
Rght-click>unmount, unmounts it...  but it can't read most of the files...  I suppose I need a bunch of commands to open various breeds of files...

You don't run that line as a command, you put it in **/etc/fstab**.  There should be similar-looking lines in there already for your other drives.  

Yeah, I'm sure you'll need to do some digging to figure out how to get what you need out of those Mac files.  If they are word-processing types of files, try throwing them at OpenOffice.  For graphics, try GIMP.  For I-got-no-clue-what-this-is, try this in a terminal:

```
file /media/floppy0/whatever/weird_file.wtf
```

The **file** command will examine some characteristics of the file and print a line or two about it.  This may give you a hint about how to proceed.

That's about it for me.  I'm glad we got your floppy sorted out, now have fun sorting those old files!  ;)  Good night and I'm out!

---

### Post by DonaldJ on 2009-03-04
Forgive my ignorance...   What is:  "/etc/fstab"?   I've looked all over the place for it..?

__________________


I insert a Window's floppy, and everything works.. but I do get ALL the character encodings... Is there a way to open those items from floppy without getting all the coding mess in your face..?

I installed "Darwine"..  It helped a tiny bit to open a few Apple items...
It seems I need Linux's version of Quark Express...

---

### Post by egalvan on 2009-03-04
My fstab for the internal floppy drive:

```
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
```

Might be of help.

ErnestG

---

### Post by DonaldJ on 2009-03-04
I don't know how to use that code, yet..?

______________


On reboot I lost all the floppy icons.. Now it's back to square-one...

______________


I got the icons back with a couple commands in this thread...  
How do I make the icons stay in the system after reboots?..

[Seems udo didn't help to set the icons, though it did seem to speed up Ubuntu a little... I wonders if udo makes an OS more susceptible to covert Net damage, given that it is sort of "wormyish"..?]

---

