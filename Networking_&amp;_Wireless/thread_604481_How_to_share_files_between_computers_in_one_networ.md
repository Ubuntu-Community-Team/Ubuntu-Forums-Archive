---
title: "How to share files between computers in one network?"
date: 2007-11-06
forum: Networking &amp; Wireless
---

### Post by Starlight on 2007-11-06
Hi! I have two computers connected to one router... one with Ubuntu, and the other one with MacOS. I need to find a simple way to transfer files between them... I tried using FTP first, but when I saw lots of really weird advanced options in gproftpd I gave up... I don't want anything advanced, I only want to send files between my two computers. Then I tried Samba... I turned it on both in Ubuntu and on Mac, but none of them seems to actually work. The computers can see each other, but not access... when I try to access Ubuntu from Mac, it asks me for a username and password... and it doesn't work even if I put the username and password I have in Ubuntu! When trying to access Mac from Ubuntu, I don't get any actual errors, just an empty place... even though my shared folder on Mac isn't empty! 

Can anyone help me make Samba work, or suggest some other simple way to transfer files, which doesn't require spending hours editing configuration files? I only want to send a few files from one computer to the other.... it shouldn't be so complicated...

edit: I'm trying ssh now, but even though sshd is supposed to be installed and running on Mac, I get an error when trying to access it...

---

### Post by kevinatkins on 2007-11-06
Hi there,

ah yes, good old Samba...

I assume you've got the samba servers running on both machines.. 

By default, share security is set to 'User' i think, and you need to add a samba user / password.. However, if it's just a quick and dirty method of sharing you want on a home network, then you can set the security the 'share', and then set permissions on the shared folder accordingly.

to do this, edit /etc/samba/smb.conf and look for the 'security=user' stanza and change to 'security=share', then restart samba by issuing 'sudo /etc/init.d/samba restart'

then simply right-click on any directory you want to share, and select share from the context menu.

hope this helps

PS - If SSH isn't working, you might need to open TCP port 22 on the Mac's firewall

---

### Post by Starlight on 2007-11-06
Thank you! :) both Samba and SSH is working now :D I sent some files with Samba, and now it says they are owned by "nobody" and I can't really do anything with them.... so I think I'll stay with SSH... it's actually better, since I can access all folders with it, not just shared ones :)

---

