---
title: "using bridge-utils to bridge from wireless to wired"
date: 2011-08-31
forum: New to Ubuntu
---

### Post by Redmage913 on 2011-08-31
Hi there,

I've got a Dell Mini 9 that I'm attempting to set up as a network bridge.  The main goal is to be able to have it constantly running while I plug my Xbox 360 and possibly other computers into a hub plugged into the LAN port of the Mini 9.

My wireless connection (eth1) is managed by Network Manager, and my wired doesn't seem to be (device not managed is listed for eth0). I set it up using a minimal install, installing the ubuntu-server package and then xubuntu-desktop.

How should I configure this?  I have some experience with the terminal, so that doesn't scare me.

Thanks,
--Red

---

### Post by Redmage913 on 2011-09-01
More information:

I have my wired (eth0) connection set up with a static IP outside of Network Manager, using /etc/network/interfaces:

IP: 192.168.0.1
Subnet: 255.255.255.0
Default Gateway: 192.168.0.1

I have no problems deleting that information, if the bridge won't be taking it into account.  Pretty much, I need help translating the bridge information in [https://help.ubuntu.com/11.04/serverguide/C/network-configuration.html](https://help.ubuntu.com/11.04/serverguide/C/network-configuration.html) to what I need: bridging from a wireless Internet connection to a wired hub.  The guide talks about using a virtual machine; I need help setting it up for a physical network.

Thanks!

---

### Post by Redmage913 on 2011-09-01
Please move this to Networking and Wireless, if one doesn't mind.

Thanks!

---

