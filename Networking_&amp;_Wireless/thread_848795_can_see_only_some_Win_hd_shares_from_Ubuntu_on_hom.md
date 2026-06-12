---
title: "can see only some Win hd shares from Ubuntu on home LAN"
date: 2008-07-03
forum: Networking &amp; Wireless
---

### Post by Sudan on 2008-07-03
Hi,
I'm very new Ubuntu user.  

I have a home LAN:

1 win notebook, connected via Ethernet cable, sees Win LAN and internet OK.  NTFS hard drive set as share entire hard drive.

1 win old desktop computer, connected via Ethernet cable, sees Win LAN and internet OK.  NTFS hard drive set as share entire hard drive.

1 dual boot Ubuntu 8.4 or Win XP on new desktop computer connected via Ethernet cable.  Booted as Win machine sees Win LAN and internet OK.  Booted as Ubuntu machine sees internet OK. And can see both win machines.  But then problem starts.

On the old desktop win machine, I can see all the files on the hard drive.  But on the notebook win machine I can see the windows network name of the computer.  But I can't see the hard drive.

I stumbled onto the network browser by going Places | Network.  This displayed a network - file browser window, location network:/// (don't know what that means).  And both win machines are displayed.  I click the icon for the old desktop and I can access the shares on the machine, dirs, hard drives, shares, etc.  And in the location field of the browser window it sasy smb://sudan/ (name of this win computer).

But when I click on the notebook machine it shows no shares, files, etc.  In the location field it says smb://keith/ (name of this win computer).

Can anyone point me to some documentation, web pages that address this kind of a problem.  I don't know where to start troubleshooting this.  Thanks.

---

### Post by superprash2003 on 2008-07-03
have you shared the directories properly in the keith pc?? in the keith pc go to the terminal and type smbtree and see if you see your shares there.. are you able to ping your keith pc from your notebook?

---

