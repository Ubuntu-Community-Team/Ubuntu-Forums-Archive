---
title: "br0 and Network Manager"
date: 2008-11-14
forum: Networking &amp; Wireless
---

### Post by bkraptor on 2008-11-14
I'm running several VMs with VirtualBox. I'm also on the road a lot, changing IPs, sometimes static, others by DHCP.

What I want is to have eth0 permanently added to br0, then have Network Manager control br0 (static, DHCP on the fly etc) just as it controlleed eth0 before, while completely ignoring eth0.

Now my understanding is that adding interfaces to /etc/networking/interfaces makes Network Manager ignore them, so that would solve the eth0 being ignored part.

How do I make Network Manager manage br0, while still having br0 in /etc/network/interfaces (for eth0 to be bound to it)?

---

### Post by nixscripter on 2008-11-14
Adding interfaces to **/etc/network/interfaces** tells Linux how to manage them.

If you want something to be used by network manager, put in: ```
auto br0
```

If you want something to be ignored, put in: ```
manual eth0
``` and then whatever configuration you want to stick.

More information about this file can be found in the man pages (online version [here]("http://www.annodex.net/cgi-bin/man/man2html?interfaces")).

---

### Post by bkraptor on 2008-11-14
Thanks for the quick answer. Sadly however this doesn't seem to work with Network Manager in Intrepid - I have no knowledge of whether this used to work in the past. In no way can I pursuade it to apply settings to the bridge interface br0. Also the setting "manual eth0" has no influence on whether Network Manager actually operates that interface or not.

I'm looking forward to more information on this. Thanks

---

### Post by nixscripter on 2008-11-15
I might have not been specific enough. Try something closer to this:

[http://ubuntuforums.org/showthread.php?t=881885](http://ubuntuforums.org/showthread.php?t=881885)

---

### Post by bkraptor on 2008-11-16
Thanks for the new link, but sadly that still does not fix the problem I am having.

Quoting from the link you gave me:
> Also, when you are working with bridges, the bridges network devices should have NO ip configuration and be in promisc mode.
That, as far as I know, is false. Ethernet interfaces added to the bridge need to be in promiscuous mode with no IP address, while an IP needs to be assigned to the bridge interface for the host system to have IP connectivity.

I have already figured out how to make Network Manager ignore my eth0 interface. However what I want it to do is to recognize the bridge interface as a properly working ethernet interface and manage it as it would for a normal eth interface (assign manual IP address, obtain IP address from DHCP server etc). At the moment Network Manager ignores a valid bridge interface, complaining that there are no ethernet interfaces.

---

### Post by Rocket2DMn on 2008-11-17
I posted on bodhi.zazen's Intrusion Detection tutorial about setting it up in a VM, which included setting up a bridge - [http://ubuntuforums.org/showthread.php?p=5787017#post5787017](http://ubuntuforums.org/showthread.php?p=5787017#post5787017)

Basically everything you need is on the vbox community docs page - [uhelp]community/VirtualBox#Networking[/uhelp]
KVM's page also has some - [uhelp]community/KVM#Creating a network bridge on the host[/uhelp]

Right now I just run a script on startup manually, but it can also be set to run automatically.
Here is my BridgeUp script for static IP, with personal information removed:
```
#!/bin/bash
sudo tunctl -t tap1 -u <username>
sudo chown root.vboxusers /dev/net/tun
sudo chmod g+rw /dev/net/tun
sudo brctl addbr br0
sudo ifconfig eth0 0.0.0.0 promisc
sudo brctl addif br0 eth0
sudo ifconfig br0 192.168.1.201 netmask 255.255.255.0
sudo route add default gw 192.168.1.1 br0
sudo brctl addif br0 tap1
sudo ifconfig tap1 up
# extra needed
sudo chmod 0666 /dev/net/tun
```
I hope that at least helps you move in the right direction.

---

### Post by bkraptor on 2008-11-18
Thank you for the links, but I think you are misunderstanding the problem I am having.

I'm already aware of how to manually set up everything needed for VirtualBox host neworking (as you can see [here](http://ubuntuforums.org/showpost.php?p=6175437&postcount=137)). What I don't like about this method is that I need to manually edit the script every time I change locations, which happens very often. I would like to have my eth0 permanently added to br0 and have Network Manager manage the bridge interface (br0). Currently Network Manager doesn't see br0 as a valid ethernet interface.

---

### Post by Rocket2DMn on 2008-11-18
The br0 interface/bridge should be able to take a DHCP address without extra configuration.  Then if you want to set it up with a static IP address, you need to edit the config file (I have done both on my home network).  I am not sure that Network Manager is complex enough to switch between the two options on a bridged device.  If you can get br0 to show up in Network Manager as an ethernet device (which *you* currently can't), then you should theoretically be able to do so.  I am not in front of an Ubuntu machine at the moment to test this out, though.

Instead of using Network Manager, you could modify your script (or make a new one) to take in parameters to easily switch between DHCP and static IP.  You can even have it read static IP details out of a config file, which would be easier to change on the fly than the script itself.  Alternatively, have it prompt you for the details.

---

### Post by bkraptor on 2008-11-19
Thank you for the ideas.

I currently like the new Network Manager a lot so instead of editing scripts and config files (which I'm used to doing a lot), I tried to give it a chance. I am stil looking for a way to make NM work with bridge interfaces.

---

### Post by tomcatacec on 2008-11-28
I met the same problem.

---

