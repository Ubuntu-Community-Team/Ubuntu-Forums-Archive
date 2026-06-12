---
title: "How to extract a exe file?"
date: 2007-06-19
forum: Networking &amp; Wireless
---

### Post by Elotero on 2007-06-19
How do you extract an .exe file?? i DLed the driver i need and i dont know how to extract it.. i have cabextract but im stuck.. dont know how to open the driver to use it.. any help?? its sitting on my desktop right now..

---

### Post by crazyjx23 on 2007-06-19
Scratch that.

---

### Post by andycyca on 2007-06-19
I don't know much, but I know .exe files won't run in Ubuntu, those are made specifically for Win. Maybe if you can tell here exactly what driver you need, someone might be able to locate a repository for you

---

### Post by elpichi on 2007-06-19
exe files? if my head doesn't fool me WINE should be able to deal with them, but i never heard of exe files being extractable O.O.

---

### Post by Elotero on 2007-06-19
sp34153... its a driver for a wireless card... i need to extract it and change it to install it.. these are the directions im following:

Unpack the Windows driver by using the unzip, cabextract and/or unshield tools (run from the Terminal), and find the INF file (.INF or .inf extension) and the SYS file (.SYS or .sys extension). You may first need to install cabextract and unshield.

I gotta change the driver to an .inf file...

---

### Post by elpichi on 2007-06-19
umm well according to those directions i would.. do the following
go to the terminal, and type:
unzip "filename" #which should extract the files to the home directory
i never noticed "unzip" was a valid command on the console

i'm half convinced that an executable could be extractable just like that, try it either way =\

---

### Post by kevdog on 2007-06-19
I think you need the cabextract package -- if you dont have a working internet connection on the Ubuntu, then you are going to have to find cabextract.deb from a different computer, and then transfer it via USB stick.  To install of USB -- if you drag the file to the desktop it would be:

sudo dpkg -i ~/Desktop/cabextract.deb  <---Substitute a different filename if cabextract is named something different


You should then be able to type (if you are in the same directory as the *****.exe file)
cabextract ******.exe

Thats about all there is to it!

---

### Post by Elotero on 2007-06-19
okay.. i guess i need sp34153.inf.. because im dying trying to extract it... thank you for the help BTW... i got a few different tutorials and im trying to follow them... from this one it sounds too easy.. this is where im stuck guys...

4. Extract the driver via cabextract
Assuming you saved the driver package (a file looking like sp34153.exe or similar) in the folder WLAN on your desktop, open a console, change to this directory and extract the files in the .exe file with cabextract:

    cd Desktop
    mkdir WLAN
    cd WLAN
    cabextract sp34153.exe (whatever the filename is in your case)


5. Install the driver with ndisgtk
Start ndisgtk - it can be found in the System - Administration menu. Just point ndisgtk to the directory where you extracted the .exe file, in my example at /Desktop/WLAN, and here to the file with the suffix .INF

his 3 days.. 
Ndisgtk/Windows wireless does not find any INF files.. i did the command in the terminal but its done with 1 error.. i cant extract the EXE file anywhere ... I need the INF file.. can post the driver?? i been at this 3 days already.. you guys are amazing though.. always good help...

---

### Post by Elotero on 2007-06-19
> **kevdog said:**
> I think you need the cabextract package -- if you dont have a working internet connection on the Ubuntu, then you are going to have to find cabextract.deb from a different computer, and then transfer it via USB stick.  To install of USB -- if you drag the file to the desktop it would be:

sudo dpkg -i ~/Desktop/cabextract.deb  <---Substitute a different filename if cabextract is named something different


You should then be able to type (if you are in the same directory as the *****.exe file)
cabextract ******.exe

Thats about all there is to it!

Thats cool.. but i have my net connected through a ethernet cable.. do you have any advice for a non usb transfer??

---

### Post by peaceforall on 2007-06-19
I don't have your answer.  I'm a new to this forum today.  Can you tell me how to post a new question here?

---

### Post by ugm6hr on 2007-06-19
> **Elotero said:**
> Thats cool.. but i have my net connected through a ethernet cable.. do you have any advice for a non usb transfer??

