---
title: "Network Manager Will Not Connect to VPN"
date: 2015-07-20
forum: Networking &amp; Wireless
---

### Post by tristan16 on 2015-07-20
Somewhere along the lines, I messed something up with the Network Manager. I can no longer connect to VPN. I can create a configuration, but when I select it from the drop down menu, nothing happens. No connecting icon, no error message, and no VPN connection. I've tried purging and reinstalling the Network Manager and the OpenVPN packages, but no success. I've even tried on a different connection, but it still doesn't do anything.

Any help is greatly appreciated. What information is required to help me fix this? I'm not sure if this is related, but here's what happened:

I had an ethernet connection and tried to set up the VPN to autoconnect. It would only connect when I manually clicked on the wired connection, and on the lock screen, it would ask me for a VPN password, then set up a default keyring. Later, I abandoned the auto-connect VPN because it caused my media server to not be visible on startup, and I reset (deleted) what I thought was the default keyring (user.keyring). Everything worked fine.

When I moved my desktop and set up a wireless connection, it said error 3, the connection couldn't be made, and I could only connect if I added it manually. I purged and reinstalled network-manager and network-manager-gnome, and it was able to connect to the WiFi automatically from the drop-down menu. Now I am having this problem with the VPN, but I'm not sure if it's related since I purged and reinstalled the network manager and OpenVPN packages.

---

### Post by tristan16 on 2015-07-20
Well that was awkward. I just tried it again, and it worked just like normal. I didn't reboot, reinstall, or anything.

---

### Post by tristan16 on 2015-07-21
Ok, re-opening this thread because the problem is back. Everything was working fine, I turned my computer off last night, and now when I turned it on again today, it has the exact same problem. I'm able to connect to the VPN if I connect on the login screen and unlock the "Default Keyring," but I'd like to be able to manage this while I'm logged in.

---

### Post by tristan16 on 2015-07-21
Looks like the problem is related to my Wi-Fi card. I have the exact same errors (connection could not be created) after a clean install. This is a problem for a new (and less panicky) thread.

---

