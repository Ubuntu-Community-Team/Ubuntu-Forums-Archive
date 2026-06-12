---
title: "competely uninstall ndiswrapper - how?"
date: 2007-06-15
forum: Networking &amp; Wireless
---

### Post by Griffiss on 2007-06-15
There's a problem with my ndiswrapper so I want to completely remove it then reinstall new version. Is there a relatively simple way to do this?

griff

---

### Post by spd106 on 2007-06-16
This information is contained in this wiki page [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper), however it is rather difficult to find the specific steps.

After reading that page, I suggest you remove any ndiswrapper packages that you already have through Synaptic. Then delete the /etc/ndiswrapper directory, along with the driver at /lib/modules/`uname -r`/kernel/drivers/net/ndiswrapper/ndiswrapper.ko. These last two step should not be necessary, though I did have to do them on one occasion.

Now you should be ok to build the new version.

---

### Post by kevdog on 2007-06-16
There is no easy way unfortunately.  Visit the sourceforge ndiswrapper website, go under documents/wiki and there you will find an uninstall section.  They list 3 or 4 ways to remove everything, but just pay attention to the first, it will do.  If you are having problems with ndiswrapper and want to try another version, I recommend the svn version.  It gives you "the bleeding edge" ndiswrapper version, and some of the problems in prior versions may have been addressed.

---

