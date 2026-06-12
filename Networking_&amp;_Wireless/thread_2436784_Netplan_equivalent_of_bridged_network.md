---
title: "Netplan equivalent of bridged network"
date: 2020-02-13
forum: Networking &amp; Wireless
---

### Post by weactivist on 2020-02-13
Sorry beforehand but I can't figure out what the netplan equivalent of this is. Any help would be appreciated.

[HTML]auto br0iface br0 inet dhcp
  bridge_ports DEVICENAME tap0

auto tap0
iface tap0 inet dhcp
   pre-up tunctl -u MYUSERNAME -t tap0[/HTML]

---

### Post by TheFu on 2020-02-13
*tap* interfaces are really slow.  Perhaps you'd rather use a *tun* or *bridge* interface?  
Sorry, I can't directly help with the 18.04 aspect of the question.  **netplan.io** is the official reference for that subsystem.
[https://netplan.io/examples](https://netplan.io/examples) has examples.

[https://ubuntu.com/blog/ubuntu-bionic-netplan](https://ubuntu.com/blog/ubuntu-bionic-netplan) has a developer view.

*pre-up* stuff has been moved into the *systemd target-wants and depends* system. It isn't available in the network subsystem anymore.  Every startup service has dependencies specified in their config file. The goal of this is so Y won't be started until X is started and running.  A quick analysis of those dependencies by systemd allows parallel startup for the required reverse-tree of services to get to the point that "networking" is up, before "multiuser" is up.  Fairly simple text files are used.

Take a look at /lib/systemd/system/networking.service file. See the After, Before, WantedBy entries?  Any reference to a filename with .target in the name is a config file. Follow a few to see how they fit together.

---

