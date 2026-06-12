---
title: "Upgrading Ubuntu version over a capped Internet connection"
date: 2009-10-01
forum: New to Ubuntu
---

### Post by diablo75 on 2009-10-01
I currently get my Internet access via an ISP that is quite expensive (but expected considering my remote location).  They sell bandwidth by the megabyte per-day and right now I buy 200 MB per day.

Pretty soon, Ubuntu 9.10 will be released and I'm the kind of guy who likes to upgrade about a month after the release (dodge the heavy traffic, let a few bugs get caught and fixed).  I will want to be able to upgrade but also interrupt the download of new packages at about 100 MB intervals so I still have some left over for other Internet browsing.  Then after about 5 to 10 days of this, I should have all the packages needed to finally go through with the upgrade.

Alternatively, I could have an Alternate CD burnt at home and mailed to me, but I would still expect many packages to require downloading after the fact and probably would still need more than 200 MB of data for downloading.

So my question is:

Has anyone ever faced a bandwidth cap like this before?  And how did you work with it during a distro upgrade?

---

### Post by scragar on 2009-10-01
I've done full upgrades without an internet connection at all, the trick is to wait for the .1 release with the first big batch of updates, then you'll want to upgrade to that using a CD if possible, because it will still be a huge download(probably larger than the official release actually).
I say this just because when the .1 release comes out you'll have a large number of updates in a very short period of time, I'm not sure if 200MB would be enough.

---

### Post by bobtfish on 2009-10-01
You could get a download manager that allows you to pause, I looked [here]("http://www.ubuntugeek.com/list-of-download-managers-available-in-ubuntu.html") and Gwget looks pretty simple, and I looked in Synaptic, it says I only need to download 228Kb for it.
Or you could order a cd/dvd from one of the various places that sell them, I've not used them but I think they're very cheap. You can also order one free from the Ubuntu website, but it says they take a very long time to send, and I don't know what you mean by a remote location, but I suppose they might not send to where you are.
Chris

---

### Post by BQAggie2006 on 2009-10-01
Maybe try to request a free CD from Ubuntu, then when it arrives, add it to your software sources, and then run:
```
sudo apt-get dist-upgrade
```

Or if you can get the CD from home follow the same procedure.

---

