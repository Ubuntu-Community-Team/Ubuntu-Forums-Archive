---
title: "hot to set static IP?"
date: 2007-08-14
forum: Networking &amp; Wireless
---

### Post by gokul_ifs on 2007-08-14
I am trying to set a statis IP for my linux machine and connect to my office net work.


In the /etc/network/interfatces file the following changes is done

[COLOR="blue"]auto eth0
iface eth0 inet static
address 10.66.176.51
netmask 225.225.225.0
gateway 10.66.176.1[/COLOR]


I have reserven this IP in the network.

Also have updated the name in /etc/hosts and /etc/hostname files.
when i do a networking restart is displays....

[COLOR="Blue"]* Configuring network interfaces.....[/COLOR]

But not able to connect to the network.

---

### Post by lloyd_b on 2007-08-14
First off - are you sure about that netmask?  225.225.225.0 does not look right - I suspect it should be 255.255.255.0.  Running with that netmask *could* be the cause of your problem...

Other than that - could you post the result of running the "ifconfig" command in a terminal window?  This will show exactly what that interface is being configured to...

Lloyd B.

---

### Post by Moezzie on 2007-08-14
try System > Administration > Network, click the network connection you wish to use and hit the propertiees button.

Here you should be able to change your settings in order to user a static ip-adress.

---

