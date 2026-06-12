---
title: "Trouble connecting to my Network Attached Storage"
date: 2008-11-21
forum: Networking &amp; Wireless
---

### Post by notbitmonk on 2008-11-21
I already checked other posts regarding connecting to samba or cifs but they talk about a share with Windows and information obtained through Windows.  I upgraded to 8.10 from 8.04.  When I had 8.04 I was able to connect to my NAS.  This is my setup:
[LIST=1]
[*]Axesstel CDMA 1xEV-DO Wireless internet receiver
[*]Netgear Rangemax Wireless Router
[*]Mobile LanDisk (this is the NAS) from Premiertek ([http://www.premiertek.net/products/enclosure35/ED-35-LANII.html](http://www.premiertek.net/products/enclosure35/ED-35-LANII.html))
[/LIST]
The NAS is to share with another Ubuntu machine that I will set (hopefully) before the year ends.  The NAS disk is formatted as FAT since it is required by the NAS.  The computer I'm using dual boots to XP and I'm able to browse the NAS without any trouble.  The computer I'll be setting up will only have Ubuntu and won't be able to browse to the NAS if the problem I'm having is pervasive.  If I access the drive through Connect to Server, it looks like is going to make the connection and then jumps to my home folder. Accessing it through Firefox only shows me the Compartido folder (that the share folder accessible to anyone in the network) but not its contents. I'm able to connect to the NAS configuration page without problems so I know there is no connection problems. Gnome Commander is not able to see the share.  Any thoughts/help?

---

### Post by notbitmonk on 2008-11-22
It appears that there is very little documentation/help regarding standalone NAS devices (basically a hard disk inside an enclosure).  Tried installing Samba on my computer from Synaptic and got the following error:
> Depends: samba-common (=2:3.2.3-1ubuntu3) but 2:3.2.3-1ubuntu3.1~ppa1 is to be installed

I have the following packages installed on my machine:
[LIST]
[*]samba-tools
[*]libsmbclient
[*]samba-common
[*]smbfs
[*]smbclient
[/LIST]
I'm not able to access my NAS or even to mount using cifs or smbfs.  This is getting to be very frustrating as I have been at it for about two months (ever since I upgraded to Intrepid).

---

### Post by notbitmonk on 2008-11-22
Upgraded the firmware of the NAS to no avail.  Sent an email to who I think is the NAS manufacturer requesting some help.  I do not think this is a hardware problem since from reading the forums this problem appears on several devices.  I really think that something broke during the upgrade from Hardy to Intrepid.  When I had Hardy I don't remember configuring samba.  It was something like I just typed the address and everything worked fine.

---

### Post by emacdonald on 2008-11-22
I have the same problem, and I believe that a bug report has been generated.

Meantime I have a work around, which works for me.

Have a look at 

[http://ubuntu.wordpress.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/](http://ubuntu.wordpress.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/)

I created a mountscript file with the following:

"#! /bin/sh

mount -t cifs -o username=server,password=server //server/Server //home/NAS/mnt/server/"

(Of course use the appropriate path names. passwords etc..)

If you already have CIFS installed then this will work, otherwise you should install it using Synaptic. (or substitute SMB etc.....)

Remember to make the script executable as described in the wordpress site link above.. 
:)

---

### Post by notbitmonk on 2008-11-29
I created an entry in fstab to mount the drive during startup.  The fstab line is very simila rto the one you show.  However, I am not able to mount the NAS.  A couple of days ago, an update came for Samba but after applying it I wasn't able to connect to my NAS drive.  Mind you that FTP works OK.

---

### Post by ecarter on 2008-12-09
Yes same problem I am afraid. NAS OKish with Vista/XP and Heron but no joy at all in Ibex. But the link below may be of interest and makes me wonder just what is going on. Certainly when Dolphin fails to scan the folders it states the protocol has died unexpectedly.
[http://forums.sonos.com/showthread.php?t=7345](http://forums.sonos.com/showthread.php?t=7345)

---

### Post by notbitmonk on 2008-12-14
For some reason I'm unable to see the thread that you post (unable to connect the remote web server)

---

