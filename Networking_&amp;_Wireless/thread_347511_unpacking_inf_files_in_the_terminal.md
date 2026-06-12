---
title: "unpacking inf files in the terminal"
date: 2007-01-27
forum: Networking &amp; Wireless
---

### Post by helliewm on 2007-01-27
How do I unpack inf files in the terminal I am following these instructions and am stuck on point 7 and point 9 

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

7. Unpack the Windows driver by using the unzip, cabextract and/or unshield tools (run from the Terminal), and find the INF file (.INF or .inf extension) and the SYS file (.SYS or .sys extension). You may first need to install cabextract and unshield.

( i have installed  cabextract and unshield). How do I unpack the driver in the terminal it is an exe file? The driver is Belkin F5D7011_1212.EXE. It is on my Desktop. 

9. Make sure that the INF file, SYS file and any BIN files are all put into one directory.

How do I put them into one directory bin the terminal?

Helen

---

### Post by hggdh on 2007-01-27
It seems this file is a self-extracting ZIP file (at least per the Belkin download site doc: [http://www.belkin.com/support/article/?lid=en&pid=F5D7011&aid=5391&scid=221](http://www.belkin.com/support/article/?lid=en&pid=F5D7011&aid=5391&scid=221)

So you will need to unzip it. If you do not have unzip installed, you can install it by 'sudo apt-get install unzip'.

So. Open a terminal, and then:

mkdir inf
cd inf
unzip ../Desktop/F5D7011_1212.exe .


What you will have done here is created a subdirectory under your home directory, and expanded the zip there.

Now see if the the .inf and .sys files are there. If they are, go ahead with your intructions.

 I do not have this card, so I cannot tell you what to do if there are more than one inf and/or sys files.

---

### Post by helliewm on 2007-01-27
Since this post I have installed bcm43xx via Synaptic Package Management ( [www.svn.berlios.de](www.svn.berlios.de) it says my network card is supported). When I go to System, Administration, Networking I now see a Wireless Connection, this was not there before I installed bcm43xx. Is my network card now supported?

I am in the UK so I have a BT Home Hub Modem/Router which gives me a SSID BTHomehub-D130 and a hexidecimal wireless key on the back of the Modem/Router.

I have also installed Wifi Radar but am unsure now what to do next to set up Wifi? Also in Netwroking there is Network connection etc.

 I am very unsure how to set my Wireless in System, Administration, Networking and WiFi Radar??
  
Helen

---

