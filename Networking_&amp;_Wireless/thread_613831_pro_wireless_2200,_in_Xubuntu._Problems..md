---
title: "pro wireless 2200, in Xubuntu. Problems."
date: 2007-11-15
forum: Networking &amp; Wireless
---

### Post by rayraymo on 2007-11-15
Hello there. 

I'm using the latest Xubuntu on a laptop installed through windows. But I'm having trouble with my wireless card- pro wireless 2200, which should be, (And kinda is supported 'out of the box'.)

Firstly I have no network-manager and so I've been trying to connect to a open wireless network via the console. But when I get to the command- sudo dhclient eth1, the console tells me that I can't get a connection.

The only source of internet I have is my unis opn wireless network and so I can't connect via lan to download network manager, which I presume will solve the problems. And so after reading this post, [http://ubuntuforums.org/showthread.php?t=399101](http://ubuntuforums.org/showthread.php?t=399101) I see I can download the 'package (and all its dependencies) from [http://packages.ubuntu.com](http://packages.ubuntu.com)'. But I'm unsure what files to download from here- [http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=network-manager&searchon=names&subword=1&version=gutsy&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=network-manager&searchon=names&subword=1&version=gutsy&release=all)

I obviously need the first one, but I can't see any that are specific to the Xfce desktop I'm using.

And soooooo I'd like to know which files I need to download, unless there is a fix for connecting via the console, (As I'll obviously be able to download networkmanager through ubuntu itself if I could connect.)

Thanks

Raymo

---

### Post by Whiffle on 2007-11-15
try this:

```

sudo ifconfig eth1 up
sudo iwlist eth1 scan
sudo iwconfig eth1 essid <nameofnetwork>
#wait a bit here
sudo iwconfig 
#make sure it connected to the access point, you should see a mac address for it #nd the name
sudo dhclient eth1

```

Shouldn't need to download any packages yourself.  Heck, you might already have it.  Try doing Alt+F2 and running "nm-applet" and see if a network manager applet pops up in your taskbar.

---

### Post by rayraymo on 2007-11-15
Thanks for the quick reply.

I tried what you said and I still get the 'no dhcp offers received. no working leases in persitent database - sleeping. ' error.

Also when search for the program you suggested it came back saying it can't find it.

---

