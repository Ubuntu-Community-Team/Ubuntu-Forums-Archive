---
title: "[SOLVED] How can I re-install the default Networking files?"
date: 2008-07-20
forum: Networking &amp; Wireless
---

### Post by Grandma_DOG on 2008-07-20
I seem to have a wounded system. Something is very wrong with the networking settings/configuration.  I've tried to solve it for weeks. I've posted requests for suggestions of what tools I need to use to diagnose this cause.

See one thread here:
[http://ubuntuforums.org/showthread.php?t=859445](http://ubuntuforums.org/showthread.php?t=859445)

The WIRED network connection now runs at 300 Baud (Yes, like the old 300 baud modem) on up to about 1/2 dialup speed.

I have set the NIC to Full Duplex 100, the DHCP is running. I'm using OpenDNS now, but still get slow connection.    There is the really weird fact that when I http to my router at 192.168.0.1 it takes several minutes to load a page that should be instantaneous on a local LAN.  So something in the system is buggered.  Sendmail may be a culprit. I've uninstalled the damn thing, but when I restart the network, it keeps trying to connect to sendmail and fails.  I can't seem to purge the system of that damn thing.

Now I just want to know how to purge/re-install all the networking packages.  Which ones, and how to do it when I'm going to kill my network.

---

### Post by Grandma_DOG on 2008-07-20
Made a new discovery.  I did a dmesg | grep eth0 and saw hundreds of 'corrupted packet recieved' messages.  That would explain why I get 25% packet loss when simply pinging.  Duplex communication would have much higher failure rate.

Anybody want to venture a guess on this one?  NIC is SIS900 chipset.

---

### Post by Grandma_DOG on 2008-07-23
I've solved the problem, finally, after 2 months.  And just in time, as I received no help or advice in restoring orignal networking files.

Culprit - 30 meter run of cat5 cable & a 100 Full duplex card that didn't seem to autonegotiate to a cleaner 10 FD speed.  It was able to get 100MB/s at a cost of 25% packet loss which rendered my effective speed to almost a 1200 Baud modem.  Once i set the speed to 10MB/s all the problems went away. When I switched back to 100MB/s they returned. Case closed.

---

