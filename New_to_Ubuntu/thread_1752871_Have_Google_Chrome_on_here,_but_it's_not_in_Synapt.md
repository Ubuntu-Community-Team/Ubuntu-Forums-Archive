---
title: "Have Google Chrome on here, but it's not in Synaptic and don't know how to remove it"
date: 2011-05-08
forum: New to Ubuntu
---

### Post by diablo75 on 2011-05-08
So I am wanting to remove this version of Google Chrome and I cannot remember where I got it from.  Must have installed it from a deb file.  Chromium is in the repositories but I added and removed it but the "Browse the web" shortcut in my root menu is still Google Chrome and it still runs.  Anyone know how I might either remove this browser or change the root menu's default browser shortcut so it's Firefox instead?

---

### Post by Not unique on 2011-05-08
I'm assuming you have already tried changing the default for now with** - SYSTEM-PREFERENCES-PREFERRED APPLICATIONS -**??

---

### Post by rosencrantz on 2011-05-08
Try 
sudo dpkg -e google-chrome 
(or google-chrome-stable) from a command line (I assume you installed a .deb package).
Or 
sudo apt-get remove google-chrome

---

### Post by Not unique on 2011-05-08
What about reinstalling it via DEB and/or PPA to see if it then turns up in synaptic and such, Could this help?
And do you have the DEB? Do you know which version it is?

---

### Post by diablo75 on 2011-05-08
> **Not unique said:**
> I'm assuming you have already tried changing the default for now with** - SYSTEM-PREFERENCES-PREFERRED APPLICATIONS -**??

No, I hadn't but when I did and checked to see what the default browser was it showed Firefox.  And then after I checked the main menu again it seemed that the default icon had also changed.  So I think that's got it fixed.

---

### Post by diablo75 on 2011-05-08
> **rosencrantz said:**
> Try 
sudo dpkg -e google-chrome 
(or google-chrome-stable) from a command line (I assume you installed a .deb package).
Or 
sudo apt-get remove google-chrome

Neither of these commands worked, saying it couldn't find those packages.  I even tried tab-completion of the package name and the closest it came up with was google earth.

---

### Post by diablo75 on 2011-05-08
> **Not unique said:**
> What about reinstalling it via DEB and/or PPA to see if it then turns up in synaptic and such, Could this help?
And do you have the DEB? Do you know which version it is?

I don't have the deb, I don't think.  If I do a search for Chrome in the main menu and run it, then check the about page, it showed it to be version 7.0.517.36 beta.  This happens regardless of whether or not the chromium-browser package is installed or not.

---

### Post by diablo75 on 2011-05-08
I'm going to mark this thread solved because I really just wanted the shortcut to change in the main menu and I've got that working now, but if anyone wants to continue trying to figure out what's up with this old version of Chrome lingering around, I'd be happy to keep things going here.

---

### Post by Not unique on 2011-05-08
How bout reinstalling via DEB or PPA to see if appears or updating it get anewer version (if possible) and see if that helps they may make it turn up.

Or have you tried **sudo dpkg -r Chrome**  already
Or **sudo dpkg -r Google Chrome**
Did you try these.

P.S. sounds like Firefox might of updated??

---

### Post by diablo75 on 2011-05-08
> **Not unique said:**
> How bout reinstalling via DEB or PPA to see if appears or updating it get anewer version (if possible) and see if that helps they may make it turn up.

Or have you tried **sudo dpkg -r Chrome**  already
Or **sudo dpkg -r Google Chrome**
Did you try these.

P.S. sounds like Firefox might of updated??

Got everything fixed now.

As mentioned a few posts up, after I went into the system preferences>prefered applications, I found that Firefox was already selected but I don't think this default was actually set until I had just then visited that control panel because after I closed it, Firefox suddenly did become the default and that large icon in the main menu was replaced.

If I searched for Chrome, it would still come up and it was the version 7 beta.

I went ahead and took your suggestion and downloaded the latest version of Google Chrome as a deb file from Google's website and installed it.  This effectively replaced version 7 beta with version 11.0.x

I was then able to remove the "google-chrome-stable" package (which didn't exist until now) using apt-get in the terminal.  I then installed Chromium via Ubuntu Software Center and it now shows Chromium instead of Chrome in the main menu when I begin searching for it (I only did this as an experiment because previously, when the Deb-based Chrome was installed, Chromium wouldn't show up in the menu (or the fact that I was typing "chrome" real fast removed "Chromium" from the search results because the endings are spelled differently).

Anyway, got everything figured out.  Thanks for the help everybody!

---

