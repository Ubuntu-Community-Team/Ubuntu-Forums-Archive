---
title: "Where is iptables config file"
date: 2007-09-11
forum: Networking &amp; Wireless
---

### Post by satimis on 2007-09-11
Hi folks,


Ubuntu 7.04 server amd64

Where is iptables config file?

satimis@ubuntu:~$ sudo find / -name iptables.conf
satimis@ubuntu:~$ sudo find / -name iptables-rules
both w/o printout

satimis@ubuntu:~$ which iptables
/sbin/iptables


TIA


satimis

---

### Post by nowshining on 2007-09-11
are you trying to config the firewall if so I really suggest arno-iptables-firewall it will give you the options in the firewall.conf file as well as  a custom.conf file to config your own rules - put them in there and restart the firewall..

then in terminal

 sudo /etc/arno-iptables-firewall restart

the commands that will work after firewall and where restart are

Stop 
Start
and of course Restart

:)

the firewall is in the synaptic package manger repos

:)

to configure the firewall open up a terminal

gksudo nautilus

input password

/etc/arno-iptables-firewall folder

and open each up with a text editor suck as gedit - double click and configure away..when done do the restart firewall above..

to the whole answer to ur question - I believe you need an external script to do so and that's what the firewall I mentioned above does.

---

