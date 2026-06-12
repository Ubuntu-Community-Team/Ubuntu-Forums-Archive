---
title: "SAMBA/CUPS--&gt;Windows, printer status?"
date: 2007-05-04
forum: Networking &amp; Wireless
---

### Post by Gorsat on 2007-05-04
I tried posting this over on Absolutely Beginner but didn't get any replies...

We have several computers at home. Many are running various flavors of Windows, one is running OS X and another, the newest addition, is running Feisty Fawn. 

I've been running a Windows Server box for domain mgmt, file/print serving, SMTP/POP, backup, etc. I'm trying to configure my ubuntu box to take over all of these tasks. For the most part, this is going just fine. I've got SAMBA set up for file serving the way I like, I've written scripts for backups and for quickly configuring a new install, etc. However, I'm stumped by one basic problem.

I'm using SAMBA/CUPS/TurboPrint to share my LaserJet and Canon inkjet printers for use from all of the other computers in the house. I've got this configured well enough that I can print just fine, check the queues from the Windows UI, etc. But the problem is that I can't figure out how to get status messages to flow back from the printers to the Windows clients. For instance, if the LaserJet runs out of paper or the Canon needs more magenta ink then the end-user (aka my wife) should get a notification on the Windows desktop. This isn't happening with my current setup. In fact, given the way the system seems to work (writing the jobs to disk and then spewing them in raw form to the printer) I can't figure out how it would ever work. I'm hoping there's a way to do this, though, because if I can't make it work then I'll have to keep using a Windows box as my print server. 

Can anyone shed any light on this? Is there any magic configuration I can tweak in CUPS and/or SAMBA to enable two-way status communication to flow between the Windows clients and the printers attached to my ubuntu box?

Thanks in advance!

---

### Post by Gorsat on 2007-05-06
Anyone?  

Someone has to know the answer to this question:  are printer status messages (like "out of paper") supported and surfaced for end-users in ubuntu?  ...and if so then are they also forwarded via CUPS/SAMBA to network clients?  

This seems like pretty basic functionality so I'm hoping the answer is yes and that I just have to go RTFM some more to make it work for me.  Otherwise, I'm going to have to keep using Windows as our print server :(

---

