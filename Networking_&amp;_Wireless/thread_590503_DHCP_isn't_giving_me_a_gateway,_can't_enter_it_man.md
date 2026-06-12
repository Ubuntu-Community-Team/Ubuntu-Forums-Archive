---
title: "DHCP isn't giving me a gateway, can't enter it manually."
date: 2007-10-24
forum: Networking &amp; Wireless
---

### Post by pomalley on 2007-10-24
DHCP isn't giving me a gateway. I've tried adding one with ```
sudo route add default gw xxx.xxx.xxx.xxx
``` but that returns ```
SIOCADDRT: No such process
``` which I've googled much but to no avail. I've configured it for static ip, giving it the ip, gateway, and netmask I know it should have (gotten from Windows) but that dies with ```
SIOCDELRT: No such process
``` When I restart network from the command line (and it's using dhcp) with ```
sudo /etc/init.d/networking restart
``` it also gives a ```
SIOCADDRT: No such process
``` (I assume when it's trying to set the gateway.)

This is on a Dell laptop using a D-Link pcmcia network card (wired, the onboard ethernet port died), with a fresh Gutsy install, but I'm having the same problem with my desktop which has been upgraded from Feisty, which worked fine.

So, I'm stumped!

Also I didn't specify in there but DHCP is giving me an ip address and a netmask.

---

### Post by pomalley on 2007-10-25
Does nobody have any ideas? I haven't had any luck so far.

---

### Post by froy02 on 2007-10-25
Are you using a router?
If so, open your browser and type "http://xxx.xxx.xxx.xxx" which is the address of your gate. If may ask you for user name and password and if you never changed the password it could be "admin" or "password" depending on your brand,  

Once you get in check if the DCHP server is enabled.  It would also give you  list of net cards asignment. Usually it alo gives you a range of address that you can use as wired network.

Most of the time the gateway ip address is 192.168.0.1.
Check the net for the possible ip gateway for your provider/router manufacturer.

I am only replying to this with the assumption that you are using a router.You need to provide more info, your hardware and setup.

---

### Post by slougi on 2007-10-28
I have very recently begun seeing the same thing. There's also for example a debian bug here: [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=445723](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=445723) although no one seems to have looked at it yet.

Here's some example output, i've edited out parts of the ip addresses:
```

slougi@gondolin:~$ sudo dhclient eth0
There is already a pid file /var/run/dhclient.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:11:09:cf:58:93
Sending on   LPF/eth0/00:11:09:cf:58:93
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPOFFER from 84.xx.xx.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 84.xx.xx.1
SIOCADDRT: No such process
bound to 88.xx.xx.237 -- renewal in 15365 seconds.

```

Manually adding the gateway works:
```

slougi@gondolin:~$ sudo route add default gw 88.xx.xx.1
slougi@gondolin:~$ 

```

It used to work until just a few days ago, I don't know if it's an update that started this or perhaps a configuration change on my ISP's side of things.

Anyone have any ideas?

---

### Post by Rogers on 2008-02-15
I'm getting this same error with a Ubuntu 7.1 server and 2 ubuntu 7. desktops.
[B]
This is my setup (I've moved stuff out into global trying to make it work) Windows clients work fine.

/etc/dhcpd.conf[/B]
[I]authoritative;
#option subnet-mask 255.255.255.0;
default-lease-time 600;
max-lease-time 7200;
option domain-name-servers runithard.com,65.32.1.65;
option domain-name "revolutionaryit.com";
option routers 192.168.0.1;
 #option subnet-mask 255.255.255.0;
option broadcast-address 192.168.0.1;
default-lease-time 600;
max-lease-time 7200;

subnet 192.168.0.0 netmask 255.255.255.0 {
  range 192.168.0.100 192.168.0.254;
#  option domain-name-servers runithard.com,65.32.1.65;
#  option domain-name "revolutionaryit.com";
#  option routers 192.168.0.1;
  #option subnet-mask 255.255.255.0;
#  option broadcast-address 192.168.0.1;
#  default-lease-time 600;
#  max-lease-time 7200;
}[/I]

---

### Post by pomalley on 2008-03-01
I had pretty much given up on this, gone back to Feisty where I can get the internet with dhcpcd. I'm all googled out on this problem. I thought maybe Hardy would fix it but it hasn't. :-(

---

