---
title: "Wired connection problem"
date: 2008-07-17
forum: Networking &amp; Wireless
---

### Post by tech_cheetah on 2008-07-17
I have a DSL broadband wired connection. The problem is that internet is up only when I start ubuntu with my modem ON. In case the electricity goes off and comes back then internet connection doesn't get up ( I try these commands - "sudo ifup eth0" and "sudo dhclient") The only solution is to restart ubuntu. I have tried wicd and ifplugd, but both didn't help.
Please help me !!
I have great expectations from Ubuntu community.

---

### Post by tech_cheetah on 2008-07-18
Anybody there to help ??

---

### Post by ibutho on 2008-07-18
You could try
```
sudo /etc/init.d/network-manager restart
```
or
```
sudo /etc/init.d/networking restart
```

---

### Post by tech_cheetah on 2008-07-18
I have tried this and it is not working. Also following commands do no good :
> sudo dhclient -r
> sudo dhclient

---

### Post by tech_cheetah on 2008-07-18
This is the output of sudo dhclient

> 
Listening on LPF/eth0/00:1d:72:43:f4:cb
Sending on   LPF/eth0/00:1d:72:43:f4:cb
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by imdano on 2008-07-18
Whats the output of ```
sudo lshw -C network
```

You can probably avoid restarting by using
```
modprobe -r <driver name>
modprobe <driver name>
``` which will unload and then reload your ethernet card.  But first you need the name of your wired driver (thats what the above command is for).

---

### Post by tech_cheetah on 2008-07-19
```
  *-network               
       description: Ethernet interface
       product: 88E8039 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 14
       serial: 00:1d:72:43:f4:cb
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.20 duplex=full firmware=N/A ip=192.168.1.2 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:07:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=iwl3945 latency=0 module=iwl3945

```

Should I use iwl3945 or sky2 in place of driver ?

---

### Post by bab1 on 2008-07-19
> Listening on LPF/eth0/00:1d:72:43:f4:cb
Sending on LPF/eth0/00:1d:72:43:f4:cb
Sending on Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

This shows that the card is asking for an IP addr from DHCP server and none is responding.  See if DHCP is setup and working correctly.

---

### Post by tech_cheetah on 2008-07-19
Administration -> Network -> Connection -> Wired Connection -> DHCP
This is what is setup here.
I dont know if there is somewhere else I need to do any other settings.

---

### Post by redmk2 on 2008-07-19
It sounds like you set up the client side.  Your Ethernet card (NIC)  is asking for an IP address.  Did you set up the server?  What do you finally get as an IP address?  Try ```
ifconfig -a
```  Set the output to us.

Are you sure dhcpd is running?  Try ```
ps -ef |grep dhcpd
``` let us know here.

If dhcpd is running, what range of addresses are in the pool?

I would start [[COLOR="Magenta"]here[/COLOR]]("http://www.debianadmin.com/ubuntu-networking-for-basic-and-advanced-users.html") for a basic understanding of dhcp.

You also can use the dhcp server in the router.  The server can be anywhere on *your* network segment. 

For a small network you can configure everything with static IP addresses.  At home I have 4 computers and a HP printer.  All have been configured with static IP and hosts files for DNS.  Easy and never a problem.

I will be back here tomorrow (10 hours on).  I can help then.

---

### Post by bab1 on 2008-07-19
I could not have said it better.  Redmk2, you read my mind.  Sure sounds like you only have half of the DHCP solution set up.  I wonder if this 
[[COLOR="Red"]http://ubuntugasuki.blogspot.com/2007/08/ip-address-is-169254-even-though-its.html[/COLOR]]("http://ubuntugasuki.blogspot.com/2007/08/ip-address-is-169254-even-though-its.html") 

is what is happening?

---

### Post by tech_cheetah on 2008-07-19
Thank you guys. It is finally working with the following sequence of commands, and i don't have to reboot my laptop anymore :

```

sudo modprobe -r sky2
sudo modprobe sky2
sudo /etc/init.d/networking restart

```

But is there way I can avoid all this manual work ?? Maybe through some software !!

dhcpd is not running on my system.

---

### Post by imdano on 2008-07-19
If the rest of you folks read his first post carefully, he says that normally DHCP works fine, but if the modem turns off and then on for any reason, he can't connect again until he reboots his computer.  Which sounds like a driver issue (and it turns out it is).  tech_cheetah, I would say the best thing to do is to automate those commands with a script.
```

#!/usr/bin/sh
modprobe -r sky2
modprobe sky2
/etc/init.d/networking restart
```Make sure you run the script with sudo, and also do a chmod +x <script name> so that its executable.

I've been kicking around with the idea of adding support for doing this kind of thing in wicd, but its not there yet.  To my knowledge NetworkManager won't do it either.  It kind of risky to completely unload someone's driver through a GUI app, where the user might not realize exactly what's going on.

---

