---
title: "dhcp problem"
date: 2006-10-18
forum: Networking &amp; Wireless
---

### Post by hwdoyle on 2006-10-18
Hello,
I've recently installed ubuntu on a machine to share an internet connection at home. 

eth0 = internet card, assigned via dhcp
eth1 = local net card, statically assigned 10.5.0.1

I am running dhcpd to assign ip addresses to computers on the local network. I have a little script that runs once the network interfaces come up to clear iptables and set up the internet sharing. 

My problem is that something is causing eth1 to get a dhcp address every so often, even though i set the ip manually in /etc/network/interfaces. This breaks my setup, as dhcpd pushes 10.5.0.1 as the router option, so eth1 must have static ip or else the client computers have no network. 

This means i have to go to the console and issue /etc/init.d/networking restart for all to be well again. 

I recently installed firestarter to mess around with, and even though i have turned it off, i suspect it might be doing something weird. 

I can't figure out what is causing eth1 to take a dhcp ip, even though i have instructed it in interfaces not to do so.

Can anybody shed some light on this? 
thanks!
Harry

---

### Post by Endwin on 2006-10-18
Did you set a default interface fot the DHCP server to listen on? **/etc/default/dhcp3-server** change the interface to your internal network. That could be part of it.

---

### Post by hwdoyle on 2006-10-18
i have it set correctly in the defaults directory, however for some reason eth1 keeps giving itself a dhcp address after a few hours even though i explicitly tell it to have a static ip in /etc/network/interfaces. what would override my setting?

it usually happens after a few hours of issuing /etc/init.d/networking restart.
harry

---

### Post by Iowan on 2006-10-18
I wonder if **dhclient** is overreaching it's authority.  I briefly looked at some of the other settings in **/etc/dhcp3/dhclient.conf** and noticed a section on **lease** and **alias** that may need investigation.

---

### Post by hwdoyle on 2006-10-18
the only lines i have uncommented in dhclient.conf are:

request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, domain-name-servers, host-name,
        netbios-name-servers, netbios-scope;


and in /var/log/messages, i see this periodically:

Oct 18 08:25:15 router dhcpd: DHCPREQUEST for 10.5.0.62 from 00:90:27:17:fa:ff via eth1
Oct 18 08:25:15 router dhcpd: DHCPACK on 10.5.0.62 to 00:90:27:17:fa:ff via eth1

above is the mac address of eth1. 

i had this same setup working fine and then i reinstalled ubuntu (changed video cards and it broke X). 

i have installed firestarter, but its status is stopped and iptables --list shows that my current custom firewall script is in place. 

and in /etc/network/interfaces i have: 


auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
        address         10.5.0.1
        netmask         255.255.255.0
        network         10.5.0.0
        broadcast       10.5.0.255

thanks for the replies,
harry

---

### Post by hwdoyle on 2006-10-18
the only lines i have uncommented in dhclient.conf are:

request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, domain-name-servers, host-name,
        netbios-name-servers, netbios-scope;


and in /var/log/messages, i see this periodically:

Oct 18 08:25:15 router dhcpd: DHCPREQUEST for 10.5.0.62 from 00:90:27:17:fa:ff via eth1
Oct 18 08:25:15 router dhcpd: DHCPACK on 10.5.0.62 to 00:90:27:17:fa:ff via eth1

above is the mac address of eth1. 

i had this same setup working fine and then i reinstalled ubuntu (changed video cards and it broke X). 

i have installed firestarter, but its status is stopped and iptables --list shows that my current custom firewall script is in place. 

and in /etc/network/interfaces i have: 


auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
        address         10.5.0.1
        netmask         255.255.255.0
        network         10.5.0.0
        broadcast       10.5.0.255

i checked in x11 in the network tools and they seem to reflect the stuff i've set in the console, so i'm stumped!

thanks for the replies,
harry

---

