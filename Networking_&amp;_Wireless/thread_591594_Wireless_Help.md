---
title: "Wireless Help"
date: 2007-10-25
forum: Networking &amp; Wireless
---

### Post by bobheaps on 2007-10-25
I am trying to get a wireless connection from my laptop. It is an Acer Travelmate 2201LCi.
I read the Howto on Ubuntu and wireless and followed (I hope) all the directions given.
I downloaded and installed nidswrapper.
I downloaded 80211BG.zip, opened it and placed all the files in a folder.
I used nidswrapper to wrap the neti220.inf file.
used modprobe.
But still no luck. What should I do now?

This is the folder that contains the driver:-

[email]root@msforcier-laptop:~/.wine[/email]/drive_c/windows/system32/drivers# ls
i2220ntx.cat  i2220ntx.sys  neti2220.inf  neti2220.PNF
[email]root@msforcier-laptop:~/.wine[/email]/drive_c/windows/system32/drivers#

this is the output of ndiswrapper -l

[email]oot@msforcier-laptop:~/.wine[/email]/drive_c/windows/system32/drivers# ndiswrapper -l
17FE:2220:0305:1468.5.conf : invalid driver!

Also, How do I find my  key s:
 Thanks in advance
17FE:2220.5.conf : invalid driver!
i2220ntx.sys : invalid driver!
neti2220 : driver installed
        device (17FE:2220) present
neti2220.inf : invalid driver!
[email]root@msforcier-laptop:~/.wine[/email]/drive_c/windows/system32/drivers#

---

### Post by pokkets on 2008-03-13
I found a page in the community help, which was loading the ndiswrapper in ubuntu with the terminal.
This worked for 7.10 gutsy, and with Hardy I have recognizing the wireless. in network, but I'm still working on the connectionso far I've had to come back to another gutsy system to use wireless 
build-essential is not automatically installed, 
but it is on the installation disk It asked me to insert the disk so it could install it

[https://help.ubuntu.com/community/WifiDocs/Device/ipn2220](https://help.ubuntu.com/community/WifiDocs/Device/ipn2220)

These instructions copy the ndiswrapper drivers on Desktop into their appropriate system folders
I think most of them are in /etc/
ndiswrapper-1.49 worked for gutsy, 1.51 seems better for hardy.
I had another problem. When I use a live disk, wireless seems to drop out
I keep a folder 'wireless-drivers' on my desktop from when I installed 
There is a package ndisgtk_0.7.2-1ubuntu1_i386.deb for gutsy and 0.8.2 for hardy and it will install a Windows Wireless Drivers option at the bottom of System Administration on the Ubuntu Desktop This needs ndiswrapper-common, and ndiswrapper-utils-1.9 before it can be loaded.These can be found in synaptic,I'm not sure if they're on the disks, but for a few packages I had to use ethernet. but a debian package only needs a double click and the package handler takes care of the rest. When I first installed gutsy I had to drag the driver files from the desktop into the folder and reinstall them with Windows Wireless Drivers. I'm still fairly new, but I have been doing a lot of trial and error, learning. I learned to make backups early.
The driver seems to stay loaded with hardy, but there are maybe two chances to change the configuration before the Desktop has authorization removed. I noticed after installation, the ndiswrapper driver folder on Desktop had most of the files locked but once installed the working copies are in the system. It's handy to have a flash or a USB drive to keep them, and I removed the Desktop folder when it was loaded. The wireless will only seems to stay recognized if there is a connection, so with hardy I load it again from the terminal. I also found that while the network configuration needs to be unlocked in Desktop. changing the Authorization at the top of Administration seemed to keep it unlocked.  

I don't know if this will solve your problem, maybe it will give you a few idea.s It's amazing how google can lead to the right answers - If you ask the right questions. Most of the time the answers are in the Ubuntu Community somewhere. Another place that is good is the bug tracker Launchpad
 [https://launchpad.net/](https://launchpad.net/)
 which is tracking Ubuntu bugs. Very often there is a fine line between a problem and a bug, but they are sometimes solved there.At the moment they're busy cleaning Hardy of bugs for it's official release in April
 Good Luck 
My next move is to get a laptop with no Windows hardware, I've been converted to Linux, and Ubuntu over the last few months.

---

