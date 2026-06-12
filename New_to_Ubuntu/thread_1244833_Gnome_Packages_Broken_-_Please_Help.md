---
title: "Gnome Packages Broken - Please Help"
date: 2009-08-19
forum: New to Ubuntu
---

### Post by Unethical on 2009-08-19
-------------------------------------------------------------------------------------------------------------------------------

(Ubuntu Hardy)
My desktop became unresponsive after I ran:

> sudo dpkg --configure -aI decided that the problem had to do with GNOME, so I tried this:

> sudo apt-get install gnome... I now have this:

> simon@simon:~$ sudo apt-get install gnome
[sudo] password for simon: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  gnome: Depends: gnome-desktop-environment (= 1:2.20.2.2) but it is not going to be installed
E: [COLOR=Magenta]Broken packages[/COLOR]
simon@simon:~$THE PROBLEM: 

Incase you haven't noticed, the packages are broken. How can I fix this problem? 

I also have a few other questions...
1) can I do a fresh install of Ubuntu WITHOUT a disc drive? (I'm using a netbook. Keep in mind I couldn't fit Ubuntu on a 2GB Flash Drive).
2) I know this may sound EXTREMELY stupid, but I accidentally removed my battery and wireless signal from my panel, and can't get them back in proper form. (I can get the battery one back, but it is just a little graphic of a plug). How can I return these to the panel?

TIA, 

U N E T H I C A L 

-------------------------------------------------------------------------------------------------------------------------------

---

### Post by Unethical on 2009-08-20
-Bump-

---

### Post by bapoumba on 2009-08-20
Please run 
```
sudo apt-get update
```

Then post the output to
```
sudo apt-get dist-upgrade
```
If it asks you to run
```
sudo dpkg --configure -a
```
Please do so. Did you have a power failure or closed the window while upgrading? How did this happen ?

---

### Post by Unethical on 2009-08-20
When I ran

> sudo apt-get upgrade 

It said everything was there. So I ran 

> sudo apt-get dist-upgrade

And the only thing that was upgraded was Wine. I was never asked to run anything else. 
=S Sorry, I am a very new Linux user... 2 days, LOL :].

---

### Post by fooman on 2009-08-20
[quote=Unethical]

I also have a few other questions...
1) can I do a fresh install of Ubuntu WITHOUT a disc drive? (I'm using a netbook. Keep in mind I couldn't fit Ubuntu on a 2GB Flash Drive).
2) I know this may sound EXTREMELY stupid, but I accidentally removed my battery and wireless signal from my panel, and can't get them back in proper form. (I can get the battery one back, but it is just a little graphic of a plug). How can I return these to the panel?
[/quote]

1) you should be able to fit ubuntu onto a 2gig flash drive (i have done so).  first you will need the ubuntu .iso file,  so download it to your hard drive. next...go to system > administration > usb startup disk creator

that will walk you through loading it onto the flash drive.

2) right-click on an empty place in the panel and choose "add to panel"....find "notification area",  click once on it and then click the "add" button.

hope that helps.

---

### Post by Unethical on 2009-08-20
Thanks for the USB tip, but the other doesn't work. It gets it on the panel, but not in the right spot, and when i move it, it won't go where I want it. I want it next to the date and time. 

U N E T H I C A L

---

### Post by fooman on 2009-08-20
> **Unethical said:**
> Thanks for the USB tip, but the other doesn't work. It gets it on the panel, but not in the right spot, and when i move it, it won't go where I want it. I want it next to the date and time. 

U N E T H I C A L

if you right-click and choose "move" it does not move??

when you right-click it....make sure "lock to panel" is not checked!  if there are other items next to the date/time....make sure they are not "locked" there as well.

---

### Post by fooman on 2009-08-20
for the broken packages...try opening synaptic (system > administration > synaptic package manager).  in the toolbar,  click edit > fix broken packages

see if that helps.  post back with any errors you see.

---

### Post by Unethical on 2009-08-20
Sorry, but could you link me to the .iso file? =3 
Thanks,

U N E T H I C A L

---

### Post by fooman on 2009-08-20
> **Unethical said:**
> Sorry, but could you link me to the .iso file? =3 
Thanks,

U N E T H I C A L
sorry,  meant to do so in the first post...


[http://www.ubuntu.com/GetUbuntu/download](http://www.ubuntu.com/GetUbuntu/download)

if using a netbook,  you may want to try the ubuntu netbook remix from here:

[http://www.ubuntu.com/GetUbuntu/download-netbook](http://www.ubuntu.com/GetUbuntu/download-netbook)

---

### Post by Unethical on 2009-08-20
> **fooman said:**
> 1) you should be able to fit ubuntu onto a 2gig flash drive (i have done so).  first you will need the ubuntu .iso file,  so download it to your hard drive. next...go to system > administration > usb startup disk creator

that will walk you through loading it onto the flash drive.

2) right-click on an empty place in the panel and choose "add to panel"....find "notification area",  click once on it and then click the "add" button.

hope that helps.

Under system>administration, there is no "USB Startup Disk Creator". D=

U N E T H I C A L

---

### Post by fooman on 2009-08-20
sorry,  did not realize you were using hardy....it is only included in intrepid and up.

no fear...you can still install the usb-creator by adding the following launchpad repo.

i know your new to all this,  so i will try to make this simple.

open a terminal (applications > accessories > terminal) and type or copy paste the following:

```
gksudo gedit /etc/apt/sources.list
```enter your password when prompted.  when the file opens,  copy/paste the following lines to the bottom of the file:

```
deb [http://ppa.launchpad.net/evand/ppa/ubuntu](http://ppa.launchpad.net/evand/ppa/ubuntu) hardy main 
deb-src [http://ppa.launchpad.net/evand/ppa/ubuntu](http://ppa.launchpad.net/evand/ppa/ubuntu) hardy main
```save and close the file.

back in the terminal,  type or copy/paste these commands,  one at a time and press enter after each:

```
sudo apt-get update
``````
sudo apt-get install usb-creator
```it should install correctly...after it completes,  check in system > administration and see if "usb creator" is listed.

---

### Post by Unethical on 2009-08-21
Awesome, I just installed 8.10 =D

Many thanks,
U N E T H I C A L

---

