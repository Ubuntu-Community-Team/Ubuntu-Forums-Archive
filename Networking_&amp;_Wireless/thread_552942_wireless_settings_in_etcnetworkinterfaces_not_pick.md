---
title: "wireless settings in /etc/network/interfaces not picked up."
date: 2007-09-17
forum: Networking &amp; Wireless
---

### Post by dmosses on 2007-09-17
Ok,

First of all the background...

New install of Ubuntu Server (Feisty - 7.0.4).

I have a new Belkin 54G wireless pci card.  I have downloaded and installed the most recent version of ndiswrapper (after failing to get it to work with ndiswrapper-utils-1.9 in the repo).  

After doing the usual depmod -a, modprobe ndiswrapper, iwconfig, ifconfig etc I managed to get the connection working - great!

I then restarted the computer and the settings were lost - not so great.

research on the internet - ah - add the settings to /etc/network/interfaces - great!

But - I just can't get it to work.

my /etc/network/interfaces file contains the following...

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

#The wireless interface
auto wlan0
iface wlan0 inet dhcp
wireless-mode Managed
wireless-essid myssid
wireless-key s:mywepkey

I can't see anything wrong, but when I do /etc/init.d/networking restart, eth0 works fine, but wlan0 fails to get an IP address from the router.

If I run ifdown, ifup, and then iwconfig the essid is not set on for the card.

To be clear - if I run the iwconfig commands from the command line I am able to connect fine - it just seems that they're not being picked up from the interfaces file.

Can anyone help me please?

---

### Post by leftyfrizzell on 2007-09-20
I'm seeing the same thing on mine.  It just doesn't seem to read the file completely.  I hope someone can figure this out.  It seems that this may be a Debian issue as Fedora, et don't have this problem as they use other config files to do the same thing.

lefty

---

