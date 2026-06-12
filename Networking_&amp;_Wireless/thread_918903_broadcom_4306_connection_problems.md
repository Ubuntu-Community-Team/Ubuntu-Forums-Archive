---
title: "broadcom 4306 connection problems"
date: 2008-09-13
forum: Networking &amp; Wireless
---

### Post by bryce4president on 2008-09-13
I'm having trouble connecting to my wireless network.  The card seems to be working considering the fact that I can see the network, but when I attempt to connect to it nothing happens. It just sits there spinning and never connects.  

I'm running Fiesty, with a Linksys WPC54G first version card.  The thing that makes me wonder is the fact that when I use the gui it shows my wireless card as eth1 and not as wlan0.  Will this make a difference?  How do I change it if it does?

---

### Post by bryce4president on 2008-09-13
So I've been pissing with this thing off and on all day trying different stickies and such.  The last thing I tried to do was run this ```
 sudo aptitude install ndiswrapper-utils-1.9
```

It didn't work, I got this error...
```
debconf: unable to initialize frontend: Dialog
debconf: (Dialog frontend requires a screen at least 13 lines tall and 31 columns wide.)
debconf: falling back to frontend: Readline
Selecting previously deselected package ndiswrapper-common.
(Reading database ... 106633 files and directories currently installed.)
Unpacking ndiswrapper-common (from .../ndiswrapper-common_1.38-1ubuntu1_all.deb) ...
Selecting previously deselected package ndiswrapper-utils-1.9.
Unpacking ndiswrapper-utils-1.9 (from .../ndiswrapper-utils-1.9_1.38-1ubuntu1_i386.deb) ...
Setting up bcm43xx-fwcutter (006-1) ...
--19:22:18--  http://boredklink.googlepages.com/wl_apsta.o
           => `wl_apsta.o'
Resolving boredklink.googlepages.com... 209.85.173.118
Connecting to boredklink.googlepages.com|209.85.173.118|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
19:22:19 ERROR 404: Not Found.

dpkg: error processing bcm43xx-fwcutter (--configure):
 subprocess post-installation script returned error exit status 1
Setting up ndiswrapper-common (1.38-1ubuntu1) ...
Setting up ndiswrapper-utils-1.9 (1.38-1ubuntu1) ...
Errors were encountered while processing:
 bcm43xx-fwcutter
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up bcm43xx-fwcutter (006-1) ...
--19:22:20--  http://boredklink.googlepages.com/wl_apsta.o
           => `wl_apsta.o'
Resolving boredklink.googlepages.com... 209.85.173.118
Connecting to boredklink.googlepages.com|209.85.173.118|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
19:22:21 ERROR 404: Not Found.

dpkg: error processing bcm43xx-fwcutter (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 bcm43xx-fwcutter

```

I don't know why it is failing, any help would be greatly appreciated.

---

### Post by Crafty Kisses on 2008-09-13
First, try the following:
```
sudo apt-get install ndisgtk
```
After you do that, you need to download the drivers, and you can get the drivers right [**here**]("ftp://ftp.linksys.com/pub/network/wp...ility_v2.0.zip"). After you have downloaded the drivers, unzip the folder, and try running the following in the Terminal:
```
sudo ndiswrapper -i lsbcmnds.inf
```
Then when you have the .inf file, open up **ndisgtk**, then you can try installing it from there.

---

### Post by Crafty Kisses on 2008-09-13
I also forgot to mention, you may need to install some other packages for this card, but try and see if this works first.

---

### Post by bryce4president on 2008-09-14
I did the ```
sudo ndiswrapper -i lsbcmnds.inf
``` 

It told me that lsbcmnds.inf already exists.

I can't install ndisgtk right now because I'm having some trouble with update-notifier right now.  Once I get that fixed I'll be able to install it.  It really creates a mess when your computer shuts down in the middle of a version upgrade ;)


One other question... Does the fact that I can see my network and that it shows a good signal strength mean nothing?  My card still isn't working even thought I can see it but just not connect?  How is this possible?

---

### Post by bryce4president on 2008-09-14
Well I got my broken packages straightened out and got upgraded to Gutsy.  When I upgraded I got the message about using restricted drivers.  I enabled the Broadcom driver from the restricted driver manager.  I chose to download the one that they suggested instead of browsing and loading what I had.  After that I rebooted and my wireless now works.

Thanks for all your help.

---

