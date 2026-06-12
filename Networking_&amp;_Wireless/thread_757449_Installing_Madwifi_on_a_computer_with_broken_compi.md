---
title: "Installing Madwifi on a computer with broken compiler"
date: 2008-04-16
forum: Networking &amp; Wireless
---

### Post by Furbs on 2008-04-16
I am trying to get my computer onto the internet. It's a 2.4Ghz celeron 634mb RAM (onboard video) with Xubuntu Gutsy Gibbon installed, and I've found that none of my programs will install because it seems the C compiler is broken. I tried installing the C compiler from CD, which also did not work. I was told in another thread to post this here, so here it goes.

I just got a D-Link Rangebooster-G (model WDA2320), which has the Atheros chipset and is supposedly workable with the Madwifi drivers. This might be a good time to say that I don't know a whole lot about computers, and especially Linux. Anyway, it seems like all the methods for installing Madwifi involve using apt-get, which will not work because I'm not connected to the internet already. Yet, I need apt-get to install the drivers to connect to the internet. This paradox has been killing my brain for the last few days and I'm hoping someone can help! Thanks so much :)

---

### Post by Whiffle on 2008-04-16
I think what you need to do is find the linux-restricted-drivers paackage for your kernel version and the madwifi tools package, copy that onto the computer somehow (usb key maybe), and then you can install them with the command:

sudo dpkg -i nameofpackage.deb

Heres the madwifi tools package:
[http://packages.ubuntu.com/gutsy/madwifi-tools](http://packages.ubuntu.com/gutsy/madwifi-tools)

and a list of the different linux-restricted-modules:
[http://packages.ubuntu.com/search?keywords=linux-restricted-modules&searchon=names&suite=gutsy&section=all](http://packages.ubuntu.com/search?keywords=linux-restricted-modules&searchon=names&suite=gutsy&section=all)

You can find your kernel version with the command (in terminal):
uname -r

---

### Post by The Cog on 2008-04-17
Yes it's rather chicken-and-egg, isn't it?

You can grab the .deb files from [http://gb.releases.ubuntu.com/releases/7.10/](http://gb.releases.ubuntu.com/releases/7.10/) with another computer and transfer them on a USB stick. Note the dependencies listed against each library - you will need to hunt down all the dependencies and their dependencies too.

You can install a .deb by just double-clicking the file.

---

### Post by Furbs on 2008-04-18
Thanks to both of you for such helpful replies! I am typing this in Ubuntu right now : )

Linux can be rough, but I'm thankful for the handy package manager and also all the helpful people in the Ubuntu community. Thanks again!

---

