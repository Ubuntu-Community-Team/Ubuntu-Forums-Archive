---
title: "Something in feisty breaks my wireless setup"
date: 2007-04-30
forum: Networking &amp; Wireless
---

### Post by syntoad on 2007-04-30
Apparently some upgrade in feisty makes me unable to connect to my school's wireless network anymore.

From a fresh install of Edgy I am able to connect with no problems. After installing Edgy updates I am able to connect as well. If I upgrade my Edgy to Feisty the connection no longer works.

The network uses WPA encryption and my main wireless card is a bcm4318. (I'm using xubuntu and network-manager-gnome by the way if it makes any difference.)

Here's what I've tried:

To rule out the kernel:
(in Feisty)
Booted with the Edgy kernels.
Used a different network card (prism2.)
Used both ndiswrapper and kernel drivers.

To rule out network manager and wpa supplicant:
(in Edgy)
Started with a fresh install of Edgy, upgraded only the packages necessary to install network-manager from feisty repositories. The connection still worked perfectly so then I proceeded to upgrade wpa-supplicant and all of it's dependencies. The wireless still worked.

I also tried backing up my gconf tree (where nm-gnome saves the connection data) and restoring it after an upgrade to no avail.

When I am trying to connect nm-applet either just hangs at "connecting to network osuwireless" The two lights on the applet (not sure what they mean) never turn on. A check of the syslog after failure tells me that authentication was successful, but then it times out while waiting for something else (60 second timeout) Sorry to be so vague on the log messages, etc. I am busy reinstalling Edgy on my laptop right now, I can't really be without internet for too long at school.

I like a  lot of the new updates in Feisty and want to be able to upgrade. Does anyone have any ideas what else could cause this problem? It seems to be similar to what some other people here are experiencing as well.

Edit:

I should probably also add that I have no trouble at all in feisty connecting to my home wireless network which uses no encryption. (I know that's bad :P My father uses an old card that doesn't support any easy encryption so my router just filters allowed MAC addresses)

---

### Post by luisromangz on 2007-04-30
Here happens the same, although I am using Kubuntu and KNetWorkmanager. I have a bcm4318 wireless card in my laptop.

---

