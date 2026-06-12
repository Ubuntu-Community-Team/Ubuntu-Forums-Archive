---
title: "Networking with Ubuntu LAMP server"
date: 2007-04-25
forum: Networking &amp; Wireless
---

### Post by trippynet on 2007-04-25
Hello,

I've installed Ubuntu 6.06 LAMP server onto a spare machine at work to do some basic web development on, only I'm having a few troubles with getting the network up and running on it.

I think that the main problem is that the gateway is on a different subnet to the IP address (I didn't set up this network). The settings are:

IP address: 192.168.180.85
Subnet Mask: 255.255.255.0
Gateway: 192.168.176.4

These settings work fine on Windows based machines, but when editing the /etc/network/interfaces file with these details, I'm only able to ping other machines on the same subnet. I also get an "SIOCADDRT: Network is unreachable" error when trying to re-start the network services after saving the config file.

Does anyone know how I'd need to configure the /etc/network/interfaces file so that the machine can find the gateway and hence access machines on other subnets.

Many thanks,

Dave.

---

### Post by trippynet on 2007-04-26
No suggestions then? :(

---

### Post by Wicca on 2007-04-26
The reason for this is, as you mentioned, that your gateway is on a different subnet. Every subnet should have its own gateway so traffic not meant for the local net can be forwarded.

I do not know the specific reason for this setup, but some questions popup in my mind:

Is your server the only machine in the 192.168.180.x subnet?
If no: Why isn't there a gateway for the 192.168.180.x subnet?
If yes: Why did you create a subnet for just 1 machine?

Why can't your server get an address in the 192.168.176.x subnet?

---

