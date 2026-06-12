---
title: "Ubuntu 12.04 Loses Static IP and resets to DHCP"
date: 2015-03-23
forum: Networking &amp; Wireless
---

### Post by rgilman on 2015-03-23
Hello all,

First my apologies if this has been posted, I did a search and didn't see it so I'm posting it as a new question.

For some reason, my eth0 connection keeps losing it's static network config for a DHCP configuration. It happens once a day, usually around 6:00 PM in the evenings during the weekdays and earlier in the day during the weekends. I've checked the network logs and I see nothing that is weird. I've copied the output from my interfaces file below. As you can see the DHCP line is commented out and I have the static configuration there. I can resolve the issue by simply restarting the network or the system, it will always come back correctly. 

It's almost like something is issuing a temporary configuration using a CL config. Any help would be greatly appreciated. If you need more information let me know.

# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface
auto eth0
#iface eth0 inet dhcp
iface eth0 inet static
     address xxx.xxx.xxx.xxx
     netmask xxx.xxx.xxx.xxx
     network xxx.xxx.xxx.xxx
     broadcast xxx.xxx.xxx.xxx
     gateway xxx.xxx.xxx.xxx

Thanks in advance for any assistance.

---

### Post by papibe on 2015-03-23
Hi  rgilman. Welcome to the forum ):P

Is this a server or a desktop? If it is a desktop, network-manager supersede the management of the network. Revert the that file as it was and set the static IP using 'Network Connections'.

If this is a server, make sure the DHCP client is not running:
```
ps aux | grep dhclient
```
If it is, that would be the reason why it is loosing its address at a certain time. Reboot your server, and you should be OK.

Hope it helps. Let us know how that goes, and if you have more questions.

Come here often, and have fun!
Regards.

---

