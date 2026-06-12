---
title: "firefox slow performance"
date: 2009-06-09
forum: New to Ubuntu
---

### Post by mpennell on 2009-06-09
First, I apologize for not searching the forum to see if this has already been discussed. I imagine it has.

My FIrefox is runing interminably slow. just trying to log in to the forum hssa taken a long time. I have long sinc finished a cup of coffee waiting to be able to post. I am typing looking at a blank screen b/c the cursor is frozen (this sentencew was typed blindly b/c the cursor froze up and it was a few minutes fefore the text popped into place-- and that happened slowly too.

This is why I am not searching-- it would take the rest of the day to complete such a search, I suspect.

Any thoughts?

---

### Post by ddrichardson on 2009-06-09
Firefox is quite memory hungry and starting to feel a little sluggish.

Have you tried Chromium?

---

### Post by sdowney717 on 2009-06-09
chromium alpha development version is really nice to use. very fast.
no plugins will work. No java no flash no pdf.
you can install, set it up using the 3rd party software deb source and it will show in the update list.

goto system - administration - software sources
and add this line for intrepid 

deb [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) intrepid main

I dont have the key setup so it always complains it is not authenticated when I install or upgrade the chromium browser.
Adding it this way your package manager will automatically notify you of chromium updates.

a forum post says this, but if you run ubuntu intrepid use my software source line.

"Can I suggest you use the chromium build instead of the gvoogle chrome build :-

You can test out the Alpha build of Chromium by adding the following lines to your 'Software Sources': -

deb [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) jaunty main

Right click here and save to the desktop, click on the 'Authentication' tab of 'Software Sources' and 'add' it.

Then update your packages and install with: -

sudo apt-get update
sudo apt-get install chromium-browser

a few links
[http://ubuntuforums.org/showthread.php?t=1179780&highlight=chromium&page=4](http://ubuntuforums.org/showthread.php?t=1179780&highlight=chromium&page=4)
[http://www.shivaranjan.com/2009/05/17/linux-how-to-install-chromium-google-chrome-web-browser-in-ubuntu-li](http://www.shivaranjan.com/2009/05/17/linux-how-to-install-chromium-google-chrome-web-browser-in-ubuntu-li)

---

### Post by mpennell on 2009-06-09
Thanks for the input guys. Now, the bit from you, sdowney, is probably a bit over my head at this point in time (I am very new to ubuntu).

Here is an interesting thing: I closed Firefox and reopened and it IS running much faster. Does this confirm to you guys the notion that it's just too "memory hungry"?

---

### Post by ddrichardson on 2009-06-09
Firefox extensions are prone to memory leaks. Disable extensions and find which one is causing it.

---

### Post by mpennell on 2009-06-09
dd, thanks, i'll check into that. You know what, though? I forgot a real basic rule of browser use from the "old world" (the Windows world): to clear cookies and to deselect the "accept third party cookies" option. Think that'll help?

---

### Post by lovinglinux on 2009-06-09
You could check if ipv6 is enabled and disable it, but I guess it comes disabled by default in Jaunty.

You could also try to [optimize Firefox databases](http://ubuntuforums.org/showthread.php?t=1088094).

Some Firefox extensions can cause different sorts of problems. When I have several extensions enabled, Firefox peformance drops about 30%.

You can test Firefox performance at [http://service.futuremark.com/peacekeeper/index.action](http://service.futuremark.com/peacekeeper/index.action)

Just for curiosity, post you tests here. Would be nice if you could test with and without extensions. Create a new profile to test it without extensions by running this command:

```
firefox -P
```

I wouldn't use Chromium yet, because it lacks basic features. You could install the new Firefox 3.5 (Beta) instead by [clicking here](apt:firefox-3.5) [apt-get]. It is much faster than the current version. Please notice that it will make a copy of your profile and save it on it's own folder, to avoid conflicts.

---

### Post by skyjacker on 2009-06-09
> **mpennell said:**
> First, I apologize for not searching the forum to see if this has already been discussed. I imagine it has.

My FIrefox is runing interminably slow. just trying to log in to the forum hssa taken a long time. I have long sinc finished a cup of coffee waiting to be able to post. I am typing looking at a blank screen b/c the cursor is frozen (this sentencew was typed blindly b/c the cursor froze up and it was a few minutes fefore the text popped into place-- and that happened slowly too.

This is why I am not searching-- it would take the rest of the day to complete such a search, I suspect.

Any thoughts?
I dumped Firefox when I installed 9.x because it kept crashing. I now use seamonkey, and it works great. Appears to be basically the same browser, but made more for Linux... Good luck

---

