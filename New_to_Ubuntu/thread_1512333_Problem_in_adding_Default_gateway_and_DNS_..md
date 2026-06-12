---
title: "Problem in adding Default gateway and DNS ."
date: 2010-06-18
forum: New to Ubuntu
---

### Post by honey_bee on 2010-06-18
Well  in linux  system I want to add IP address along with Default Gateway and DNS.
For assigning IP to eth0 i use the command

**# ifconfig etho 192.168.1.10 subnet mask 255.255.255.0 up**this remain temporary and when I restart my system it lost the IP address .Well to permanently add IP address in etho I use the file

**#cd /etc/sysconfig/network-scripts and then use # vi ifcg-eth0 to add IP address and Network Mask.**
How can I add Default Gateway and DNS permanently in ifcg-eth0 file or there is any other file for it ?

thanks
honey

---

### Post by jtarin on 2010-06-18
Are you using a router?

edit ```
/etc/dhcp3/dhclient.conf
``` 
You will see a line for your DNS setting
Of course you want to enter your own DNS resolvers here.Note the comma separating the two number and the semi-colon ending.
```
prepend domain-name-servers 20x.6x.2xx.2xx,2xx.6x.2xx.2xx;
```

Then go to /etc/resolv.conf and edit that file thusly...or your can reboot and it should overwrite what is in there.
The last one is my router....it's not usually necessary to put that in their but .....
```
nameserver 20x.6x.2xx.2xx
nameserver 20x.6x.2xx.2xx
nameserver 19x.1xx.x.x
```


If you scroll down just a little further you will see your setup for assigning your IP and gateway.

---

### Post by honey_bee on 2010-06-18
thanks for your reply. well I  have three computers in my lab for testing purpose .All three are connected with a small 4 ports switch. the configuration of each computer is 

Computer A Linux
IP address 192.168.1.10
Subnet Mask 255.255.255.0
Default Gateway 192.168.1.1

Computer B Linux
IP address 192.168.1.20
Subnet Mask 255.255.255.0


Computer C Windows xp
IP address 192.168.1.30
Subnet Mask 255.255.255.0


In my Linux system I want to add Default Gateway. For that purpose I open # vi /etc/sysconfig/network
and add gateway as following

NETWORKING=yes
HOSTNAME=router
GATEWAY=192.168.1.1

I save the file and restart the network services. from another computer fedora and windows xp i can ping the computer but when i try to ping the default gateway it say " Destination Host Unreachable/Resquest time out "

Please guide me that how can I fix this issue ? is there any mistake u thing that why Default Gateway not not responding from computer B and C?

---

### Post by jtarin on 2010-06-18
From your 2 Linux computers post the results of the command ```
route -n
```
From your XP post the results of the command ```
route print
```

---

