---
title: "USB autorun"
date: 2011-09-04
forum: New to Ubuntu
---

### Post by hookitup on 2011-09-04
Hellp ppl, 

so i got this 1gb usb from a friend and i deleted everything on it but it seems a locked down auto run feature thing is still on it, as soon as u plug it in it runs a website, how do i go about removing this , any good programs to use, i tried going to gparted and formatting it thinking it will erase everything but apparently not,, any suggestions ?

---

### Post by snip3r8 on 2011-09-04
Why not just format the drive

---

### Post by hookitup on 2011-09-04
i believe i did, useing gparted ,,, i selected the device on the top right then said create new partition table then i got this warning saying "This will ERASE ALL DATA on the entire disk".

---

### Post by snip3r8 on 2011-09-04
> **hookitup said:**
> i believe i did, useing gparted ,,, i selected the device on the top right then said create new partition table then i got this warning saying "This will ERASE ALL DATA on the entire disk".

did you click apply?

---

### Post by hookitup on 2011-09-04
yes !!!, and the damn autorun is still there,

---

### Post by snip3r8 on 2011-09-04
> **hookitup said:**
> yes !!!, and the damn autorun is still there,
Run 
```
ls -a
```
on the flash drive and post the output

---

### Post by hookitup on 2011-09-04
ok so when the usb is inserted two things pop up one is a read only file
 (/media/20110121_1203)


and the other is read-write
 (/media/3D06-2429)

Here is the outcome of ls -a on both 
```
dark@darkmyth:/media/3D06-2429$ ls -a
.  ..  .Trash-1000
dark@darkmyth:/media/3D06-2429$ cd /media/20110121_1203
dark@darkmyth:/media/20110121_1203$ ls -a
.  ..  autorun.inf  laucher.exe
dark@darkmyth:/media/20110121_1203$ 

```

---

### Post by snip3r8 on 2011-09-04
> **hookitup said:**
> ok so when the usb is inserted two things pop up one is a read only file
 (/media/20110121_1203)


and the other is read-write
 (/media/3D06-2429)

Here is the outcome of ls -a on both 
```
dark@darkmyth:/media/3D06-2429$ ls -a
.  ..  .Trash-1000
dark@darkmyth:/media/3D06-2429$ cd /media/20110121_1203
dark@darkmyth:/media/20110121_1203$ ls -a
.  ..  autorun.inf  laucher.exe
dark@darkmyth:/media/20110121_1203$ 

```

now try ```
sudo rm *
``` in the flash drive directory (**careful with this command**)

---

### Post by hookitup on 2011-09-04
i guess my friend said he got it in a surf magazine in the mail , and it takes you straight to there web sight ,,, its dumb and a waste of space ,, need to remove this thing

---

### Post by alegomaster on 2011-09-04
> **snip3r8 said:**
> now try ```
sudo rm *
``` in the flash drive directory (**careful with this command**)

I just want to refer to one part 

> **snip3r8 said:**
>  **careful with this command **

Make sure it is in the usb directory or _**else**_ it might ruin your entire system

---

### Post by gordintoronto on 2011-09-04
When the flash drive is inserted, open Accessories/Terminal and enter this command:
lsusb

You will get several lines of output, and I *think* two of them will be for your flash drive. One of them might look a bit like this:
Bus 002 Device 003: ID 13fe:3400 Kingston Technology Company Inc. 

The other might look like a CD drive!

The most useful information looks useless, the nine characters which follow "ID". You can Google them, and usually learn more about the device.

The other command you might try is:
sudo fdisk -l
which might show you that there is an unexpected storage "device."

If you think this type of flash drive is annoying for Linux users, you wouldn't believe how much mischief they can cause for Windows users...

---

### Post by 3rdalbum on 2011-09-05
Getting rid of the actual file that causes this is somewhere between "difficult" and "impossible"; it depends on the drive. Merely reformatting won't work because there's hardware inside the drive causing the file to be protected. As I understand it, it's actually a virtual partition.

Although you can't remove the virtual partition without a soldering iron, you can stop the 'autorun' from happening on your Linux computer.

