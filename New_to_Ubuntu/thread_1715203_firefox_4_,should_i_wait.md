---
title: "firefox 4 ,should i wait?"
date: 2011-03-26
forum: New to Ubuntu
---

### Post by werty2010 on 2011-03-26
i have ubuntu 10.10 installed with the default firefox 3.16.16
i went to their homepage and saw that firefox 4(not beta) was available for download
i'd like to install it but im not sure if i should wait for the updates through the update manager, if eventually comes to "10.10" ?

---

### Post by mikewhatever on 2011-03-26
The update will come eventually, but it might take until 3.6 reaches EOL. If you want Firefox4 now, then don't wait.

---

### Post by hakermania on 2011-03-26
[http://ubuntuforums.org/showthread.php?t=1712247](http://ubuntuforums.org/showthread.php?t=1712247)   :)

---

### Post by sammiev on 2011-03-26
Been using it since it came out. Read [this]("http://ubuntuforums.org/showthread.php?t=1712247") if you want it now. GL :)

---

### Post by hakermania on 2011-03-26
> **sammiev said:**
> Been using it since it came out. Read [this]("http://ubuntuforums.org/showthread.php?t=1712247") if you want it now. GL :)

Double post :P

---

### Post by werty2010 on 2011-03-26
since im on a 64bit installation i'd like to know if you had any problems with extentions....?

---

### Post by sammiev on 2011-03-26
> **werty2010 said:**
> since im on a 64bit installation i'd like to know if you had any problems with extentions....?

As well here running 64bit with no problems. GL :)

---

### Post by stmiller on 2011-03-26
> **mikewhatever said:**
> The update will come eventually, but it might take until 3.6 reaches EOL. If you want Firefox4 now, then don't wait.

Ubuntu is not going to update to Firefox for 10.10 and earlier.

There is a mozilla stable ppa you can use to upgrade to Firefox 4:

[http://www.omgubuntu.co.uk/2011/03/firefox-4-ppa-for-ubuntu-10-04-and-10-10-users/](http://www.omgubuntu.co.uk/2011/03/firefox-4-ppa-for-ubuntu-10-04-and-10-10-users/)

---

### Post by I2k4 on 2011-03-26
The only extensions I like that aren't available are those that are Windows exclusive anyway:  IE Tab and Cooliris.  

There is one site I reference regularly that is using some old Java code that is not working right on FF4, otherwise it's a faster browser and seems not to cause some of the rendering errors that were screwing up FF3.6 and requiring "try again" clicks.

I've found it's still worth doing about:config tweaks for pipelining, etc. - the ones I'd done carried through to the upgrade, so didn't need to redo them.

---

### Post by kherring7383 on 2011-03-27
I've been using Ubuntu for about a year now, and for me, if there's one thing I've learned, is to wait until the official release is in the Repository. If you have no issues with the current version of Firefox I'd suggest sticking with it.

---

### Post by Enigmapond on 2011-03-27
> **kherring7383 said:**
> I've been using Ubuntu for about a year now, and for me, if there's one thing I've learned, is to wait until the official release is in the Repository. If you have no issues with the current version of Firefox I'd suggest sticking with it.

It already has been released and it works wonderfully. There are still extensions that aren't working but that will remedy soon I'm sure, given their release schedule this year...

```
sudo add-apt-repository ppa:mozillateam/firefox-stable
sudo apt-get update && sudo apt-get upgrade
```

This repo is for 10.04 and 10.10 only.

Cheers!

---

### Post by aaaaalex on 2011-03-27
Non you should not :-D

After reading this thread yesterday i uped to FF 4 and now, after about 24 hours I can say it was well worth it. I am not using that many add-ons but all the ones i want are already up and running on FF 4. 

Why wait until tomorrow if you can surf the web faster today?

---

### Post by werty2010 on 2011-03-27
followed your instruction and it works as it should be
thank you all for your help

---

### Post by beew on 2011-03-27
> **kherring7383 said:**
> I've been using Ubuntu for about a year now, and for me, if there's one thing I've learned, is to wait until the official release is in the Repository. If you have no issues with the current version of Firefox I'd suggest sticking with it.


Updated versions for 99.99% of softwares will never make it into the official repos (with exceptions like Firefox only because of a very recent change in policy but even that has to wait for a long time) In Ubuntu the repository is frozen even before release except for security updates and some bug fixes (so if you use LTS there will be no feature updates for programs over 3 years)

 I have used Ubuntu for about 8 months and one thing I have learned is that ppas are great and all the warnings about instability are vast exaggerations (there are occasional problems but so far nothing that I could not get myself out of) It is a lot more stable to keep up to date with ppas than to upgrade the whole OS every 6 months wiping out all customizations and potentially turning your work system into a beta testing box.

@OP,

Use the Mozilla ppa posted above. I installed ff4 the next day it came out, works great.

---

### Post by R.Bucky on 2011-03-27
I have mirrored the Firefox 4 Stable repo on my server. If you want to install it via Synaptic/apt-get, add the following line to your sources.list:

deb [http://firefox.nwlinux.us](http://firefox.nwlinux.us) lucid main

Then

sudo apt-get update
sudo apt-get install firefox. 

Seems fine in Ubuntu Desktop 10.04 32-bit.

---

### Post by 3177 on 2011-03-27
```
    sudo add-apt-repository ppa:mozillateam/firefox-stable     sudo apt-get update && sudo apt-get upgrade
```
there you go man. 
no need to wait.

---

### Post by 3177 on 2011-03-27
> **R.Bucky said:**
> I have mirrored the Firefox 4 Stable repo on my server. If you want to install it via Synaptic/apt-get, add the following line to your sources.list:

deb [http://firefox.nwlinux.us](http://firefox.nwlinux.us) lucid main

Then

sudo apt-get update
sudo apt-get install firefox. 

Seems fine in Ubuntu Desktop 10.04 32-bit.


that only re-installs firefox 3.16

---

### Post by R.Bucky on 2011-03-27
Check the repo again. [http://firefox.nwlinux.us/pool/main/f/firefox/](http://firefox.nwlinux.us/pool/main/f/firefox/)
it's in there...

---

