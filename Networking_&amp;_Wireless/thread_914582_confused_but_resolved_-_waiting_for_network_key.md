---
title: "confused but resolved - waiting for network key"
date: 2008-09-08
forum: Networking &amp; Wireless
---

### Post by bfallik on 2008-09-08
A few days ago (while trying to show a friend some photos, no less), my laptop (Intel wireless, Hardy 8.04.1) stopped connecting to my home network.  The only symptom was mousing over the networkmanager applet displayed "Waiting for network key", similar to some posts in here like [this]("http://ubuntuforums.org/showthread.php?t=896325") one.

Initially I suspected a hung router or bad RF, but neither seemed possible.  The laptop had always connected fine previously.

I searched online and suspected the problem was with network manager attempting to get the key from the keyring.  System -> Preferences -> Encryption and Keyrings showed TWO keyrings, login and default.  This seemed odd, and didn't match any other Ubuntu machine to which I had access.  I deleted the 'default' keyring (literally named 'default') and deleted and recreated my home network manually.  networkmanager connected immediately, and no 'default' keyring was created.  The key was stored in the 'login' keyring.

Why is nm looping when it can't find the key?  Shouldn't it fail fast and notify the user?

How did the 'default' keyring get created?  Which one should nm use?  It didn't seem to contain anything of value.

---

