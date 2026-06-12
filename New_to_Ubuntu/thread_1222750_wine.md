---
title: "wine"
date: 2009-07-25
forum: New to Ubuntu
---

### Post by cello on 2009-07-25
Hello, ill try to install wine, but something going wrong when i start Wine/Browse C:/ Drive, ill get error (Failed to open URL "~/.wine/drive_c".)

The wine is up to date, what is the problem? :confused: Ill what I what is play some win game, maybe here is some tutorial for newbie?


Everything going OK, u can close or delete the topic! Thanks

---

### Post by Mark Phelps on 2009-07-25
If you're trying to use Wine like a Unix version of Windows Explorer to browse your folders and files in your MS Windows partition -- that will not work.  Wine is an interface that allows you to INSTALL and run SOME MS Windows programs -- inside your Ubuntu installation.  You can't use Wine to access your existing MS Windows installation.

---

### Post by Armor Nick on 2009-07-25
> **Mark Phelps said:**
> If you're trying to use Wine like a Unix version of Windows Explorer to browse your folders and files in your MS Windows partition -- that will not work.  Wine is an interface that allows you to INSTALL and run SOME MS Windows programs -- inside your Ubuntu installation.  You can't use Wine to access your existing MS Windows installation.
That's not entirely true. Wine creates a virtual C drive (~/.wine/drive_c/) and while you cannot browse a dual boot installation, it should be possible to browse this virtual c drive.

Have you tried executing 'configure wine' first, or typing winecfg in the run command? Also try manually browsing to the virtual c drive with nautilus (or dolphin if you use Kubuntu). You use Ctrl+H to view hidden folders, btw.

---

