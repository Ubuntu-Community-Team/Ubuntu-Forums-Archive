---
title: "Ubuntu 18.04 server networking issues"
date: 2020-05-29
forum: Networking &amp; Wireless
---

### Post by squidee on 2020-05-29
I recently started using a new network switch and I'm pretty sure it reset all my network configs on Ubuntu. I've spent days trying to fix this but all the forums are referring to ifupdown not netplan. Is the best way to go around this just to backup everything and put it on a new OS? I know it's Ubuntu not the computer because in the BIOS and before start-up the LED on the switch lights up. When the OS loads it turns off. I can turn it on in the root shell (Off the top of my head I think it was something eth0 up) and the internet would boot back up but after a reset the problem would repeat.I would appreciate any help and sorry if this is a bad format, I'm new to this forum! Thanks!

---

### Post by TheFu on 2020-05-29
Please be extremely accurate with terms.  I doubt a "switch" has anything to do with changing networking on any OS.  Generally, switches are transparent on the network.  

Same for "hubs".

A "router" may provide answers to requests made by a client machine, but the client machine has to request that data first.  Common services that a router may provide are DHCP, where a client machine would request network configuration settings from the router.  IP, netmask, gateway, DNS servers.  If the router doesn't provide those, then either the computer needs to be correctly, manually, configured with that data OR another DHCP server needs to exist on the network.  Almost any Linux machine can be a DHCP server.

So, if you want help with setting up a static IP for a wired network connection, we can help with that. Just say which version of the OS and which DE you are running. If you are running a server and there isn't a GUI, I can help with that, but probably cannot help with a GUI/Desktop answer.
Ubuntu Desktop Guide: [https://help.ubuntu.com/stable/ubuntu-help/net.html.en](https://help.ubuntu.com/stable/ubuntu-help/net.html.en)
Ubuntu Server Guide: [https://ubuntu.com/server/docs/network-introduction](https://ubuntu.com/server/docs/network-introduction)

If you want help troubleshooting the DHCP problem with your network, we need accurate, correct, information. Using the wrong terms means we cannot help.

Regardless, you'll need to follow instructions and provide information back for all the questions. Partial answers will prevent correct answers.

Your choice.

---

