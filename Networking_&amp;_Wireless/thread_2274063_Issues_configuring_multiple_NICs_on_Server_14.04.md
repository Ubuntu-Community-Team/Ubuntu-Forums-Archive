---
title: "Issues configuring multiple NICs on Server 14.04"
date: 2015-04-17
forum: Networking &amp; Wireless
---

### Post by bluefishkiller79 on 2015-04-17
Greetings All-  

I am posting this in the network section but please feel free to move it to server section if needed.

I am having issues configuring multiple interfaces (as well as virtual IP's) on Server 14.04.

I have 4 physical NICs:
eth0 eth1 eth2 eth3

I confirmed this looking in /sys/class/net and it lists:
eth0 eth1 eth2 eth3 lo

Also an ifconfig lists all the adapters and their proper hardware MAC addresses

When I installed Server 14.04 it gave me the option to configure primary interface so I chose eth0 just to start with assuming once I patch I could go back and configure the additional interfaces.

i have no issues with eth0 and networking is fine.  /etc/network/interfaces has this configured:

# The primary network interface
auto eth0
iface eth0 inet static
       address 10.110.130.240
       netmask 255.255.255.0
       network 10.110.130.0
       broadcast 10.110.130.255
       gateway 10.110.130.1
       dns-nameservers 10.110.130.20
       dns-search *******.com   (I have a real name in here)


As is I have no issues with eth0.  First I wanted to try and add a virtual IP onto this interface before configuring eth1, eth2, and eth3 so what I added to /etc/network/interfaces config file is this:

auto eth0:1
iface eth0:1 inet static
         address 10.110.130.241
         netmask 255.255.255.0
         network 10.110.130.0
         broadcast 10.110.130.255
         gateway 10.110.130.1

Saved the config and restarted the interfaces (also even rebooted as well) however I can not PING the virtual IP.  The main IP works fine still.  After beating my head on the table for an hour  I completely removed the eth0:1 settings and rebooted the server.  eth0 at this point is still working fine.  Not wanting to continue troubleshooting the virtual IP issue i moved on to trying to configure a different interface.  ***Note all NICs are on the same VLAN without any doubt***

I open /etc/network/interfaces and add this into the config (as i know that I have a real interface called eth1 with proper MAC address)

auto eth1
iface eth1 inet static
       address 10.110.130.241
       netmask 255.255.255.0
       network 10.110.130.0
       broadcast 10.110.130.255
       gateway 10.110.130.1
       dns-nameservers 10.110.130.20
       dns-search *******.com   (I have a real name in here)

I save the config and reboot the server.  The server takes FOREVER to come up.  Networking at this point is completely broken including eth0.  I edit /etc/network/interfaces and remove everything related to eth1 that I have just configured.  Save the config and reboot the server (server is in dev not Production so I don't mind a reboot everytime).  Server comes right back up with no issue and eth0 is working fine again.


I apologize for the very long post but I wanted to provide as much detail up front as possible.  I am at a complete loss right now.  I come from a Red Hat shop but now work for a company that uses Ubuntu Server (note that I have no preference to what version of Linux I use).  I really feel that I am going crazy at this point.  I could care less about the virtual IP but I do need to get the other physical NICs working.  Any help would be greatly appreciated!

Best regards,
SysAdmin going crazy over this

---

### Post by michi1983 on 2015-04-17
Hi,

please provide this script as well:
[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

I got some questions though. 
What exactly is your gateway? 
Are all your 4 NICs connected to something? (to what?l

Greetz

---

### Post by bluefishkiller79 on 2015-04-17
I have applied all updates on this server.  it is currently at 14.04.2.  Gateway is 10.110.130.1.  Server is physically connected to Cisco Nexus 7000.  It is running on an a Supermicro server with 4 physical NIC cards.  There are other physical servers (HP AIX) connected to this switch.  They are 10.110.130.200-239 and they use 10.110.130.1 as their gateway. eth0 is 10.110.130.240 using gateway 10.110.130.1 and I have 3 other IPs available for this server 241 for eth1, 242 for eth2, and 243 for eth3.  I can PING other AIX servers with no issues and they can PING my .240 address.  The link above seemed to reference wireless troubleshooting.  I am trying to configure the other interfaces on my server and that is the issue I am having as I edit the /etc/network/interfaces file.  Thank you for any help that you can provide

Thank you

---

### Post by michi1983 on 2015-04-17
The name of the script is a little misleading ;)
It gives you ALL the network info you need of your machine incl. hardware, drivers, modules etc. So pls be so kind and provide it anyways ;)

What happens when you set eth1 up with your provided details but leave the last two lines out regarding the DNS.

What does ```
dpkg -l | grep resolvconf
``` say?

---

### Post by SeijiSensei on 2015-04-17
First, don't connect multiple adapters to the same network subnet.  It will cause all sorts of routing problems.  Use eth1-3 to connect to other networks for which this machine will act as a router, or leave them idle.

Next, try limiting the definition for eth0:1
```

auto eth0:1
iface eth0:1 inet static
address 10.110.130.241
#netmask 255.255.255.0
#network 10.110.130.0
#broadcast 10.110.130.255
#gateway 10.110.130.1

```
Because eth0:1 is just a "virtual" interface, it shares the same network, netmask, broadcast and gateway settings as eth0 itself.  Restart networking or reboot, then post the results of ifconfig inside [noparse]```

```[/noparse] tags.

If you have a firewall enabled on this machine, turn it off for testing purposes.

---

### Post by bluefishkiller79 on 2015-04-17
Indeed I did have some serious routing issues going on!  All IP's are properly working now and the other physical NICs have been setup on different networks with working IP's as well.  I cant' thank you all enough for your quick responses and excellent knowledge.  Thank you both for your help!

---

