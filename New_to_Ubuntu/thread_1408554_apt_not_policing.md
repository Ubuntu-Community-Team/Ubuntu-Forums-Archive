---
title: "apt not policing"
date: 2010-02-16
forum: New to Ubuntu
---

### Post by degarb on 2010-02-16
I just installed two games, neither put any lnk in the app/games.   I know how to to put a link on desktop, but there appears no way to put a link in the game menus.  Furthermore,  I have no idea what games were installed on the game pack, and assume just a bunch of files in user/bin.  The apt should never allow this.  Haven't seen this-editing apps menu and tracking install--in manual.  Easy and intuitive in Windows for any beginner.

I use gnome.  Is this something to do with gnome v k?  

Anyway, two issues should be fixed.

---

### Post by degarb on 2010-02-16
Found way to add in google.  In vector, you can just click update menus and it finds all executables on system. 

I think a right click context menu when you click on applications, should offer short cut to the system>pref>main menus.  Would be nothing to do and aleviate headaches for many.

---

### Post by HarrisonNapper on 2010-02-16
> **degarb said:**
> Found way to add in google.  In vector, you can just click update menus and it finds all executables on system. 

I think a right click context menu when you click on applications, should offer short cut to the system>pref>main menus.  Would be nothing to do and aleviate headaches for many.

One of the wonderful things about Linux is that most utilities (like Gnome) are licensed under a GNU license and/or are otherwise open source. If it's something you're interested in, add a right click menu and pass it around! :) As you say, it would be a fairly easy project and you could package it as a deb and make that feature available for all ubuntu users

---

### Post by degarb on 2010-02-17
> **HarrisonNapper said:**
> One of the wonderful things about Linux is that most utilities (like Gnome) are licensed under a GNU license and/or are otherwise open source. If it's something you're interested in, add a right click menu and pass it around! :) As you say, it would be a fairly easy project and you could package it as a deb and make that feature available for all ubuntu users


How does a non programmer do this?  Is it something simple?

---

### Post by mikewhatever on 2010-02-17
Well, apt is not a policeman, and isn't supposed to be. The lack of menu launchers may have something to do with Gnome Menu or the game installer, but not apt. Perhaps you can elaborate on what you installed exactly, although post #1 indicates that you don't know. Odd.

---

### Post by degarb on 2010-02-17
> **mikewhatever said:**
>  Perhaps you can elaborate on what you installed exactly, although post #1 indicates that you don't know. Odd.

Exactly.  

Yesterday, I poured through the usr/bin/game directory and found two games that didn't have menu items.  Since part of a game pack, there would be no way a user could run them.   Perhaps, other games did install in menu with what ever package they were a part.  

Then, one thinks, maybe you install some package, and nothing shows in menu.   I am hoping the properties on package might help me know at least the name of the executable. I am not sure this is true.  As a new user, I don't like not knowing where the executables are being put.  

On my kids vector linux machine, kalvoro (typing program)  installed somewhere, but a file find brings up nothing, and nothing in menus.  All I can do is uninstall, but I bet there is a working program somewhere.  I just don't know.

---

### Post by chaanakya_chiraag on 2010-02-17
Go to the command prompt (Applications->Accessories->Terminal) and type in ```
sudo update-menus
```entering your **login** password if necessary (**the password will not show when you are typing**!!)  This should achieve the same thing as the update menus menuitem in vector linux :)

---

### Post by degarb on 2010-02-17
I just installed a java scheduler (I come to love my windows scheduler in last 7 years after I discovered it and gradually become reliant on it for so many things.)  But, no menu I can find!

I think that Ubuntu should have a summary of installed files and shortcuts.  It took me over a minute to find the drapes shortcut, when a bubble after install could have tipped me off in 5 seconds.

a suggestion.

---

### Post by mcduck on 2010-02-17
> **degarb said:**
> Exactly.  

Yesterday, I poured through the usr/bin/game directory and found two games that didn't have menu items.  Since part of a game pack, there would be no way a user could run them.   Perhaps, other games did install in menu with what ever package they were a part.  

