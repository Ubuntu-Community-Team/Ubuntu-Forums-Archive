---
title: "Networkmanager does not bring up network until login"
date: 2008-05-21
forum: Networking &amp; Wireless
---

### Post by Silby on 2008-05-21
Hi,

Networkmanager seems to not bring up wireless networks until a user logs on. This is a small discomfort because users are stored on a remote ldap server. After (re)starting the computer a user must log on with a local account, wait for the wifi connection to automagicly connect to the preferred network (yay, thank you networkmanager), log off and then log on again with the account stored in the ldap directory.

When dropping to the console and checking nm-tool, it happily sees all the available hotspots, but the connection is inactive. 

Is there a way to force networkmanager to automaticly connect to the default hotspot before a user logs on ? Ive always disabled networkmanager, but come 8.04 i'd prefer to use it.

This happens under Hardy, clean setup, nothing done with WEP/WPA or the like yet.

Regards

---

