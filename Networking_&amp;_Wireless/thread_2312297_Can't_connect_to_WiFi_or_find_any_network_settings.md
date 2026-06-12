---
title: "Can't connect to WiFi or find any network settings?"
date: 2016-02-03
forum: Networking &amp; Wireless
---

### Post by sean109 on 2016-02-03
Couldn't seem to find an answer for this anywhere. 

I installed Ubuntu 14.04  LTS about a week ago, I set up my wifi when prompted during the set up process. Everything was working fine. Yesterday after booting my laptop I opened Firefox and couldn't connect to the Internet. 

I then realised there was no wifi symbol in the bar at the top of the screen, and when I go to system settings nothing comes up under network. 

I'm connected to my home wifi on my phone right now, but still can't connect to it on my laptop.

---

### Post by ajgreeny on 2016-02-03
On your 14.04 installation were you updating using the proposed repos?

If you were you need to disable them and download three library packages and install them using dpkg.
See [http://ubuntuforums.org/showthread.php?t=2311992&p=13432377#post13432377](http://ubuntuforums.org/showthread.php?t=2311992&p=13432377#post13432377) for some more info in another thread.

---

### Post by sean109 on 2016-02-03
It wasn't an update, I had burned Ubuntu 14.04 to a CD and on installation wiped Windows completely. 

I can't seem to run the Network Manager either, I might have updated to an unstable version because I had that box checked in the update settings.

---

### Post by ajgreeny on 2016-02-04
Did you do a normal update of the OS once it was installed?
Open software-sources, go to the Update tab and see if the proposed repos are enabled.  We can work from there.

---

### Post by sean109 on 2016-02-04
I ended up completely reinstalling and everything is now back to normal. Still don't know what happened, but I appreciate your help nonetheless!

---

### Post by ajgreeny on 2016-02-05
OK, that is good news, but do make sure you are not using the proposed repos for your updates or you may end up in the same position again.

---

