---
title: "The first Hurdle"
date: 2010-09-28
forum: New to Ubuntu
---

### Post by 1000piecepuzzle on 2010-09-28
I am new to Linux and Ubuntu, I installed Ubuntu 9.10 onto my old laptop and formatting the previous windows operating system. 

I love how smooth it works and was excited to start learning more about the terminal and getting a few programs installed along with an internet connection. 

However, I've trying to set-up a wireless internet connection. 

I started by following this tutorial and downloading a ndiswrapper and transfering it onto my laptop via usb stick but was stopped by this seemingly simple error = 

gzip: stdin: not in gzip format
tar: Child returned status 1 
tar: Exiting with failure status due to previous errors

Having searched forums extensively I can't seem to find a single straight forward answer. I tried strings of different commands but it seems like maybe i just need a program such as unrar or what? 

Thanks 
x

---

### Post by andrewthomas on 2010-09-28
What tutorial are you referring to?

What kind of wireless card do you have?

---

### Post by 1000piecepuzzle on 2010-09-28
I forgot to post the link

its [here]("http://ubuntuforums.org/showthread.php?t=112526")

and my wireless card info is = 

88w8335 Libertas 802.11b/g Wirelees 
Marvell technology group Ltd.
32 bits
version 43

etc.

At the moment I haven't even reached the issue of configuring my wireless though, its the problem with unzipping a file 
(a task which I'm sure I'll need to do alot more in the future!) 

thanks for the response

---

### Post by Paqman on 2010-09-28
First place to look is System > Admin > Hardware drivers. There may be a driver for your wifi card you can install from there.

---

### Post by 1000piecepuzzle on 2010-09-28
but I don't want to move on from the problem of unzipping a file! 

Surely unzipping a file is a simple affair? I'm just missing the simple answer??

---

### Post by Jcarr_toonist on 2010-09-28
Is this the command that you are using?

> tar -zxvf nameOfArchive.tar.gz

Trying removing the z flag from the command.

---

### Post by ibizatunes on 2010-09-28
If it was me, i would download 10.04 LTS release, as 9.10 wont have the lastest drivers (kernel), and your wireless card may work out of the box :-)

---

### Post by bbqsandwich on 2010-09-28
> **ibizatunes said:**
> If it was me, i would download 10.04 LTS release, as 9.10 wont have the lastest drivers (kernel), and your wireless card may work out of the box :-)

I second this. Is there a reason you need 9.10? More wireless cards work out of the box, no ndiswrapper needed, as each new version of Ubuntu comes out. :)

---

### Post by bruno9779 on 2010-09-28
What is exactly the name of the file that you are trying to open, and what command is giving you those errors?

Also, the usb stick won't do. You will need to do some updates, and install stuff from the command line. ("apt-get install" fetches programs from ubuntu servers and installs them)
So, it is best if you plug the ethernet cable while you set up the wifi access

The following tutorial is tailormade for you card, and comes from [launchpad]("https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/120570").

> Step 1: Open Terminal from "Applications->Accessories->
Terminal"

Step 2: Run the following commands (copy-paste each line below to the Terminal then hit <enter> after each line)

sudo aptitude update
sudo aptitude install ndisgtk ndiswrapper-common ndiswrapper-modules-1.9 ndiswrapper-utils-1.9

Step 3: Download the Windows driver file Marvell_88w8335_WinXP.tar.gz provided by forumuser caljohnsmith at the following location:

[http://ubuntuforums.org/showthread.php?t=976928](http://ubuntuforums.org/showthread.php?t=976928)

You will first need to register and log into ubuntuforums with your own username before you can download the file. But it should be worth the effort.

Step 4: Open a Terminal and enter the following command to start ndisgtk:

gksudo ndisgtk

Click on "install new driver". Click on "None", next to "Location". Navigate to the location where you extracted the contents of the downloaded file Marvell_88w8335_WinXP.tar.gz. The extracted folder contents should contain the file mrv8335.inf

Select this driver file mrv8335.inf to install it.

Step 5: Open Terminal from "Applications->Accessories->
Terminal" and enter the following command in Terminal:

gksudo gedit /etc/modules

# Now add the module ndiswrapper to the list of modules to be automatically loaded at boot by adding

ndiswrapper

# to the end of the /etc/modules file. (Gedit editor automatically opens)

Step 6: Reboot your pc and retest wireless

Step 7; If wireless still does not work after rebooting, or if authentication does not work, try disabling security on the router and retry connecting via wireless.

---

### Post by cariboo on 2010-09-28
> **1000piecepuzzle said:**
> but I don't want to move on from the problem of unzipping a file! 

Surely unzipping a file is a simple affair? I'm just missing the simple answer??

Doesn't file-roller startup when you double-click the file?

---

### Post by 1000piecepuzzle on 2010-09-28
Thanks for the responses.

There was no particular reason for me to install 9.10 as I just had it on a CD laying around. 

My Ubuntu is currently updating and upgrading over an ethernet cable, I'll try the steps by bruno and see how far that gets me 

Thanks

---

### Post by Calash on 2010-09-28
> **1000piecepuzzle said:**
> Thanks for the responses.

There was no particular reason for me to install 9.10 as I just had it on a CD laying around. 

My Ubuntu is currently updating and upgrading over an ethernet cable, I'll try the steps by bruno and see how far that gets me 

Thanks

Before trying all that, check the Hardware Drivers tab under System>Administration.  With the updates the native drivers may be available.  If not go ahead and follow the instructions posted.

---

### Post by 1000piecepuzzle on 2010-09-28
Brilliant! My first Linux system is ready and wireless. 

The driver worked fine and connected without a hitch, I imagine that linux didn't take to kindly to a file being transfered over a memory stick. 

I'd like to make an innocuous superficial comment about the desktop colours of 10.04 feeling rather drab compared with 9.10.

---

### Post by oldos2er on 2010-09-28
> **1000piecepuzzle said:**
> I'd like to make an innocuous superficial comment about the desktop colours of 10.04 feeling rather drab compared with 9.10.

Themes and backgrounds are easily changed: [https://help.ubuntu.com/community/UbuntuEyeCandy](https://help.ubuntu.com/community/UbuntuEyeCandy)

---

