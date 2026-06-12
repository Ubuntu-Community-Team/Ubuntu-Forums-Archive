---
title: "Is the Synaptic Package Manger safe?"
date: 2009-01-15
forum: New to Ubuntu
---

### Post by aireq on 2009-01-15
One thing I hate(d) about windows is how if you just want to try a piece of software or some tool you can install it, and uninstall it but it every program would seem to leave extra registry settings, library dll, config files etc.. laying around. 

If I add software through the synaptic package manager and uninstall by using the "mark for complete removal" option. Well the software really be completely gone?


Eric

---

### Post by zvacet on 2009-01-15
It will be uninstalled,but yo can find it in **/var/cache/apt/archives** just in case that you want to install it again. You don't have to download it one more time.

---

### Post by mtausig on 2009-01-15
Yes, it will. If you remove a package normally, the configuration files will be kept, but if you "completely remove" (aka "purge") it, everything will be deleted.

---

### Post by cdtech on 2009-01-15
> If I add software through the synaptic package manager and uninstall by using the "mark for complete removal" option. Well the software really be completely gone?
Yes, they will be completely removed. Some packages are automatically installed to satisfy dependencies for other packages which could remain on the system. Using the command line "sudo apt-get autoremove" will clean out these packages. You can also use the GUI (synaptic package manager), on the left panel select "Status" then select the "Not installed (residual config)" to remove any leftover packages.

---

### Post by aireq on 2009-01-15
OK cool . ..but does it work? If you were to ask microsoft if you can uninstall a program they would say sure.

With Ubuntu  if you mark a program for "complete removal" and then run "sudo apt-get autoremove" what if any chance is there that that program still left something somewhere?


Eric

---

### Post by Bölvaður on 2009-01-15
As far as I have noticed it removes everything if you "completely remove"/purge it. You are able to search for leftovers from the program as there is no registry or hidden stuff like that (perhaps semi hidden files).

cd /
find | grep firefox

If I'd tried to uninstall firefox I could have tracked down remaining files like that, but there probably will be no important files found.
Also you can search for config files (personal settings) for programs under ~/.firefox (that is hidden file under your /home/user/.firefox

in nautilus the filemanager you can see hidden files by ctrl+h

---

