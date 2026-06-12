---
title: "How to stop inerface coming up at boot time"
date: 2005-10-26
forum: Networking &amp; Wireless
---

### Post by shartrec on 2005-10-26
I have a laptop with wireless pcmcia and builtin ethernet.  I rarely use the ethernet and don't want it to start on boot, because itinterferes with the routing and ntp waits for ages.

I removed the auto entry for eth0 in my /etc/network/interfaces and if I stop all the interrfaces and run ifup -a it doesn't start, but it always starts somewhere during the boot;

_My Interfaces file_.
# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
#mapping hotplug
#       script echo
#       map wlan0

# The primary network interface

auto wlan0
allow-hoplug wlan0
iface wlan0 inet static
        address 192.168.0.3
        netmask 255.255.255.0
        broadcast 192.168.0.255
        gateway 192.168.0.253
        wireless-ap 00:09:5b:cc:74:19
        wireless-essid kelpie
        wireless-mode managed
        wireless-channel 11
        wireless-key blah:blah:blah restricted

iface eth0 inet static
        address 192.168.0.103
        netmask 255.255.255.0
        gateway 192.168.0.253

---

### Post by fabiand on 2005-10-26
Hey,

have you tried network-admin to deactivate the appropriate (ethX) device?

maybe the configuration is built from different files...

- fabiand

---

### Post by emendelson on 2005-10-26
Did you try commenting out the last four lines in your interfaces file?

---

### Post by shartrec on 2005-10-26
I did try deactivating the interface in network-admin, but that just removes the configuration from the interfaces file.  That stops it working but also means I can't bring the interface up with ifup eth0, when I do want to plug in using ethernet.  (Large movies take a very long time to transfer over wifi. :( )

The man page for interfaces says:
"Lines beginning with the word "auto" are used to identify the physical interfaces to be brought up when ifup is run with the -a option. (This option is used by the system boot scripts.)"
I don't have an auto line for eth0 so it should remain unconfigured.  I think it is just a bug in the way Ubuntu starts up,  but I can't find it.

---

### Post by mlomker on 2005-10-26
Refer to [this thread.]("http://www.ubuntuforums.org/showthread.php?t=77422")

---

### Post by shartrec on 2005-10-27
[QUOTE=mlomker]Refer to [this thread.]("http://www.ubuntuforums.org/showthread.php?t=77422")[/QUOTE]

Thanks for the link.  It was not the solution I was looking for but had links that led to the real solution.
[U]
The solution is[/U] 
Update /etc/default/hotplug, change the net agent policy NET_AGENT_POLICY=auto.  The original setting is all (which is really a bug and contradicts the interfaces file man page's implied policy).

I also installed and configured ifplugd which brings the ethernet up and down when the cable is plugged in / removed.  I also set the metric on each of my interfaces to prefer the ethernet when it is there.  (I set metric 5 for eth0 and 10 for wlan0)

---

### Post by emendelson on 2005-10-28
Hmm... In my /etc/default/hotplug, the line in question reads:

NET_AGENT_POLICY=hotplug

I use Network Manager as described here (see the "Important note" at the end of the section) and have no delays on bootup. No ifplugd installed, no other modifications other than disabling ntpdate on startup (as described elsewhere on the page).

[http://www.columbia.edu/~em36/ubuntubreezythinkpadt42.html#netmanager](http://www.columbia.edu/~em36/ubuntubreezythinkpadt42.html#netmanager)

---

### Post by mlomker on 2005-10-28
> NET_AGENT_POLICY=hotplug


That is what mine reads as well.  I wonder the OP has a machine upgraded from Hoary?  That often results in configuration files that aren't properly overwritten because they were previously customized.

---

