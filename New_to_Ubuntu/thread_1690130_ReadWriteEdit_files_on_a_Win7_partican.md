---
title: "Read/Write/Edit files on a Win7 partican"
date: 2011-02-17
forum: New to Ubuntu
---

### Post by Curisu on 2011-02-17
Installed Ubuntu 10.10 a few days ago and I've been having trouble getting permissions to read/write/edit files on my Win7 partican. Whenever I click into my hard drive with the Win7 stuff on it, I can view the files, I can copy/paste the files into my Ubuntu 10.10 partican, but I cannot edit, write, or change permissions on any files that are in my Win7 partican which makes opening my .exe files via Wine quite a pain.

When I try to click "Allow Executing file as program" under Properties->Permissions in the Win7 partican while on my Ubuntu OS it will just simply not let me put a check mark in the box.

I've read the guide for allowing edit/read/write for NTFS particans and have done what it has said there but that didn't seem to help either(I may of done it wrong since I'm new with Ubuntu).

As far as how I installed Ubuntu 10.10, I used "ubuntu-10.10-desktop-amd64.iso". I made the installer on a removable USB drive and installed Ubuntu 10.10 on a 500GB external hard drive and left my computer set to run off Ubuntu on my external before it even tried to run off my internal(which has my Win7 stuff in it). I made "/"(100GB) and "swap"(10GB) particans on this external.

I would just simply like to be able to edit/write/change permissions so my I can access my programs on my Win7 partican while I am on my Ubuntu partican so I don't have to copy/paste files all over my computer. Thanks for any help that can be given and if any more information is needed, please just let me know and I'll get the info in ASAP.

---

### Post by lightningfox on 2011-02-17
Try the steps in these articles and see if it works

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[http://www.ehow.com/how_6943148_mount-ntfs-partition-ubuntu.html](http://www.ehow.com/how_6943148_mount-ntfs-partition-ubuntu.html)

---

### Post by Curisu on 2011-02-17
Well tried to do NTFS Config Tool but for some reason it seems to not want to stay open(says its opening and then it just auto closes; Thinking it may be a 32 bit vs 64 bit thing).

As for mounting my Win7 partican, I mounted it and was able to mark Folders as "Allow Executing file as program", but I am not able to set "Allow Executing file as program" on any of the .exe files in the folder(such as Winrar.exe).

---

### Post by 3rdalbum on 2011-02-17
1. You can't give execute permission to files on an NTFS partition, because NTFS doesn't support this.

2. You don't need to; open a terminal and type 'wine ' and then drag the file into the terminal.

3. Most Windows programs can't be run in-place, they need to be "installed" into Wine just as you would install them into Windows.

4. You don't need WinRAR, Ubuntu's archive manager can handle RAR when you have installed the "unrar" package.

---

### Post by Curisu on 2011-02-17
> **3rdalbum]1. You can't give execute permission to files on an NTFS partition, because NTFS doesn't support this.[/quote]
I read a guide that was supposed to allow you to read/write NTFS on Ubuntu:
[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

Used the 64bit method of doing this because I'm using the 64bit OS. I see this guide says its just for read/write on NTFS so I guess that means even with the guide I linked to above, permissions are just not executable with the files on an NTFS partition as you said.

[quote=3rdalbum]2. You don't need to said:**
> 
Doing this seemed to work just fine but what about programs that need a couple of .exe files to run(some games need program1.exe and program2.exe to run in either a certain order or at the same time).

[quote=3rdalbum]3. Most Windows programs can't be run in-place, they need to be  "installed" into Wine just as you would install them into Windows.Ok, that makes sense, I'll give that a try.

[quote=3rdalbum]4. You don't need WinRAR, Ubuntu's archive manager can handle RAR when you have installed the "unrar" package.[/quote]I'll look for it in the software center; I was really just using WinRAR as an example though.

---

### Post by synapsys on 2011-02-18
In my opinion, the best way to do this is to have your Windows partition auto-mounted at startup. You can edit your /etc/fstab file to make this happen. If you've never done this before, follow this guide, and be careful not to delete any of the information already contained in fstab. 

[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

I use this method to auto-mount an NTFS partition from a Win7 x64 installation on a separate disk, and it works perfectly fine. I would recommend using the UUID for the partition, but you can also use the device id. Here's what my fstab entry looks like.

```
UUID=C888B00688AFF15C /media/vDisk ntfs-3g defaults,locale-en_US.utf8 0 0
```

---

### Post by Curisu on 2011-02-19
> **synapsys said:**
> In my opinion, the best way to do this is to have your Windows partition auto-mounted at startup. You can edit your /etc/fstab file to make this happen. If you've never done this before, follow this guide, and be careful not to delete any of the information already contained in fstab. 

[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

I use this method to auto-mount an NTFS partition from a Win7 x64 installation on a separate disk, and it works perfectly fine. I would recommend using the UUID for the partition, but you can also use the device id. Here's what my fstab entry looks like.

```
UUID=C888B00688AFF15C /media/vDisk ntfs-3g defaults,locale-en_US.utf8 0 0
```
Was looking through this and I found out in my "ect" folder I have no fstab file so there is nothing for me to work with. Would there be any way to fix this?

---

### Post by synapsys on 2011-02-20
> **Curisu said:**
> Was looking through this and I found out in my "ect" folder I have no fstab file so there is nothing for me to work with. Would there be any way to fix this?

It's "etc" not "ect" and you do have an fstab file located there or else you wouldn't be able to boot into Ubuntu. Try to follow the guide at the link I posted, it will explain everything...

---

### Post by Morbius1 on 2011-02-20
The irony of all this is that wine doesn't care if it's executable. Wine is incapable of determining if a file has a Linux executable bit set. Wine isn't stopping you from running an exe file Ubuntu is through something called "cautious-launcher".

Open up "Properties" on /usr/share/applications/wine. The first thing you see in the Command Box is "cautious-launcher".

Now go to /usr/bin/cautious-launcher -  it's a script that checks to see if it has a Linux executable bit set.

If you right click an *.exe file and select Properties  -> Open With -> Add -> Use a custom command > type in:  wine
In the "Open With" tab mark the "wine"[COLOR=Black] you added [/COLOR]as the default ( from the Wine that's already selected) and theoretically every time you run an exe it should select the wine without the cautious launcher script.

---

### Post by Curisu on 2011-02-20
> **synapsys said:**
> It's "etc" not "ect" and you do have an fstab file located there or else you wouldn't be able to boot into Ubuntu. Try to follow the guide at the link I posted, it will explain everything...
Ah my mistake, haha, was typing in "ect" not "etc", learned my copy/paste helps with this, my bad, thanks for pointing that out. I have a bad habit of preferring typing things to copy/pasting things. I will try this later on tonight when I'm not busy.

> **Morbius1 said:**
> The irony of all this is that wine doesn't care if it's executable. Wine is incapable of determining if a file has a Linux executable bit set. Wine isn't stopping you from running an exe file Ubuntu is through something called "cautious-launcher".

Open up "Properties" on /usr/share/applications/wine. The first thing you see in the Command Box is "cautious-launcher".

Now go to /usr/bin/cautious-launcher -  it's a script that checks to see if it has a Linux executable bit set.

If you right click an *.exe file and select Properties  -> Open With -> Add -> Use a custom command > type in:  wine
In the "Open With" tab mark the "wine"[COLOR=Black] you added [/COLOR]as the default ( from the Wine that's already selected) and theoretically every time you run an exe it should select the wine without the cautious launcher script.
Thanks Morbius; Opened a root privileged file browser with "gksudo nautilus" command in Terminal. From that window that popped up from the "gksudo nautilus" command, opened /usr/share/applications/wine and changed the "Command" box in "Wine Windows Program Loader" from "cautious-launcher %f wine start /unix" to "wine start /unix". Now everything in I try to launch that is a .exe file starts up without a hitch as long as it works in Lunix.


[U][B]
Edit regarding synapsys' post:[/B][/U]
I've gotten to the part where it shows all the permissions for mounted partitions(yes, my windows  partition is unmounted). All it is showing is information for my /swap(dev/sda5) /swap(dev/sdd5) and /ext3(dev/sdd1) parts. My HPFS/NTFS(/dev/sdb2) partition is not displayed so I couldn't go any further. I did look and I do have a file for the "HPFS/NTFS(/dev/sdb2)" partition in my "/dev" named "sdb2".

Only thing I can figure is that my Win7 stuff is on my internal hard drive and my Ubuntu 10.10 is on a external hard drive.

[U][B]
Edit 2 regarding my original post:[/B][/U]
I guess since I found out that changing the command area in the "Wine Windows Program Loader" under "Properties"(when run as a root user) from "_*cautious-launcher %f *_wine start /unix" to "_*wine start /unix*_" will start up program with Wine without the "executable bit" warning coming up, I suppose this thread is solved but I'd still like to know if anyone knows any answer regarding my first edit. Thank you.

---

### Post by MoganKat on 2011-02-24
I am having difficulty removing the "cautious-launcher %f " from the Wine Properties; can you give me a quick walkthrough on how you were able to edit the command?

Thank you

---

### Post by synapsys on 2011-02-25
> 
_** Edit regarding synapsys' post:**_
I've gotten to the part where it shows all the permissions for mounted partitions(yes, my windows  partition is unmounted). All it is showing is information for my /swap(dev/sda5) /swap(dev/sdd5) and /ext3(dev/sdd1) parts. My HPFS/NTFS(/dev/sdb2) partition is not displayed so I couldn't go any further. I did look and I do have a file for the "HPFS/NTFS(/dev/sdb2)" partition in my "/dev" named "sdb2".


That step is only to help you identify what the partition's device name is. Since you already know that it's /dev/sdb2, you can use this info for the next steps. In /etc/fstab, you're basically defining which partition you want to mount, where you want to mount it, and what driver/options to use when mounting. /dev/sdb2 is the partition you want to mount. You then need to define where you want it to be mounted (e.g. a sub-folder within /media.) Then you need to specify what driver and settings you would like to use (ntfs-3g and the default settings have always worked fine for me.) 

Hope that helps!

---

