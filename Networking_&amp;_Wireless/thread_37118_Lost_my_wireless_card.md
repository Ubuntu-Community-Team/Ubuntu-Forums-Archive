---
title: "Lost my wireless card"
date: 2005-05-25
forum: Networking &amp; Wireless
---

### Post by Beernut on 2005-05-25
I screwed up my wireless card it's a Netgear MA401.  I installed Kismet last night and the WLAN-NG driver with apt-get but that was as far as I got so I didn't configure anything beyond that.  The card was working OK now today when I booted the card doesn't work.  When I click on the network monitor icon I get the Following error.

```
Please contact your system administrator to resolve the following problem:

SIOCGIFFLAGS error: No such device
```

Here is what I have in my interfaces file however the card doesn't show up.

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth1

# The primary network interface
    iface eth1 inet dhcp
        
# wireless-* options are implemented by the wireless-tools package
        wireless-mode managed
        wireless-essid any

       auto eth1

DUH!  I posted this in the wrong forum I am using Hoary maybe I should just turn it off for tonight I'll post this in on the Hoary Board.   ](*,)

[***Reposted here on the Hoary Board***](http://ubuntuforums.org/showthread.php?p=187284#post187284)

---

### Post by stevenyu on 2005-05-26
does** lspci **still sees the wifi NIC?

---

