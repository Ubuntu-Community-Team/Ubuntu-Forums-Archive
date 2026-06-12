---
title: "[SOLVED] Restarting USB Wireless Connection / Service"
date: 2008-05-19
forum: Networking &amp; Wireless
---

### Post by jethin on 2008-05-19
Hi,

I'm connecting to the 'Net using an external Belkin USB Wireless adapter. It usually works on boot, but sometimes the Network Manager (or nm-applet or some other daemon -- newbie alert) loses it's connection for no apparent reason. I can click on other hotspots using the nm-applet gui, but the light on the device itself doesn't flash, leading me to believe that some larger service on my machine has been effected.

So, I'm basically trying to figure out how I can reconnect/refresh (or connect to another wi-fi hotspot) upon losing an open wireless connection without having to reboot my machine.

BTW, I found a long thread [[http://readlist.com/lists/lists.ubuntu.com/ubuntu-users/12/62561.html]("http://readlist.com/lists/lists.ubuntu.com/ubuntu-users/12/62561.html")] that recommended trying these two commands which didn't work for me:

/etc/dbus-1/event.d/25NetworkManager restart
/etc/init.d/dbus restart

This issue also seems to have been mentioned here:
[http://brainstorm.ubuntu.com/idea/1185/](http://brainstorm.ubuntu.com/idea/1185/)

Thanks, Jeremy

---

### Post by james_vanb on 2008-05-19
Sorry to say I don't have a solution for you, however had same problem in Xubuntu Gutsy.  Ended up manually configuring and giving up on the NM.  Hasn't been a problem in Ubuntu Hardy.  If you don't need to roam, consider manual config.

---

### Post by jtrindle on 2008-05-19
Absolutely consider manual config.

Also consider WICD.  Unfortunately, it's not in the regular repositories.  There are instructions on sourceforge:

[http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)

Installing this package will remove network-manager.

for your restart question, you might try 

sudo /etc/init.d/networking restart

but that doesn't always work.  Since it's USB you could unplug the actual device, wait a few seconds, and plug it back in to see if that lets you reconnect.

---

### Post by jethin on 2008-05-22
Thanks for the suggestions. I installed Wicd, which works OK, but it's doing the same thing Network Manager was: Whenever I lose a network connection -- or try to disconnect or open a new connection -- my USB device disappears. I'm pretty sure this is a system thing as even the wireless option disappears from the System -> Networking gui. So, can anyone tell me what I might do to keep my system from removing my USB device completely whenever it loses a connection?

Is it possible this is a permissions problem (ie Wicd can disconnect but can't reconnect because it isn't root and this causes my wireless USB device to be removed?) I'm guessing here, but I'd sure like to fix this behavior. Thanks, Jeremy

---

### Post by jethin on 2008-05-27
I just wanted to add an update to this thread in case anyone stumbles across it. I've discovered that the bugs I'm experiencing may be with the way Ubuntu interacts with my wireless device: a Belkin F5D7050 3000 series USB adapter. I've found this tutorial which I'm going to try to implement:

[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_(Ralink_rt73_driver](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_(Ralink_rt73_driver))

The funny thing about all this is that my adapter works about 75% out of the box. It's just that when it goes down it's difficult to get it going again, and there's little info about exactly what is causing it to misbehave. In any case, I'll keep y'all posted on any progress.

---

### Post by jethin on 2008-07-16
Just wanted to close out this thread. The tutorial I listed above did get my device working pretty well, and as per jtrindle I now use manual config to control my USB Wi-Fi connection. Mostly it works fine, though it would be nice to have an app/gui that would make it easy to discover/change hotspots. I also have to re-do the install part of the tutorial anytime I update my kernel.

FWIW, WICD didn't work well for me. Good luck!

---

