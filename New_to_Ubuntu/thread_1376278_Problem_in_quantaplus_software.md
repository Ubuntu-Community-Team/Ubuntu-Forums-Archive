---
title: "Problem in quantaplus software"
date: 2010-01-09
forum: New to Ubuntu
---

### Post by Ashishkhandelwal on 2010-01-09
Hi,

I have installed quanta plus software as i fount on net that quanta plus is nearest to dreamweaver.But now i am facing a problem in it as it is not able to open any php files which are located on another PC.Although my PC is connected to that PC in the network but still i have to copy those files in my local system and then only it is opening.But i want it to open directly.Is there any solution for this problem.Please help me.

---

### Post by markjensen on 2010-01-09
Mount the remote filesytem.   Then you will be able to point to it in reference to your filesystem root.

On a related note, why did you install quanta from the net (presumably a google search and off a web page).   If you use the package manager, you will automatically get all updates and bugfixes.  :)

---

### Post by Ashishkhandelwal on 2010-01-09
I have installed it from add/remove in ubuntu.I have also mounted that file system using smb://192.168.0.8 that is samba server.But when i am opening it from there it is not opening ands i have to save it on my local system first then only it is opening.But every time it is not possible to open it so if there is any permanent solution then please tell me.

---

### Post by markjensen on 2010-01-09
Accessing it via smb://xxx.xxx.xxx.xxx isn't mounting it.

There is a detailed procedure here: [http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)

But basically, you need to create a mount point in your filesystem, like /media/otherpc

Then you can use one of the mount commands in the above thread to mount it (the command varies if you use passwords on your share, or if it is read/write or read-only)

Once you get it working with your mount command, you can add an entry into fstab to make it always attempt to mount it at boot time.

---

### Post by Itchikins on 2010-02-01
Hi,
I'm going to jump in on this thread as it is the closest to my problem that I have found in about a day of research.
I am having the same problem, but unlike the original poster I already have my network drives mounted in /etc/fstab.   They are working great in all programs EXCEPT Quanta Plus.   
When trying to open any file on a network drive I get the following error:
> The file <filename> could not be loaded, as it was not possible to read from it.  Check if you have read access to this file.I can use any other editor, Screem, Bluefish, gedit, pico, etc and open, modify and save files on these same network drives.
Something I just realized is that Quanta Plus is a KDE app.  Could it be that there is some KDE networking component that I am missing?  This does happen to be a fresh Ubuntu install on a new computer.  I have Quanta Plus installed on my old computer and it works fine but over the years I have installed many programs on it and perhaps it has a KDE networking piece that hasn't been installed on this new computer.

Any help would be appreciated as I really like using Quanta Plus!
Thanks,
Itchikins

---

