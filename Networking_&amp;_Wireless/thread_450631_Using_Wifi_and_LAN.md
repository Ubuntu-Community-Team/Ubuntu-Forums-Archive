---
title: "Using Wifi and LAN"
date: 2007-05-21
forum: Networking &amp; Wireless
---

### Post by swatF1RESTORM on 2007-05-21
I'm trying to get my laptop setup to use at work. I still want to be able to use wifi at home but the LAN at the office. I tried setting up 2 different locations via network-manager but I am still unable to access via the LAN.

It makes sense to me to think that I should be able to set my wifi up at wlan(x) and the LAN as eth(x) but I'm not sure how to do that. Is the easiest way to 'man ifconfig' and see how to modify the interfaces or is there a different way to go?  I've tried using [this]("http://ubuntuguide.org/wiki/Ubuntu:Feisty/Networking") guide to get this setup but I am unable to 'disable wireless roaming' in feisty. On the Connections tab in Network Settings I select 'Wireless connection' and click 'Properties'. I uncheck the box that says 'Enable roaming mode' and hit ok but as soon as I go back into the properties the check box is enabled again.

Should I try to manually edit the /etc/network/interfaces? If so what do I need to put there to have wlan(x) and eth(x) set up for wireless and wired respectively?

swatF1RESTORM

---

### Post by swatF1RESTORM on 2007-05-21
I copied my results from:

ifconfig
hosts
hostname

[here]("http://www.pastebin.ca/500957"). (<--link)

In case that's of any use in diagnosing my problem

---

### Post by Darkhack on 2007-05-21
Most of the time wlan0 will be wireless and eth0 will be a line but not always.  I know some Atheros cards use ath0.  My wireless card comes up as eth1 but works perfectly.  I'm pointing this out so you don't end up confusing the devices or panic when one doesn't come up.

I assume you have the wireless working?  You seemed to imply that you only had troubles with the LAN.  Most likely your office uses something called DHCP which is Dynamic Host Configuration Protocol and it makes life a lot simplier by helping to automatically get the proper information needed to connect.

Ignore NetworkManager for now as it doesn't always work and open up a command line and type *sudo nano /etc/network/interfaces*.  Don't touch the wlan0 setting but look for eth0 or add it if it isn't listed.  Edit it so it looks like this...
> auto eth0
iface eth0 inet dhcp
gateway 192.168.1.1

I'm not 100% sure if you need the gateway (router's IP address) but it won't hurt to put it in there.  Ctrl-S to save and Ctrl-X to exit from Nano.  Now you can use ifconfig.  It should work by simply doing... *sudo ifconfig eth0 up*

If your LAN is not on DHCP then you will need to configure it manually.  Ask the network guy at your office for the necessary information.

---

### Post by swatF1RESTORM on 2007-05-21
Thanks for the response! 

I AM up on wireless and judging from the packet count on ifconfig eth1 is my wireless, although that 's just my guess. I'm not sure why my wireless is set up eth1 but I would like to have the wireless be wlan0 and the LAN be on the eth(1 or 0) interface. I have all the information to manually setup for the LAN i'm just not sure how to get it entered.

---

### Post by Darkhack on 2007-05-21
There is no easy way to change the device names from eth to wlan.  I think it has to do with how the driver is written.  I would just ignore it.  Okay, so your LAN is setup manually instead of dynamically with DHCP.  Go back to the interfaces file with *sudo nano /etc/network/interfaces* and then alter the eth0 section to look like this...

> auto eth0
iface eth0 inet static
essid NetworkName
address 192.168.1.100
netmask 255.255.255.255
broadcast 192.168.1.255 
network 192.168.1.0
gateway 192.168.1.1 


Just replace those values with the ones that are appropiate for your LAN.  After saving the file, to restart the eth0 device, do...

> sudo ifconfig eth0 down
sudo ifconfig eth0 up

---

