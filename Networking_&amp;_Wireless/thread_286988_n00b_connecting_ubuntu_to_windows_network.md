---
title: "n00b connecting ubuntu to windows network"
date: 2006-10-28
forum: Networking &amp; Wireless
---

### Post by luken8r on 2006-10-28
Ok, to preface, I am a complete ubuntu n00b, only using it for a week or two at work.  Here is my problem, probably very simple:

My home pc, which runs WinXP home, has a bum hard drive.  I need to get the files off of it to back it up. My DVD/CD burner is either on the fritz or is burning coasters because of the corrupted sectors on the drive. My only recourse is to try and upload the stuff from my home PC to my work laptop which is running Ubuntu.
My problem is, I cant seem to get the Ubuntu to find my home network

My network is as follows:

Cablemodem/wireless gateway
MS PC connecting to the network using the wireless connection.  Has LAN IP of 192.168.0.2
Ubuntu laptop connecting to the wired port of the router with IP of .0.3
Both have internet connectivity, so the ubuntu laptop is on the network in some state. 

What do I need to set on the Ubuntu laptop to connect to the shares on my Win PC? I can see the Windows network, I can even see the domain, but when I try to enter the domain, its telling me "Folder contents could not be displayed".
If its simple enough, please just direct me to the FAQ or whatever
Thanks!

---

### Post by John.Michael.Kane on 2006-10-28
[http://samba.org/samba/docs/man/Samba-HOWTO-Collection/](http://samba.org/samba/docs/man/Samba-HOWTO-Collection/)
[http://www.linuxheadquarters.com/howto/networking/samba.shtml](http://www.linuxheadquarters.com/howto/networking/samba.shtml)
[http://www.reallylinux.com/docs/sambaserver.shtml](http://www.reallylinux.com/docs/sambaserver.shtml)
[http://tldp.org/HOWTO/SMB-HOWTO.html](http://tldp.org/HOWTO/SMB-HOWTO.html)

---

