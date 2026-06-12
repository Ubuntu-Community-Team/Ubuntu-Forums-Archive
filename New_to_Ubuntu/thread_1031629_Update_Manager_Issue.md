---
title: "Update Manager Issue"
date: 2009-01-05
forum: New to Ubuntu
---

### Post by matteojg on 2009-01-05
How can I remove packages that I don't wish to install from the Update Manager?

Yesterday I had a notification icon inform me that there were 19 updates available for installation, I clicked on the icon and it opened the update-manager showing a list of updates almost all for printer applications. Well, I don't have a printer so I figured why bother installing the updates...then today I noticed my system was using 150 Mib just to show me the desktop (and I even have visual effects set to none), when it usually uses around 70-80 when not running anything. 

The only change I could think of was that little notification icon on my top panel, so I removed it from the panel but memory usage did not change. Next I opened the update manager and looked for a way of removing the entries but could not find one. I tried unchecking all the entries, closing the manager, and then re-adding the notification area...and up popped the icon again really pushing those printer upgrades. So as a last resort I installed the upgrades I have no use for, the icon disappeared, and -sure enough- memory usage dropped by a staggering 80Mib.

So...how can I deal with this without installing updates to manage non-existent peripheral devices, and why is so much memory being sucked up when updates are available but not yet installed?

All useful replies will receive a thanks.

Ubuntu 8.10
Update-Manager V. 0.93.34

Dell Inspiron 600m
Intel Pentium M 1.5 GHz
250 MiB

---

### Post by stoogiebuncho on 2009-01-05
The only way I know of is to figure out which packages these updates are for and then remove those packages from synaptic.

After all, the update manager isn't installing new software, it's just updating software you already have.  So if you get rid of the original packages, it won't try to update them anymore.

However, I don't know if this is really recommended.  If it was me I'd just install all the updates.  They're small, and they don't take long.

---

### Post by bdk6m2007 on 2009-01-05
Update manager is asking you to update the packages because you have a current version installed and there is a newer one available.  If you really don't want to see those packages in update manager, and you really do not need the old versions, then remove the offending packages (synaptic is probably the easiest way)

---

### Post by chewit on 2009-01-05
There is quite alot of apps installed with Ubuntu which you may not need. Read my article about applications you could remove.

[http://edhewitt.co.uk/2008/10/27/streamlining-ubuntu/](http://edhewitt.co.uk/2008/10/27/streamlining-ubuntu/)

---

### Post by 2hot6ft2 on 2009-01-05
Locking package versions
System>Administration>Synaptic Package Manager search for the packages you no longer want to update , select them one at a time and click on Package then Lock Version that's it. It wont try to update them anymore.

---

### Post by gettinoriginal on 2009-01-05
This site is great for streamlining Ubuntu for packages you don't need if you don't use.  But since it is not mentioned in the site, if you don't have a printer, just type printer into quick search, and you can pick and choose by the description if you need to keep it.  :P 

[http://edhewitt.co.uk/2008/10/27/streamlining-ubuntu/](http://edhewitt.co.uk/2008/10/27/streamlining-ubuntu/)

---

### Post by matteojg on 2009-01-05
A warm thanks for the helpful advice...I will remove the packages dealing with printers, tvs, phones, etc., maybe lock a few things I'm not sure about, and remove an applet or two.

Does anyone have any thoughts on the memory issue though?
Why would Update-Manager use so much MiB when its not even actively installing things but simply waiting for me to decide whether I want to install some upgrade it has detected?

---

### Post by gettinoriginal on 2009-01-05
I have not checked my usage, but will next time, thanks for the heads up :o

---

