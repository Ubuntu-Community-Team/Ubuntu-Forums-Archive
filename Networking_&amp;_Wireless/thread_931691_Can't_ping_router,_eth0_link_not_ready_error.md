---
title: "Can't ping router, eth0: link not ready error"
date: 2008-09-27
forum: Networking &amp; Wireless
---

### Post by sredhar on 2008-09-27
Guys,

I am installing 8.04 on a dell poweredge 2600 server and i am having network problems. At first i tried dhcp, but that didn't work and now i am trying static ip. That's not working either.

in the dmesg log i see this error. 

dmesg | grep -i eth0
[92.541636]     e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[3516.715934]   ADDRCONF (NETDEV_UP): eth0: link not ready.

I guess for some reason my ethernet card is not working. I am a little lost on what to do next. 

i tried unload the module and load it again with lsmod but that didn't work either.

This is the output of lshw


lshw -C Network
*-network
Decription: Ethernet interface
prodcut: 82544GC Gigabit Ethernet COntroller (LOM)
logical name: th0
configuration: broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI firmware=N/A ip =192.168.15.4 latency=64 mingnt=255 module=e1000
multicast=yes


Also in dmesg i get the ADDRCONF_NETDEV_UP): eth0: link not ready error.


Also, iwlist eth0 scan gives a "Interface doesn't support scanning" error. 

I connected the server to a dlink router and i can't see the server as connected in the router GUI. I made sure the cable works by connecting it to another computer and that works.

Also i am not able to ping the router which is 192.168.15.1. I guess that is because the eth0 link is not working. I am lost on what to do next.

Also i searched around for ADDRCONF error but the people who have this error have multiple interfaces and i have only one interface.

Routing table has the following 

Destination        Gateway           Genmask        Flags      Metric    Ref    Use     Iface
192.168.15.0       0.0.0.0           255.255.255.0   U         0         0        0     eth0
0.0.0.0            192.168.15.1      0.0.0.0         UG        100 0     0        0     eth0


Any help would be greatly appreciated.


Thank you.

---

### Post by sredhar on 2008-09-27
Guys,

This is the last time you guys will be seeing me. After this i will log off the internet permanently and commit seppuku.

Here was the problem.

I am trying to install hardy on a poweredge 2600 server and this is my first time installing on a server. Apparently there are two network interfaces for the server. One is for Remote Access Controller which is used to access the server for remote system management. I didn't take a good look at the back and just plugged the Ethernet cable in to the interface i saw. That was the interface for RAC and not the server itself. There is another interface which was below the video interface and i couldn't see it at first. I was able to ping the RAC ip address and then it striked me if there was another interface and yes there was. As soon i changed the cable everything worked like a charm. :)

---

### Post by Iowan on 2008-09-27
Sounds more like a time for celebration than suicide - unless the disappointment of success is too much to tolerate... ):P

---

