---
title: "Cannot access windows shares"
date: 2008-09-12
forum: Networking &amp; Wireless
---

### Post by kougaru on 2008-09-12
I have two computers connected to a router. One is a Windows Vista machine and the other is Ubuntu Hardy. I setup file sharing on both and the Windows machine can see everything on the network, but the ubuntu machine can't seem to see anything. I can ping the windows machine from the ubuntu machine so I know I can connect to it.

The only error message I could find was when I use smbtree.
    		
cli_rpc_pipe_open: cli_nt_create failed on pipe \srvsvc to machine XXXXXX.  Error was NT_STATUS_ACCESS_DENIED

---

### Post by dmizer on 2008-09-12
Please see the second link in my sig.

---

### Post by gregphil on 2008-09-12
Ubuntu 8.04.1 browsing of shared authenticated Windows shares is broken.  Ubuntu 8.04.1 can browse anonymous (guest) Windows shares but not authenticated shares.

This only applies to applications that us the gnome gvfs library (like nautilus).  the legacy command line tools and KDE GUI applications do not have this bug.

See my other posts about work-arounds.

[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/207072](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/207072)
[http://bugzilla.gnome.org/show_bug.cgi?id=524485#c26](http://bugzilla.gnome.org/show_bug.cgi?id=524485#c26)

Sorry.

---

### Post by jbizcocho on 2008-09-12
The temporary fix for this is to downgrade Samba back to the version that shipped with Gutsy which is 3.0.28a.  You'll have to add the gutsy sources and then "force version" to this version in synaptic  Afterwards you might need to get a fresh smb.conf file from gutsy also (maybe not) the problem should go away.

Your other alternative is to use fusesmb.  you basically type "fusesmb /path-to-folder-you-want-to-be-the-network-folder and this will display your shares also.

I haven't quite figured it out yet completely but it works for most of what I need so I'm happy.

---

### Post by gregphil on 2008-09-13
I don't think that is correct, as far as I can tell the bug has nothing to do with the Samba version, it is a bug in the authorization library certain applications choose to link to (i.e. gnome's gvfs).

[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/207072](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/207072)
[http://bugzilla.gnome.org/show_bug.cgi?id=524485#c26](http://bugzilla.gnome.org/show_bug.cgi?id=524485#c26)

You can show it is not a Samba bug by doing the browsing using some application that does not use the gvfs library (like command line smbtree, smbclient, or any KDE applications, command line or GUI).

AND, as I mentioned elsewhere, you can connect with the Nautilus network file browser if you enter the full path to the share (like smb://COMPUTER/SHARE) in the target text box on the Nautilus file browser.  Click on the pencil to toggle between target icon mode and target text mode.

Good Luck.

---

### Post by jbizcocho on 2008-09-16
Why did the behavior return when I downgraded then?  I understand what you're getting at and having a look through my system logs reveals something less than what was supposed to be was happening on auth requests, but I simply don't have those problems using 3.0.28~.

---

### Post by hohlraum on 2008-09-19
I'm still seeing this in intrepid alpha 6. they going to let this slide for another release as well?  these kind of regressions should be show stoppers for the release of an OS, not a blip the 'known issues' section of the release notes. :mad:

---

