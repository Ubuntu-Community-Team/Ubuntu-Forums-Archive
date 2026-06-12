---
title: "Wireless help required for non-newbie!"
date: 2006-12-05
forum: Networking &amp; Wireless
---

### Post by maggot_brain on 2006-12-05
Hello everyone,

I've been using Ubuntu and previously Debian for about five years now so I'm now novice, but I am having serious problems with my USB wireless card.  I'm using the latest stable distribution, 6.10.

My wireless cards is a Buffalo WLI-U2-KG54-2A and is USB.  Apparently it is based on the Ralink rt2xx0 chipset.  The windows drive is actualy rt2500usb.sys so this would seem to support that assertion.  All the computers on the wireless network have static IP addresses.

On the default install I have a device rausb0.  The kernel does display a message about it using old proc/net/wireless support. I couldn't get it to work at all.  I therefore decided to compile a new kernel.  I did so and included that new ralink wireless drivers.

When I booted the new kernel, I instead had a new device wlan0.  I decided to disable encryption on the router and see if I could get any connectivity.  I typed the following into the /etc/network/interfaces file:

iface wlan0 inet static
address 192.168.11.2
netmask 255.255.255.0
gateway 192.168.11.1
wireless-essid 'My ESSID'
auto wlan0

I then restarted networking.  When I try to ping the router's ip address (192.168.11.1) I just get host unreachable.  The iwlist -scan command does correctly detect my router though.  Does anyone know anything else I can do as I'm stumped.  I just want connectivity first.  I'll tackle encryption later.  Iwconfig does seem to be able to change channels etc ok as well.

Any tips would be most appreciated.

Ananda

---

