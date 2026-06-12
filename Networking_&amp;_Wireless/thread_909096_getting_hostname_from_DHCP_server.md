---
title: "getting hostname from DHCP server"
date: 2008-09-03
forum: Networking &amp; Wireless
---

### Post by anigel on 2008-09-03
Hi,

I am trying to configure a fresh 8.04.1 install (x86) for deploying on a quite large network (180 workstations), in replacement of a customized gentoo.

One of my first problems is the following : I couldn't manage to get hostname from DHCP server.

I installed dhcpcd, and tried the same configuration that gentoo, but -H option seems to be ignored. Setting options in /etc/default/dhcpcd does not work anymore. This option should change my default hostname (ubuntu) in a more meaning hostname that make sense for my network, and then used by a large number of personal scripts to help me manage the network.

Any idea ?

Thanks,

---

### Post by Iowan on 2008-09-03
If the new box is the DHCP server, check under **/etc/dhcp3**. Otherwise, **/etc/dhcp3/dhclient.conf** has a default to get hostname from DHCP server.

---

### Post by anigel on 2008-09-04
Hi,

The box is not the server : it is just one of the dozens of workstations ;).

I saw the options in the dhclient.conf file, but it is just not working... Same problem with the dhcpcd client.

Ubuntu seems just to ignore these configuration directives ?

---

### Post by Iowan on 2008-09-04
IIRC, there was another similar thread about getting hostname from DHCP server. 
 [Found it!]("http://ubuntuforums.org/showthread.php?t=885642") Unfortunately, it seems to have gone unsolved.

---

### Post by anigel on 2008-09-10
Well, I did not have enough time to wait : solved using another distro...

---

