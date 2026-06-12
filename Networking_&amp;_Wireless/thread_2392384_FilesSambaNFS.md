---
title: "Files/Samba/NFS"
date: 2018-05-20
forum: Networking &amp; Wireless
---

### Post by geeky-1 on 2018-05-20
I've been using the Files utility to copy files between my computer and my server (used mainly for backup) for several years now, and my external backup drive for a few months now. It seems every time I rebuild my server with newer hardware (processor and/or hard drives) and install a new fresh version of Ubuntu, I have problems getting Samba working correctly. I've gotten it to work after some hassle reconfiguring (there's a thread I posted with links).

Some time ago, someone suggested I use some type of backup software. I intend to do that eventually, but haven't gotten around to it. I suppose I'll try out the built-in backup software in System Settings sometime.

Also, people have suggested using NFS instead of Samba due to security concerns, but when I looked up NFS, it is complicated and requires using the command line. It is easier and faster to be able to drag and drop files and folders between Files utility from my main computer drive to the backup drive and server data drive. Is there any NFS GUI that functions like the Files utility? My latest problem is copying files with special characters - even though both my main computer drive and server data drive are Ext4 format, it seems Samba is limited by Window file naming restrictions and causes problems copying files with special characters that Linux allows, so that is more incentive to move to NFS.

---

### Post by SeijiSensei on 2018-05-20
Some file browsers, including Dolphin for KDE and, I believe, Nautilus, let you specify sftp:// urls to connect to servers.  All the server needs is to run openssh-server.  With Dolphin you can have two windows open, one local and one remote, and drag-and-drop files between them.  I'd imagine Nautilus works the same way.

You can install the SSH server with "sudo apt install openssh-server".  If you have an account on the server with a password, that's generally all you need.

I upload files to my remote servers this way all the time.

---

### Post by modomobo on 2018-05-20
You didn't mention which platforms you're using, but NFS can be used through a desktop UI on OS X and MS-Windows. Once you have a NFS share mounted, you can drag and drop files via the GUI.

I just set up both Samba and NFS on Ubuntu 18.04 and while NFS was a little more complicated, it is much faster for copying large files and it doesn't have the naming restrictions that you noted.

What platform(s) are you using?

HTH

---

### Post by geeky-1 on 2018-05-22
Ubuntu 16.04 LTS on my PC and 18.04 LTS on my server.

I guess I must have created an account here with a different e-mail as I'm back to single digit beans and got some warning about spam accounts with new e-mail. My profile used to have the Ubuntu version in it.

---

### Post by SeijiSensei on 2018-05-22
Did you try the sftp:// approach?

---

### Post by geeky-1 on 2018-06-30
I can't figure out how to set up Nautilus (Files utility, correct?) to use sftp. I followed these [instructions]("https://www.memset.com/docs/other-memset-services/memstore/accessing-memstore-third-party-clients/sftp-access-ubuntu-linux/"), but there is no "Service type" from which to select SSH. Also nothing shows up in the Recent Servers section.

Now I have something weird happening - not sure if it's because I installed SSH server, but when I delete a folder in Files, it prompts me if I am sure I want to permanently delete it as normal and acts as if it's deleted, but isn't. When I try to drag the folder from my computer to the server, it asks if I want to merge. Whenever I delete the folder off the server, then press F5 to refresh, it reappears. So I'm not able to delete any thing off the server now??? Also, from the server, when I delete it from the shared drive, it does the same thing, but if I open the drive directly, I am able to delete it. So there is something strange going on with the share.

---

