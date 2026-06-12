---
title: "[SOLVED] How do I download network manager gnome and transfer it to another pc?"
date: 2008-01-24
forum: Networking &amp; Wireless
---

### Post by spleencheesemonkey on 2008-01-24
Hope I have placed this question in the right forum.
My ralink wireless card suddenly stopped working but my ethernet connection remained fine. In an uneducated effort to solve the problem I stupidly deleted network-manager-gnome from synaptic package manager which has left me with no internet connectivity at all.

My question is: Is it possible to  install network manager from the gutsy live cd?  If so, how please.

I have another option of transferring the package files from another PC (I have a bootable version of Gutsy on a usb key) - how do I download, save then transfer and install the packages to my PC?  I can't see an option to choose where to save the package files to within synaptic package manager - and wouldn't know where to save the files to, to get them to install properly.

I hope this makes sense and somebody can help.

---

### Post by hahahan on 2008-01-24
Spleencheesemonkey,

Do some reading and learn about the teminal config programs ( man iwconfig and dhclient ) and you will live happy without any GUI Networkmanagers. ALso [http://tldp.org/HOWTO/NET3-4-HOWTO.html](http://tldp.org/HOWTO/NET3-4-HOWTO.html) is a good source.

---

### Post by gwbennett on 2008-01-24
Or, if you're just looking for it to work rather than for an educational experience, you can go into "software sources" (system, administration) and add your CD as a source.

Then sudo apt-get install nm-applet or whatever the package name is.

Or, on a different computer you ca "sudo apt-get install -d packagename" and that will just download the deb pkg...then sneaker net it over to the other computer, and double click it to install.

---

### Post by spleencheesemonkey on 2008-01-24
hahahan - many thanks for taking the time to reply.  I may well look into that in the future, but for now I need a quick way of getting internet connectivity back on my PC.

---

### Post by spleencheesemonkey on 2008-01-24
gwbennet -  Thank you.  After adding the cd as a source, will I then have to navigate to the cd in the terminal before using apt-get?  

I guess I'm asking how it will know to look at the cd rather than trying (then failing) to connect to the internet to download it.

---

### Post by hahahan on 2008-01-24
Gwbennet offered you a solution if you want to stick to the GUI Networkmanager.
Asuming you have all the drivers installed and NO encryption involved you could try:
**Open a terminal:
**type ifconfig -a
if there is no line containing UP for your Ethernetcard do :sudo ifconfig YOURNIC up.
**type sudo iwconfig YOURNIC essid NAMEOFNETWORK
**type sudo dhclient YOURNIC
If you are lucky Y'll be online now.
But again, getting familiar with the terminal configuration tools will make your live easier.

---

### Post by spleencheesemonkey on 2008-01-24
Many thanks to both of you for your responses.  I will try them when I get home.

---

### Post by spleencheesemonkey on 2008-01-24
Not having much luck here I'm afraid.  The CD was already added as a source in the software sources menu that you provided however when I tried to install network-manager-gnome in the terminal it tried to connect to the ubuntu server to download the file and subsequently failed.
When I tried to download the package on another computer I get the following:

sudo apt-get install -d network-manager-gnome
Reading package lists... Done
Building dependency tree       
Reading state information... Done
network-manager-gnome is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 79 not upgraded.
3 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Download complete and in download only mode

I take it this is telling me that it hasn't downloaded the package at all because the other PC that I'm using has it already installed?

Hope you people out there are still able to provide assistance.

---

### Post by jetsam on 2008-01-24
I think the third post in this thread has the answer to your problem:

[http://ubuntuforums.org/showthread.php?t=611967]("http://ubuntuforums.org/showthread.php?t=611967")

I guess the package manager knows that network manager has been updated since the release, so it doesn't want to install from the CD.  Hopefully the thread I linked to can fix you.

---

### Post by spleencheesemonkey on 2008-01-25
Many thanks to all of you who replied.  Now got the internet connection sorted by ethernet.....now to post my next thread which started all of this in the first place!

---

### Post by rosegarden78 on 2008-01-25
What about the repositories from Canonical from the local library?

---

