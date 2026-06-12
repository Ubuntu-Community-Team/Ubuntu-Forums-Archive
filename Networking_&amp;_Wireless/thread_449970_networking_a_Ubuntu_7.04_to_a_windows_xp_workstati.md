---
title: "networking a Ubuntu 7.04 to a windows xp workstation/print server."
date: 2007-05-20
forum: Networking &amp; Wireless
---

### Post by Papillonrus on 2007-05-20
I have been seeking a how to or a walk thru on connecting a linux "Ubuntu" box to a windows workstation.  I have found plenty for connecting windows to a linux server and a few connecting to a stand alone print server.  while eventually I will set up a linux server for file and printer sharing.  I'm just not yet ready to do that.  Trying to wean myself and my family from M$ slowly.  
Setup:  windows XP with a HP5510v printer.  3HHD Storage, Storage~1, Storage~2.
1 xp workstation
1 windows 2000 workstation
1 dell laptop Latitude LS P3-500, Ubuntu 6.10
1 dell laptop C610 dual boot Ubuntu 6.10 and XP
1 dual boot Ubuntu 7.04 and windows 2000
connecting thru a Linksys WPC54G wireless router and a Linksys Cable Modem.

For the moment I want to connect to the Print Server for printing and file storage from the Linux OSs.   That should teach me how to connect to the other M$ shares.  Also this might be part of the first question.  But a I need a good tutorial for connecting to a network windows printer.  I've been learning this on my own from what I research on the web and from finding the right books to read.  Thanks for your help.  Darrell

---

### Post by Dzenhax on 2007-05-20
Hi,

     I think I understand that your files and printer are on the windows box and are shared out in the windows fashion.

     For the printer I had luck using the add printer utility in Ubuntu.  System -- Administration -- Printing, click new printer.  Check the Network printer radio button.  In the drop down menu choose windows printer SMB.
For host I'd put ip address to the windows printer just to keep it simple.  Printer would be the windows share name and the username and password on the windows box.

Choose the manufaturer and model just like in windows and next again.  Name it and click apply.

For the file server click Places and connect to server.  In the service type, pick windows share.  Fill in the other info as appropriate.  Leave domain name blank if you are on a workgroup.  You can also try the browse network button.

Hope that helps.

---

