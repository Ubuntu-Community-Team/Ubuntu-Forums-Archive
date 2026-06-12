---
title: "Ralink RT3090/Realtek RTL8101 Slow Wifi, Lubuntu 15.10 (So very confused)"
date: 2015-12-04
forum: Networking &amp; Wireless
---

### Post by lowang2 on 2015-12-04
Hello,

I'm experiencing some very slow wifi speeds on my laptop. I'm getting no more than roughly 50kbps download speeds here. 

I've installed Lubuntu 15.10 on a Lenovo Ideapad S405. 

Problem 1:
I'm trying to post my "Wireless Info Script" info here but I'm having trouble doing it. I've opened the command line terminal and typed in:
wget -N -t 5 -T 10 [https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info](https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info) && \
chmod +x wireless-info && \
./wireless-info

BUT in return I get this: wget: --tries: Invalid number '-5' 

What does this mean? 

Problem 2:
I wanted to know what kind of wireless card I have installed so I typed in: sudo lshw -C network
BUT , I ended up getting two results; 1.Ethernet interface: Realtek Semiconductor RTL8101/2/6E , Result 2; Wireless interface: Ralink corp. RT3090 Wireless 802.11n 1T/1R PCIe


I'm so confused now
What do I need to do in order to get that wireless info script for someone on this forum to diagnose my problem with my slow wifi connection ?

---

### Post by Robert_Knapp on 2015-12-04
Realtek Semiconductor RTL8101/2/6E is your hardware for wired connections. Ralink corp. RT3090 Wireless 802.11n 1T/1R PCIe is your wireless hardware.

In your wget command, did you somehow enter "-t -5" instead of "-t 5"? The error I get for that matches your error.

I have had endless troubles with RT3090, and you'll find many such stories around the 'net. The short story is that Linux has very poor support for it. I have tried the suggestions from many, many google hits -- spending about two days on it -- even trying them across different kernels: in 12.04, 14.04, and 15.10. All with no luck. The rt2800pci driver is selected for this card, and it barely works at all. At ten feet away from the router, the signal is almost gone (as confirmed by e.g. `wavemon`). I have to place the router right next to the machine in order to get a usable connection.

At one point there was a presumably good driver for it ([https://launchpad.net/~markus-tisoft/+archive/ubuntu/rt3090](https://launchpad.net/~markus-tisoft/+archive/ubuntu/rt3090)) but it has long since fallen out of date. I think the only "solution" would be to use an old kernel (going back to Ubuntu 10.04) with that driver, following something like [http://www.techytalk.info/ubuntu/ralink-wireless/](http://www.techytalk.info/ubuntu/ralink-wireless/) (there are many such guides saying basically the same thing). And I can give no assurance that that will even work.

The most practical solution would seem to be getting a wireless usb with good linux support and then blacklisting rt2800pci and friends (as shown in the second link above).

---

