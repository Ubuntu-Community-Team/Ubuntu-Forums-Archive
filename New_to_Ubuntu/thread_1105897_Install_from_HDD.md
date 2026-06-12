---
title: "Install from HDD"
date: 2009-03-25
forum: New to Ubuntu
---

### Post by epicmono on 2009-03-25
My friend wants to use Kubuntu but he doesn't have an internet connection. Without that he won't be able to download and install the mp3 and dvd playback files. Is there any way that I can download an OFFLINE installer to those things ( and other softwares like VLC and Xine and Grip ) so that I can take those files to his PC and install them?

I would prefer having .deb files even if they are older version rather than have to compile from source. I'm just too dumb to compile. :D

---

### Post by arochester on 2009-03-25
Look at Keryx:  [http://keryx.betaserver.org/](http://keryx.betaserver.org/)

---

### Post by egalvan on 2009-03-25
Here is one solution...

[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)


or you can buy the 8.10 repo's on DVD here

[http://www.osdisc.com/cgi-bin/view.cgi/products/linux/ubuntu/repo.html?ad=distrowatch](http://www.osdisc.com/cgi-bin/view.cgi/products/linux/ubuntu/repo.html?ad=distrowatch)

The DVD set will not have the most up-to-date, but it will be close.
And it only has the "main" and "universe" repos.

---

### Post by KCG102282 on 2009-03-25
Use remastersys and make a installable copy of your system for him to install.

---

### Post by balaknair on 2009-03-25
Option 1:
Use something like apt-on-cd on a PC with internet access(which already has all the packages needed) to copy all the needed packages on to a CD or DVD, add the CD to 'Software Sources' and install from that. If you don't have the files installed on the first PC, use Synaptic to get the files(see option 3). Just make sure you're using the same version of Ubuntu though(same release, same architecture- eg: 8.10, 32-bit; the flavor- Ubuntu, Kubuntu, Xubuntu- doesn't really matter much, but occasionally some extra packages might be needed, for which you can check method three)

Option 2:
You can get the deb files individually from the Ubuntu servers
( [http://packages.ubuntu.com/](http://packages.ubuntu.com/) )

Option 3:
If the net-connected PC(your PC) and the target PC(your friend's PC) are using different flavors of K/X/Ubuntu, and you just want to download the deb files(without installing on your computer), choose that option in the Synaptic confirmation dialog(see screenshot). Then use apt-on-cd to put those on to an installable CD/DVD.

---

### Post by epicmono on 2009-03-25
Thanx.. Will try apt on cd thing.. If i download from synaptic only the installer where will the deb file be saved?

---

### Post by EXCiD3 on 2009-03-25
[Keryx]("http://keryx.betaserver.org") will be the easiest option. It is as if you were working from your offline machine, but you can download the packages (and all the dependencies) from any computer, Windows, Linux, or Mac. No need for burning CDs or searching for dependencies. Keryx will also check for updates as well so you can have all the updates as well.

---