Then, one thinks, maybe you install some package, and nothing shows in menu.   I am hoping the properties on package might help me know at least the name of the executable. I am not sure this is true.  As a new user, I don't like not knowing where the executables are being put.  

On my kids vector linux machine, kalvoro (typing program)  installed somewhere, but a file find brings up nothing, and nothing in menus.  All I can do is uninstall, but I bet there is a working program somewhere.  I just don't know.

Not everything in /usr/bin/game is actually a graphical game, and adding terminal apps to menus doesn't make much sense.

Anyway, it's the package's responsibility to include menu entries. If the programs's package didn't add the menu entries there peobably was a reason for that. At least I've yet to find a package in Ubuntu repositories that should have a menu entry but doesn't have one.

What comes to executables, for any user-level app you can be quite sure to find the executable in /usr/share/bin. But if unsure, the "which" comamnd will tell you the executable file of a program and where that file is.

For ading the menu entries, just right-click on the menu and select "Edit Menus". The "update-menus"-command requires you to have the Debian Menu package installed. That will create a menu section which includes pretty much every single program on your system, no matter if having it on your desktop's menus makes any sense or not.

---

### Post by degarb on 2010-02-17
> **mcduck said:**
> 

For ading the menu entries, just right-click on the menu and select "Edit Menus". The "update-menus"-command requires you to have the Debian Menu package installed. That will create a menu section which includes pretty much every single program on your system, no matter if having it on your desktop's menus makes any sense or not.

Right clicking does nothing on gnome here.   The right click contextual menu is missing.  It is one line of code to add a short cut to the main menu prefs, and is first place user would look, since right clicking usually brings up such a menu. 

I would need to snaptic 'debian menu" and install, run, then use the main menu prefs to unclick the unneeded programs?  Does sound like a head ache and risk duplication.

---

### Post by mikewhatever on 2010-02-17
> **degarb said:**
> I just installed a java scheduler (I come to love my windows scheduler in last 7 years after I discovered it and gradually become reliant on it for so many things.)  But, no menu I can find!

I am not familiar with that particular application, yet, I am rather confident that it is not maintained by Ubuntu devs, and, I dare say, have nothing to do with Ubuntu.

You mentioned /usr/bin/game directory earlier, which doesn't exist on my installation. Can you post the output of **ls /usr/bin/game** to see what's in there.

> I think that Ubuntu should have a summary of installed files and shortcuts.  It took me over a minute to find the drapes shortcut, when a bubble after install could have tipped me off in 5 seconds.

a suggestion.

You mean the bubble like in Windows telling you there is a new application installed and covering the logout icon? God forbid. It took me a lot longer then one minute to figure out how to disable that.

You might find this to be interesting reading -> [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

---

### Post by degarb on 2010-02-17
a log would be nice, or message box.  Log is better, so I can see what exactly was done to my system.

I am still apoplectic that ubuntu doesn't allow a user control of where things are installed.  I would go crazy installing on a second usb drive or stick, rather than on my 6 gig hd.

---

### Post by mikewhatever on 2010-02-17
Well, Ubuntu is not for everyone, as well as Windows or OSX. Frankly, I am tired of arguing against what seems to be personal preferences, unfamiliarity and learning curve. Ubuntu is not Windows, and if that's the point you are making, then we are in agreement. Use what fits you best, and good luck.

---

### Post by HarrisonNapper on 2010-02-18
> **degarb said:**
> a log would be nice, or message box.  Log is better, so I can see what exactly was done to my system.

I am still apoplectic that ubuntu doesn't allow a user control of where things are installed.  I would go crazy installing on a second usb drive or stick, rather than on my 6 gig hd.

tail -f /var/log/messages

---

### Post by HarrisonNapper on 2010-02-18
> **degarb said:**
> How does a non programmer do this?  Is it something simple?

It's simple if you have the time and desire to learn. No such thing as a non-programmer, just times when you consume, times when you create.

I would suggest starting with a bash script that goes through /usr/bin/games, /usr/local, and /opt, and prompts whether a menu item should be created for each executable shell script.

---

### Post by mcduck on 2010-02-18
> **degarb said:**
> a log would be nice, or message box.  Log is better, so I can see what exactly was done to my system.

I am still apoplectic that ubuntu doesn't allow a user control of where things are installed.  I would go crazy installing on a second usb drive or stick, rather than on my 6 gig hd.

There's absolutely no change that anything would be installed on wrong drive. Nothing is isnatlled randomly, everyhting goes into pre-defined standard directories.

And the reason why you can't select where to install stuff is because Linux doesn't install programs into a single location. Instead all the fiels of a package are put into different directories based on the purpose of those files. All executable files go to one place, documentation to one place, icons to one place and configurations to one place. This might seem strange for people coming from Windows, but it actually makes lots of sense and after you've learned what those locations are you'll be able to find different files much easier than in Windows. :)

