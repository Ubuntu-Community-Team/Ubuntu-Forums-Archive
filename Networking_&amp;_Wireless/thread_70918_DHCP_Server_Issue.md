---
title: "DHCP Server Issue"
date: 2005-10-01
forum: Networking &amp; Wireless
---

### Post by Reg Hollis on 2005-10-01
I've run a few searches on here to see if anything answers my issue, but have so far come up blank - if anybody knows of any I've missed, then I apologise.

I run Ubuntu on my home system, on which there are two ethernet cards.  eth0 connects to a router, which in turn connects to two other machines and a cable modem.  eth1 connects to my XBox, for use on XBox Live.

When running Windows XP, I have always been able to use this configuration, meaning that the XBox will connect to the XBox Live service via my PC, in turn via the router and cable modem.  I would like to be able to do the same under Ubuntu, so I can finally burn my XP disc.

I installed the dhcp3 server as per the instructions on the Unofficial Ubuntu Guide site, telling it to listen on eth1.  However, whenever I try to start or restart the dchp3 server, it fails.

Being completely green to Ubuntu networking, I don't know what my next move should be - any pointers?  Please don't tell me MS have been so callous as to ensure that an XBox can not be connected via a Linux machine some how...

---

### Post by cwaldbieser on 2005-10-02
[QUOTE=Reg Hollis]I've run a few searches on here to see if anything answers my issue, but have so far come up blank - if anybody knows of any I've missed, then I apologise.
I run Ubuntu on my home system, on which there are two ethernet cards.  eth0 connects to a router, which in turn connects to two other machines and a cable modem.  eth1 connects to my XBox, for use on XBox Live.
When running Windows XP, I have always been able to use this configuration, meaning that the XBox will connect to the XBox Live service via my PC, in turn via the router and cable modem.  I would like to be able to do the same under Ubuntu, so I can finally burn my XP disc.
I installed the dhcp3 server as per the instructions on the Unofficial Ubuntu Guide site, telling it to listen on eth1.  However, whenever I try to start or restart the dchp3 server, it fails.
Being completely green to Ubuntu networking, I don't know what my next move should be - any pointers?  Please don't tell me MS have been so callous as to ensure that an XBox can not be connected via a Linux machine some how...[/QUOTE]
I don't know anything about the XBox Live requirements, but you need to configure Ubuntu at the minimum to do packet forwarding.

In WinXP, do you have to have Internet connection Sharing set up for XBox Live to work?   Or does it go through some special program on WinXP?  

How does the XBox physically attach to the computer?  Is it a standard ethernet connection?  Can you just plug it into your router?

---

### Post by Reg Hollis on 2005-10-03
[QUOTE=cwaldbieser]I don't know anything about the XBox Live requirements, but you need to configure Ubuntu at the minimum to do packet forwarding.
In WinXP, do you have to have Internet connection Sharing set up for XBox Live to work?   Or does it go through some special program on WinXP?  
How does the XBox physically attach to the computer?  Is it a standard ethernet connection?  Can you just plug it into your router?[/QUOTE]

The XBox connects through a standard internet connection, which I could connect direct to thr router if I wanted to run another 50 foot of cable.  However, since I've already gone through that once and it works perfectly well through WinXP, I'd rather try to avoid it.

Yes, I run with Internet Connection Sharing on WinXP.  XBox Live doesn't have any special requirements really - just access to a broadband internet connection.  If I can't get it sorted, it's no big deal - it just means I have to boot up my WinXP partition more than I'd really like to.

As for packet forwarding, I don't even get far enough for that to become an issue - the DHCP server won't even start up to provide the XBox with an IP address.

---

### Post by Tuxbee on 2005-10-03
Try to find the log
Probably /var/log/messages.log
Find someting like "No Interface configured to listen to" ?
Then add 
```
INTERFACES="eth0"
```
to the file /etc/default/dhcp3-server
where eth0 is the interface the dhcp server needs to listen to

gl

---

### Post by Reg Hollis on 2005-10-04
I appreciate the suggestion Tuxbee, but I have have already edited the config file to have it listen to eth1 (eth0 is my direct internet connection, eth1 is my connection to the XBox).

It's bound to be something really simple I'm overlooking somehwere, I just can't figure out what!

---

### Post by cwaldbieser on 2005-10-04
[QUOTE=Reg Hollis]I appreciate the suggestion Tuxbee, but I have have already edited the config file to have it listen to eth1 (eth0 is my direct internet connection, eth1 is my connection to the XBox).
It's bound to be something really simple I'm overlooking somehwere, I just can't figure out what![/QUOTE]
Well, are there any error messages when the dhcp server fails?  Anything show up with "dmesg"?  Maybe a log in /var/log somewhere?

---

### Post by pingswept on 2005-10-04
[QUOTE=Reg Hollis]
As for packet forwarding, I don't even get far enough for that to become an issue - the DHCP server won't even start up to provide the XBox with an IP address.[/QUOTE]

Here are some other paths you could try if you're still stuck on getting the DHCP to work:

1. Get packet forwarding working, and then use the DHCP on your router (which you may need to enable).

2. Install ethereal and sniff eth1 as you start up the XBox. Is the XBox definitely requesting an address? If it is, is eth1 definitely not responding?

3. What error message do you get when dhcp3 won't start, anyway?

4. The command dhclient might help with testing.

Keep us posted.

---

### Post by 8086 on 2005-10-08
The reason you are not getting dhcpd to work is that it is expecting the configfile to be /etc/dhcpd.conf. I have no idea why this has not been fixed! The quickfix for this is to link to the correct file:

(do this as root: sudo -s)
```
cd /etc
ln -s dhcp3/dhcpd.conf .
```

---

### Post by bluefrog on 2005-10-16
Using Edubuntu I have the same problem.

No subnet declaration for eth0 (192.168.1.244).
Oct 17 00:19:03 localhost dhcpd: ** Ignoring requests on eth0.  If this is not what
Oct 17 00:19:03 localhost dhcpd:    you want, please write a subnet declaration
Oct 17 00:19:03 localhost dhcpd:    in your dhcpd.conf file for the network segment
Oct 17 00:19:03 localhost dhcpd:    to which interface eth0 is attached. **
Oct 17 00:19:03 localhost dhcpd: 
Oct 17 00:19:03 localhost dhcpd: 
Oct 17 00:19:03 localhost dhcpd: Not configured to listen on any interfaces!

here's my dhcpd.conf
ddns-update-style            none;

default-lease-time           21600;
max-lease-time               21600;

option subnet-mask           255.255.255.0;
option broadcast-address     192.168.1.255;
option routers               192.168.1.244;
option domain-name-servers   192.168.1.244;
option domain-name           "ltsp";          # <--Fix this domain name

option root-path             "192.168.1.244:/opt/ltsp/i386";

option option-128 code 128 = string;
option option-129 code 129 = text;

    subnet  192.168.1.0 netmask 255.255.255.0 {
        range dynamic-bootp 192.168.1.1 192.168.1.253;
    }

here's my /etc/default/dhcp3-server

INTERFACES="eth0"

i've done the ln -s trick just in case... but still same error. btw when i apt-get intall dhcp3-server it doesn't ask me to fill in the interface.

---

### Post by bluefrog on 2005-10-17
problem solved for me.

turned out that the server was looking for /etc/ltsp/dhcpd.conf

---

