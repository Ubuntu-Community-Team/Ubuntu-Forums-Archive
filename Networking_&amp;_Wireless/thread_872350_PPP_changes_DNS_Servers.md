---
title: "PPP changes DNS Servers"
date: 2008-07-27
forum: Networking &amp; Wireless
---

### Post by Tixer on 2008-07-27
I have a server with two interfaces, eth0 and eth1. eth0 is used to share files to other computers on the network (the network also supplies internet via a router), and eth1 is so the server has a dedicated connection to the tubes. eth1's PPPoE connection has a habit of disconnecting, but that's not important right now.

The problem I'm having is that whenever the PPPoE connection is started, all the DNS servers change from my custom configuration to some random thing assigned by the modem. This wouldn't be half bad, aside from the fact that they're not even valid servers.

Therefore, whenever the modem cuts out, I have to ssh into the server over the LAN, run pon dsl-provider, then manually edit /etc/resolv.conf to use 4.2.2.1. Then I need to spend time fighting ddclient, which is convinced that my IP was updated and that dyndns will ban me if I update it too fast (except it hasn't had internet access). Finally, I need to relaunch Azureus, so that it binds to ppp0 again. You can imagine the frustration this leads to.

So specifically, I want to solve the problem with the DNS servers changing. I want to either make it impossible for any program to change what I've specified manually in resolv.conf (chattr +i, anyone? Will that work?), or change the setting that pon has to no longer assign DNS servers every time it runs.

---

### Post by dentaku65 on 2008-07-28
The resolv.conf is not the correct file to change DNS not privided by your internet provider. In the DHCP situation you must edit:
```
sudo nano /etc/dhcp3/dhclient.conf
```
and change the line
```
#prepend domain-name-servers;
```
to
```
prepend domain-name-servers 208.67.222.222, 208.67.220.220;

```
Then restart your box.

In the example above you can force the DNS IP of [Opendns]("http://opendns.org/"); of course you can set the iP DNS you want.

---

### Post by Iowan on 2008-07-28
That same **/etc/dhcp3/dhclient.conf** file has an option (the very next line...) ```
request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, domain-name-servers, host-name,
        netbios-name-servers, netbios-scope;

```Removing the ** domain-name-servers,** portion should also make the problem go away (the "prepend" line will give you control over "first choice", though).

---

### Post by chmac on 2008-08-18
> **dentaku65 said:**
> ```
prepend domain-name-servers 208.67.222.222, 208.67.220.220;

```

Tixer, did this work for you? When I connect via pppoe this setting is ignored by dhclient. Likewise (I think) when I connect to ppp connections (GSM modem). When I connect to a wireless / wired network, the correct dns servers are prepended, but not when I connect to ppp connections.

Anyone have any suggestions?

---

### Post by sl1mshadyx on 2008-08-19
[http://ubuntuforums.org/showthread.php?p=5619186#post5619186](http://ubuntuforums.org/showthread.php?p=5619186#post5619186)

---

### Post by chmac on 2008-08-19
> **sl1mshadyx said:**
> [http://ubuntuforums.org/showthread.php?p=5619186#post5619186](http://ubuntuforums.org/showthread.php?p=5619186#post5619186)

As per [my reply on that thread]("http://ubuntuforums.org/newreply.php?do=newreply&p=5619655"), no dice. Removing 'usepeerdns' from the /etc/ppp/peers/dsl-provider means no dns servers at all are set by ppp.

---

