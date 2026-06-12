---
title: "Hosed network manager, won't run?"
date: 2011-07-19
forum: New to Ubuntu
---

### Post by trooperchix on 2011-07-19
My son brought back his laptop to me.  Network manager has disappeared off his taskbar and I can't find my way back to it.  As far as I have been able to tell, it appears partially uninstalled, as if he started deleting various folders.  I need to figure out how to reinstall it without requiring any internet connection.  He runs Lucid.  I'm stumped.  

Thanks.

---

### Post by MyR on 2011-07-20
> **trooperchix said:**
> My son brought back his laptop to me.  Network manager has disappeared off his taskbar and I can't find my way back to it.  As far as I have been able to tell, it appears partially uninstalled, as if he started deleting various folders.  I need to figure out how to reinstall it without requiring any internet connection.  He runs Lucid.  I'm stumped.  

Thanks.

If he started deleting various folders, the system probably has bigger problems than a missing network manager.

Open up a terminal and enter network-manager to see if that turns up any useful info.

The package is called network-manager.  You can use an "alternate" install CD as a software repo to reinstall it.

Or you could download the package and its dependencies on another computer and transfer them to his and install them.  In synaptic right click on the package, click properties and select dependencies. You can mark it for installation or reinstallation and it may tell you which are missing

Hope this helps.

---

