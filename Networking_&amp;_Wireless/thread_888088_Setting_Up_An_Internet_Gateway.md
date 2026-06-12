---
title: "Setting Up An Internet Gateway"
date: 2008-08-12
forum: Networking &amp; Wireless
---

### Post by jonathanmotes on 2008-08-12
Has anyone set up an internet gateway with Hardy? I've been trying the  tutorial here: 
[http://www.cahilig.org/ubuntu-and-debian-internet-gateway-ip-masquerading](http://www.cahilig.org/ubuntu-and-debian-internet-gateway-ip-masquerading)
all day and I can't seem to get it to work.

Thanks!

---

### Post by Iowan on 2008-08-12
What part isn't working? Do the client computers get addresses?  If your ISP issues DHCP addresses, **eth0** might need to be set up for DHCP.

---

### Post by jonathanmotes on 2008-08-12
Thanks for the reply and I'm sorry about the lack of details! I was in a hurry when I posted.

> If your ISP issues DHCP addresses, eth0 might need to be set up for DHCP.
I'm not sure whether it does or not. How would I figure that part out?

> Do the client computers get addresses?
I'm not sure what you mean, but running ifconfig shows the ip addresses that I assign in the /etc/network/interfaces file. When I do so, my internet connection to the computer (future gateway) is instantly disabled when I make the changes. However, I'm not completely certain that I am setting it up properly. Here's what I'm doing (see my comments in the scripts):)

```

# The primary network interface
auto eth0
iface eth0 inet static
    #is this right - or should it be the ip that I get when I visit whatsmyip.org?
    address 192.168.1.2
    netmask 255.255.255.0
    #I'm assuming that this should be the ip of my DSL modem (which is 192.168.1.1)
    gateway 192.168.1.1

auto eth1
iface eth1 inet static
    address 192.168.1.3
    netmask 255.255.255.0

```

For the nameserver ips in the /etc/resolv.conf file, I'm using the ISP DNS ips from this webpage:
[http://support.centurytel.net/index.cfm?action=centurytel.support.help_mac](http://support.centurytel.net/index.cfm?action=centurytel.support.help_mac)

For the DHCP, I set up the /etc/dhcp3/dhcpd.conf file like this:
```

authoritative;
subnet 192.168.1.0 netmask 255.255.255.0 {
        range                           192.168.1.100 192.168.1.200;
        #domain name server ips are taken from the website mentioned above
        option domain-name-servers      209.142.136.220,207.230.192.254;
        #I'm not sure this is the correct ip (this is the ip of my modem)
        option routers                  192.168.1.1;
        default-lease-time              600;
        max-lease-time                  7200;
}

```

When I run ```
/etc/init.d/dhcp3-server start 
```
I get a error that says something is wrong with the configuration file, but it doesn't offer any specifics.

EDIT: I also made changes to the /etc/sysctl.conf file because I ran across a post somewhere that said to uncomment line 38 in the file:```
#net.ipv4.ip_forward=1
```
I didn't uncomment the other line: ```
#net.ipv6.ip_forward=1
```

Thanks for the help!

---

### Post by dmizer on 2008-08-13
Try this howto instead: [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

---

### Post by jonathanmotes on 2008-08-13
> Try this howto instead: [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

Thanks! This is exactly what I have been looking for: a well polished and unambiguous guide!

---