For example to find a program's documents in Windows I'd have to browse through the Program Files-directory trying to figure out what name the installer decided to give to that program's directory (usually that would be the name of the company that made the program, not the actual name of the program itself). After I've found that I'd have to figure out that program's own way of arranging files and directories, as there is no standard for that, or just browse around until I find the docs.. On Linux, on the other hand, I know I just go to /usr/share/doc and open the directory with the same name as the program.

Of course you *can* select what drives/partition you mount into every directory, and that allows you to put stuff into different drives/partitions and even use different filesystems for different purposes. But that definitely isn't something that you should even think about in any normal deskop use. Just give the root partition enough space and conentrate on managing your own files, the package management is perefectly capable of managing the system stuff for you. :)

---

### Post by degarb on 2010-02-18
> **mcduck said:**
> There's absolutely no change that anything would be installed on wrong drive. Nothing is isnatlled randomly, everyhting goes into pre-defined standard directories.

And the reason why you can't select where to install stuff is because Linux doesn't install programs into a single location. Instead all the fiels of a package are put into different directories based on the purpose of those files. All executable files go to one place, documentation to one place, icons to one place and configurations to one place. This might seem strange for people coming from Windows, but it actually makes lots of sense and after you've learned what those locations are you'll be able to find different files much easier than in Windows. :)

For example to find a program's documents in Windows I'd have to browse through the Program Files-directory trying to figure out what name the installer decided to give to that program's directory (usually that would be the name of the company that made the program, not the actual name of the program itself). After I've found that I'd have to figure out that program's own way of arranging files and directories, as there is no standard for that, or just browse around until I find the docs.. On Linux, on the other hand, I know I just go to /usr/share/doc and open the directory with the same name as the program.

Of course you *can* select what drives/partition you mount into every directory, and that allows you to put stuff into different drives/partitions and even use different filesystems for different purposes. But that definitely isn't something that you should even think about in any normal deskop use. Just give the root partition enough space and conentrate on managing your own files, the package management is perefectly capable of managing the system stuff for you. :)

I don't find it puzzling, just limiting. 

My usr directory is taking up like a third my hard drive. (home is about 2%)  I need to move it off the hard drive asap, or I will not have a computer worth running.   This is a snap in windows.   But considered risky in Linux?  I have a saved post on how to partially mount this.  I have read it twice, and will read several more times before attempting this.  

How can something so limiting,  so against the spirit of user control of their system, be good?  



----------------------------------
I could have been spared months of windows xp reinstalling if programs stayed in one place, perhaps years over last 22  years. In principle, I don't want a program in 3 places, I want each program in 1 directory of my choosing with write priveleges as I define.   I never install any program that relies on installing crap all over my drive (docs settings/system32) or registry, if I can avoid it.  I think, based on the sheep design,  most programmers never actually manage a real computer system, other than light use.   Especially not for business use, where we just want stuff to work, regardless of how many reinstalls of the OS.

---

### Post by mcduck on 2010-02-18
> **degarb said:**
> I don't find it puzzling, just limiting. 

My usr directory is taking up like a third my hard drive. (home is about 2%)  I need to move it off the hard drive asap, or I will not have a computer worth running.   This is a snap in windows.   But considered risky in Linux?  I have a saved post on how to partially mount this.  I have read it twice, and will read several more times before attempting this.  

