---
title: "virtual box in linux mint"
date: 2010-02-27
forum: New to Ubuntu
---

### Post by misswham on 2010-02-27
i downloaded virtual box from the repositories in LM.  it is 3.0.1.  Is it true that this version of VB doesnt have usb support?  I remember when I put it in Ubuntu 8.04, I was told only the version off of the virtual box website had USB support.  Is this still true?  I have already installed XP on it and it used a lot of harddrive space to do it.  If I DO need the one from the website for usb support,  How do i override the one I already have even though I have already alloted 50 gbs of space for XP.

---

### Post by cariboo on 2010-02-27
I can't tell whether the open source version of virtualbox can acces usb devices, as I use the closed source version. To check, start virtualbox, and on the main page scroll down to usb and plug in a usb device and see if it's detected.

What are you doing with XP, that you need 50Gb's of hard drive space. I usually run XP on a 8Gb virtual drive which includes a full Office 2K installation and I still have plenty of space to install more.

---

### Post by misswham on 2010-02-27
All of them show up in the usb part but when I plug them in they are NEVER recognized in XP.  When I loaded it before, it wouldnt show up and I was told that the version in the repositories did not support usb so I just erased the whole harddrive and started over with the installation of hardy and VB and I didnt want to do it again.  I went to usb filters on each device and checked yes and still nothing and then i went back and checked yes and still nothing then it dawned on me that I should have downloaded it from the site.  So I was just wondering if that was the problem here.

I have 750 gbs of space and I was afraid that only 10 mbs wasnt enough for the OS and the upgrades and my printer, scanner, lotus office, microsoft office etc.

---

### Post by misswham on 2010-02-27
I was told to upgrade to the newer version and I tried but it said 

Error: Conflicts with the installed package. 

Can someone please tell me how to rectify this without having to go and reinstall the whole OS and VB and XP?

---

### Post by JKyleOKC on 2010-02-27
Open up Synaptic, find VirtualBox in its list of installed programs, click its checkbox and select "Remove" from the popup menu that results. Then click "Apply" and the existing VirtualBox program will be removed. However your XP installation will remain on your hard drive, as will the hidden VirtualBox directory in your home directory.

Next, go to the VirtualBox web site's downloads area and download the appropriate version; there are different versions there for the different versions of Ubuntu. Once it's downloaded to your system, find the file in Nautilus and double-click it. This will bring up the installer to put the new version in place. You may have to run an additional command to create the necessary driver, but this may not be necessary. If it is, you'll get a message telling you what to do the first time you try to launch VirtualBox.

Once you get to the VirtualBox screen, you'll find your XP installation is still there and is ready for use. However you'll need to install the Guest Additions again, since they are slightly different for the newer version 3.1.4...

---

### Post by misswham on 2010-02-28
you said to find the file in nautilus.  where is nautilus?  i went to preferences and clicked nautilus actions configurations and didnt see anything here either.

---

### Post by JKyleOKC on 2010-02-28
Sorry about that; I forgot that Mint uses IceWM! There should be something similar to "Add/Remove Programs" but if you can open a terminal window just type "sudo apt-get remove VirtualBox" (without the quotes) into it. Note the capital letters in the program name! When asked for your password, type the login password; you won't see any indication that you are typing but it's going in okay. That will remove the existing vbox program and you can then download the one from their web site and install it with no conflict.

---

### Post by misswham on 2010-02-28
thanks got it to work.

---

