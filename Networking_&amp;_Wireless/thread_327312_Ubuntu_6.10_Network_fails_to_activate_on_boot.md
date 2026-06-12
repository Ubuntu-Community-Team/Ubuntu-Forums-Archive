---
title: "Ubuntu 6.10 Network fails to activate on boot"
date: 2006-12-29
forum: Networking &amp; Wireless
---

### Post by KB8GT on 2006-12-29
System is dual boot Windows XP Home and Ubuntu 6.10.  

Network fails to activate on a Ubuntu  boot after  a 'Shut Down'.   However. when Windows is booted first the Network in Ubuntu works great from a Windows 'Restart'.    The network in Ubuntu remains active during  'Restarts' from Ubunto.  In fact, one can go back and forth between Windows and Ubunu using 'restarts', and have an active network.   However, once shut down and a direct boot to Ubuntu the network is a no go.

The readout from sudo dhclient results in a failure ping to the router after a direct Ubuntu boot.   I have also tried sudo /etc/init.d/ networking restart after a direct Ubuntu boot.   The network in not established.

A Ubuntu boot from a Windows 'restart' using sudo dhclient  indicates that the IP address for the Ubuntu is 'bound' to the address given  Windows.  

The network card is wire and set for DHCP.   Two other computers one,  Unbutu 6.01 only,   and a Windows Laptop have working networks via the same router.

Looking for a way for a direct boot to Ubuntu 6.10,  without going first to Windows,  and force the activation of the network.

Thank You 
Larry

---