How can something so limiting,  so against the spirit of user control of their system, be good?  



----------------------------------
I could have been spared months of windows xp reinstalling if programs stayed in one place, perhaps years over last 22  years. In principle, I don't want a program in 3 places, I want each program in 1 directory of my choosing with write priveleges as I define.   I never install any program that relies on installing crap all over my drive (docs settings/system32) or registry, if I can avoid it.  I think, based on the sheep design,  most programmers never actually manage a real computer system, other than light use.   Especially not for business use, where we just want stuff to work, regardless of how many reinstalls of the OS.

How is that limiting? It's just different, instead of managing the locations of single programs, scattering them around your directory structure, you just control the locations of whole directories and directory trees. That's lot more powerfull, moving lots of stuff to different drives, and still maintaining them in the same location in the file system hierarchy. :)

Also what make you think moving things arund would be considered "risky"? Messy, and unorganized, perhaps, if you are talking about moving single applications around. :D But there's nothing risky about using separate drives or partitions for different directories.

The reason why you wouldn't want programs to spread stuff into different places in Windows is that Windows handles uninstalling of programs pretty badly and that stuff stays easily on your drive even when uninstallign the actual program. That's not a problem on Linux, the package manager is your friend and handles all the files for you.

I'm starting to think you are still a bit stuck on the ideas and habits you've learned on Windows, while much of that stuff doesn't really apply on other operating systems. :)

For example you are now having probelms with the /usr directory filling your root partition. If you were to make more room by moving programs to different palce you' actually have to do a lot more work, installing every program to a different drive. The Linux way would beto simply move the whole /usr directory to different drive. That's lot less work to do that changing the install directory of every program you install from now onwards. And like I said, the files will still appear in the very same place as before. :)

---

### Post by degarb on 2010-02-18
> **mcduck said:**
> For example you are now having probelms with the /usr directory filling your root partition. If you were to make more room by moving programs to different palce you' actually have to do a lot more work, installing every program to a different drive. The Linux way would beto simply move the whole /usr directory to different drive. That's lot less work to do that changing the install directory of every program you install from now onwards. And like I said, the files will still appear in the very same place as before. :)


I just spent last half hour pouring through 3 pages trying to get a handle on how to do this.  

Is there a simple way, or a paragraph (code okay.) to do this?

---

### Post by chaanakya_chiraag on 2010-02-18
I'm pretty sure you would have to play around with /etc/fstab, but **be careful**.  One wrong step and you're gone.  The first thing would be to create a new partition or connect the new drive.  Then, you would have to tell /etc/fstab to mount the drive/partition as /usr.  Then, all you have to do is reboot!

---

### Post by mcduck on 2010-02-18
> **degarb said:**
> I just spent last half hour pouring through 3 pages trying to get a handle on how to do this.  

Is there a simple way, or a paragraph (code okay.) to do this?


This is usually best done at the time when you install Ubuntu, as you can define separate partitions for different directories in the installer and everything is automatically done for you. But here's how to do it afterwards (You should probably do this when running froma live-CD):

