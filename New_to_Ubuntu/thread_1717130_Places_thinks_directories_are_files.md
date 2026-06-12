---
title: "Places thinks directories are files"
date: 2011-03-29
forum: New to Ubuntu
---

### Post by Julian Lewis on 2011-03-29
Hi, my lap top is running 10.10
On the "places" menu I get the message 
/home/julian/ is not a file
when ever I try to access my home directory. It also says /home/julian/Pictures etc etc are not files. I know that, they are directories.

If I go via "computer" and drill down to my home directory it works OK.
It works when things really are files.

Only when I try to access a directory directly from "places" do I get the error.. yes directories are not files so how do I tell gnome not to treat them like files ?

Or how can I reset the "places" behavior to the default ?  

Thanks

---

### Post by QLee on 2011-03-29
See if this helps.

When you have accessed(clicked on) "Computer" from the top panel, you are looking at a file browser window which shows whatever partitions are on your hard disk (shown as drive icons), a cdrom if you have one and "Filesystem" (also shown as a drive icon), is that correct?

If so. right click on the "Filesystem", and select "Properties" from the context menu (should be down at the bottom). After the properties sheet opens, select the "Open With" tab to see what the system thinks it should do. (Note: That Open With tab on the properties sheet has a reset button) You probably want it to be, Open Folder.

---

### Post by Vaphell on 2011-03-29
have you used Open with ... feature from rightclick menu on some folder?

Try rightclicking any folder, open with... , select filebrowser from the list, tick checkbox to make selected app a default choice for folders, apply. Maybe some other app which accepts files only is currently assigned to folders.

---

### Post by mikewhatever on 2011-03-29
I thought everything was a file in *nix. :confused:

---

### Post by Julian Lewis on 2011-03-29
> **QLee said:**
> See if this helps.

When you have accessed(clicked on) "Computer" from the top panel, you are looking at a file browser window which shows whatever partitions are on your hard disk (shown as drive icons), a cdrom if you have one and "Filesystem" (also shown as a drive icon), is that correct?

If so. right click on the "Filesystem", and select "Properties" from the context menu (should be down at the bottom). After the properties sheet opens, select the "Open With" tab to see what the system thinks it should do. (Note: That Open With tab on the properties sheet has a reset button) You probably want it to be, Open Folder.
Yes that fixed it.
I tried right clicking from the places menu but that failed as usual.
So drilling down from computer and the using open with file browser on my home directory fixed the problem.
I didn't realize that open with applied to directories... some how Bazero had decided to be the default application for just about everything including pictures and directories. This looks like Bazero is a bit too enthusiastic about taking iver the world   .
Thanks again for good advice... and the next guy who replied.

---

