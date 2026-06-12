---
title: "Change SSID of network from command line (over ssh)"
date: 2013-10-15
forum: Networking &amp; Wireless
---

### Post by Jake_Bruce on 2013-10-15
Hi there!

I am working with a robot which is running Ubuntu 12.04.2 LTS, and I connect to it only via ssh. 

It broadcasts a wireless network named "VEHICLE_03", and I need to change the SSID of its network to a specific whitelisted name (say, "LAB4000") so my university's routers will stop jamming the signal.

Just to be clear, the robot doesn't connect to an external wifi network: it broadcasts its own, and I join that network with my laptop in order to ssh into and/or control the machine.

Since I connect only over ssh, I've only got the command line to work with.
Is there a configuration file or a startup script where I should be able to change the SSID of the network that my robot produces?

Thanks!
Jake

---

### Post by papibe on 2013-10-15
Hi Jake_Bruce. Welcome to the forum ):P

A few thoughts:

There are several ways to set up a Wifi hot spot in Ubuntu, but the most common is through NetworkManager. If that the case, the main config file would be '/etc/NetworkManager/NetworkManager.conf'. After you modified it, you would need to restart the network:
```
sudo service network-manager restart
```

If there's a Desktop version (GUI) running on the machine supporting the robot, it is possible to connect using a graphic environment, just as you were login locally. The default (pre installed) option would be using 'Desktop Sharing' on the robot, and using 'Remmina Remote Desktop client' on your machine.

I hope this helps. Let us know how it goes.
Regards.

---

### Post by Jake_Bruce on 2013-10-15
After a few frustrating moments finding no configuration options anywhere on the machine, I realized that there is in fact an independent wireless router inside the chassis. Hah!
That explains why I had no luck changing things on the machine itself. I've now used the router configuration page to change the SSID, and all is well.

Thanks for the reply!
Jake

---

