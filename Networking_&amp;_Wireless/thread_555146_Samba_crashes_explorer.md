---
title: "Samba crashes explorer"
date: 2007-09-19
forum: Networking &amp; Wireless
---

### Post by jmegit on 2007-09-19
A little background information:
I'm trying to setup a file server for a house of university students, I chose Ubuntu for the task and have been relatively happy so far.  The house has 2 xp machines, 1 vista machine and the ubuntu file server all connected to a dlink router.  The windows boxes all share files amongst each other no problem, however the ubuntu share is causing some problems.  

When connecting to the samba share, all shared folders/files are listed normally, browsing folders is quick - everything appears to work.  When trying to grab a file, the normal windows "calculating time remaining" dialog appears, and essentially hangs explorer.  The time remaining is never calculating, and it appears that the file is never actually transfered.  The only exception to this is small text only documents (around 1kb small) - they have no problem being transfered.

From the samba side of things, it appears that witin the logfile for the specific connected client, a broken pipe error is outputted - which I have been unable to debug over the past week.  I've tirelessly searched google and these forums for a solution, but have yet to find one.  This is my last resort.

Regarding the smb.conf, I have made countless changes to it based on solutions offered for similar problems, to no avail.  I just totally removed samba and reinstalled it to start from scratch (slightly out of anger) - so my config file would be at defaults (I used the shared fodlers GUI to add new shares).

Any help is appreciated..

---

