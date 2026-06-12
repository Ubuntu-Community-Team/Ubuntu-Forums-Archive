---
title: "Network Connection Messed after Playing with Firewalls"
date: 2007-08-04
forum: Networking &amp; Wireless
---

### Post by nuttycc on 2007-08-04
I installed Ubuntu Feisty 64 bit the other day (it's not the latest version perhaps, but it shouldn't matter here) and all was going swimmingly.

However, I wanted to set up a firewall... so i did > sudo apt-get install guarddog

this confused me, so i tried

> sudo apt-get install gnome-lokkit

After setting the configuration in this, **my internet connection continued to work fine**

Later on I restarted, and nothing happened. I tried removing them both, flushing iptables and restarting to no avail. I have no idea what to do <_< the rest of the computers on my network are fine.

---

### Post by smileypaul on 2007-08-04
hey man,
  
run   ifconfig    make sure you get a valid ip, and if you, make sure you can ping the router (default gateway) .. thats the first step you should be looking at for trouble shooting.

you can also just simply restart networking (no need to shut down )

sudo /etc/init.d/networking restart

---

### Post by nuttycc on 2007-08-05
ifconfig - yeah it finds it to be 192.168.0.21 which is correct

PING 192.168.0.1 (192.168.0.1) 56 (84) bytes of data.
ping: sendmsg: Operation not permitted
...

sudo /etc/init.d/networking restart

 * Reconfiguring network devices
There i already a pid file /var/run/dhclient.eth0.pid with pid 5292
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
...

Listening on LPF/eth0/00:15:f2:f2:11:b4
Sending on LPF/eth0/00:15:f2:f2:11:b4
Sending on Socket/fallback
DHCPRELEASE on eth0 to 192.168.0.1 port 97
send_packet: Operation not permitted
There is already a pid file /var/run/dhclient.eth0.pid with pid 6847448

etc. :mad:

It connects to the network fine, but nothing seems to work. Firefox won't work, I can't connect with Xming on my windows machine and apt-get can't download stuff.

---

### Post by nuttycc on 2007-08-06
bump... :(

---

### Post by ytsen on 2007-09-10
I have the same trouble!

  After playing with the encryption of my sitecom router and fiddeling with some config files (not sure exactly what changed!!). 

  Note that it worked, at least cabled, I have Feisty Fawn Kubunty (ubuntu 2.6.20-15.27).

  My situation:

  * I can get a valid IP both over the wireless and the cabled device
  * I cannot ping the router  (though I was able to ping the router ONCE but only from another shell than the one in which I was fiddling but I could not reproduce that behaviour afterward).
  * When trying to ping the router (or anything), I get the  "sendmsg: Operation not permitted" warning, just as mentioned above in this thread.

   * I am logged in as root, outside addresses can't be pinged.

  * Doing manually  "/etc/init.d/networking stop" I get the message as above: 

send_packet: Operation not permitted 

      and when I do "start" I get this:


root@ubuntu:/home/ytsen# /etc/init.d/networking start
 * Configuring network interfaces...                                                                                                                              Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:16:6f:af:1d:0f
Sending on   LPF/eth0/00:16:6f:af:1d:0f
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPOFFER from 192.168.0.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.0.1
bound to 192.168.0.100 -- renewal in 422487 seconds.
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:16:d3:45:98:5b
Sending on   LPF/eth1/00:16:d3:45:98:5b
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPOFFER from 192.168.0.1
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPACK from 192.168.0.1
bound to 192.168.0.101 -- renewal in 367755 seconds.
RTNETLINK answers: No such device
run-parts: /etc/network/if-up.d/avahi-autoipd exited with return code 2
                                                                             

  This didn' get away after blacklisting the drivers below, seemed to get worse actually, but then my system came down due to no more space left on device (running on usb stick).

 prism2_pci
 prism2_cs
 prism2
 hostap_pci
 hostap
 hermes
 p80211

  But I didn't check which drivers are actually used, puppy uses ipw2200 successfully. There I have no trouble at all, so I'm sure it's something in feisty.

  *  The problem persisted after removing the avara directory.

  *  Switched off IPv6 system wide as described in the trouble shooter.

  So you see I tried a LOT, but I give up for now.

  This the only thread I could find that has the same problem. I hope though that someone posts a follow up, I will when I solve this (later for sure).

  Cheers,

Ytsen.

PS. In the routing table the loopback device is not present. But it is in Puppy.  I'm not sure if this is a problem, anyone?

---

