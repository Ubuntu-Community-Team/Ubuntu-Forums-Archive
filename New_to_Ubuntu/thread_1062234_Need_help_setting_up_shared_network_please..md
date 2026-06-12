---
title: "Need help setting up shared network please."
date: 2009-02-06
forum: New to Ubuntu
---

### Post by scotttie on 2009-02-06
Hi everyone,
I have a vista pc and a ubuntu pc and they are both on a cabled home network. I wold like to share file between the two as I have a scanner on the vista pc which is not compatable with Linux hence the requirement to access folders on the vista pc.
I have loaded samba but cant seem to configure the systems to see each other.
any help greatly appreciated
Scottie

---

### Post by mjheagle8 on 2009-02-06
[http://ubuntuforums.org/showthread.php?t=373917](http://ubuntuforums.org/showthread.php?t=373917)
[http://ubuntuforums.org/showthread.php?t=880887](http://ubuntuforums.org/showthread.php?t=880887)

these two look like they should be able to help you.
:)

---

### Post by Kellemora on 2009-02-06
Hi Scottie

Go into Synaptic and install smbclient and smbtree also.  If you see smbfs is installed, uncheck it, it prevents several shares from showing.

Next edit your smb.conf file to change your workgroup name to the workgroup name you use on your system.
The Ubuntu default is WORKGROUP = WORKGROUP while the windows default is WORKGROUP = MSHOME, it's best to come up with your OWN workgroup name.  EG: WORKGROUP = SCOTTIE.
That should be the ONLY thing you need to change in the smb.conf file.  It's located /etc/samba/smb.conf

Next you want to go into System/Admin/users and groups and add the users who will need access to the shared folders.
You may also want to install System-Config-Samba while you are in Synaptic to facilitate GUI changing of the data rather than using command line.  Many get by without it, but it's handy sometimes.

That should be everything you need to get everything up and running smoothly.

The reason I had you load smbtree is that from Terminal, if you type smbtree it will show all of your shared folders.  This is handy if for some reason they do not appear in Places/Network and you want to check to see if the network and samba are working correctly.  Nautilus has a few bugs in it and sometimes will not show shares, sometimes it will, it has a mind of it's own in that regard.
IF your shares show using smbtree, but not in Places/Network, you can go up to Go/Location and type in the IP number of your computer you need to access, that will bring up the shares.

Good Luck

TTUL
Gary

---

### Post by scotttie on 2009-02-07
Thanks Kellemora,
I have tried all as you suggested but could not find "smbtree" anywhere!
I can ping either PC but cannot see any shared folders across the network from either direction dont really know what to try next?
Regards 
Scottie

---

