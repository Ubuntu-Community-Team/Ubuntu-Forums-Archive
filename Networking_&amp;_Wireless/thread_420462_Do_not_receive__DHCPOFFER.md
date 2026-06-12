---
title: "Do not receive  DHCPOFFER"
date: 2007-04-23
forum: Networking &amp; Wireless
---

### Post by laszlo on 2007-04-23
Hi there,

I have an IBM T21 laptop with a CISCO 350 pcmcia card. Under both edgy and fiesty I can connect to my wireless router but do not receive an IP address. From my router stats, it says it has registered and has assigned it an IP against the MAC address but the machine has not picked it up. I have tried it with and without network manager gnome, tried ifup/down, iwconfig and dhclient  but it makes no difference. Any help would be greatly appreciated.

---

### Post by kpjoyce on 2007-04-26
Sorry to reply with no helpful information ... but have you solved this issue?  I am facing the same thing.  The wireless card connects to the access point just fine, but cannot get an IP assigned.

---

### Post by bukwirm on 2007-04-26
What output do you get if you run

sudo ifdown **interface**
sudo ifup **interface**

?

---

### Post by sdide on 2007-04-26
Please post output of
~$ cat /etc/dhcp3/dhclient.conf | grep -v ^#

---

### Post by kpjoyce on 2007-04-26
Thanks for your help.  I feel a bit guilty about comandeering someone else's thread.

To be clear: I think that DHCP works, at least it has with wired connections.  But it is at that stage in the process that my attempts to wirelessly connect fail.

> 
kpjoyce@kpjoyce-laptop:~$ sudo ifup ath0
There is already a pid file /var/run/dhclient.ath0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/ath0/00:90:96:3d:73:6a
Sending on   LPF/ath0/00:90:96:3d:73:6a
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
kpjoyce@kpjoyce-laptop:~$ sudo ifdown ath0
RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.ath0.pid with pid 19288
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/ath0/00:90:96:3d:73:6a
Sending on   LPF/ath0/00:90:96:3d:73:6a
Sending on   Socket/fallback
DHCPRELEASE on ath0 to 192.168.1.1 port 67


> 

kpjoyce@kpjoyce-laptop:~$ cat /etc/dhcp3/dhclient.conf | grep -v ^#

send host-name "<hostname>";
request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, domain-name-servers, host-name,
        netbios-name-servers, netbios-scope;
timeout 30;



---

### Post by sdide on 2007-04-27
The dhclient.conf, looks about right.

Well, maybe we can try static addresses, if the AP does not act as a DHCP server, you won't get an address with dhclient.

If you know the address of your AP, try say 192.168.0.1

try 

~# ip a a 192.168.0.50/24 dev eth1

and add a default route

~# ip r a default via 192.168.0.1 dev eth1

replace address and device accordingly. 50 is just a random number that should be something that another computer on the same network does not have.

---

### Post by Bingo on 2007-05-07
Any updates on this?  I have the exact same setup and have never been able to get it to work.

Thanks in advance.

---

