---
title: "Can browse samba shares using Konqueror / Dolphin but can't open files?"
date: 2008-05-20
forum: Networking &amp; Wireless
---

### Post by Mogul345 on 2008-05-20
I'm using Kubuntu 8.04, and I've got an odd problem. I have some Samba shares set up on a WinXP box and I can access my shares just fine. However, if I go to open up a file on one of the shares, say an .xls spreadsheet or .pdf file, it'll act as if the file is going to open but it doesn't. I have no problem copying the file locally to my kubuntu machine, however, then opening the file.

I double checked my sharing/security settings on my XP box. "Everyone" has full control for both sharing & security.

I went to a console, and started kpdf from the command line. Then I went to File -> Open, navigated to the samba share and tried to open a .pdf, and the console reported the following:

kpdf: WARNING: Unknown mimetype 'application/x-executable'.

When I try to open the .xls file, OpenOffice acts like it's launching, but once the progress bar is done the startup window disappears and nothing happens. Navigating to the share in OpenOffice's open dialog is also successful, but when I go to open, again, nothing happens.

Any ideas on how to solve this? This kinda stinks.

---

### Post by d.tamm on 2008-10-23
I have exactly the same problem. Same Kubuntu version. Can browse directories, seem to be able to create new files, but cannot open files nor copy them.
This applies when I mount the share, manually or via fstab or smb4K doesn't matter.
If I use Konqueror's smb://... protocol everything works fine, but there I can't open files directly e.g. in OOo but must copy them to the local disk.
The share is public, but even if I log in with username/password I get the same behaviour. The shares are on a yes box N2100 which internally runs a sort of Linux.

Does anyone have a solution?

---

### Post by t.rei on 2009-08-03
I'm having the same problem.

A workaround for me is, to not-use dolphin but instead "nautilus --no-dekstop" (also called "open folder" in the properties menu) to do my work.

I hope there is a fix around. I will now continue searching. Not being able to work on my companies shares makes me a sad panda. :(


*edit* Today at work this solution stopped working. Too bad, karmic was getting really good, but this is such a huge decline in functionality I guess its back to jaunty for now.

---

### Post by t.rei on 2009-08-05
I have not found any solution to this problem so far. But oviously somebody did, or they switched away from kde? Or back to jaunty? 

I am seriously impacted in my workflow by this. (Faxes, Scans and severals Documents are all located on some corporate servers running microsoft shares). Does anyone have any pointers? 

I even thought it might be ubuntuone related, but no. *sighs*

---

### Post by dmizer on 2009-08-05
Take a look at the 6th link in my sig.

---

### Post by t.rei on 2009-08-05
Thanks for the good amount on information. However my problem is not that I cannot browse samba shares. That works flawlessly. But when I try to open, or copy, a file on the samba share I am getting a "file not found" error. Usually a filnema.part then resides on my local drive, where I wanted to copy the file to. Working on the file within the samba share - like it used to work on jaunty - does NOT work at all. Uploading a local file to the samba share does not work either.

---

### Post by dmizer on 2009-08-05
> **t.rei said:**
> Thanks for the good amount on information. However my problem is not that I cannot browse samba shares. That works flawlessly. But when I try to open, or copy, a file on the samba share I am getting a "file not found" error. Usually a filnema.part then resides on my local drive, where I wanted to copy the file to. Working on the file within the samba share - like it used to work on jaunty - does NOT work at all. Uploading a local file to the samba share does not work either.
Yes, but I would suggest the same fixes for your issue as I would for not being able to browse.

---

