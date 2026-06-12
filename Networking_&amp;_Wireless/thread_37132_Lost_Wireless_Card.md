---
title: "Lost Wireless Card"
date: 2005-05-26
forum: Networking &amp; Wireless
---

### Post by Beernut on 2005-05-26
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

---

### Post by poofyhairguy on 2005-05-26
Yeah, that WLAN-NG driver got me the other day. Same exact problem. I had to reinstall.

I think the root of it is is that it doesn't use the normal wireless tools.

---

### Post by Alexander Kirillov on 2005-05-26
[QUOTE=Beernut]I screwed up my wireless card it's a Netgear MA401.  I installed Kismet last night and the WLAN-NG driver with apt-get but that was as far as I got so I didn't configure anything beyond that.  The card was working OK now today when I booted the card doesn't work.  When I click on the network monitor icon I get the Following error.

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

       auto eth1[/QUOTE]
 What do you get if you manually type
sudo ifup wlan0

I had a similar problem with ndiswrapper; they were solved by having ndiswrapper module loaded at every boot, by adding it to /etc/modules

---

### Post by Beernut on 2005-05-26
Thanks for the replies I really don't want to reinstall.  I didn't get anything trying ifup wlan0 but when entering sudo ifup eth1 i get the following errors.

sudo ifup eth1
Error for wireless request "Set Mode" (8B06) :
    SET failed on device eth1 ; No such device.
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device eth1 ; No such device.
Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
sit0: unknown hardware address type 776
Bind socket to interface: No such device
Failed to bring up eth1.

I guess I'll try loading ndiswrapper on boot I tried turing it on in a terminal but just got errors.  I have another laptop a much older Dell running the same card hwo do I tell what driver that is running?

---

### Post by beefbowl on 2005-08-21
i must bump this thread as i too seem to have ran into this problem, after installing the wlan_ng from the synapic package manager ubuntu dosnt seem to register my card, well i use a linksys WPC11 V3 which uses the PRISM2 chipset, i know it works with the Orinoco drivers supplied with Ubuntu in a fresh install but not everything likes the orinoco drivers. But that at least worked, wlan_ng just stopped it from even reconizing the card. any help?

---

### Post by Psquared on 2005-10-06
Same issue here after distro-upgrade to Breezy. Networking under Sytem sees only my ethernet card and my modem. The wireless card does not show up. When I boot back into the older kernel it shows up fine.

Something in Breezy no doubt.

---

### Post by TimelessRogue on 2005-10-21
Well, it seems nothing has changed with this particular problem.  In my case, I upgraded from Hoary (in which my Linksys WPC11 Ver.3 worked just fine with no tweaking) to the pre-release of Breezy.   Wireless worked fine from the get-go in Breezy ... until I upgraded to the final release ... with the new 2.6.12 kernel.  Guess what!  No more wireless.  And I, too, get the message:

Please contact your system administrator to resolve the following problem:

SIOCGIFFLAGS error: No such device

Out of curiosity, I reinstalled the pre-release version of Breezy and lo and behold!  Wireless was back up and running!  Now I'm back to the latest version and things are back to where they were with no wireless.

So what's up with that?  I'm not going to "retrograde" ... and neither should we have to ... so what's the answer, guys?  Anyone have any ideas?

---

### Post by Psquared on 2005-10-22
OK --- here's a solution that seems to be working. At least it worked for me.

If its not there, create a file called /etc/modprobe.d/ipw2200. Either way, insert the following into the file:

options ipw2200 hwcrypto=0

Save the file and then do this:

modprobe -r ipw2200
modprobe ipw2200 hwcrypto=0

I have no idea what these does, but my intel pro wireless card suddenly started working for me. It did flake out after a reboot, but it was because I had a file in /etc/modprobe.d called ipw2200.save. Once I deleted that file wireless started back up and has survived several reboots. I purposely left it on all last night and it was still connected this morning.

Good luck!!

---