I haven't used cabextract manually - but your question sounds straightforward.
Go to Synaptic Package manager - and Search for cabextract, then select it for installation (if you haven't already).
In Terminal:
```
cd Desktop
cabextract sp34153.exe
```

If this is how cabextract works - then this should extract the files to your desktop.  

The problem you have been having appears to be that your .exe file is on your Desktop (according to your first post) - but the instructions you are following state:
> Assuming you saved the driver package (a file looking like sp34153.exe or similar) **in the folder WLAN on your desktop**

---

### Post by kevdog on 2007-06-20
Great just as above if you have an ethernet wired connection its even easier!!!

From command line install package:

sudo aptitude install cabextract

Assuming what you said about the file being on your Desktop in the WLAN folder:

cd ~/Desktop/WLAN
cabextract ******.exe <---Again whatever name of cabinet file

Some .exe files you find for drivers are cabinet files, and others are self-extracting zip files.  Im not sure which yours is.  If for some reason cabextract doesnt work, first verify the command syntax is OK --- type
cabextract --help

and it will give you some options.  If its truly a self extracting zip file (with a .exe extension) I believe a program like arK would open it -- sorry I dont know the equivalent Gnome package name for arK -- arK is for KDE

---

### Post by Elotero on 2007-06-20
> **ugm6hr said:**
> I haven't used cabextract manually - but your question sounds straightforward.
Go to Synaptic Package manager - and Search for cabextract, then select it for installation (if you haven't already).
In Terminal:
```
cd Desktop
cabextract sp34153.exe
```

If this is how cabextract works - then this should extract the files to your desktop.  

The problem you have been having appears to be that your .exe file is on your Desktop (according to your first post) - but the instructions you are following state:

Thank you fro your help.. as soon as i get home i will try and tell you how it goes... a thousand thank yous!!!!!!!!!!!!!

---

### Post by Elotero on 2007-06-20
> **kevdog said:**
> Great just as above if you have an ethernet wired connection its even easier!!!

From command line install package:

sudo aptitude install cabextract

Assuming what you said about the file being on your Desktop in the WLAN folder:

cd ~/Desktop/WLAN
cabextract ******.exe <---Again whatever name of cabinet file

Some .exe files you find for drivers are cabinet files, and others are self-extracting zip files.  Im not sure which yours is.  If for some reason cabextract doesnt work, first verify the command syntax is OK --- type
cabextract --help

and it will give you some options.  If its truly a self extracting zip file (with a .exe extension) I believe a program like arK would open it -- sorry I dont know the equivalent Gnome package name for arK -- arK is for KDE


I will try this as soon a i get home.. thank you so much.. i will let you know how it goes..!!

---

### Post by Elotero on 2007-06-20
> **peaceforall said:**
> I don't have your answer.  I'm a new to this forum today.  Can you tell me how to post a new question here?

Make sure your not in a specific question already.. and from Networking and Wirelss page hit the button on top that says "Make New Post" .. then people can see what you need and help you out.. hope this helps!

---

### Post by pandorazboxx on 2007-06-20
if you're connected to the internet i think you can do:

```
sudo aptitude install cabextract
```

EDIT: nevermind i didn't see this was two pages, someone got it first though

---

### Post by ugm6hr on 2007-06-20
> **Elotero said:**
> Thank you fro your help.. as soon as i get home i will try and tell you how it goes... a thousand thank yous!!!!!!!!!!!!!

One further thought.  **If you have access to a Windows PC** with USB - you could just run the .exe on the Windows PC, then copy the extracted files onto a USB memory stick (or email them to yourself), and that should work on Ubuntu.

This would save a lot of hassle (and is how I installed my ndiswrapper driver).

---

### Post by Elotero on 2007-06-20
I had to go with this last method.. still no dice.. unwrapped the file in my girls PC and no dice.. no .inf extension.. inx and iss.....

---

### Post by ugm6hr on 2007-06-21
> **Elotero said:**
> I had to go with this last method.. still no dice.. unwrapped the file in my girls PC and no dice.. no .inf extension.. inx and iss.....

Are you sure that .exe file was actually a Windows driver?  I'm fairly certain that Windows (98-XP) requires a .inf and sometimes .sys (from memory - maybe incorrect) to get wireless to work.  Sometimes it's worth trying drivers for all Windows versions - sometimes 98 works better than XP.

What is your wireless card brand / model / version?
Try typing *lspci* (for internal/PCMCIA/PCI) or *lsusb* (for USB) in Terminal to see what Ubuntu identifies it as.

Check the ndiswrapper wiki to see if it works with your card, and where to get the correct driver from:
[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/)

This is of course assuming that there isn't a native Linux driver available.

---

### Post by BlingStudly on 2008-06-04
Sorry folks I realize this is an old thread but my 2 cents: I use the standard Archive Manager to open EXE archives.

---

