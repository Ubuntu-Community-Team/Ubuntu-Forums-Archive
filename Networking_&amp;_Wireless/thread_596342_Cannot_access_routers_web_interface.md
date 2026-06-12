---
title: "Cannot access routers web interface"
date: 2007-10-29
forum: Networking &amp; Wireless
---

### Post by PureW on 2007-10-29
Hello, before you point it out, I have looked at several topics about this, but not found any answers.

I cannot access the routers web interface where I make all the settings for the router (ports open and so on).
What is supposed to happen when I enter 192.168.0.1 which is the router is that I'm supposed to 
get a popup asking me to enter login data.

-Im running a pretty fresh install of Ubuntu 7.04
-I have no problems with connecting to the internet. 
-I **can't** ping the router
-I connect to the router with a wire
-The same computer connects fine to the the routers web interface with Windows XP

This is my ifconfig:

```
eth0      Link encap:Ethernet  HWaddr 00:0E:0C:D0:B7:AF  
          inet addr:192.168.0.10  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:cff:fed0:b7af/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:205805 errors:0 dropped:0 overruns:0 frame:0
          TX packets:140963 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:281173494 (268.1 MB)  TX bytes:14803012 (14.1 MB)
          Base address:0xcc00 Memory:feae0000-feb00000 

eth1      Link encap:Ethernet  HWaddr 00:13:8F:81:80:30  
          inet addr:192.168.0.10  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Base address:0xe400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:57 errors:0 dropped:0 overruns:0 frame:0
          TX packets:57 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4152 (4.0 KB)  TX bytes:4152 (4.0 KB)

```

I have two networkcards but only using one of them.

---

### Post by superyounan1 on 2007-10-29
can you go online? ping anything else on the network?

---

### Post by PureW on 2007-10-30
> **superyounan1 said:**
> can you go online? ping anything else on the network?

Yes, I can go online, and I can ping for example [www.google.com](www.google.com), but I can't ping the router or my laptop which is on the same network.

---

### Post by MariusSilverwolf on 2007-10-30
Just a guess here, but your ifconfig output shows both NICs using the same internal IP address (192.168.0.10) with both connections being UP.  If you take down eth1 and try to ping/access the router again, you *should* be successful.

---

### Post by PureW on 2007-10-30
> **MariusSilverwolf said:**
> Just a guess here, but your ifconfig output shows both NICs using the same internal IP address (192.168.0.10) with both connections being UP.  If you take down eth1 and try to ping/access the router again, you *should* be successful.

How do I take eth1 down? I can't disable it through the GUI because there is no checkbox to disable it, but I read that I could comment out eth1 in /etc/netwok/interfaces
source [: http://ubuntuforums.org/showthread.php?t=165259](":http://ubuntuforums.org/showthread.php?t=165259")

---

### Post by nicean on 2007-10-30
In the terminal: `sudo /sbin/ifconfig eth1 down` or `sudo /sbin/ifconfig eth0 down` will take down one interface or the other.

If you'd like to try to get a new DHCP address (assuming your router is set up to give 'em out), `dhclient eth0` or `dhclient eth1` should get you a new lease.  Might be smart to do this on the interface that you don't take down, just to be sure you've got a sane IP address and that the routing table gets set up correctly.

Note that using ifconfig to take down an interface will only last until you bring the thing back up or you reboot the machine.

HTH.

---

### Post by PureW on 2007-10-30
Thank you guys, that's it. After disabling one of the network cards, I can ping the router and enter the routers web interface.

---

### Post by MariusSilverwolf on 2007-10-30
Always happy to help.  Glad we got it worked out. :-)

---

