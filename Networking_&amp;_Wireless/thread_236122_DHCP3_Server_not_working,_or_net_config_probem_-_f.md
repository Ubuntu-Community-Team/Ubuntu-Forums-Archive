---
title: "DHCP3 Server not working, or net config probem - fresh install"
date: 2006-08-14
forum: Networking &amp; Wireless
---

### Post by DagonSphere on 2006-08-14
I'm having a really annoying problem.  After I do a fresh install of Xubuntu 6.06, I cannot for the life of me get DHCP3 Server to hand out IP addresses.  I've setup several Red Hat boxes without a problem, but this is the first time I'm doing this with a Debian distro, and I'm not sure it's a problem with DHCP.  I may have missed something in the configuration of the network cards.  Here's what I have:

eth0: static address hooked up to my internal network
eth1: hooked up to a DSL line (A wireless tranceiver with a static ip, but the configuration is just like a DSL line)

Before I start setting everything up, I ran this:

```
apt-get update
apt-get upgrade
```

Then I set up my network cards

/etc/network/interfaces

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
        address 192.9.200.254
        netmask 255.255.255.0
        broadcast 192.9.200.255

auto dsl-provider
iface dsl-provider inet ppp
provider dsl-provider

    pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf

```

/etc/hosts
```

127.0.0.1       localhost lo
192.9.200.254   internet

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

/etc/hostname

```
internet
```

And I restarted the network

```
/etc/init.d/networking restart
```

Then I installed dhcp3-server

```
apt-get -y install dhcp3-server
```

And then I configured it

/etc/default/dhcp3-server

```
# Defaults for dhcp initscript
# sourced by /etc/init.d/dhcp
# installed at /etc/default/dhcp3-server by the maintainer scripts

#
# This is a POSIX shell fragment
#

# On what interfaces should the DHCP server (dhcpd) serve DHCP requests?
#       Separate multiple interfaces with spaces, e.g. "eth0 eth1".
INTERFACES="eth0"
```

/etc/dhcp3/dhcpd.conf

```
# ddns-update-style interim;

subnet 192.9.200.0 netmask 255.255.255.0 {

        option subnet-mask              255.255.255.0;
#       option domain-name-servers      192.9.200.254;
#       option routers                  192.9.200.254;
        option time-offset              -16000;

range 192.9.200.71 192.9.200.75;

# Ed's Computer
host cam-01 {
        hardware ethernet               00:c0:4f:a0:ba:85;
        fixed-address                   192.9.200.21;
        option domain-name-servers      192.9.200.254;
        option routers                  192.9.200.254;
}
}
```

And I restarted it.
```

/etc/init.d/dhcp3-server restart
```

I get no errors on the network, and no errors on starting dhcp3-server (from the command line).  It just won't hand out IP address to any clients.

I chose dhcp3-server over dhcpd because I want to use Firestarter, and from what I read it only like to cooperate with dhcp3-server.  Although, I did try dhcpd, and I had the same problem, which is why I'm thinking it's a network card configuration problem.

Any help is appreciated!!

EDIT:  I failed to mention that I tried this on two different boxes, serving two different networks.  One at work, and one at home.  All the hardware is functional, because when I reverted back to my RH install, and everything works.

---

### Post by NetworkGuy on 2006-08-14
Do you get any messages in a log file?   /var/log/messages or maybe an area for dhcpd3?

Maybe something in a log file would tell you why it isn't working correctly.

---

### Post by DagonSphere on 2006-08-14
ARRRRRRRRGH!  The nic aliases got switched.  I swear I checked thost friggin' things a dozen times ](*,)

---

### Post by mpvano on 2006-08-14
A recent update did that to me TOO! It was easy enough to fix by re-editing iftab, but I found it pretty annoying!

Mario

---

