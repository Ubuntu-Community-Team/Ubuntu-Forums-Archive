---
title: "Card gets IP from DHCP, but networking doesn't work"
date: 2007-03-02
forum: Networking &amp; Wireless
---

### Post by brandon_r87 on 2007-03-02
Hello,

My computer is running Xubuntu Edgy and has a ipw2200.  It was working, but then after a restart it stopped.  The card can see networks fine with wifi-radar and can even get an IP address no problem using dhclient, but after that can't even ping the router.  I even changed the static DHCP to make sure that it was getting the correct IP address and it did.  I don't know what is stopping me from using the internet, or networking, at this point.

Brandon

---

### Post by Metaljaz on 2007-03-02
The ipw2200 driver should work out of the box - at least it does on edgy. Try typing these commands from the terminal window:

sudo lsmod | grep ipw2200

to see if the driver is loaded. If it doesn't show up try
Code:

sudo modprobe ipw2200


Read this thread:

[http://www.ubuntuforums.org/showthread.php?t=360735&highlight=ipw2200](http://www.ubuntuforums.org/showthread.php?t=360735&highlight=ipw2200)

---

### Post by brandon_r87 on 2007-03-02
OK, fixed it.  I had both the wired and the wireless enabled in Network Settings.  After disabling the wired, the wireless now works.  This should be the case though, should it? It should be able to use both, right?  Either way, I don't mind switching it back and forth if I really ever want to go wired.

And yes, I already had the ipw2200 module loaded but thanks anyway.

---

