---
title: "Uninstall Handbrake?"
date: 2009-11-24
forum: New to Ubuntu
---

### Post by Nakron on 2009-11-24
I recently downloaded handbrake 0.9.4 (the Ubuntu 9.10 deb GUI) from handbrake.fr. and installed it with the GDebi installer.  Handbrake doesn't seem to work with this version.  Now I want to uninstall it, but nothing I do seems to work. Any suggestions?

---

### Post by sandyd on 2009-11-24
sudo apt-get remove handbrake
or go to synaptic and remove the package thats named hanbrake
if your using 9.10, the fact that handbrake doesnt start is a well known bug....

---

### Post by JohnAStebbins on 2009-11-25
> if your using 9.10, the fact that handbrake doesnt start is a well known bug.... 

The original poster is trying to install the new 0.9.4 handbrake release and the packages for the new release are specifically for karmic.  There were some corrupt packages initially on the download page, but they would not have installed at all.  0.9.4 works fine for me.  And working handbrake packages have always been available for karmic.  All you had to do was visit the handbrake forums to find out about the development snapshots.

Current download statistics show ~2500 ubuntu downloads of the new release.  No other complaints of it being nonfunctional so far.

But the exact command to remove would be:
dpkg -r handbrake-gtk
or
dpkg -r handbrake-cli

depending on whether you install the gui or cli package.

---

### Post by Nakron on 2009-11-26
Thanks ever so much. I'll try downloading it again. We'll see if that works.  Cheers,  Nakron

---

### Post by Nightstrike2009 on 2009-11-26
It works in Ubuntu 9.04 if thats any help, its one of 9.10's many bugs LOL :)

---

### Post by steveg944 on 2010-02-27
This is an old post, but I just had this problem. Handbrake was not showing in Synaptic.
[I]
sudo apt-get remove handbrake [/I]did not work either

This did work:
sudo apt-get remove handbrake**-gtk**

---

### Post by jward3010 on 2010-02-27
Possibly this is a good time to mention autocomplete in the terminal. Maybe you use it sometimes, maybe you don't. The way you use autocomplete is type out part of the name of a command and hit TAB, it will give suggestions if there are a few options or it will autocomplete the full command name if there is only one possibility. In regards apt-get and trying to find packages you have installed or want to install, use autocomplete here too. For example I would have typed out:
```
sudo apt-get remove handb...[TAB for rest]
```
And the result may have been:
```
sudo apt-get remove handbrake-gtk
```
It prevents me from guessing and ONLY gives what's available, also, it generally speeds up your work with everything.

---

