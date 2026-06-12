---
title: "Can't set Network alias IP addresses from the command line"
date: 2017-09-11
forum: Networking &amp; Wireless
---

### Post by mike4ubuntu on 2017-09-11
I don't know how to set alias IP addresses from the command line.  At one time, you could define alias IP addresses in /etc/network/interfaces and then use ifconfig to to start/stop them.  Apparently, you can't do that anymore in 16.04 and later when the Network Manager is running.  How, do you do it now from the command line.  I can set them from the GUI by going into the Network Manager config and adding the alias addresses there, but there  does seem to be a way to do it from the command line.  Anybody know how to do it from command line.

---

### Post by mike4ubuntu on 2017-09-11
I found a couple of utilities that actually do seem to control Network Manager configurations from the command line.  Apparently, you can use either "nmcli" or "ip" commands.  However, the changes don't seem permanent.  I suppose I could create a systemd startup service that could set this after every reboot.  Is that the best way?

> 
If you need an additional IP address just for the moment you can add it to any interface on your machine with

 sudo ip address add <ip-address>/<netmask> dev <interface>

for instance

 sudo ip address add 172.16.100.17/24 dev eth0

would add 172.16.100.17 using a 24bit netmask to the list of addresses configured for your eth0.

You can check the result with

ip address show eth0

and you can delete this address again with

sudo ip address del 172.16.100.17/24 dev eth0

Of course these changes are lost when you reboot your machine.


---

