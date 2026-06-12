---
title: "Prevent Network Manager from connecting to open network"
date: 2008-01-22
forum: Networking &amp; Wireless
---

### Post by LucaTNT on 2008-01-22
Hi everyone.

I own a WPA2 wireless connection, and I use it from my laptop, but everytime I turn the laptop on it automatically connects (after logging into KDE, I usa Kubuntu Gutsy) to a unencrypted network.

How can I set Knetworkmanager to connect automatically to my own network or at least not to connect to the open one?

I found many similar threads but they all regerded gnome-network-manager.


Thanks in advance.

---

### Post by motin on 2008-06-28
> **LucaTNT said:**
> Hi everyone.

I own a WPA2 wireless connection, and I use it from my laptop, but everytime I turn the laptop on it automatically connects (after logging into KDE, I usa Kubuntu Gutsy) to a unencrypted network.

How can I set Knetworkmanager to connect automatically to my own network or at least not to connect to the open one?

I found many similar threads but they all regerded gnome-network-manager.


Thanks in advance.

There is a bug report related to this issue at [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/46123](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/46123)

However, the most useful comment is found in one it's duplicates' comments. Basically, it explains that in Hardy, NM will only attempt to automatically connect to the networks listed in nm-editor (right-click on the Network Manager applet -> Edit wireless networks). Then remove the networks that you do not want to automatically connect to.

---

