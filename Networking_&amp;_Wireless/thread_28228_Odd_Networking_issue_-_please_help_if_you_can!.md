---
title: "Odd Networking issue - please help if you can!"
date: 2005-04-19
forum: Networking &amp; Wireless
---

### Post by neilthemonster on 2005-04-19
Hi all.

I've got a little network here, with my laptop running Ubunty Warty connecting to my wife's PC (XP Home) and a small storage box running WIn 2k.

Here's the odd thing. I can connect absolutely fine to the XP box through the 'Network' icon on Warty, and browse all the shared folders.

However, I have three complete drives shared on the Win2K box, and when I try to access that machine, I get an error message saying I don't have the necessary permissions to access it.

I can VNC into that box absolutely fine, and access the folders from the XP box.

Does anyone have any suggestions, please?

Many thanks.

Neil

---

### Post by jbharrison on 2005-04-19
Not sure if you are using a gui tool...but I recommend doing things manually from shell. That way things are relatively distro-independent.

First make sure you have a username/password on the Windows system you are connecting to. Setup the appropriate priveleges on the security tab and sharing tab of the share:

Sharing tab: Everyone full control
Security: Everyone read access, <username> full control.


On the linux system as root:

Make a mount point for the share:

$ mkdir -p /mnt/<server>/<share>

Ex: /mnt/homepc/myshare

Mount to the share as follows:

$ mount -t smbfs -ousername=<windows username>,uid=<your linux UID> //<ip of windows machine>/<share name> /mnt/homepc/myshare

Ex: mount -t smbfs -ousername=jbharrison,uid=101 //192.168.0.100/myshare /mnt/homepc/myshare

Enter your windows password.

The share will now be mounted to /mnt/homepc/myshare


Good Luck

Joe

---

