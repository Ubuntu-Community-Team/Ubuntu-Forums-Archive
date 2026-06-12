---
title: "Help for Xubuntu 7.04 networking XP"
date: 2008-05-13
forum: Networking &amp; Wireless
---

### Post by intimaswisesa on 2008-05-13
Hi all,

I have just moved to this xubuntu 1 month ago and I have been running in circles on how to setup the network connection between xubuntu and XP.


I have visited a lot of forums and got a lot of information, yet I stuck in how I got the smbfs and fusesmb or nautiluss

Having installed the xubuntu I use the command sudo apt-get install samba and it worked! Then I type sudo mousepad /etc/samba/smb.conf and changed the configuration.


The other computers are able to connect to my computer and access it, however I could not see their computers :(

I have read so many instructions to show the computer network by using the smbfs and fusesmb. But the problem is I can't get the smbfs and fusesmb from my cd rom and it is not connected to internet :( 

Please help me if anyone in here knows how to

1. install the smbfs and fusesmb offline (which means I download the package and install it offline in my xubuntu which is not connected to internet)

2. help me to show the windows network in my xubuntu 7.04 without using smbfs and fusesmb

3. Last but not least, how do i install the printer from windows and use it for printing. ( my printer is canon BJC1000 in windows xp)

Any kind of help would be greatly appreciated :)

---

### Post by Iowan on 2008-05-13
[Here]("http://ubuntuforums.org/showthread.php?t=789444") is a post with some details.  [This  ]("http://ubuntuforums.org/showthread.php?t=690640&highlight=master+browser") one discusses master browser settings.

---

### Post by intimaswisesa on 2008-05-13
Thanx :)
The problem now lies in the repository because when I tried to install the sambacommon they say that I need the llibreadline4 :(

Where can I get these things and when I managed to get it they require something else.

Why are there so many dependencies? :(

Where i could get all the files required for samba ...

Thanx for the link :)

---

### Post by Iowan on 2008-05-14
Hmmm... how did you install - Synaptic, Aptitude, apt-get?  Seems like whatever I last used (?) got dependencies, too.

---

### Post by him610 on 2008-06-08
Yes, you have some more configuration work to do to be able to browse your local network using Xubuntu, XFCE, and Thunar.

These procedures, that I found somewhere on the web a few weeks ago were written by some kind soul who figured it all out, worked for me a few weeks ago.

Procedures:

~Create a folder and share it with XFCE's Applications -> System -> Shared Folders. (This should trigger a Samba install if you don't already have a share, and it should allow you to define the proper workgroup)

~ Install fusesmb in Synaptic (from Universe repository)

~ Edit (sudo mousepad /etc/modules) /etc/modules and add the word 'fuse' to the modules to be loaded (without quotes)

~ Reboot, so the fuse module loads, and the proper workgroup is read for samba.

~ In XFCE Applications -> System -> Users and Groups... Properties of your username... User Priveleges Tab... check "Allow use of fuse file systems..."

~ Create a directory (for non command-line peeps... gksudo thunar) that you are going to mount your network browse to... I used /media/network. Change permissions to read / write for group and others (777).

~ In XFCE Applications -> Settings -> Autostarted Applications... Add an application... name and describe as you wish... for command line, put: fusesmb /media/network (Or whatever mountpoint you created).

~ Open Thunar, and navigate to the parent folder of your mountpoint... then drag the 'mounpoint folder' to the places (shortcut) pane of thunar.

~logout and log back in (So the user privilege and fusesmb autostart will take affect)

Woohoo!... network browsing like Nautilus, in Thunar. (assuming your samba was set up right, with the correct workgroup, etc.) 

Good luck.

---

