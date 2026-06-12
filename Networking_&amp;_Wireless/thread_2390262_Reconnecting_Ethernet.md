---
title: "Reconnecting Ethernet"
date: 2018-04-27
forum: Networking &amp; Wireless
---

### Post by kazakore on 2018-04-27
I run Ubuntu Studio so the core components are XFCE/Xubuntu based but hopefully this should make much difference.

Basically I'm currently trying to set up some broadcast gear and having rather a ballache! What's the issue? The units have a dedicated Management ethernet port, so I connect to it on the laptop, I can do some work on a single unit but as soon as I need to power cycle that unit, or move my connection to another unit, the ethernet connection goes and wont come back once connected again. I have to log off and back in again to get the ethernet connection back. Surely this isn't right!!

What can I do to get my ethernet connections automatically reconnecting?

Or at minimum something from the terminal to save me logging out and in to get it back up??

---

### Post by TheFu on 2018-04-27
From the description, it isn't clear how anything is connected.  Please describe.

What is managing the network and providing addresses?  A router?  A DHCP server?  Is everything setup with static IPs?
What are the network settings for each port on all the connected gear?

---

### Post by kazakore on 2018-04-27
Sorry for the rush posting.

Yes manually set static IP through XFCE's Network Manager GUI (from the Panel.) Automatically connect is checked.

Ethernet module is named enp0s25, rather than the more common eth0.

IP: 198.98.18.50
SN: 255.255.255.0
GW: 198.98.18.254

The units all have the management port set to 198.98.18.1 so until configured manually point-to-point they can't be on a management network via a switch etc as there would be an IP conflict (but that's not in the plan anyway as once set up they can be configured from the external management until via the main LAN port.)

---

### Post by TheFu on 2018-04-27
Switches aren't routers.  WIthout a router, you'd need to setup routing between the systems manually  like we do when two computers are directly connected via a single ethernet cable.

I have no idea what a "management port" is.  Is that their internal IP or an external gateway/router or the IP to some management device?

Having 2 devices on the same network with the same IP blocks both devices.

---

### Post by kazakore on 2018-04-27
As I said I am connecting directly to the item point to point! No switch. No router. No other network gear of any kind! As I said there can't be due to them having the same IP on the management port out of the factory!

A management port in a network port on which is configured a http interface for setting up of the item. It does not do any of the other usual network operation. It is usually designed for point-to-point connection to configure a new unit. This is opposed to the main LAN port through which all data usually travels (in this case on the whole asynchronous video data.)

If I physically connect the cables and THEN sign in to the laptop it works. But once I have changed settings the unit need rebooting, or I need to connect to the next unit, the connection dies. As soon as I lose connection it does not reconnect to either the same unit or to a newly connected unit with exactly the same configuration no matter what I do!

So as clearly said more than once the issue is with REconnection of the ethernet network. Why is my ethernet network, when connected point-to-point to a piece of equipment, requiring me to log out and back into Ubuntu to get the network running? Now can I get the connection re-established without logging out and in or restarting my laptop??

---

### Post by kazakore on 2018-04-27
In short:

If I remove my network cable and plug it back in why doesn't my network come back to life?

You don't really need to know the rest of the information, it's just noise!

---

### Post by TheFu on 2018-04-27
Thanks for the info. What seems clear you might not be clear to others.
 
It isn't noise.  It is necessary background, since we don't know what the real issue is at this point.  People ask questions here all the time, but it turns out to be the wrong question, especially around networking.  Coming in with ZERO background means having to ask questions to gain a little understanding before sending someone completely down the wrong direction.  "The internet doesn't work" is usually a DNS problem, not a networking issue at all. That's 1 example.

I missed "directly connected" in any of the prior posts,because it wasn't there.  It is VERY unusual for people to do that here, so I asked for clarification.  It is clearer now. Much appreciated.  We are just trying to help, after all.

Here is a guess that will fix the issue.  I'm not positive, but I am 90+% confident.  Network-manager

So, network-manager has a bad habit of requiring a userid login before it does anything. For most people, that isn't an issue, but you (and I) have different needs. Setup a static IPs using the "old school" method in the /etc/network/interfaces file.  If you are on 16.04 or earlier, this should work.  More recent versions changed things to using netplan.

There is an Ubuntu help webpage just about this - it is overly complicated because it has to deal with odd setups. Google will find it easily.  "ubuntu static ip" - [https://help.ubuntu.com/lts/serverguide/network-configuration.html](https://help.ubuntu.com/lts/serverguide/network-configuration.html)
There are 6 lines you need to put into the /etc/network/interfaces. Once a device is listed in that file, network-manager will ignore it inside the GUI.
```
auto enp0s25
iface enp0s25 inet static
  address 198.98.18.50
  gateway 198.98.18.254
  netmask 255.255.255.0
  dns-nameservers 1.1.1.1 1.0.0.1 208.67.220.220 208.67.222.222
```
Then restart networking (sudo service networking restart) and all should be fine. If that doesn't get the static IP, might need to convince network-manager to release the interface - somehow. IDK.

And if you don't need network-manager for anything else, it is 100% safe to purge the packages. I do.

Good luck.  Hopefully, someone smarter can provide a better answer if this doesn't solve it.

---

### Post by kazakore on 2018-04-27
Firstly let me say thank you for your patience and sorry for my impatience.

> **TheFu said:**
> 

I missed "directly connected" in any of the prior posts,because it wasn't there.

Actually it did. Which is part of the reason I got impatient. My second post says "The units all have the management port set to 198.98.18.1 **so until configured manually point-to-point** they can't be on a management network via a switch etc as there would be an IP conflict" which very celarly states a point-to-point connection, so the information was already there in black and white before I reiterated it.


> 
Here is a guess that will fix the issue.  I'm not positive, but I am 90+% confident.  Network-manager

So, network-manager has a bad habit of requiring a userid login before it does anything. For most people, that isn't an issue, but you (and I) have different needs. Setup a static IPs using the "old school" method in the /etc/network/interfaces file.  If you are on 16.04 or earlier, this should work.  More recent versions changed things to using netplan.

There is an Ubuntu help webpage just about this - it is overly complicated because it has to deal with odd setups. Google will find it easily.  "ubuntu static ip" - [https://help.ubuntu.com/lts/serverguide/network-configuration.html](https://help.ubuntu.com/lts/serverguide/network-configuration.html)
There are 6 lines you need to put into the /etc/network/interfaces. Once a device is listed in that file, network-manager will ignore it inside the GUI.
```
auto enp0s25
iface enp0s25 inet static
  address 198.98.18.50
  gateway 198.98.18.254
  netmask 255.255.255.0
  dns-nameservers 1.1.1.1 1.0.0.1 208.67.220.220 208.67.222.222
```
Then restart networking (sudo service networking restart) and all should be fine. If that doesn't get the static IP, might need to convince network-manager to release the interface - somehow. IDK.

And if you don't need network-manager for anything else, it is 100% safe to purge the packages. I do.

Good luck.  Hopefully, someone smarter can provide a better answer if this doesn't solve it.

This looks like it could be what I need and I'll give a play tomorrow. Currently that file contains only:
```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

```

I admit I found it a little strange that *ifquery -l* only gives the interface *lo* as a result so I couldn't even try ifdown/up to get it restarted.

I had tried restarting the NetworkManager with systemctl command as this helps on the occasions my wifi dies when changing locations on occasions (I think if my laptop is locked and I go from one SSID I have saved to another or something similar) but that didn't help. I still get confused with Services vs SystemD and systemctl etc etc and it's definitely something I could do with learning more about. Thanks for the pointers for the named service to restart and the command to do so :)

---

