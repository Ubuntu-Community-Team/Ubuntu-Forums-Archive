---
title: "Help Installing Network Manager"
date: 2007-02-19
forum: Networking &amp; Wireless
---

### Post by matt80 on 2007-02-19
Hi,

I have a clean install of Ubuntu 6.10 and when I try to install Network Manager from the graphical add programs tool, i get the following error:

"Network Manager cannot be installed on your computer type (i386)"

My CPU is an Athlon XP 1900+, but in Device Manager it is just listed as "Processor". I have tried installing from the command line with:

apt-get install network-manager-gnome

But it just says that it cannot find anything to install with that name. And since I cannot get on the Internet (which is why I need network manager), wouldn't this be useless anyway? (I thought apt-get installs stuff from the Internet?).

Thanks for any help

---

### Post by ctsdownloads on 2007-02-19
Wild guess here, did you install the 64bit version of Ubuntu? I could be fishing here...

---

### Post by matt80 on 2007-02-19
I downloaded: ubuntu-6.10-desktop-i386.iso. I'm pretty sure that's correct?

Might it be a problem that Device Manager doesn't recognise the specific type of CPU I have? Now I'm fishing :)

---

### Post by mikewhatever on 2007-02-19
You probably need to enable some extra repositories in the sources.list.
System->Administration->Software Sources and add Universe and Multiverse.

---

### Post by matt80 on 2007-02-19
OK, I will try that - but aren't they all online repositories? I need network manager because I cannot get my internet connection working (wireless setup), so enabling more online repositories would make no difference... or is that not how it works?

---

### Post by mikewhatever on 2007-02-19
Yes they are. If there is no connection, then that's probably the reason for the error. You can get the network manager package from the link below:
[http://ubuntuforums.org/showthread.php?t=286188&page=2&highlight=intel+wireless+3945](http://ubuntuforums.org/showthread.php?t=286188&page=2&highlight=intel+wireless+3945)
someone there put all the dependencies together. Use some removable media to install. 
Have you tried entering network name and WEP in System->Administration->Networking? It should work this way. A network manager just makes it easy to switch between different networks.

---

