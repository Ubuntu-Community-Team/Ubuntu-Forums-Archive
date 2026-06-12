---
title: "Printing &amp; file sharing"
date: 2005-10-22
forum: Networking &amp; Wireless
---

### Post by mark on 2005-10-22
I have a desktop PC (Intel D865GLC mainboard, using the on-board network interface) and a Sony VAIO PCG-GRZ610 laptop (also using the on-board, wired NIC).  I also have an HP LaserJet 6P connected to the parallel port on the desktop.  The computers are connected via a NetGear RP-614 router so I can share my DSL Internet connection.  On both systems I dual boot between Ubuntu 5.10 and Windows XP Professional.

Windows-to-Windows, I have no problems sharing files or printing from the laptop to the desktop-connected printer.  If the desktop is running XP and the laptop Ubuntu, I can print to the HP from the laptop, but I get login requests on file sharing that just keep repeating.  If both systems are running Ubuntu, I cannot get to the desktop printer from the laptop and file sharing attempts prompt me for a user name and password (which I thought I had assigned, using *System > Administration > File Sharing*) - but it keeps coming up with the login request.

I've read the CUPS and Samba docs, Google'd for help and searched this forum.  If I missed the answer, I'll apologize now.  But my question still remains:
[INDENT]How do I share files and printers between 2 Ubuntu systems on a network?[/INDENT]
I've installed the Samba package on both systems and tried myriad ways of talking to the printer.  Can somebody point me towards something that's a little more specific than "edit the config file (or point your printer app) to *ipp://hostname/printers/printername*"?  In other words, something simple, dumb & stoopid that I might be able to understand...

(For any Ubuntu devs that might be lurking, this should be *way* simpler than it is now...)

---

### Post by mark on 2005-10-28
By now, 70+ people have read this and no one has replied.  It would seem to be a problem that's either too trivial to respond to or one that nobody has an answer to.  If it's the former, please, *somebody* post a link or something to something useful and I'll shut up.  If the latter, please post a response and let's see if it warrants some kind of escalation.

If I'm overlooking something that's blatantly obvious, please post about it.  My embarrassment is nothing if answers a common (I would imagine) question - and if it'll let me get my printer working from both %^&( computers!<g>

---

### Post by etitor on 2005-10-29
Sorry to hear about your Samba troubles. Some months ago I experienced the same and, not needing to share with Windows machines, switched to NFS file and printer sharing: the wisest decision possible!

As for the printing sharing under NFS, please see [http://occy.net/printing](http://occy.net/printing).

Good luck.

---

### Post by Buffalo Soldier on 2005-11-10
Hi mark,

Hope you've found the solution. If not, maybe this [Ubuntu as print server](http://ubuntuforums.org/showthread.php?t=77304) thread can help. It helped me in setting print sharing between 2 Ubuntu computers.

---

