---
title: "Broke my wifi - IPW2200"
date: 2005-11-02
forum: Networking &amp; Wireless
---

### Post by BlueNoteMKVI on 2005-11-02
So this is my second wifi thread of the day, for my second laptop.

I installed Kubuntu on my Centrino laptop, and everything worked fine.  Now I've managed to break it and I can't figure out how to get it back.

The ideal goal would be:
-When the laptop is at home, it assumes a static IP address on my home network
-When I go elsewhere (coffee shop, school, whatever) it uses DHCP to get an IP address

In a perfect world, I would have to do very little (or nothing at all) to make this happen - it would simply go through the list of preferred networks in order.  This may be a bit much to ask.  At the moment, I would settle for just DHCP everywhere.

When I boot my computer, I have no connection.  If I run:
```
sudo dhclient eth1
```
...then I have a connection, no problem.

In the KDE "Network Settings" panel I have eth1 set to automatic dhcp, activate when the computer starts.  I still have to manually run dhclient to get a connection.  What gives?

---

### Post by BlueNoteMKVI on 2005-11-02
so it turns out the problem was not my wifi setting at all...but somehow the eth0 (wired NIC) line got screwed up.  I fixed that line to read:

```
iface eth0 inet dhcp
```

Now everything is cool.

---

