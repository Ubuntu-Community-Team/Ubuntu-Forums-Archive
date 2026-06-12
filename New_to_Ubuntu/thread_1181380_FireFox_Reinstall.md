---
title: "FireFox Reinstall"
date: 2009-06-07
forum: New to Ubuntu
---

### Post by ericstrom on 2009-06-07
I've been having trouble with FireFox lately and I would like to COMPLETELY delete it and then reinstall it. The only thing I want to keep though is the bookmarks. How do a go about doing a COMPLETE deletion and reinstallation ? 

Currently running Jaunty/9.04 and FireFox 3.0.10.

---

### Post by benny bronx on 2009-06-07
Go to bookmarks in the toolbar-organize bookmarks-import and backup-backup.  That will save a copy to the folder you chose for downloads.  Go to synaptic and search firefox and completely uninstall all that are marked as installed.  Go to your home directory, view-hidden files, and then delete the mozilla folder.  To reinstall go to synaptic and and reinstall the packages you uninstalled. To restore your bookmarks, bookmarks-organize bookmarks-restore-choose file.

   I would suggest first just deleting the mozilla folder in /home, after backing up your bookmarks, to see if that solves the issues you are having.

---

### Post by lovinglinux on 2009-06-08
> **benny bronx said:**
>    I would suggest first just deleting the mozilla folder in /home, after backing up your bookmarks, to see if that solves the issues you are having.

+1 

Most problems on Firefox are profile related and re-installing it is unnecessary.

---

