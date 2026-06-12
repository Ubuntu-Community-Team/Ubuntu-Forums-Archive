---
title: "problems with renewing ip address"
date: 2006-12-21
forum: Networking &amp; Wireless
---

### Post by Elisei on 2006-12-21
Hello;

i am using dapper and i am having a bit of a problem with i guess ip address: it is dynamic and can only be assigned to my wireless interface once; once the lease time expires, so does the ip address and dhclient cannot find another available 'dhcp offer'; after that in order to reconnect to the internet the whole machine must be rebooted.; i am connecting through a router wirelessly and have even maxed out a lease time(on router): it is now set to 288,000 seconds;

I also run apache2(without websites :-? ) and some of the .conf files were modified to obtains static ip: and it worked fine when suddenly it stopped:

the only file that i realy have modiied is /etc/network/interfaces:
iface lo inet loopback
        address 127.0.0.1
        netmask 255.255.255.255
        network 127.0.1.0
        broadcast 127.0.1.255
        gateway 127.0.1.1

iface eth0 inet static
        address 192.168.1.111
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1

iface wlan0 inet static
wireless-essid Zorine
        address 192.168.1.102
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1

auto wlan0

Can someone suggest what could be causing it?

Thanks;

---

### Post by kidders on 2006-12-21
Hi there,

According to your config file, your wireless interface shouldn't be using DHCP at all, since you've manually assigned it 192.168.1.102.

---

