---
title: "Updating software"
date: 2010-06-11
forum: New to Ubuntu
---

### Post by rtspear on 2010-06-11
Hi all -

I have Stellarium 0.10.4 installed and working. There's a new 0.10.5 available that I'd like to install - how do I do that?

Richard

---

### Post by SlidingHorn on 2010-06-11
Instructions on the main stellarium page are pretty detailed:

> Stellarium 0.10.5 available for Ubuntu 10.04
Stellarium 0.10.5 binary packages are now available for Ubuntu 10.04 Lucid Lynx through a Launchpad PPA (Personal Package Archive).

Stellarium's Ubuntu Releases PPA can be found at Launchpad:
[https://launchpad.net/~stellarium/+archive/stellarium-releases](https://launchpad.net/~stellarium/+archive/stellarium-releases)

To get the updated Stellarium packages, you can either:

a) use the Software Sources utility to add the "ppa:stellarium/stellarium-releases" line to the list of software sources, and then use the Synaptic package manager or the Ubuntu Software Center to update Stellarium's packages.

b) open a terminal and run some commands:

To add the PPA to the list of repositories:

sudo add-apt-repository ppa:stellarium/stellarium-releases

and then, to look for package updates:

sudo apt-get update

As the Launchpad PPAs are not as extensively mirrored as Ubuntu's main repositories, downloading the packages may be slow. If the download halts, cancel and restart the installation. In most cases, the download's progress will be saved and it will continue from the point it stopped. 

[http://www.stellarium.org/](http://www.stellarium.org/)

---

### Post by rtspear on 2010-06-15
Ah! I missed this:

"a) use the Software Sources utility to add the "ppa:stellarium/stellarium-releases" line to the list of software sources, and then use the Synaptic package manager or the Ubuntu Software Center to update Stellarium's packages."

Thanks!

Richard

---

### Post by drmahesvaran on 2010-07-20
> **SlidingHorn said:**
> Instructions on the main stellarium page are pretty detailed:



[http://www.stellarium.org/](http://www.stellarium.org/)

Updated Thanx :D:D:D:D:D:D

---

