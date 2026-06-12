---
title: "Optimizing /etc/network/interfaces"
date: 2006-09-13
forum: Networking &amp; Wireless
---

### Post by Tonren on 2006-09-13
Hi guys.  I have a laptop with 2 basic configurations:

1.) Wired, in my dorm room - no wireless networks available
2.) Roaming around campus - multiple wireless networks with their own ESSIDs and APs, no encryption.

Right now, this is what my /etc/network/interfaces looks like:

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
        pre-up ifconfig eth1 down
        pre-up ifconfig eth0 up

auto eth1
iface eth1 inet dhcp
        pre-up /home/mcantor/bin/wireless
```

This is what's in /home/mcantor/bin/wireless:

```
#!/bin/bash

sudo rmmod bcm43xx
sudo modprobe bcm43xx
sudo ifconfig eth0 down
sudo ifconfig eth1 up
sudo iwconfig eth1 ap any
sudo iwconfig eth1 essid any
```

I think this is OK, except that on bootup (which is the important thing - this should all be automatic!), it's going to waste time trying to connect to the wireless network if I'm actually wired.

My question to you folk is this: How do I make my /etc/network/interfaces check for a wired connection before attempting wireless?

---

### Post by Tonren on 2006-09-27
Bump... can anyone help me out?  I really think that Ubuntu should be able to emulate Windows in this respect... plugging in an ethernet cable should initiate ifup eth1, and on boot, it hsould be able to query which connection is active.

---

### Post by wieman01 on 2006-09-27
_My proposal:_
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp
```
You don't need anything else if you are not going to use wireless. Restart the network and see for yourself if it works:
> sudo /etc/init.d/networking restart

---

### Post by Tonren on 2006-09-27
wieman, the trouble with that, I think, is that if a connection is unavailable, it will hang on Configuring Network Interfaces.  Also, I DO want to use wireless!  It should be able to detect what kind of connection is available on bootup, and configure the corresponding device.

---

### Post by wieman01 on 2006-09-28
Yes, that's indeed the trouble. The system will try to connect via both devices. The only way you can stop that is by pressing "crtl + c". 

I don't know any other way... Sorry for it.

---

### Post by Tonren on 2007-01-08
Does anyone know of a solution for this yet?  There really should be a way to emulate Windows' automatic network configuration capabilities.  Why can't Linux networking detect whether or not there's a cable plugged into the ethernet port?  Why can't Linux networking detect whether or not there are available wifi networks before wasting two minutes trying to connect?  I feel like it MUST be able to do these two things.  How??

---

### Post by darkmediator on 2007-01-10
@Tonren what @wieman has posted is the solution!
Network-manager tries to find out the wireless network interfaces not listed in "/etc/network/interfaces". If u follow the solution u'll realise ur query has been solved! As for 2 minutes of time being wasted, that happens in windows too. It tries to connect to configured wireless devices!
Now network-manager stores ur "wireless device password" in keyring manager! If u do not want it to bug every time for keyring password when u login, then u need to install pam_keyring! I dunno much about pam_keyring, but the solution for pam_keyring has been posted in here/ubuntuforums only!

---

### Post by Tonren on 2007-01-10
@darkmediator,

There are a few issues with that solution.  First, network-manager simply will not work on my laptop.  I spent twelve hours straight trying to get it to work, and try as I might, it just cannot connect to wireless networks.  It detects them, but can't connect.  If it did work, that'd be great, because I do want wireless to be configured on boot and not on GNOME login.  

I still feel like there has to be a simple /etc/network/interfaces -based solution to this somewhere.  Maybe everyone just uses network-manager and that's why no one seems to care about this, but I couldn't get it working.

---

### Post by tturrisi on 2007-01-10
To ALWAYS check for the wired connection before any wireless intervfaces are activated put this in the interfaces file:
```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
allow-hotplug eth0
iface eth0 inet dhcp

# your wifi stuff below
```

and there's a TON of info from a terminal using:
man interfaces

---

