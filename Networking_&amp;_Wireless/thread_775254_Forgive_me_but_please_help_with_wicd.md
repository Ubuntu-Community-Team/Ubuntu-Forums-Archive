---
title: "Forgive me but please help with wicd"
date: 2008-04-29
forum: Networking &amp; Wireless
---

### Post by noiseordinance on 2008-04-29
I've been told that wicd will help me stop getting asked about the wireless password prompts in 8.04. I can't seem to figure out where to get, or how to install it though. Please helP!

---

### Post by kevdog on 2008-04-30
From the wicd website:

Installing Wicd in Ubuntu

Installing Wicd in Ubuntu is very simple. You just have to add the Wicd repository to the Ubuntu package manager. To open the package manager in Gnome, go to Administration > Synaptic Package Manager. When it appears, go to Settings > Repositories > Third Party Software > Add..., and enter the following line:

    deb [http://apt.wicd.net](http://apt.wicd.net) gutsy extras 

where gutsy is your version of Ubuntu in lowercase (dapper, edgy, feisty, gutsy, hardy). Then, click Reload, and wait while the package lists are downloaded. Now, search for "Wicd", and right click on it. Select Install, then press Apply, and Wicd will automatically be downloaded and installed for you. This will also keep you automatically up to date with the latest and greatest version of Wicd. Please note that this will remove network-manager, which is the default GNOME network manager and may cause loss of network connection temporarily.

In GNOME, to get the tray icon to automatically appear at boot, go to System > Preferences > Sessions. In the "Startup Programs" tab, click the "New" button. Give it a name ("Wicd" works fine). For the command, enter "/opt/wicd/tray.py".

In KDE, you'll need to make a desktop file, so see this post for the directions on how to fix it up. ****

---

### Post by noiseordinance on 2008-04-30
Got it installed. Unfortunately I can't connect with it. It sees all wireless networks in my area, just doesn't actually connect. I have rebooted since install, no good. Then I disabled the gnome network manager, still no good.

---

### Post by noiseordinance on 2008-04-30
According to this thread ( [http://ubuntuforums.org/archive/index.php/t-479018.html](http://ubuntuforums.org/archive/index.php/t-479018.html) ) i have to uninstall gnome manager to get it to work. How do I do that?

---

### Post by noiseordinance on 2008-04-30
or should i even uninstall it?

---

### Post by kevdog on 2008-04-30
I think the installation of wicd uninstall network-manager-gnome by default?  I could be wrong but that is the way it used to work.  Are you sure you still have it installed?

---

