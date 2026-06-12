---
title: "ndis wrapper: myriad of different ways to install, which is easiest?"
date: 2011-03-12
forum: New to Ubuntu
---

### Post by Bob Abouille on 2011-03-12
I've seen Ubuntu users tell newbies to:

1) Use device manager
2) Use Synaptic
3) Insert install CD and go to terminal
4) Use software center
5) Use the GUI ndiswwrapper installer
Each  of these options require a different set of follow up instructions. The results are permutation upon permutation of different, time-consuming actions to take. 

I'm not bright enough for that. I am searching for one, single Best Practice for a newbies to make ndiswrapper work.
 
I have tried what I was told should be the easiest, using ndiswrappergtk. I used Synaptic to import ndiscommon successfully, I installed ndiswrappergtk successfully, but I could not find any application afterwards and my wireless still doeesn't work.

I do not mind putting in the time to eventually use Ubuntu, if I can eventually use it. But right now, it just seems like Ubuntu is made for people who are smarter than me. Which is a shame, because I am trying to extricate myself from the for-profit world in all fronts of my life. Not to mention Windows 7 hates my usb ports.

I even put an ad on craigslist for a Linux mentor, but in Buffalo, the pickings are thin.

---

### Post by pi3.1415926535... on 2011-03-12
Sorry, I was not able to determine whether you had been able to install ndiswrapper. [Here]("http://sourceforge.net/projects/ndiswrapper/files/") is the sourceforge download, I believe that it require compiling.

---

### Post by bkratz on 2011-03-12
ndisgtk is the gui, not ndiswrappergtk. It will automatically load the ndiwrapper files you need and show up under system>>administration>>windows wireless drivers.

---

### Post by wep940 on 2011-03-12
Well, the normal situation in which one would use ndiswrapper is if they do not have any way to connect to the internet - meaning you can't hardwire a connection temporarily between your PC and the router. Ndiswrapper should really be used as sort of a last resort, as there are many drivers becoming available as restricted drivers and open source drivers. 
 

The normal procedure would be to hardwire a connection from your PC to your router, then open a terminal window and do the following:
[LIST]
[*]sudo apt-get update
[/LIST]Then look under system/administration/additional drivers and see if a driver shows, and if so, enabling it, then disconnecting the hardwire connection.
 

If, however, you are unable to do the above, or if you know you need to use ndiswrapper, the easiest way is as follows:
[LIST]
[*]Boot Ubuntu
[*]place the LiveCD in the drive
[*]using "Places", navigate to the /pool/main/n folder on the LiveCD. You will see two folders there - one for ndiswrapper and one for ndisgtk, the GUI'd front end for ndiswrapper.
[*]go to the ndiswrapper folder first, double-click on the ndiswrapper-common file to begin it's installation and wait for it to finish
[*]double-click on the ndiswrapper utilities to begin it's installation and wait for it to finish
[*]go to the ndisgtk folder next, double-click on the ndisgtk file to begin it's installation and wait for it to finish
[*]exit the terminal
[/LIST]The above has installed ndiswrapper and the easy to use GUI interface.
 

Next you need to locate the Windows driver files for your adapter - the .inf and .sys files, and copy them to a folder in Ubuntu. It's important to note 2 things about these drivers:
[LIST]
[*]they *MUST* be Windows XP drivers ONLY
[*]they *MUST* match the architecture of the Ubuntu you have installed - 32-bit drivers for 32-bit Ubuntu (the "normal" download), 64-bit drivers for 64-bit Ubuntu
[/LIST]Now, to install the drivers in Ubuntu:
[LIST]
[*]go to System/Administration/Windows Wireless Drivers to start ndisgtk
[*]click on the "add" or "new" (I don't have it in front of me right now)
[*]point it to the .inf file for your driver
[*]click "OK" or whatever the prompt is
[*]exit ndisgtk
[/LIST]Now check to see if wireless is enabled and works:
[LIST]
[*]right-click on the network manager icon and be sure "Enable Wireless" shows and is clicked to be enabled. If it doesn't show or is greyed out, stop here and post back to the forum for more help
[*]left-click on the network manager icon and see if wireless networks show
[/LIST]Other things to remember:
[LIST]
[*]if you use MAC filtering on your router, the MAC address for the adapter must be in the routers table or you won't be able to connect
[*]if you use encryption, be sure to select the correct type and enter in the password/passphrase as required
[*]if your network is "hidden" - meaning the router does not broadcast the network name - then you *must* use the "Connect To Hidden Network" option in network manager
[/LIST] 
EDIT:  I should add that for the vast, vast majority of users there is no need to download the source code for ndiswrapper and compile it.  There are some older posts out there for using ndiswrapper that say you need to do so, but just loading it from the LiveCD works fine.

---

### Post by beew on 2011-03-12
What are you trying to install with ndiswrapper? I think that is something of the past when there was no Linux driver for some wifi cards and as a result people were forced to use Windows drivers with a wrapper. This is definitely not recommended except as a last resort.

---

### Post by wep940 on 2011-03-12
> **beew said:**
> What are you trying to install with ndiswrapper? I think that is something of the past when there was no Linux driver for some wifi cards and as a result people were forced to use Windows drivers with a wrapper. This is definitely not recommended except as a last resort.
As per the opening of my post.....

---

### Post by beew on 2011-03-12
The easiest way is to spend $15 and get a usb wireless card. :) Seriously, considering that you need to use ndiswrapper you must have an old machine.

---

### Post by bkratz on 2011-03-12
> **beew said:**
> The easiest way is to spend $15 and get a usb wireless card. :) Seriously, considering that you need to use ndiswrapper you must have an old machine.



Well, be careful, my usb wireless device has to use ndiswrapper!

---

### Post by beew on 2011-03-12
> **bkratz said:**
> Well, be careful, my usb wireless device has to use ndiswrapper!

Yes, do some searching before buying. I was lucky, I had one that I used in XP before I knew Ubuntu(internal card dead) and it works out of the box with Ubuntu, plugged in and connected, no fuss. In XP I had to install drivers using a mini CD.

---

### Post by Bob Abouille on 2011-03-12
Actually, it turns out I first installed Ubuntu 10.10 without connecting to a LAN...so I uninstalled, and reinstalled while connected to a wire, and Ubuntu took care of it all during installation. I made sure to check "install updates during installation" during the setup process.

Wireless works fine, writing to you on it right now.

Thanks for all the help and occasional trash talking.

---

