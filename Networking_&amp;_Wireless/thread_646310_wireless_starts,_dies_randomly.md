---
title: "wireless starts, dies randomly"
date: 2007-12-21
forum: Networking &amp; Wireless
---

### Post by DrIdiot on 2007-12-21
I can connect fine to wireless networks, but sometimes, usually when I am torrenting or doing something else that takes up a lot of bandwidth, my wireless will suddenly die.  I will no longer see any wireless networks.  Restarting dbus and networking do not fix the problem.  The only way I can fix the problem is to restart the computer.

What should I do to troubleshoot this problem?

Thanks.

---

### Post by fb314 on 2007-12-21
what is your driver ?

find it with lshw, then unload/reload the dedicated module. For me (I have the same problem), I've written the script /usr/local/bin/wifi-restart:
modprobe -r iwl4965; modprobe -a iwl4965

---

### Post by Rony_b on 2007-12-21
I have the same problem, but i didn't understand part of the solution
 it would help if you`ll elaborate : 
what is lshw? 
and where can i reload the driver ?

thanks

---

### Post by Rony_b on 2007-12-21
okay, i figured out the first part ( easy enough ) - but i still need some instructions about the way to reload the driver

---

### Post by DrIdiot on 2007-12-21
thanks, ill try it next time my wireless crashes.

the command to remove a module is:
modprobe -r <module>

to add is:
modprobe -a <module>

you have to determine what your module is.  to do that type in sudo lshw | grep wireless (if you use wireless)

for example, i get:
harrison@abelian:~$ sudo lshw | grep wireless
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ipw3945 driverversion=1.2.2mp.ubuntu1 firmware=14.2 1:0 () ip=192.168.2.83 latency=0 link=yes module=ipw3945 multicast=yes wireless=IEEE 802.11b


so my driver is ipw3945

---

