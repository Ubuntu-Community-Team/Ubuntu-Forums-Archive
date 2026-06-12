---
title: "Issues Setting Up a Wireless Access Point on Ubuntu Server 7.4 with BCM4306 card"
date: 2007-08-12
forum: Networking &amp; Wireless
---

### Post by sneakyjoe on 2007-08-12
I am trying to configure the wireless NIC in my x86 Ubuntu Server 7.4 linux box. I had trouble getting my BCM4306 card to function at first, but followed this tutorial [http://ubuntuforums.org/showthread.php?t=185174](http://ubuntuforums.org/showthread.php?t=185174) and now the card functions properly.

My first concern with the Network Devices in my system is regard to the names of my devices - eth0, eth1, eth2, and lo. 

There are two wired cards in my system: eth0 and eth2. eth0 is the device the computer uses to connect to the world and and does function properly. The second device "eth2" is not configured in /etc/network/interfaces and does not serve any purpose as of yet. 

There is one wireless card in my system, which I am trying to configure as a wireless access point. I have spent several hours googleing and attempting various tutorials, all of which have failed, been too ambiguous, or have not met my goals. 

I've attempted to follow tutorials pointing to the use of the hostap-utils tool as this seems the right direction to head. However, the package does not work: 
```
:~# apt-get install hostap-utils
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following NEW packages will be installed:
  hostap-utils
0 upgraded, 1 newly installed, 0 to remove and 24 not upgraded.
1 not fully installed or removed.
Need to get 0B/52.0kB of archives.
After unpacking 209kB of additional disk space will be used.
Selecting previously deselected package hostap-utils.
(Reading database ... 14362 files and directories currently installed.)
Unpacking hostap-utils (from .../hostap-utils_1%3a0.4.0-1_i386.deb) ...
Setting up bcm43xx-fwcutter (006-1) ...
--16:06:54--  http://boredklink.googlepages.com/wl_apsta.o
           => `wl_apsta.o'
Resolving boredklink.googlepages.com... 72.14.203.118
Connecting to boredklink.googlepages.com|72.14.203.118|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
16:06:55 ERROR 404: Not Found.

dpkg: error processing bcm43xx-fwcutter (--configure):
 subprocess post-installation script returned error exit status 1
Setting up hostap-utils (0.4.0-1) ...
Errors were encountered while processing:
 bcm43xx-fwcutter
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

It appears the package points to a link from where it requires a file and in return gets a big fat 404 or the tutorial I used to set up the card using bcm43xx-fwcutter is not compatible with hostap.

My next concern is that the wireless device does not turn on when I start the computer. I have to input ```
ifconfig eth1 up
``` to bring the device up then using a series of ifconfig and iwconfig commands to configure it to connect to my wireless router because it will not read configuration from /etc/network/interfaces
My wired card, eth0 functions fine and does properly configure itself from /etc/network/interfaces

Finally after the previous problems have been solved, how do I set up the card to function as a wireless access point using WEP encryption? I would like the server to configure the Wireless NIC as an access point, deal with handling addresses using a DHCP daemon (or better method if it exists), use MAC address authentication, and provide access to the internet for connected users by bridging the connection between my wired nic eth0 and wireless nic eth1 or some other more effective method.

---

