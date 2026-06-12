---
title: "Would really appreciate some advices for sharing files in Ubuntu Win7 network"
date: 2014-08-29
forum: Networking &amp; Wireless
---

### Post by kent9 on 2014-08-29
I have a mix of computers in my home with file shares on different boxes spread out. 
The list would be:
One HTPC in the living room, with some movies locally stored Win7 home
One HTPC in the bed room, clean machine only playing movies Win7 pro
4 Laptops 3 on win7, 1 on win 8.
Current gaming machine, Win7 with 3 shares on different disks with movies, pictures and documents. Mostly used to play media content on the HTPC machines.
One OTC Nas 4TB with movies, one some linux dist.
Ubuntu Server (14.04 LTS) to be the main server for all the junk I have

What I want to do is to use the Ubuntu server to act as the main sharing area without moving all the data there, not enough space anyway.

My question is: 
Can I mount the different shares spread out in different machines to one shared area on the server with fstab, and then use samba to share this with all the machines that need access. 
Any advices around this would highly appreciated. 

What I done so far us to set up Bind9 on the Ubuntu Server so it now acts like DNS server for the local net, it's probably a bit overkill but it's fun and I want to learn more about how it works. 
The DNS seem to work as it should, the machines can see each other in the local net (ping nslookup dig). 

Installed samba but haven't touched any of config there. 

Next thing is possibly a LDAP and a FTP server but that's another issue.

Any pointers would be helpful.

---

### Post by TheFu on 2014-08-29
a) don't use FTP. 99.99999999% of the time it is a bad idea.  Use sftp instead, which is probably already installed and working on your system if openssh-server is there.  WinSCP is a nice Windows client. [http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp)

b) Having primary storage all around your network is NOT a best practice. It makes backups extremely complex and as humans, we start to forget where the primary and where the backups are located.  If you don't do backups - well - I can't help.

c) The best media server that I know for a home network is Plex Server.  It will let you centralize media and stream it to hundreds/thousands of playback devices. It can transcode on-the-fly to support specific formats as needed by certain (cough - chromecast) devices. Of course, transcode in realtime requires a capable CPU.  Plex Server is in the software center.

d) mounting storage from different systems around your network can be done with Samba - there is a server for Linux so Windows clients can see/access that storage and there is a client for Linux so it can access storage on Windows machines that are shared in the normal way.  Just install the mount.cifs program (sorry - don't recall which package that is inside), then setup a mount anyway you like - /etc/fstab or shell script or using autofs (my favorite). If you want to use autofs, I can post my cifs settings - 3 files on the Linux side are used and it sorta "just works" after that.  The main failure with CIFS mounts is that the user credentials limit which single user has access to the storage. That is bad on a multi-user system like Linux.  For that reason, I much prefer to have all network storage hosted on Linux, so that multiple users/groups can have access while still being controlled.

e) bind is overkill and 1 way that I've been hacked over the years. I don't run bind anymore.  Instead, I use the ddwrt router firmware to provide DHCP reservations and DNS lookups for the LAN. [http://blog.jdpfu.com/2011/07/18/use-your-router-to-centralize-your-network-device-management](http://blog.jdpfu.com/2011/07/18/use-your-router-to-centralize-your-network-device-management)

Hope this helps.

---

