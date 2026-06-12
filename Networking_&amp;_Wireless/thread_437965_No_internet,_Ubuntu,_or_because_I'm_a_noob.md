---
title: "No internet, Ubuntu, or because I'm a noob?"
date: 2007-05-09
forum: Networking &amp; Wireless
---

### Post by afterburner on 2007-05-09
Hi all, I have a problem with my USB D-Link DWL-G122 A2 wireless adapter.

Here is the story. 

I have a wireless D-Link router that's connected to my internet provider's box. From this wireless router, I have a cable going to one of my desktops, and I have the D-Link G122 A2 USB adapter in another room, to receive the wireless signal there, for my fresh Ubuntu 7.04 install. 

The computer that's connected to the internet by cable  has working internet, and is running WinXP. Here is the story with the other computer...

After the fresh install, the USB adapter is detected by Ubuntu, since the lights on the adapter are lit up, and I can see the wireless networks that are available - my 'default' network, and my neighbors wireless. When I click on my network, it briefly connects (a message pops up), and then a few seconds later disconnects (another message). 

In my Network Settings: 
I have wlan0, wmaster0, wired connection, and modem. Both the wlan0 and master are default for the example above. Default being the wlan0 (D-Link) settings are - Roaming mode, all fields are blank. wmaster0 is set to the same thing. There are minus (-) signs beside the wlan0, and wmaster0 in the network settings, but there is a blank box beside the wired connection option. 

Since I'm a noob, I don't really know how what to do, do get internet to work. I tried setting the wlan0 to automatic configuration (DHCP), still no checkmark beside the the wlan0, when I unplug and plug back in the USB adapter, and wireless network default shows up, same story says connected, then disconnects right away. If I fill in the ESSID field to 'default' or Local Area Connection 2, as it shows up on my WinXP box, then the obtion of putting a checkmark beside wlan0 shows up, and when I click on it, the wlan0 icon becomes red (Im assuming becasue thats how working internet is supposed to show), however, there are no longer any wireless networks being detected. 

In my Network Tools:
For some reason, its set to loopback interface (lo) - protocol IPv4, IPv6 -HOST ( IP Adress 127.0 etc..)
When I select wlan0, i get IPv6  and a letter and number combination for IP address.

So, can anyone help me out please?

Im not sure how to set up the wireless on Ubuntu. Mind you, I had Win2000 before, and wireless worked fine.

Previous thread.

[http://ubuntuforums.org/showthread.php?t=415984](http://ubuntuforums.org/showthread.php?t=415984)

Thanks.

---

### Post by afterburner on 2007-05-10
Bump.

---

### Post by Pfrankie on 2007-05-10
Not a reply per se, but a related question... I'm new to Ubuntu 7.04 myself (although not to *nix)

Is there a webpage out there for *nix noobs for configuring the "wireless connection"? What did you use?

---

### Post by Buffalo Soldier on 2007-05-10
Have you tried the guide here --> [https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)

what's the content of your /etc/network/interfaces file?
```
sudo gedit /etc/network/interfaces
```

If it is not managing your network connections you'll need to comment out the references to all interfaces (except lo) in /etc/network/interfaces to let Network Manager handle them.

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
# auto eth1

# iface eth1 inet dhcp
```

---

### Post by afterburner on 2007-05-10
sudo gedit /etc/network.interfaces

auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth1 inet dhcp

auto ath0
iface ath0 inet dhcp


iface eth0 inet dhcp
auto eth0

---

### Post by Pfrankie on 2007-05-10
Try the fix from my post in this thread:

[http://ubuntuforums.org/showthread.php?t=425910&page=2](http://ubuntuforums.org/showthread.php?t=425910&page=2)

If this doesn't work BuffaloSoldier's fix should also work. Also, his linked guide is useful.

---

