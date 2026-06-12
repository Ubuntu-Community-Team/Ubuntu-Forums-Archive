---
title: "unable to access my computer by IP address since 7.10 upgrade"
date: 2007-10-19
forum: Networking &amp; Wireless
---

### Post by javajoe220 on 2007-10-19
Ever since I upgraded to 7.10 I can no longer access my machine via its IP address at port 8080

I can ping localhost, 127.0.0.1, and 192.168.0.103 with no problem  but when i attempt to access my machine via a URL @192.168.0.103 it does not work

summary:
[http://localhost:8080](http://localhost:8080) OK
[http://127.0.0.1:8080](http://127.0.0.1:8080) OK
[http://192.168.0.103](http://192.168.0.103) NO

I need to be able to access that URL from other machines.  It does not work from other machines nor my own.

I have no firewall installed that I am aware (assuming the upgrade didn't put one on)
My router is setup to allow all traffic through.  

This is very bizarre.  Any thoughts?

Thanks!

---

### Post by wolfger on 2007-10-19
> **javajoe220 said:**
> I can ping localhost, 127.0.0.1, and 192.168.0.103 with no problem  but when i attempt to access my machine via a URL @192.168.0.103 it does not work

summary:
[http://localhost:8080](http://localhost:8080) OK
[http://127.0.0.1:8080](http://127.0.0.1:8080) OK
[http://192.168.0.103](http://192.168.0.103) NO
First thought:
For localhost and 127.0.0.1 you specified the port and it worked. For 192.168.0.103 you did not specify a port, and it did not work. Try specifying the port.

Second thought:
a .103 IP leads me to the conclusion that you are using DHCP to dynamically assign addresses (Ubuntu default), and the number 103 indicates this is not the only machine on the network. So... are you sure this machine is still .103 after the upgrade? Open a command line and type 'ifconfig -a' to check. Using DHCP, your IP may change each and every time you reboot. If you want this machine to always be remotely accessible, I suggest giving it a static IP address.

---

### Post by javajoe220 on 2007-10-19
SOLVED:
At the same time of my Kubuntu upgrade I also upgraded to JBoss 4.2 which only binds to the local address by default.  During the JBoss startup I needed to bind it to the machines IP address:

./run.sh -b 192.168.0.103 

It now works fine - no issues with Kubuntu!

Thanks for the help.

---

