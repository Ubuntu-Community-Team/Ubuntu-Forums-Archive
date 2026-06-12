---
title: "Reset network settings, come prepared!"
date: 2008-05-31
forum: Networking &amp; Wireless
---

### Post by pterosky on 2008-05-31
I wanted to rename the Host name ("user name"-desktop) and read in the forum that I should just edit these two files, substituting "user name"-desktop with the new Host name:

```
gksudo gedit /etc/hostname
gksudo gedit /etc/hosts
```

That didn't work. When I opened my computer I would have to right-click on the network icon, disable and then enable the network to get the it up and running. Also, programs like HTTrack didn't play well with the new Host name, so I entered the original Host name("user name"-desktop), but the problem persisted.

I then figured that if I uninstalled and reinstalled the network, the network settings would be reset and all would be good, so I searched some more and found this for resetting the network settings:

```
sudo apt-get remove --purge network-manager net-tools
```
Then re-boot your system and re-install them again
```
sudo apt-get install network-manager net-tools
```
[http://ubuntuforums.org/showthread.php?t=724699](http://ubuntuforums.org/showthread.php?t=724699)

Oh boy, was I in for a world of hurt. 

I of course couldn't get on the internet since everything network related on my machine was gone, I also didn't have a 8.04 Live CD to reinstall from. I dug out a 7.04 Live CD and managed to download and burn a new 8.04 Live CD, only to realize that I couldn't really use it to reinstall the network.

Then the dependency hell started. I read somewhere that the individual packages could be downloaded from [http://packages.ubuntu.com/hardy/net/](http://packages.ubuntu.com/hardy/net/), fine. I downloaded the network-manager and network-manager-gnome packages to the desktop of the Live CD and moved them into my 8.04 installation home folder with ```
gksudo nautilus
``` Booted up, clicked on network-manager only to be greeted with the message "Error: Dependency is not satisfiable: ifupdown". Back to the Live CD, get that package. Boot up, click on that package, message "Error: Dependency is not satisfiable: net-tools". Again, Live CD, get that package. Boot up, click on that package, success, no dependencies unsatisfied! 

So to get my network up and running I needed these packages, installed in that order:

net-tools -net-tools_1.60-19ubuntu1_i386.deb
ifupdown - ifupdown_0.6.8ubuntu8_i386.deb
network-manager - network-manager_0.6.6-0ubuntu5_i386.deb
network-manager-gnome - network-manager-gnome_0.6.6-0ubuntu3_i386.deb

Reboot and install Network Manager via the Add/Remove applications interface.

Lesson learned today:
Ask for help to simple problems before trashing the system by running random commands in the terminal and wasting hours trying to fix it. I did learn a bit about how packages work the hard way :)

---

