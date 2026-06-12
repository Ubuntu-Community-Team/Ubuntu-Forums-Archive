---
title: "Automatically run a command after connecting to a network"
date: 2008-08-13
forum: Networking &amp; Wireless
---

### Post by andrewkk on 2008-08-13
I have a script that I want to automatically run whenever I connect to my wireless network. Can this be done?

---

### Post by Iowan on 2008-08-14
I don't have the details, but the **/etc/network/if-up.d** directory looks like a place to start.

---

### Post by andrewkk on 2008-11-25
The scripts in /etc/network/if-up.d/ don't appear to be executed when I connect to a wireless network.

I think [this the answer]("http://projects.gnome.org/NetworkManager/developers/") I'm looking for: > NetworkManager provides a detailed and capable D-Bus interface on the system bus. You can use this interface to query NetworkManager about the overall state of the network and details of network devices like current IP addresses or DHCP options, and to activate and deactivate network connections.

---

