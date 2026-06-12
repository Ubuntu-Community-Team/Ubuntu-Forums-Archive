---
title: "Multiple issues through networking problem"
date: 2013-11-07
forum: Networking &amp; Wireless
---

### Post by arnotte.alex on 2013-11-07
Hi all,

First of all this is my first time posting and I am a total Linux newbie, so please forgive me if I am posting in the wrong Section - however I do have multiple issues, including some Networking and Wireless... 
About the specs: I am running Ubuntu 10.04 (lucid) distro on an Apple Powerbook G4 (12 inch) 1.33GHz, which I installed through the computer's Open Firmware mode using a thumbdrive, since the machine's DVD-drive is broken.
Now after installation, the first and most important issue I had, was that the WIFI wasn't working. I read on some Forum that installing the WICD Network Manager solved that issue for some powerbook users, so that's what I did. Doing so, however, it uninstalled the built in Ubuntu network manager at the same time. However, the issue still remained unresolved. 
After some more in-depth research, I found the correct Driver for the WIFI-Card (it's the b43-legacy Driver). So I added the source to the Software Center and I found the driver, but (and there's the next issue), nothing can be installed through the software center anymore.... All programs are still available, the "install" button is still clickable (as is the uninstall button for allready installed software), but once pressed, absolutely nothing happens. The button greys itself so obviously it got the download "order", but nothing shows up on the left side-panel, where all download/install/uninstall  operations are shown in the "In Progress" section, so I couldn't even uninstall WICD( which stopped working after I added the source for the b43-legacy wifi driver (a message appeared a couple of times btw, stating that installation would involve installing from untrusted sources)),.
Ever since that started, I also have had a stop sign in the status bar on the top right corner; the message says:

Error: Marking the upgrade(E:Error,pkgProblemResolver::Resolve generated breaks, this may6 be caused by held packages.)

after looking that up, I checked out the running processes, but the apt-get process isn't even running (using the terminal I tried to download and installed software packages, but every time I've gotten a error message basically saying that an instance of the process is already running)...

Now yesterday, I tried reinstalling ubuntu completely from ground up through a thumbdrive again, yet that suddenly didn't work (however that was an Open Firmware issue, so I won't be going into it here, since it would be off-topic).

Is there any way to completely repair all System-Files / reinstall them maybe in some way without using an installation CD or USB or whatever ?

For some reason the ubuntu rescue option at boot-up isn't working (wether by accessing it through the "rescue" keyword, or setting it to true and then trying to execute it... )

Anyone can help me, I could really use every help I can get, I'm totally lost....

---

### Post by Bucky Ball on 2013-11-07
Welcome. Are you online with a cable? If not, that's the issue. Sounds silly question, but never know ... ;) Sounds like you're not which is why apt-get is not working. 

The Broadcom drivers will be ready and waiting if you get online with a cable and do an update. You shouldn't need to do anything manually. You will find them in Additional Drivers.

Also, you give a lot of information, a good thing, but you omit the release you are using (13.10 by any chance?). 12.04 LTS is a good place for a beginner to start. Stable, a known entity and supported until 2017 (non-LTS releases only have nine months support).

---

### Post by arnotte.alex on 2013-11-07
well I am actually posting from the powerbook itself.... it has a 24/7 ethernet connection; and the distro is 10.04 lucid, since I heard it was supposed to be the smoothest for these old powerbooks...

---

### Post by Bucky Ball on 2013-11-07
10.04 LTS has reached end-of-life and is no longer supported. Install 12.04 LTS or go for something lighter like Xubuntu 12.04 LTS. Ubuntu 12.04 is supported until 2017, Xubuntu until 2015.

---

### Post by arnotte.alex on 2013-11-07
well i'd love to but for some reason i can't anymore, something with the open firmware... and when trying to upgrade from the update manager, i get an "unresolved problem occured while calculating the upgrade " error message :(

---

### Post by Bucky Ball on 2013-11-07
> **arnotte.alex said:**
> ... when trying to upgrade from the update manager, i get an "unresolved problem occured while calculating the upgrade " error message :(

Sounds like not enough room on the partition, though I could be wrong. The upgrade needs some headroom (not sure how much) as it needs to download stuff it later deletes to do the upgrade. If there's not enough room then won't happen. Not as simple as replacing one with the other, even though they may be similar in size once the upgrade is installed. 

If you can free up some space and grow the partition a bit, give that a try. Unless I'm off the mark, that is. ;)

---

### Post by wildmanne39 on 2013-11-07
The fact that 10.04 is EOL is also the reason you can not upgrade but you would not want to anyway from 10.04 to anything with unity it would cause a lot of breakage, the best thing to do is back up important data and do a fresh install.

I suggest a light distro like lubuntu.

---

### Post by arnotte.alex on 2013-11-07
@Bucky Ball
It couldn't be size issue, sinze the entire HD (80Gb) is only for ubuntu , and i don't have any files on it yet so the system has the enitre 80 gigs for itself left (minus the standard installation files obviously)...

@WildMan:
ok, thank's for the tip, I'll do so! then again another question: is it possible to do so from an internal point of view, since the dvd drive doesn't work and a thumbdrive installation fails (tried it with 10.04 and 12.04 all over again hoping to just redo an entire clean install)?

---

