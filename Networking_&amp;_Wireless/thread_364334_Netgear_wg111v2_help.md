---
title: "Netgear wg111v2 help?"
date: 2007-02-18
forum: Networking &amp; Wireless
---

### Post by thegreenblob on 2007-02-18
Ok, my friend installed ubuntu yesterday and he has a netgear wg111v2 and tried following [this]("http://www.ubuntugeek.com/how-to-install-netgear-wg111v2-wireless-dongle-card-on-ubuntu-edgy.html") guide on how to get it to work but... he keeps getting > Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ndiswrapper-utils-1.8

When using ```
sudo apt-get install ndiswrapper-utils-1.8
```

That command. So... any help?

---

### Post by teaker1s on 2007-02-18
because it's not connected to internet or not all repositories  enabled

---

### Post by thegreenblob on 2007-02-18
Ok... So... he rebooted and apparently it works now. But theres another problem. He got the wireless dongle turned on and the machine reconizes it but when he does

```
sudo dhclient wlan0
```

He gets the normal thing except with this at the end instead.

> No DHCPOFFERS received.
No working leases in persistent database - sleeping.

And then the wireless still don't work... So any more help...?

---

### Post by teaker1s on 2007-02-19
not sure specifically but I have helped many people setup wireless easily by installing
[COLOR="Red"]network-manager-gnome[/COLOR]


 now on your desktop panel you want to click system administration networking

it's important to make sure that devices show un-configured so network-manager-gnome can control them. Shutdown and remove Ethernet cable, boot and you should now left click network applet next to volume icon select your network and put in Passphrase or network key

---

### Post by phossal on 2007-02-23
> **thegreenblob said:**
> Ok, my friend installed ubuntu yesterday and he has a netgear wg111v2 and tried following [**this**]("http://www.ubuntugeek.com/how-to-install-netgear-wg111v2-wireless-dongle-card-on-ubuntu-edgy.html") guide on how to get it to work but...

Of course, that's just *my* guide stolen without credit. If he's not getting a dhcp offer, either the modules that are blacklisted are preempting the ndiswrapper drivers, the ndiswrapper that's installed is the wrong one, or WEP/WPA is set (and it shouldn't even be *on* while trying to establish an initial connect) incorrectly.

---

