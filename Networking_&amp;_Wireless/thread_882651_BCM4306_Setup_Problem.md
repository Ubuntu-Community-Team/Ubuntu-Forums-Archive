---
title: "BCM4306 Setup Problem"
date: 2008-08-07
forum: Networking &amp; Wireless
---

### Post by RegLinUsr on 2008-08-07
I am attempting to use [**_Broadcom 4306 With Ndiswrapper 54 Mbps_**]("http://ubuntuforums.org/showthread.php?t=201902&highlight=broadcom+4306+wireless+feisty&page=81") but I can not get past the *'build-essentials'* step. While running the command *'sudo aptitude install build-essential'* I receive the error *'Couldn't find any package whose name or description matched "build-essential"'* and it finishes with *'No packages will be installed, upgraded, or removed.'* I have my CD in the drive but I do not believe that it is being accessed. The CD is listed as one of the sources in the Adept Installer.

I can connect to the internet via my Mac but not with the Kubuntu PC at the moment w/o wireless. Thanks for any help submitted.

Kubuntu 8.04.1

---

### Post by chili555 on 2008-08-07
Let's see if we can properly add your install CD as a source. Put the CD in the tray and open a terminal and do:```
sudo apt-cdrom -add
```It will take a few moments to think and execute, so be patient.

---

### Post by RegLinUsr on 2008-08-07
Thank you but that didn't seem to do anything. I still have the same issue. Upon issuing that command, it immediately (no 'think and execute' pause) pops up with the information for the command 'apt-cdrom' showing the command and option requirements as if I issued the command with the -h option. When I get to the step *'sudo aptitude install build-essential'*, there is no activity from the CD drive so it still doesn't seem to be looking at the drive for program installs.

---

### Post by Ayuthia on 2008-08-07
> **RegLinUsr said:**
> Thank you but that didn't seem to do anything. I still have the same issue. Upon issuing that command, it immediately (no 'think and execute' pause) pops up with the information for the command 'apt-cdrom' showing the command and option requirements as if I issued the command with the -h option. When I get to the step *'sudo aptitude install build-essential'*, there is no activity from the CD drive so it still doesn't seem to be looking at the drive for program installs.

You might try that command without the -:
```
sudo apt-cdrom add
```It should ask you to load your Ubuntu installer CD.

If you are able add the CD, you will need to run an update:
```
sudo apt-get update
```
You should be able to install build-essential.  If that doesn't work, but the CD is installed, you can try to install ndiswrapper:
```
sudo apt-get install ndiswrapper-utils-1.9
```

---

### Post by chili555 on 2008-08-08
> You might try that command without the -:Quite correct. Sorry for the error.

---

### Post by RegLinUsr on 2008-08-08
When I run the command sans "-" I get the following message: 

[I]Using CD-ROM mount point /cdrom/
Unmounting CD-ROM
Waiting for disc...
Please insert a Disc in the drive and press enter
Mounting CD-ROM...
E: Failed to mount the cdrom.[/I]

I can access the CD manually, no problem. I also attempted this using my external CD drive with the same results. I even attempted this through the *Adept Installer* but to no avail. It doesn't seem to want to add the CD drive as a software source. What files do I need off of the CD that I can copy to the hard drive and run from there? Or, can I download the necessary files from the internet via my Mac, copy them to an external HD and then install them to my Kubuntu computer? The external HD can be accessed with no problem from my linux computer.

---

### Post by chili555 on 2008-08-09
When you simply drop the CD in the tray and close it, does it mount, that is, does a little icon appear on your desktop? If so, go to Places -> Filesystem -> Media and see if it mounted as something other than 'cdrom' such as 'cdrom0.' Then specify where the CD is mounted with:```
sudo apt-cdrom -d /media/cdrom0 add
```

---

### Post by RegLinUsr on 2008-08-11
I can access the CD, no problem, as I stated before.

> **chili555 said:**
> ... go to Places -> Filesystem -> Media and see if it mounted ...[/CODE]

I do not see any "Places" menu anywhere.

EDIT: I was able to get the CD functioning finally but *only* after some heavy-handed work on the fstab. The CD drive wasn't even present in there?! I do not understand that at all. I am not too sure about Kubuntu distro so far. I've had more problems with this distro than any other and most of the problems are little, simple things... until getting my wireless functioning. I followed the setup steps in the tutorial above and now I boot to a blank screen with my internal fan spinning at full tilt! Ughhh!

---

