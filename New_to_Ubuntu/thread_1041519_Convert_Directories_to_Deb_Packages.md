---
title: "Convert Directories to Deb Packages"
date: 2009-01-16
forum: New to Ubuntu
---

### Post by DazedandConfusedWithLinux on 2009-01-16
Okay, I have absolutely no clue how to work ubuntu, but i really want to at least make it look like xp (for my own reasons) I got the theme, but it's a zip file, which i extracted, then what?

also, alien worked for me in that it created a (Locked? I can't delete it) directory (or folder) but not a deb package. Help please?

Thanks

---

### Post by HotShotDJ on 2009-01-16
> **DazedandConfusedWithLinux said:**
> I got the theme, but it's a zip file, which i extracted, then what?Normally, you do not need to extract the theme archive.  Just go to System --> Preferences --> Appearance. Then click on the "Install" button in the "Theme" tab.  In the "Select Theme" window, browse to and select the "zip" file and then click on "Open"
> **DazedandConfusedWithLinux said:**
> alien worked for me in that it created a (Locked? I can't delete it) directory (or folder) but not a deb package. Help please?Need more information.  How did you run alien? What was the input package?  What, if any, messages did alien give you during the conversion process?

---

### Post by DazedandConfusedWithLinux on 2009-01-16
Alien eiher says file not found or that i cant install it beacuse of usr/...something line whatever, and when i go to the location, i get a meaningless text file

And the zip file gets n error, and the regular folder brings me to anotherfolder which brinngs me to nothing

---

### Post by stonecoldjha on 2009-01-16
see making your system look like windows isn't a difficult thing.you need to have an appropriate GTK theme(like Linsta if you want a vistaish look) and a beryl theme(like some transparent vista like ones for a vistaish look,or i remember there is one even looking like xp,i.e. it has blue window borders.)these themes can be downloaded off [www.gnome-look.org](www.gnome-look.org)

now,lets install emerald via synaptic(go to system>administartion>synaptic package manager,and search for emerald,and install it).now go to system>preferences>emerald.open it and click on import and direct it to the location of your beryl theme that you downloaded.once imported,double-click the theme.now go to system>preferences>session.click on add,and enter the command "emerald --replace"(name it emerald).reboot and see the beryl theme in action
to install a GTK theme,just right click anywhere on your desktop,choose the theme tab,and just drag the GTK theme from the desktop into the window.now click customise,then click controls,choose the theme you installed and it will kick in.

---

