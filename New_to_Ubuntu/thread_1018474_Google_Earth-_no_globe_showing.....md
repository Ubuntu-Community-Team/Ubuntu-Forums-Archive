---
title: "Google Earth- no globe showing...."
date: 2008-12-22
forum: New to Ubuntu
---

### Post by M0GEJ on 2008-12-22
Hello, 
I just installed Google Earth (4.3) on my laptop. It worked well first time I opened it up but now whenever I open it all I see is the background with no options showing in either places or layers. I can open it up by typing gksu googleearth
in the terminal and everything appears to to work just fine but not through application-network-google earth. Any ideas?
I am using Xubuntu Intrepid Ibex........

---

### Post by ohzopants on 2008-12-22
As of last night, I am having the same issue with Ubuntu running gnome.

There is no output in the terminal that points to anything going wrong either.

I installed it to /opt/google-earth.

---

### Post by vanadium on 2008-12-22
Start nautilus with root permissions ("gksudo nautilus"). Show hidden files (view menu). Navigate to .config in your home directory, and delete the folder Google. After that, start googleearth again.

---

### Post by M0GEJ on 2008-12-29
I am still having problems with google earth (globe still not showing). Any further ideas?
cheers

---

### Post by livewyer on 2008-12-30
I, too, have had similar problems.  First it flickered like crazy, after some changes the globe and menus wouldn't appear.  Here's how I fixed them:

[LIST=1]
[*]Switched to Metacity window manager with fusion-icon (install in Terminal with ```
sudo apt-get install fusion-icon
```).
[*]Opened Nautilus in terminal with ```
gksudo nautilus
``` and moved a copy of /home/livewyer/.config/Google to root's desktop and deleted the original.
[*]Ran in Terminal ```
gksudo googleearth
```.
[/LIST]

This worked for me, though I look forward to when this workaround is not necessary.  I installed the latest version of Google Earth from Google instead of the older version available in the repositories.  I'm running Ubuntu 8.10 on a Lenovo R400 with the integrated graphics card.

---

### Post by M0GEJ on 2009-01-01
cheers- still no joy though. I can still open google earth through the terminal but not through the menu. I think I will just give up on it to be honest. Thanks anyway:)

---

