---
title: "Set up static IP address(Ubuntu 7.10)"
date: 2007-11-25
forum: Networking &amp; Wireless
---

### Post by OziX on 2007-11-25
How do I set up a static IP address? I've found a lot of guides and how-to's on this topic but I don't understand half of what they say. So, can someone help a Ubuntu newbie to set up a  static IP address? Maybe point me to an easy-to-use tutorial?

I'm using a wired router and the reason why I need a static IP is that I want to forward some ports for uTorrent.

---

### Post by kevdog on 2007-11-25
Are you using a wired or wireless connection?

---

### Post by OziX on 2007-11-25
> **kevdog said:**
> Are you using a wired or wireless connection?

wired

---

### Post by kevdog on 2007-11-25
Assuming your wired interface name is eth0 this is what you can do:

sudo ifconfig eth0 down
sudo ifconfig eth0 *IP_address* netmask *netmask* up
sudo route add default gw *gateway_address*


Values in italics you need to provide.

---

### Post by OziX on 2007-11-25
> **kevdog said:**
> Assuming your wired interface name is eth0 this is what you can do:

sudo ifconfig eth0 down
sudo ifconfig eth0 *IP_address* netmask *netmask* up
sudo route add default gw *gateway_address*


Values in italics you need to provide.

See, what I meant when I wrote "...I don't understand half..." in my original post was that I am a newbie when it comes to Ubuntu and networking. I'm sure what you're saying would solve my problem, but I don't understand it very well.

Where do I get all this information about IP address, netmask etc? How do I know if my wired interface name is eth0?

---

### Post by stroyan on 2007-11-25
Actually, those ifconfig and route commands will only set up a temporary configuration that won't remain when you reboot.  You can set a static IP address and related values using the "System->Administration->Network" menu item, or with "sudo network-admin".  That will change settings in the /etc/network/interface file that will be used when rebooting.

You need to find an IP address that fits in with the way your wired network is configured.  If you are using a typical home router then it has a range of addresses that it hands out using the DHCP mechanism.  You should find out more about your router and see what address range it is handing out for DHCP and what addresses are available for you to configure as static IP addresses.  The netmask and DNS server addresses can be the same as your router is setting up for its DHCP clients.  Look at what ifconfig reports for your systems settings with DHCP.  (The DNS server is set in /etc/resolv.conf.  It should be fine to leave it the way the it was set up when using DHCP.)

---

### Post by kevdog on 2007-11-25
Type ifconfig at command line (or lshw -C network)

Likely an eth0 interface name will be shown.

As far as setting a static IP address -- are you using a router and your computer is inside a LAN??
What is the IP address of the router?

---

### Post by IronClouds on 2008-02-01
> **kevdog said:**
> Type ifconfig at command line (or lshw -C network)

Likely an eth0 interface name will be shown.

As far as setting a static IP address -- are you using a router and your computer is inside a LAN??
What is the IP address of the router?

The IP of **my** router is 192.168.0.1. How do I find out what address range it is handing out for DHCP? I am using the D-Link DI-524 and am on a wired cable connection. Roaming mode is enabled on eth0, which I'm currently connected to.

I don't know if I'm asking the right questions or providing the right information, either. I know a bit about forwarding ports (in Windows), which is what I'm ultimately trying to do. I just need to set up a static IP.

I, too am a **complete** Linux newb. So please dumb it down a bit. I do know that those commands are to be entered in Terminal, though. Like I said, I ultimately want to forward certain ports for use in BitTorrent clients. **ANY** help in this matter would be greatly appreciated. Thanks in advance!

---

### Post by kevdog on 2008-02-01
So it sounds like you want to port forward certain ports from your router to your computer -- meaning 3 things

#1) your computer needs a static IP address
#2) you need to adjust the computer firewall to allow certain incoming ports
#3) on the router you need to port forward certain ports to your static IP

How are you connecting now?  Do you use network manager?
A simple guide you might want to read to accomplish #1 would be located here:
[http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)
(you might not need the wpa part)

#2) Adjust incoming ports using firestarter (good for beginners with Ubuntu) or Guarddog (KDE - proabably better than Firestarter however need kde installed) or modify iptables manually (really complex)

#3) Need to do on your router -- should be self-explanatory.

---