1. create a new partition on your new drive (use some Linux-compatible filesystem, not FAT or NTFS. I'd go for Ext4)

2. Mount your installed system's partition, and the new partition you just made.

3. Copy the contents of your current /usr (from the installed system, not the live-CD!) directory into that new partition.

4. Add the partition to /etc/fstab (again , fstab on the installed system, not live-CD) , setting the mount point to /usr.

5. Delete the contents of the old /usr directory to free the space on your root partition

6. Reboot back to the installed system, everything in /usr is now on the new partition.

If you need more detailed instructions just search this forum for instructions about moving your /home to separate partition. The process is exactly the same, only with /usr instead of /home.

---

### Post by degarb on 2010-02-18
> **chaanakya_chiraag said:**
> I'm pretty sure you would have to play around with /etc/fstab, but **be careful**.  One wrong step and you're gone.  The first thing would be to create a new partition or connect the new drive.  Then, you would have to tell /etc/fstab to mount the drive/partition as /usr.  Then, all you have to do is reboot!

Just saved and read Roger Morton's guide to moving home directory.   There are the minor things left unexplaned in the manual-- like determining the linux drive name for the stick-- which would be above my an average user knowledgebase, without more googlings.    In the end, he was unable to unmount the home dir, since used by the cli.  He had to reboot, but linux wiped out! And, he had to use some recovery console to get back in to linux!  The recover console of linux is another, thing I would need to google.   He concluded his manual page needed some work and improvement, though not un-doable. 

So, I conclude, I am limited by the difficulty.  But in time, probably next winter, will have enough bravery to try this.   Also, the average home and business computer user, would never be able to do this.   To me, it even seems risky for the commandline/recovery console competent user.   

Maybe some program could be written to automate this for the average person not to screw up, so more machines/netbooks/old computers could run Ubuntu.

---

### Post by degarb on 2010-02-18
> **mcduck said:**
> This is usually best done at the time when you install Ubuntu, as you can define separate partitions for different directories in the installer and everything is automatically done for you. But here's how to do it afterwards (You should probably do this when running froma live-CD):

1. create a new partition on your new drive (use some Linux-compatible filesystem, not FAT or NTFS. I'd go for Ext4)

2. Mount your installed system's partition, and the new partition you just made.

3. Copy the contents of your current /usr (from the installed system, not the live-CD!) directory into that new partition.

4. Add the partition to /etc/fstab (again , fstab on the installed system, not live-CD) , setting the mount point to /usr.

5. Delete the contents of the old /usr directory to free the space on your root partition

6. Reboot back to the installed system, everything in /usr is now on the new partition.

If you need more detailed instructions just search this forum for instructions about moving your /home to separate partition. The process is exactly the same, only with /usr instead of /home.


I didn't think of doing it from the live live cd.   Nor did morton.    This would make things easier.  and more reversable if things wouldn't boot or work.  I would think.

One more thing, you could just copy with nautist right?  no problem?


---------------------

It would be cool if this were just a live cd tool.  this would end future threads concerning this and make Ubuntu that much cooler.

---

### Post by mcduck on 2010-02-18
> **degarb said:**
> I didn't think of doing it from the live live cd.   Nor did morton.    This would make things easier.  and more reversable if things wouldn't boot or work.  I would think.

One more thing, you could just copy with nautist right?  no problem?


---------------------

It would be cool if this were just a live cd tool.  this would end future threads concerning this and make Ubuntu that much cooler.
Sure, you can do the copying with nautilus (if you start it as root, by running "gksudo nautilus).

And the reason I recommend doing it from live environment is that it's the only way that allows you to delete the existing data from the old /usr directory. You can't do that on a running system, but if you don't do it you won't get the used disk space back on the root partition. :)

Fixing any possible errors in fstab would work the same way no matter if you edited the fstab directly on the installed system or from a live system, either way you'd have to fix it from a live system.

---

### Post by chaanakya_chiraag on 2010-02-18
Not really.  Boot up, hold Shift to get to the GRUB menu, select Recovery Console, and nano /etc/fstab should do the trick :D

---

### Post by mcduck on 2010-02-18
> **chaanakya_chiraag said:**
> Not really.  Boot up, hold Shift to get to the GRUB menu, select Recovery Console, and nano /etc/fstab should do the trick :D

well, if you do a bad configuration for the /usr directory in your fstab you most likely won't be able to use nano, or even boot into recovery mode. You would be missing quite large part of the system wihtout the /usr directory..

---

### Post by chaanakya_chiraag on 2010-02-19
Hmmm...I'm not exactly sure how recovery mode works, but I thought it basically is a foolproof system...I'll have to find out next time I bork my system :D

---

### Post by mcduck on 2010-02-20
> **chaanakya_chiraag said:**
> Hmmm...I'm not exactly sure how recovery mode works, but I thought it basically is a foolproof system...I'll have to find out next time I bork my system :D

I doubt it would be foolproof enough to survive missing most of the system resource files, which are located in the /usr directory, just like most of the programs are (even the command-line apps).

Recovery mode is really just booting in the same way as usually, but only loading the most important services (and of course logging you in as root).

---

