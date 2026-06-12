---
title: "Installing a Windows program"
date: 2011-07-23
forum: New to Ubuntu
---

### Post by Inisfad on 2011-07-23
I currently have a Windows and an Ubuntu partition on my computer.  I have purchased an electronic catalog that I want to install, however, the catalog is designed for Windows.  I originally installed the catalog in my Windows partition, but it is a PIA to continually have to shut down Ubuntu (Lucid) and restart in Windows to see the catalog.  I have been trying to research this on the internet, but frankly cannot find a solution.  I have Wine installed, and rather than run Windows virtually inside Ubuntu, was hoping that I could run the electronic catalog with Wine.  When I open the installation DVD, of course, the set up file will not run - when I click it, Wine advises that the set up file is not marked as an executable.  I am unable to change the properties, as I am not the owner.  Opening permissions indicates that the owner is 'user #1096' (totally unfamiliar and not my user/owner name).  I am a complete newbie, but it would be really helpful if I could get this program to run in Ubuntu.  Thanks for any (simple) instructions or advice you can offer.

---

### Post by CaptainJamie on 2011-07-23
Well I'm not brilliant at this but i do know that if you run in terminal ```
 sudo chown <yourusername> <pathtofile> 
``` you own the file

---

### Post by TeoBigusGeekus on 2011-07-23
You could copy the dvd to your hard drive, change the permissions of the installer and try again.

---

### Post by CaptainJamie on 2011-07-23
oh also 

```
 sudo chmod +x <pathtofile> 
``` 
makes it executable I think

---

### Post by Inisfad on 2011-07-23
OK, stupid question - the DVD is listed in /media/cdrom0.  Is that what I use as the path?  (As in I tried that and although 'root' is now the owner, I still do not have permission).  Or am I to do the path to the actual set up file within the CD? (And if so, will all the other exe files in the CD run, or must I do this with each one?)  I did try the chown command with the setup.exe file, but nothing changed.  Sorry to be such a pain.

---

### Post by Inisfad on 2011-07-23
> **TeoBigusGeekus said:**
> You could copy the dvd to your hard drive, change the permissions of the installer and try again.

 And I'm sorry, I don't quite understand what this means.  When I use the chown command, the ownership doesn't change:

 owner@owner-laptop:~$ chown jane /media/cdrom0/setup.exe

 chown: changing ownership of `/media/cdrom0/setup.exe': Read-only file system

 owner@owner-laptop:~$ ls -l /media/cdrom0/setup.exe

-rw-rw-r-- 1 1096 voice 258792 2008-08-28 15:12 /media/cdrom0/setup.exe

---

### Post by TAspr on 2011-07-23
What Worked For You?

---

### Post by Tea4all on 2011-07-23
A cd is read-only. Try running wine from the command line instead. ```
cd /media/cdrom0
``` and ```
wine setup.exe
``` or whatever the installer name is.

---

### Post by wildmanne39 on 2011-07-23
Hi, if you are not able to run it in wine you can install virtualbox and install windows in it then you will not have to reboot to run window programs.
[http://www.virtualbox.org/](http://www.virtualbox.org/)

---

