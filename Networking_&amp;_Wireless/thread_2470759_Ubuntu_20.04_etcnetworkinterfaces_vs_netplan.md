---
title: "Ubuntu 20.04 /etc/network/interfaces vs netplan"
date: 2022-01-10
forum: Networking &amp; Wireless
---

### Post by tricia279 on 2022-01-10
Hi there,
I have an Ubuntu 20.04 and I need to configure a static network.
I did so at /etc/network/interfaces (see picture), BUT it did NOT work.
Normally it should work without using NETPLAN.

My questions are:
1) Why does this not work ?
    => if 'ping' nothing happens
2) Is it a MUST to use netplan ?
3) Should I remove this item, when I want to use netplan ?

I appreciate very much your help.

Regards
Tricia279

Additional informations:

Manual Network Configuration

/etc/network/interfaces

At system z600:
#Ethernet
auto ens4
iface ens4 inet static
address 10.60.0.1
network 255.255.255.0
dns-server 10.60.0.1

At system raspy-2:
#Ethernet
auto eth0
iface eth0 inet static
address 10.60.0.2
network 255.255.255.0
gateway 10.60.0.1
dns-server 10.60.0.1

---

### Post by TheFu on 2022-01-10
20.04 deprecated the interfaces file. Use netplan.  Netplan uses YAML for configuration.  There are lots of examples for a simple static IP in these forums.

Please don't post images for text files.
Please use forum 'code tags' when posting text config files. With YAML, that is critical since only 'code tags' will maintain the indentation.
Code-tags how-to: [Https://ubuntuforums.org/misc.php?do=bbcode#code](Https://ubuntuforums.org/misc.php?do=bbcode#code)

I would remove the /etc/network/interfaces file after getting netplan working, just to prevent future confusion.

---

### Post by tricia279 on 2022-01-11
Thank you for the quick answer :P

---

### Post by chili555 on 2022-01-11
Why not put your settings in Network Manager?

---

