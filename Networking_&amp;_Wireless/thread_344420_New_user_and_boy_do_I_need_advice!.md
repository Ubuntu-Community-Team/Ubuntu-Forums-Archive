---
title: "New user and boy do I need advice!"
date: 2007-01-22
forum: Networking &amp; Wireless
---

### Post by Steiny1 on 2007-01-22
Hello, 

I installed Edgy last night and I have no idea how to use a Linux program. I desperately want to dump Windows but I have some learning to do.  In order to do this however I need to find out how to install my wireless card (PCI - Netgear WG311 v1) So I can continue to learn online .  I have seen posts where something called "breezy" allowed for the use of the card and then many more posts by people just like me who have no clue and need a hand.  In order for me to start to understand Edgy, I need someone who would have the patience to explain the process step by step to a person whose first look at the OS was last night at about 11PM.  Where do I get upgrades and other apps once I am on line again?  

P.S. - I have seen in the replies to some of these posts alot of code and commands which with a little experience I will learn, but currently I do not even know where to type the code or in windows talk, how to open a command prompt.  

Can someone please help?  


Thank you in advance for your effort and help...:D

---

### Post by cosborn72 on 2007-01-22
Congratulations.  You have chosen the right path.  Linux will do you right, and Ubuntu is the best place to start....=D> 


1.) First,  the "command prompt" in ubuntu is called the terminal.  I don't remember exactly what category it is under (it's different in gnome and KDE), but it should be labeled as terminal. 

Most of the forum people will use terminal commands, because it is easier than saying "open this window then click on this button and then do this and then this..."

When commands are posted in the forums, they usually can be copied and pasted into the terminal.  (just make sure you paste one line at a time).

2.) If you want to know the best place to start- go to: 

[http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)

I have been using Ubuntu for 2 years, and I'm still finding great stuff there.

3.) To get upgrades and updates, look for a program called Synaptic (or, if you are using KDE- you should have Adept).   This is a package manager that will allow you to install all kinds of new software, and you can update everything on your system with a few mouse clicks.

4.) Regarding your wireless card.  Linux's big hurdle into the mainstream computer market is that hardware manufacturers don't make a lot of drivers for it.  This means that installing hardware can be tricky.  I have used Linux on two laptops.   On the first, it took months of hunting answers to get the card to work.  On the second, it started working as soon as I installed ubuntu.

Search the forums for answers into how to get you card to work- although some of them might be heavy in the technical stuff.

Have you looked to see if there is a program call wireless network assistant.  It is possible that your card is working- ubuntu requires that you manually set up your wireless network, and i know that on my system, the card appeared inactive (no blinking light) until I actually tried to connect through the assistant.

---

### Post by esaym on 2007-01-22
You should perhaps start here for general help and knowledge: [http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper)

Hang out on these forums alot and read read read.

Wireless should work out of the box for that card.  Try perhaps installing networkmanager sudo aptitude install network-manager 

