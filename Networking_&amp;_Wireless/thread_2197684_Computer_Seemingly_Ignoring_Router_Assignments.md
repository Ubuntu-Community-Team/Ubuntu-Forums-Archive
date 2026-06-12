---
title: "Computer Seemingly Ignoring Router Assignments"
date: 2014-01-05
forum: Networking &amp; Wireless
---

### Post by Michael_Kolonay on 2014-01-05
I recently moved into a new house and thus have begun the process of setting up a new home network.  At the moment I am working on assigning static ips to a few machines to make connections smoother and also allow for some slightly more advanced port forwarding projects.  I have a d-link DIR-605L router, and for starters I am attempting to assign an address to an old iMac of my girlfriends I recently converted to a Linux box in hopes of using it as a make-shift server.  Since this machine will be fixed I am tempted to simply use the interfaces file to assign a truly static ip, but next I will be assigning addresses to some laptops, so I want to make sure I can use the router's DCHP reservation feature.  I have successfully employed a similar tactic at my parents house to assign my laptop an address whenever I enter the house, so I figured the task would be easy, but the network is behaving strangely.

The DCHP reservation works by assigning ip addresses based on mac address, so I found the necessary information in the routers DCHP Client list and cross checked it with the results of ifconfig on the iMac.  The section of the router's configuration is straightforward asking for only computer name (I stuck with the name that appeared in the DCHP client list), mac address, and the chosen ip address.  As stated in the comments, the ip address has to be within the DHCP IP Address Range, so I chose .170, a number at the upper end of the .199 range.

Unfortunately, when the router is reset in order for the changes to occur, nothing happens.  All the devices are disconnected momentarily, but when service is restored new ips are assigned by the DCHP server to every device including the iMac which was just given a reserved address (this is to say in this case the iMac ended up with .103).  I have tried removing power to the router and disabling the networking on the iMac, but nothing seems to make the router assign the reserved address.

I apologize I do not have the output of any troubleshooting, but I honestly do not know where to begin...

---

### Post by TheFu on 2014-01-05
For reserved static IPs, definitely DO NOT use the DHCP dynamic IP range. Always use a different range for static IPs.

Rebooting the router is only half the reset needed. You must restart the networking on each client computer too. Under Ubuntu server that is with 
**sudo service networking restart**
I haven't a clue how to do it under "desktops", sorry.  A reboot would certainly accomplish it on a desktop.

To be much more help we need facts concerning the router settings and all the settings from each client machine. [http://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking](http://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking) might help.  Real IPs, real netmasks, real MACs.

---

### Post by SeijiSensei on 2014-01-05
I wouldn't bother with the router at all if you are setting up a server.  Just define the interface in /etc/network/interfaces and, as TheFu says, choose an IP address outside the range the router provides.  The server will communicate just fine with the rest of the network.  

You can specify DNS information in the [interfaces file]("https://help.ubuntu.com/12.04/serverguide/network-configuration.html#name-resolution") like this:

```

iface eth0 inet static
    address 192.168.3.3
    netmask 255.255.255.0
    gateway 192.168.3.1
    dns-search example.com
    dns-nameservers 192.168.3.45 192.168.8.10

```

---

### Post by Michael_Kolonay on 2014-01-05
Thank you both for your replies.  I understand that conventional wisdom says do not assign static IPs within the range of the DHCP, but the router demands addresses within the range in order to utilize the DHCP reservation function.  As stated I am happy to use the interfaces file to define the network connection of the desktop seeing as it will be stationary, but I will want to define sudo-static IPs for the laptops while they are at home while leaving them open to DHCP while on other networks.  

I would try your suggestions as far as making sure I am actually restarting networking at all levels, but I have hit a new snag with the iMac regarding keyboard functionality in grub that I will be posting in the appropriate subset of the forum.

---

### Post by Iowan on 2014-01-05
The online manual for that DIR-605L confirms the somewhat  nonstandard reservation technique. I presume you saved the settings.
After you reboot the router, does it retain the reserved address settings?

---

### Post by Michael_Kolonay on 2014-01-05
I am going to call this one solved.  **sudo service networking restart** was all it took to cause the settings go into effect.  Dumb mistake.  Thank you all for the help though.

---

