---
title: "firefox 3.5 and 3.6"
date: 2009-11-11
forum: New to Ubuntu
---

### Post by Sup3r3g0 on 2009-11-11
How do I install both firefox 3.5.3 and firefox 3.6b2? Do I create a separate profile for each one?

---

### Post by bodhi.zazen on 2009-11-11
Firefox is available as a binary.

Download it from here : [http://www.mozilla.com/en-US/firefox/all-beta.html](http://www.mozilla.com/en-US/firefox/all-beta.html)

extract the archive

run it from the command line or make a custom launcher.

No you do not need a separate profile to run firefox 3.6.

See also : [http://support.mozilla.com/en-US/kb/Installing+Firefox+on+Linux](http://support.mozilla.com/en-US/kb/Installing+Firefox+on+Linux)

---

### Post by slumbergod on 2009-11-11
or add the PPA for mozilla-daily:
[http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) karmic main

Reload synaptic then just add firefox 3.6.

If it is stable you can uncheck the repo to stop it from updating each day. If you don't like it, you can just remove it in synaptic.

It worked fine alongside FF3.5.4 just sharing my profile.

---

### Post by itsbrad212 on 2009-11-11
just install:

firefox-*version*-branding

(search around in synaptic. *version *is like, 3.5)

---

### Post by Sir Jasper on 2009-11-11
Hi,

The latest stable version, at least for Windows, is 3.5.5 and you could try that and/or 3.6 in Wine (both Windows versions are available from PortableApps) where they should run quickly and efficiently in Wine.

I have tried 3.5.5 in Wine only because I will not be upgrading from ´buntu 9.04 (which works extremely well) to 9.10 until next February/March.

My regards

PS  My  ´buntu FF right- click context menu was so cluttered with things I never use that I installed  the add-on ¨Menu Editor¨ and I cleared some 2/3rds out.

---

### Post by PaulInBHC on 2009-11-11
Following these instructions, sort of...

[http://support.mozilla.com/en-US/kb/Installing+Firefox+on+Linux](http://support.mozilla.com/en-US/kb/Installing+Firefox+on+Linux)

I extracted the tar to the downloads location. There I found a folder Firefox. I moved the folder to Home. in the terminal I typed

cd /home
~/firefox/firefox

This only works after you close the other firefox.

---

### Post by winotree on 2009-11-11
You really ought to consider the advice and link offered by **slumbergod **in post 3.  Several  weeks ago I had the two versions of Firefox set up and running on my old EeePC and could open both simultaneously.  I've settled on the 3.5.6pre -- just got an update this evening.  Nice.  ;)

---

