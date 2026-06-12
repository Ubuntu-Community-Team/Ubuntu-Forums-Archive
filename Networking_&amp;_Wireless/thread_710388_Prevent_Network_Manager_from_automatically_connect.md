---
title: "Prevent Network Manager from automatically connecting to Wireless"
date: 2008-02-28
forum: Networking &amp; Wireless
---

### Post by mocha on 2008-02-28
I have an unusual situation.  I have a wired network connection that has a static IP assigned to it though the Network Manager.  This was accomplished though /etc/network/interfaces.  The problem is that when the box is rebooted, the Network Manager always connects to some random wireless network with the nm-applet.

This appears to be happening because the wired network doesn't appear in the nm-applet anymore since it was assigned a static IP.  Is there anyway to fix this so that the wireless networks don't connect?

The solution is not to let Network Manager manage the wired network.  I don't want it that way for various reasons.

---

### Post by motin on 2008-06-28
> **mocha said:**
> I have an unusual situation.  I have a wired network connection that has a static IP assigned to it though the Network Manager.  This was accomplished though /etc/network/interfaces.  The problem is that when the box is rebooted, the Network Manager always connects to some random wireless network with the nm-applet.

This appears to be happening because the wired network doesn't appear in the nm-applet anymore since it was assigned a static IP.  Is there anyway to fix this so that the wireless networks don't connect?

The solution is not to let Network Manager manage the wired network.  I don't want it that way for various reasons.

There is a bug report related to this issue at [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/46123](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/46123)

However, the most useful comment is found in one it's duplicates' comments. Basically, it explains that in Hardy, NM will only attempt to automatically connect to the networks listed in nm-editor (right-click on the Network Manager applet -> Edit wireless networks). Then remove the networks that you do not want to automatically connect to.

---