Install the "gconf-tools" package, if it isn't already installed. Go to the terminal and type "gconf-editor". Browse in this window to /apps/nautilus/preferences and check the "media_autorun_never" checkbox in the right pane.

This stops autorun from happening on your discs, but there's no real loss; it's rare to find an autorun that's useful on Linux, and it's also a potential security hole on Linux and Windows.

---

### Post by PatrickD-52761 on 2011-09-05
> **3rdalbum said:**
> Getting rid of the actual file that causes this is somewhere between "difficult" and "impossible"; it depends on the drive. Merely reformatting won't work because there's hardware inside the drive causing the file to be protected. As I understand it, it's actually a virtual partition.

Although you can't remove the virtual partition without a soldering iron, you can stop the 'autorun' from happening on your Linux computer.

Install the "gconf-tools" package, if it isn't already installed. Go to the terminal and type "gconf-editor". Browse in this window to /apps/nautilus/preferences and check the "media_autorun_never" checkbox in the right pane.

This stops autorun from happening on your discs, but there's no real loss; it's rare to find an autorun that's useful on Linux, and it's also a potential security hole on Linux and Windows.

I would agree with you on this. SanDisk does this with their Cruzer Micro USB drives also. They mount an autorun, which (when plugged into a Windows drive) will open the U3 Launchpad. It makes them annoying to use on Windows and Linux. 

I'll have to try the gconf-editor route also (although I don't have an issue with the autoruns per se).  But, I wanted to pass that tidbit about different USB Drives having the "virtual partition" installed, for other people with other brands of USB drives.

Have a great weekend:)
Patrick.

---

### Post by hookitup on 2011-09-05
> **snip3r8 said:**
> now try ```
sudo rm *
``` in the flash drive directory (**careful with this command**)

just tried sudo rm * and this was the outcome :(

```
dark@darkmyth:~$ cd /media/20110121_1203
dark@darkmyth:/media/20110121_1203$ sudo rm *
[sudo] password for dark: 
rm: cannot remove `autorun.inf': Read-only file system
rm: cannot remove `laucher.exe': Read-only file system
dark@darkmyth:/media/20110121_1203$ 

```

---

### Post by alegomaster on 2011-09-05
I think chmod might help here. I have no clue if it will work in this situation. You could try out using chmod. I can't tell you any commands now, but I might be able to later.

Also mark the thread as solved when it is solved.

---

### Post by ubun2geek on 2011-09-05
Did you right-click and format?

---

### Post by linuxman94 on 2011-09-05
Is this a sandisk drive?  If so that stuff would be the u3 junk.  You'll have to use this program from windows to get rid of it.

[U3 removal tool]("http://www.softpedia.com/get/Tweak/Uninstallers/U3-Launchpad-Removal-Tool.shtml")

---

### Post by 3rdalbum on 2011-09-05
> **OpenOffice.org said:**
> Did you right-click and format?

It won't do anything. As I've already explained, the virtual partition is protected in hardware. Without a soldering iron, you can't remove it.

---

### Post by hookitup on 2011-09-06
there is nothing about formatting it and also no it is not a san disk ,, just a random freebeee i got that has an embedded .inf files to take me to there website. which is annoying for my ubunut machine but super annoying for my windows machine.  

linuxman94: do you think the u3 removal will work for this ?

---

### Post by bmbaker on 2011-09-06
i was just looking for similar information on how to stop usb/harddrives from opening up in nautilus, when i tried to chage it in gconf it just say no schema!
does anyone know another way to to do this?
cheers

hmmm just remembered dconf does it now :-)

---

### Post by linuxman94 on 2011-09-06
> **hookitup said:**
> there is nothing about formatting it and also no it is not a san disk ,, just a random freebeee i got that has an embedded .inf files to take me to there website. which is annoying for my ubunut machine but super annoying for my windows machine.  

linuxman94: do you think the u3 removal will work for this ?

No if it's not a sandisk it won't work.  What brand is it?

---

### Post by hookitup on 2011-09-09
no and idk its like a surf company , thats why they have this annoying auto run on it so it brings you to there sight.

---

