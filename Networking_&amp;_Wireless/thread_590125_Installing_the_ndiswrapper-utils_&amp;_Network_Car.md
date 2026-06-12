---
title: "Installing the ndiswrapper-utils &amp; Network Card"
date: 2007-10-24
forum: Networking &amp; Wireless
---

### Post by cybergig on 2007-10-24
I have looked on the v7.04 CD which the help file claims that the ndiswrapper-utils is located within the CD so I can configure the network but I don't find it. Furthermore I do not know why the operating system doent even detect my wireless hardware but it doesnt, as far as I know it is a Bordercom linksys compatible network card, my father bought it and stuck it into my PC a while back so I don't know which make/model it is.  I would like some help in resolving my little problem, I have tried installing v6.06 and getting it to work, and v7.04 but neither claims to see my network card. I have checked the device profile there (or whatever it is) and the OS sees the card perfectly but everywhere else it doesnt see it at all, so I figured I would use the windows driver since I was able which is where I am stuck now. The ndiswrapper-utils isn't located on the CD if it is I'm having trouble seing it via the add remove porgam utility. I will be reinstalling xandros since I can get that to work, I will look forward to your reply.

I run Feisty Fawn, waiting for the other CD's to come in before I try 7.10

---

### Post by Bob69 on 2007-10-24
I don't believe you will find the ndiswrapper file on the 7.04 CD.  At least I was not able to do so.
To see the type of network card you have do the following:
Start the Terminal program.
type without the quotes "lshw -C network"  -- This should show the interface and the driver
associated with each network device.

I did a google search and downloaded the ndiswrapper files:
1.  file: ndiswrapper-common_1.38-1ubuntu1_all.deb

2.  file: ndiswrapper-utils-1.9_1.38-1ubuntu1_i386.deb

I was able to install them using the package manager.

Then you need to find the window drivers for your card and place them
in your home folder. There should be two files.  One ending in .inf and the other in .sys. Change to that folder.

Now do the following:
1.  sudo ndiswrapper -i ( yourfilname.inf)
2.  ndiswrapper -l     (Shows if the driver was loaded)
3.  ndiswrapper -m
4.  modprobe ndiswrapper

Hopefully this will get you up and running.  I am no expert and I found all this info
from other posts on the Ubuntu forums.  Good Luck.

Bob69

---

### Post by Onay on 2007-10-24
Here's some advice from weeks of my own struggles.

I installed ndiswrapper .deb packages, and it always falsely worked. After looking into the installations themselves, I found out that something was corrupt or not installed correctly. I'm not going to say that this is an easy fix, but it isn't anything crazy.

In a nutshell, you need to install build-essential tools from the command line, synaptic, or the Live CD. then get the ndiswrapper source **(Important: get 1.47; Later versions freeze up gutsy!)** from sourceforge. Do a "make uninstall && make && sudo make install" and the correctly working version will now work.

Now you can install your drivers, and "sudo depmod -a" and "sudo modprobe ndiswrapper" it to get it working. Hopefully that helps.

I also sent in a tutorial, but it hasn't been approved yet I guess.

---

### Post by cybergig on 2007-10-24
Hi I tried both of your suggestions and I'm still not getting anything to work, I downloaded the wrapper and the ndsgtk, didn't get to the ndsgtk part yet because I cant seem to install the wrapper. Anyways, when I get to the make part it reads the install file in the package but a whole lot of errors come up and I followed it by instruction. It has been several years and I have not been able to connect to the internet from ubuntu. It's amazing that I can connect via fedora, xandros and suse but not ubuntu. I went through all the documentation for 6.06, 6.10, and 7.04 and tried all of them, all the stuff in the documentation I mean. I also followed both of your advice and I find myself pissed that I have been on this for several days and I can't get it to connect at all let alone the "ndiswrapper" problem. Now could an official ubuntu guy point out exactly what needs to be done because I'm at a loss.

The reason why I really want ubuntu is because I heard it was great and I want full experience with it instead of the other flavors but if this keeps up its the trash bin. I am stuck with feisty, I haven't gotten gusty yet... but anyways... I got my card information and it says theres a driver installed for it, yet nothing happens.

Broadcom BCM4303

Edit:
Now that I go through the supported network cards list, its not even listed :| so does that mean I'm totally screwed until somethings done within the ubuntu community?

---

### Post by cybergig on 2007-10-25
Okay I ran into another snag, I finally managed to get the ndiswrapper installed after 4-5 formats... again.. Now, the hardware isn't being seen at all, ubuntu claims it isn't there (Well the ndisgtk.. thats where I saw it) I unplugged and replugged the hardware but still nothing. Any ideas?

---