Installing software in ubuntu: [http://64.233.167.104/search?q=cache:DmPDS6o8cpMJ:monkeyblog.org/ubuntu/installing/+ubuntu+installing+packages&hl=en&gl=us&ct=clnk&cd=1](http://64.233.167.104/search?q=cache:DmPDS6o8cpMJ:monkeyblog.org/ubuntu/installing/+ubuntu+installing+packages&hl=en&gl=us&ct=clnk&cd=1)

the server is down so there is the google cache of it.  Look at the "Installing software with the terminal" section

Also I would recommend installing ubuntu 6.06 dapper instead of ubuntu 6.10 edgy. Edgy is more of a beta version and still has bugs and such.  Dapper will have support for the next 2 years while edgy will only have support for a few more months I think?

---

### Post by dsimpson on 2007-01-23
Hi, I am still in the learning process myself and can relate what it feels like to be at the very beginning of a learning process. I went through the same thing. Most replies are pretty generic in content, it seems that everyone on these forums assume that you know the basics. Here is a little more in depth info, sometimes you may be past this point but I don't want to give you any less than what is helpful. 

First, All code that you see in the posts are entered into Terminal, you find this by going to Applications/Accessories/terminal. If you don't understand exactly what is meant concerning entering a bit of code, ask! everyone is very helpful and will take the extra step to post it for you. 
Another important tool is Synaptic, you can find this at System/Administration/Synaptic. You will find that you will use this a lot at first, but eventually you will be entering more into terminal than at first.
The 3rd place I will mention is under Applications/(add/remove). This is another tool to add more functions, software, and tools to your system. 

For your specific problem you might start at add/remove and enable wireless assistant. Click on add/remove then internet and scroll down to wireless assistant, I used that for my Belkin router and it was a simple one step process, and then I was online. Networking to another computer, though is another issue. 

Take the advice and check out the link to the Ubuntu wiki and here is another that I found after much searching, most repliers to your posts will provide answers but don't list helpful links. I use and find most helpful [http://doc.gwos.org/index.php/DapperCust](http://doc.gwos.org/index.php/DapperCust)   -  you can go there and can most likely find a link to your version of Ubuntu.

I know this is a lot to take in at first, but I believe the best way is to totally dump Windows and jump in with both feet. I have my problems, but find it more exciting actually trying, (and succeding) to learn something useful about the computer as opposed to stupidly clicking the mouse button and depending on software that you have to purchase to run. The knowledge will come, and after a short time you begin to realize that you have learned more than you ever thought you would. Happy computing and welcome to Ubuntu.

---

### Post by Steiny1 on 2007-01-23
I wanted to thank each of you who replied to my question.  I will follow all of the advice given and see where I get.. Just an update..  I installed Automatix to assist me in installing ndiswrapper to allow me to install the correct driver for the wireless card.  As a matter of frustration, Automatix requires an internet connection to open and install ndiswrapper to install the driver to get an internet connection.  Wow!  I can't believe the full circle I just made! I will start over using your helpful tips..  

Thank you again..

---

### Post by Steiny1 on 2007-01-23
Okay, 

I tried to add the Wireless assistant program with Add/ Remove and found out that this option is not supported for my PC (I386).  Any other ideas?  I have also researchde and read the other info provided and nothing seems to work!  I have read that the Wireless card I have does work with Ubuntu, I just cannot figure out how to make it so.  

P.S. - Still works with Window!  What a shame!  I am sooo close to getting rid of Windows, I can taste it.  I cannot connect via regular Ethernet connection as the hardwire is about 75 feet away from the PC.  

If anyone else has some ideas, I would greatly appreciate your input.

---

### Post by esaym on 2007-01-24
> **Steiny1 said:**
> Okay, 

I tried to add the Wireless assistant program with Add/ Remove and found out that this option is not supported for my PC (I386).  Any other ideas?  I have also researchde and read the other info provided and nothing seems to work!  I have read that the Wireless card I have does work with Ubuntu, I just cannot figure out how to make it so.  

P.S. - Still works with Window!  What a shame!  I am sooo close to getting rid of Windows, I can taste it.  I cannot connect via regular Ethernet connection as the hardwire is about 75 feet away from the PC.  

If anyone else has some ideas, I would greatly appreciate your input.


It should work fine and is supported by the native linux wireless driver: [http://madwifi.org/wiki/Compatibility#WG311](http://madwifi.org/wiki/Compatibility#WG311)

I don't use edgy or gnome so I really can't help you.  I just know that I have never had a problem using several wireless cards from that list on computers that I installed the 6.06 dapper version on.

I will try to help you more with this in the coming days but right now I am very busy :o 

For now type these commands into the terminal and post what they say:
ifconfig
iwconfig

Each one will spit out info about your network cards...

---

### Post by dsimpson on 2007-01-25
Hi, I hope this might help, took it from Dapper/Edgy cust. advice. It will walk you through step by step, but, you must already be familiar with the terminal, as all the steps to install the software is entered there. Good luck with this...

How to: Broadcom Wireless cards without Ndiswrapper for Dapper and Edgy

    * In my edgy knot 2 testing I found that edgy users can stop the guide after competing stage 4 or 4b as it 'just works' with out network-manager if you fill in the SSID and set the wireless device to DHCP in the "networking" option under System > Administration 


This Should work with Apple hardware as well as PC's.

How to get a wireless card working in Ubuntu 6.06 or 6.10 with a Broadcom chipset 43xx


This guide assumes 2 things:

        * Wired Internet access on the machine with the wireless card on it, in my case i had a 10/100 LAN card that i was using as i couldn't get wireless to work which gave me full access to internet - although it is possible to put the files required on a CD and then add that CD as a repo in synaptic on the wireless machine, how to do this is not covered here, you could even extract the firmware on a different PC and place it in the right location on a remote PC using a CD/Pen drive taking a .deb of network manager with you.
        * A CLEAN install of dapper or edgy, most of the problems/failures in the responses to this guide have been because of unclean installs giving configuration that gets in the way of this guide and stops it from working, my dapper was installed during the Flight 5 stage and updated from there to knot 2 so its not necessary to reinstall from 6.0* or even if it has been updated from breezy but you might want to think about reinstalling if you've messed around with Ndis prior to this. 


Okay so you have a wireless card that shows up in ubuntu but doesnt connect to any wireless network?

The reason the card shows up but doesn't work is because ubuntu is only distributed with its driver (so it can recognize it) not with its firmware (so it can USE it) for legal reasons.

However you can take the firmware out of the windows drivers and put them into ubuntu and make the card work!

Follow these steps to get your wireless card working under ubuntu dapper 6.06:

To find out if your card has a broadcom chipset run the following command:
file.pngCode:

lspci | grep Broadcom\ Corporation

If that returns a string of numbers followed by the words Broadcom Corporation and then some more numbers then your in luck! But if not, try my guide anyway, it cant do any harm and it might work for you, its largely untested for cards other than mine and the success stories posted here so give it a go and see!

Here is my output from doing this:
file.pngCode:

lspci | grep Broadcom\ Corporation 0000:02:0d.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)


(edited) If you get the following output:
file.pngCode:

lspci | grep Broadcom 05:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

this guide WILL NOT work for you. The reason behind this is that the firmware for the bcm4318 is still messed up. Those responsible for the bcm43xx project are still working on hacking this so that it does work. Until then you will be stuck using NDISwrapper. If you would like more information, please refer to the forum topics at the bottom of this article.(/edited) [CrippsFX]

Prerequisite

        * Ubuntu dapper
        * A wireless card that shows up in Ubuntu
        * A driver installation CD (for Windows) OR a driver for your card from the internet
        * Access to the Ubuntu Universe Repository 


[edit]
1) Ensure you have access to the other ubuntu repos

