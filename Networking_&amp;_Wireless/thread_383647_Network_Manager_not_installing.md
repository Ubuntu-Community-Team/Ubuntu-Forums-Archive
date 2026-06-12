---
title: "Network Manager not installing"
date: 2007-03-13
forum: Networking &amp; Wireless
---

### Post by SGorilla on 2007-03-13
Hi, on fresh install of Ubuntu 6.10 it tried to install network manager by using the command "sudo apt-get install network-manager-gnome network-manager".
When i press enter it comes up with an error: "Couldn't find package network-manager-gnome"
I also tried "sudo apt-get update" and that failed too.
Can anyone help?

EDIT: I found network manager and i have put it on a USB stick. It's called NetworkManager-0.6.4.tar.bz2 how do i install it from there? I'm pretty new to Linux but i know the basic basics.

---

### Post by cyberdork33 on 2007-03-13
apt is probably failing if you have no internet access. can you connect via ethernet until you get the utilities needed for wifi?

that file on your thumbdrive is probably source which will have to be compiled. Try to fix apt first as you are going to need that more than once.

---

### Post by SGorilla on 2007-03-14
I tried putting my router on WEP but it still didn't work. Can't i put all the files necessary onto a USB stick in windows?

---

### Post by cyberdork33 on 2007-03-14
the idea behind apt is that is calculates all the dependencies automatically, and installs them if needed. If you try to do that manually, you will probably end up searching for dependency after dependency, then those programs' dependencies as well. Just plug your computer into a ethernet jack temporarily, install all the neeed stuff to get WiFi working (network-manager, wifi drivers, etc) then you can connect via wireless after that for all the future.

---

