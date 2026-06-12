---
title: "NetworkManager only works when manually selecting"
date: 2007-02-23
forum: Networking &amp; Wireless
---

### Post by Darwin Award Winner on 2007-02-23
I have an odd problem here. I have NetworkManager all set up to connect to both my own wireless router and my school's wireless network, both of which use WPA (but different kinds). The University also provides non-encrypted wireless. The problem is, though, that when I first log in, or when I resume from hibernate/suspend, NetworkManager automatically picks a network and starts trying to connect ... and fails. It doesn't fail all the time. It is most frequently successful with the unencrypted network, and almost never successful with the University wireless. However, after I let it time out and fail to connect, if I go and select the same network from the dropdown list, it connects almost immediately. The connection *must time out* before this will work. Disabling and re-enabling does not work, switching networks back ana forth doesn't work. If it fails to connect, it will continue failing until it is allowed to time out. Then it will work normally.

Does anyone have any idea what's going on here? Or at the very least how to set the time-out period to a lower number?

---