Follow the intructions on the second heading from this page to ensure you have the universe enabled [https://wiki.ubuntu.com/MOTU/Packages?action=show&redirect=UniversePackages](https://wiki.ubuntu.com/MOTU/Packages?action=show&redirect=UniversePackages)


[edit]
2) Copy your windows driver to your desktop

Use this driver with preference to any other:
[http://boredklink.googlepages.com/wl_apsta.o](http://boredklink.googlepages.com/wl_apsta.o)
if this fails, your could use any of these:

        * Copy the driver from the CD that came with the Card
        * Copy it over from your windows partition if you have access to it, it will be located here: /Windows/System32/Drivers/bcmwl5.sys
        * Obtain it from here -http://sidulus.textdrive.com/bcmwl5sys.zip
        * Get any driver for your card of any date from their website - use this if initially you are not successful first tome try some newer/older drivers 


[edit]
3) Install bcm43xx-fwcutter

Open a terminal (dont worry) and type the following:
file.pngCode:

sudo apt-get install bcm43xx-fwcutter

It will ask for your password and may ask you to press y to install, but dont worry its really easy

GUI Alternative: go to System in the top Gnome bar then Administration then Synaptic Package Manager
From here click Search and search for bcm43xx-fwcutter
synapticsrearch.png

Right click on its entry in the package window, select Mark for Installation and then click apply
synapticselect.png


[edit]
4) Extract your Cards firmware from the driver

Open a terminal (dont worry) and type the following:
file.pngCode:

