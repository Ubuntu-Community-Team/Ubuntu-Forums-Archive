---
title: "Firefox, Namoroka, Minefield Oh my!"
date: 2011-03-26
forum: New to Ubuntu
---

### Post by Triton46 on 2011-03-26
Hi All, 

I am running Ubuntu 10.10.  In an effort to install Firefox 4.0RC2, I removed my stable installation, downloaded the tar.gz from Mozilla and installed 4.0.  After some issues, I removed 4.0 and attempted to reinstall Firefox 3.5...instead I got Namoroka (code name for pre 3.6 beta).  I removed this version and attempted to pull the stable version down from Ubuntu Software Center in Gnome...nope, now it only pulls Namoroka.  

So, I live with it and tonight Software Manager wants to download an updated to Firefox...4.0.  Great!  After the installation I now have two installs (separate directories) of Mozilla Firefox.  

I just want to return to the original install (one directory) and continue to receive updates/plugins for that directory.  What do I need to do?

---

### Post by Triton46 on 2011-03-27
Found my issue.  I had about 5 other repositories enabled under "Other Software" in the Gnome Software Sources.  After I removed those sources and reinstalled Mozilla Firefox I  only get the stable version.  :)

---

### Post by I2k4 on 2011-03-27
Got a good chuckle from your title.

I'm new too, and had the same trouble, initially getting "Namoroka" installed along with the beta "Minefield" which seem to be special FF versions for Ubuntu - somebody more knowing might explain.

I found this link, and used the last method with success:

[http://techie-buzz.com/ubuntu/install-firefox-4-in-ubuntu.html](http://techie-buzz.com/ubuntu/install-firefox-4-in-ubuntu.html)

In Lubuntu, it is 
- uninstalling the version you've already got
- open the Synaptics Package Manager > Settings > Repositories > Other Software > Add
- enter  ppa:mozillateam/firefox-stable  in the box
- close and be sure to Reload to update
- then search for "firefox" and find the new version and install it like any other package

I have to say, on my main computer the update installed as "Minefield" again while on my netbook it is just plain Firefox 4, who knows?

---

