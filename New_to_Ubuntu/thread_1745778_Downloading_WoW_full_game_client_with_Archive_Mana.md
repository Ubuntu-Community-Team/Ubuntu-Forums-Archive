---
title: "Downloading WoW full game client with Archive Manager"
date: 2011-05-01
forum: New to Ubuntu
---

### Post by RolandMcLean on 2011-05-01
Alright, here's how it goes. I've been trying to download the WoW full game client off the battle.net site for about 2 hours now with Archive Manager, as it's the only option Ubuntu gives me for what to download it with. But when I try to open the file from the downloads page once it's complete, I get 

"Archive:  /home/roland/Downloads/InstallWoW.exe
[/home/roland/Downloads/InstallWoW.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /home/roland/Downloads/InstallWoW.exe or
          /home/roland/Downloads/InstallWoW.exe.zip, and cannot find /home/roland/Downloads/InstallWoW.exe.ZIP, period."

I'm suuuuuuuuper new to Ubuntu, and have absolutely zero idea what that means. I already have a WoW account, and downloading the game off my CD's is out of the question, as they're in a different city.

Should I be using "Archive Manager"? How do I go about getting around this problem? Has anyone else had it also?

---

### Post by Risenn on 2011-05-01
[http://tom-geiger.de/?p=109](http://tom-geiger.de/?p=109)

Is what I'm looking at to help you at the moment

---

### Post by collisionystm on 2011-05-01
> **RolandMcLean said:**
> Alright, here's how it goes. I've been trying to download the WoW full game client off the battle.net site for about 2 hours now with Archive Manager, as it's the only option Ubuntu gives me for what to download it with. But when I try to open the file from the downloads page once it's complete, I get 

"Archive:  /home/roland/Downloads/InstallWoW.exe
[/home/roland/Downloads/InstallWoW.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /home/roland/Downloads/InstallWoW.exe or
          /home/roland/Downloads/InstallWoW.exe.zip, and cannot find /home/roland/Downloads/InstallWoW.exe.ZIP, period."


I'm suuuuuuuuper new to Ubuntu, and have absolutely zero idea what that means. I already have a WoW account, and downloading the game off my CD's is out of the question, as they're in a different city.

Should I be using "Archive Manager"? How do I go about getting around this problem? Has anyone else had it also?

Ardhive manager is for compressed files like.zip or .tar or .gz or .rar....etc....

Your exe file needs to be ran with wine.

Look in your software center for Play On Linux. It installs wine and has an option for installing WoW

If its not there google winehq

Go to the site and add the ppa for ubuntu

Sorry, id help more but I'm on my droid =)

---

### Post by _outlawed_ on 2011-05-01
[http://www.winehq.org/download/ubuntu](http://www.winehq.org/download/ubuntu)

PPA for Software Sources: **ppa:ubuntu-wine/ppa**

Open terminal and:

```
sudo apt-get update
```then either install Wine via terminal command or Synaptic. I recommend the Stable version, as the developement version has the risk of regressions each time a new release is put out:

Stable build:
```
sudo apt-get install wine1.2
```Development build:
```
sudo apt-get install wine1.3
```After Wine has been installed enter this command in terminal to configure Wine:

```
winecfg
```Then just open the .exe with Wine and you'll be set to go :)

---

### Post by Risenn on 2011-05-01
we're trying to install WoW through the WoW client from battle.net, WoW does not appear in games center. Any other tips? we do not have the discs.

---

### Post by eriktheblu on 2011-05-01
Patience, and make sure you have adequate disk space. Seriously, It will take several hours even on a high speed connection. With the temp files, installation can eat up more than 30 GB of HDD (I had to expand a partition once because of that)

If you run into errors during the install, check the properties of the WoW folder as it has in the past made a habit of changing the permissions to read only.

The downloaded installer seems to be a bit more straightforward than the install disks, so there really shouldn't be any problem.

---