sudo bcm43xx-fwcutter -w /lib/firmware ~/Desktop/wl_apsta.o

This will create lots of new files in the /lib/firmware directory, this is the firmware part of the driver that will make your card work with ubuntu!
libfirmware.png


[edit]
4B) Extract your Cards firmware from the driver

Just to be safe we'll put the driver in the kernel folder too

file.pngCode:

sudo bcm43xx-fwcutter -w /lib/firmware/`uname -r` ~/Desktop/wl_apsta.o


You may have to repeat this step each time the kernel is updated or you may not, your results may vary.

Note The location and name of the .o file for this command may differ in your case, if you really get stuck type bcm43xx-fwcutter and then hit space, find your file using the GUI and then drag and drop it into the terminal.


[edit]
5) Install Network Manager

I find that this is the best way to manage wireless connections
file.pngCode:

sudo apt-get install network-manager-gnome

It may ask for your password and may ask you to press y to install, but dont worry its really easy

You may find that Network Manager adds itself to system > preferences > sessions >startup programs or you may not, if you find its not included, add
file.pngCode:

nm-applet --sm-disable

as found here: [http://ubuntuforums.org/showpost.php?p=1082980&postcount=32](http://ubuntuforums.org/showpost.php?p=1082980&postcount=32) , Network Manager might not work for Apple users, he says that a program called wifi-radar worked for him instead so if network manager is no good for you try this program instead

This might apply for non apple users as well [https://wiki.ubuntu.com/WifiDocs/Driver/bcm43xx#head-cf3f0ec9146ae9441b39c4bed74e5d044ef78d2f](https://wiki.ubuntu.com/WifiDocs/Driver/bcm43xx#head-cf3f0ec9146ae9441b39c4bed74e5d044ef78d2f)


[edit]
6) Bookmark this page and Reboot

Press Ctrl + D and then click on add
bookmark.png

Then log out & reboot Return to this page after logging back in again


[edit]
7) Use your new Wireless connection

From what i remember network manager should now show up by your clock and display your current connection, if your lucky it will show a series of bars, this means your now using your wireless connection so lucky you!
nm.png

If it doesnt, right click on it and tick "Enable Wireless" then left click on it and select the wirless network of your choice.

Thanks, i hope this helps...


[edit]
Issues:

    * Ensure the router you are connecting to supports 802.11 B connections as this is what the card is now set up to use, check if your router has a "mixed" 

setting rather than a G only setting which it should as G is backwards compatible with B

For anyone that is having problems, try this:
file.pngCode:

modprobe bcm43xx

and reboot

Information about networkmanager

[https://wiki.ubuntu.com/NetworkManager](https://wiki.ubuntu.com/NetworkManager)

people seem to be having trouble getting this specific card: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02) working using this guide, take a look at this post for help:

[http://ubuntuforums.org/showpost.php...4&postcount=43](http://ubuntuforums.org/showpost.php...4&postcount=43)

or

[http://ubuntuforums.org/showpost.php...&postcount=218](http://ubuntuforums.org/showpost.php...&postcount=218) if your looking to Ndis instead

If you find your driver comes in a windows EXE format, typically this will just extract the drivers and can be run using Wine and then collected from your wine directory in the same places you can find them in windows you could try renaming them to filename.zip and seeing if they open that way too.
[COLOR="Lime"]Retrieved from "http://doc.gwos.org/index.php/BroadcomWireless"
[/COLOR]
Categories: Networking | Dapper
Views

    * Article
    * Discussion
    * Edit
    * History

Personal tools

    * Create an account or log in

Navigation

    * Main Page
    * Community portal
    * Current events
    * Recent changes
    * Random page
    * Help
    * Donations

Search
 
Toolbox

    * What links here
    * Related changes
    * Special pages
    * Printable version

MediaWiki

    * This page was last modified 22:47, 5 October 2006.
    * This page has been accessed 2,366 times.
    * About Ubuntu Document Storage Facility
    * Disclaimers

I know this is a lot of information with very little support, but not knowing how far along you are on the learning curve I cannot say whether this will help you or not, but wanted to send this in case you can utilize it. :biggrin:

---

