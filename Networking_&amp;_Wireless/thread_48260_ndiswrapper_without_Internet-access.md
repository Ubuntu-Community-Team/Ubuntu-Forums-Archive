---
title: "ndiswrapper without Internet-access"
date: 2005-07-11
forum: Networking &amp; Wireless
---

### Post by boschtoo on 2005-07-11
Hi there everyone,
I've just installed Kubuntu for testing purposes on a (little older) machine that stands around in my office. Unforunaltely, this PC had a RedHat  Fedora 3 intall before, that worked with a USB WIFI-dongle. So, here I am now with a basically working machine, but no network connection (there's no ethernet card on this box). I googled around for a while, but I can't find any clues on how to install the ndiswrapper without any  internet connection on the machine. Basically I thought that this would be matter of a quick download (kinda like some packages from freshmeat when I installed the RH box)... but: oops! Seems that the "user friendliest linux distribution" does not like unplugged systems.
So my question is: is there any way to install ndiswrapper (and, as far as I understood some tool-packages needed in order to work) without direct internet connection? I have a few other PC's with internet and a USB key (I managed it to work with Kubuntu quite easy).

No "first priority matter", it's just a test. But any help would be appreciated.
Thanks in advance,

Rodolphe

---

### Post by varunus on 2005-07-11
You could download the .deb files from [http://packages.ubuntu.org/hoary/](http://packages.ubuntu.org/hoary/) manually, copy them over on CD or USB stick, and then install them manually.

---

### Post by boschtoo on 2005-07-11
Thanks varunus for your quick reply!
It's just that your link is broken... (?)... tells me to check the correct URL. But my google searches all broutght me up to image download sites... none where one ca select it's packages one by one.

And what packages do I need exactly? There seems to be a ndiswrapper-tools package as well... do I need that?

---

### Post by varunus on 2005-07-12
Oh, I'm sorry. Made a typo there.  The correct URL is [http://packages.ubuntu.com/hoary/](http://packages.ubuntu.com/hoary/)   O:) 

You will need the ndiswrapper-source package and the ndiswrapper-utils package. You will also need "build-essential" and "linux-headers" for your kernel version (if this is a clean install, you'll need linux-headers-2.6.10-5-386). You will need to compile ndiswrapper from the package; I think there are instructions on these forums somewhere.

Good luck.

---

