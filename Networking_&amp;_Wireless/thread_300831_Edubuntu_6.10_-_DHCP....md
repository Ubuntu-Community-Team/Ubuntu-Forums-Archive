---
title: "Edubuntu 6.10 - DHCP..."
date: 2006-11-16
forum: Networking &amp; Wireless
---

### Post by kory on 2006-11-16
Hello everyone.  I had just started to install 6.06 but noticed that 6.10 was out so I decided to give that a shot instead.  :)

I've scoured the forum and Googled other resources for the last two days but thought it's finally time to ask the experts for help.  :)

I have a server w/ two NIC cards.  One of them (the 10/100 card) connects back to our school's primary network (192.168.1.x) and the other serves as the subnet card for the thin clients (1Gbs; 192.168.0.x).

My dhcpd.conf file is:

```

authoritative;

subnet 192.168.0.0 netmask 255.255.255.0 {
  range 192.168.0.20 192.168.0.250;
  option domain-name "example.com";
  option domain-name-servers 192.168.0.1;
  option broadcast-address 192.168.0.255;
  option routers 192.168.0.1;
  option subnet-mask 255.255.255.0;

# Set the amount of time in seconds that
# a client may keep the IP address

default-lease-time 86400;
max-lease-time 86400;

  if substring( option vendor-class-identifier, 0, 9 ) = "PXEClient" {
    filename "/ltsp/i386/pxelinux.0";
  }
  else{
    filename "/ltsp/i386/nbi.img";
  }
  option root-path "/opt/ltsp/i386";
}
```

My interfaces config file is:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth2
iface eth2 inet static
address 192.168.1.20
netmask 255.255.255.0
gateway 192.168.1.1

auto eth1
iface eth1 inet static
    address 192.168.0.254
    netmask 255.255.255.0
    network 192.168.0.0
    broadcast 192.168.0.255
    gateway 192.168.0.1
```
As you can see, I've assigned a static IP from the school network to the 10/100 card and am using the default 192.168.0.x address during the install process.

I can confirm that a client is receiving a DHCP address from the server but DNS doesn't seem to be working.  I can ping the server and the server can ping the client but when I try to ping an external domain from the client, I don't get anywhere.  I can ping an external domain from the server.

I'm also not using PXE yet as I wanted to get the clients working before delving into the PXE emulation.

I would greatly appreciate any insight anyone might offer.

Thx much, in advance!

Regards,
Kory

---

### Post by bijesz on 2006-11-16
Hi,

Try to narrow the problem.

When you try to ping an external computer, you try it with hostname or with ip address?

I suggest you to try with ip address to confirm that routing works.

If it works it will be a name resolution problem, if not it's also a routing problem.

---

### Post by kory on 2006-11-17
Hi, bijesz.  Thx much for your reply.

I actually can't ping to any other IP address outside the 192.168.0.x subnet.  For example, our router is 192.168.1.1 on the "school" side.  I can't ping to that router, however, I can ping to the Edubuntu server at 192.168.0.1.

Hope this helps!

Regards,
Kory

---

### Post by bijesz on 2006-11-17
> **kory said:**
> Hi, bijesz.  Thx much for your reply.

I actually can't ping to any other IP address outside the 192.168.0.x subnet.  For example, our router is 192.168.1.1 on the "school" side.  I can't ping to that router, however, I can ping to the Edubuntu server at 192.168.0.1.

Hope this helps!

Regards,
Kory

So it seems that this a routing problem.
Type "route" in the shell, and post the output here.

---

### Post by kory on 2006-11-17
I wasn't sure which info you wanted so here's the "route" info from the server itself:

```
root@complabsrv:/home/edubuntu# route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
172.16.213.0    *               255.255.255.0   U     0      0        0 vmnet8
192.168.245.0   *               255.255.255.0   U     0      0        0 vmnet1
192.168.1.0     *               255.255.255.0   U     0      0        0 eth2
192.168.0.0     *               255.255.255.0   U     0      0        0 eth1
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth2
default         172.16.213.2    0.0.0.0         UG    0      0        0 vmnet8
root@complabsrv:/home/edubuntu# 

```

And here's the route info from the client (I had to manually type this in below from the output):

```
complab9@complab9:~$ route
Destination     Gateway     Genmask       Flags  Metric  Ref     Use  Iface
192.168.0.0     *           255.255.255.0 U      0       0         0  eth0
default         192.168.0.1 0.0.0.0       UG     0       0         0  eth0
complab9@complab9:~$

```

I'm also finding out that for some reason, the server wants to keep resetting it's DNS info on the static NIC to some random DNS IP address.  I'm having to go back in every five minutes or so to put our DNS server IP in there.

Thx for your continued help!  :)

Regards,
Kory

---

### Post by bijesz on 2006-11-20
Hi Kory,

It's good to see that you are proactive and provided both routing tables.

The problem is on the client side, however the client obtain it's settings from the server (dhcpd).

You should edit your dhcpd.conf file on the server:

change this line:

```

option routers 192.168.0.1;

```

to

```

option routers 192.168.0.254;

```

Another solution is to change your server's ip address to 192.168.0.1

BTW as I see you're running the server on a virtual machine.

---

### Post by kory on 2006-11-27
Hi, bijesz.  I had a "moment" over our Thanksgiving break.  Turns out all I needed to do was run a crossover cable from the server thin-client NIC to the switch then plug the client's NIC card into another port on the switch.  I know have DHCP capabilities.  Now I'm getting the dreaded "can't access tty" error on the client side when trying to PXE into the server.  I'll open a new thread.

Thx again!

Regards,
Kory

---

