---
title: "HOWTO: Internet sharing with Ubuntu (NAT Gateway)"
date: 2008-03-03
forum: Networking &amp; Wireless
---

### Post by SpaceTeddy on 2008-03-03
I keep reading that people want to share their internet connection through an Ubuntu computer. So, i will put down a few basic steps that one has to do to turn any ubuntu installation into a **basic** gateway for other computers.
The Settings i am going to write down here are permanent ! so please remember this if you  use a mobile device that it will always (!) act as a gateway for the configured network card.

In the following, i will refer to the network device that is connected to the internet as eth1. It is not compulsory that the internet device is called that - other possible names are: eth0, ath0, ppp0, ... and many more.
The computer/network with the clients is, in my case, connected to the network device eth0. This can also vary quite a lot, too. 
Please make sure you know what device is which for you, and adjust **all** commands and configurations accordingly.

The basic scheme of what this setup looks like is:

PC-Client <---> PC-Gateway (ubuntu) <---> Internet

[SIZE="5"]Prerequisites[/SIZE]
Your ubuntu Computer has internet connection and you know which network device provides this functionality.

NOTE: how you are connected to the internet does not matter (ethernet, cable, wifi, dsl), as long as you have a second network device besides the one you are connection this should work.

[SIZE="5"]Configuring the network card[/SIZE]
the network card that serves the clients (eth0) needs a static ip address. This can be done outside of network manager and would be recommended that way, since you might need nm to still connect the gateway to the internet itself. 
Note that this will result in network-manager to completely ignore the network card that you configured for the client network, thus rendering eth0 unavailable in nm.

edit the network configuration file and set eth0 to a static ip. to open the config use this command
```
gksu /etc/network/interfaces
```
now, to configure eth0, you will need add a few lines to the file. Also, this configuration ONLY works on ethernet cards, NOT on wireless. If you need a wireless card to be manually configures, there are a few sticky threads in this forum that will explain how to do it. I'll try to update this later and make sure i have an example for wireless cards ready aswell :)

add the following lines to the file
```
auto eth0
iface eth0 inet static
        address 10.8.16.1
        netmask 255.255.255.0
        broadcast 10.8.16.0
        network 10.8.16.0

```
This will set a static ip address for eth0 (10.8.16.1) and take the network card out of nm. these changes only take effect after rebooting. To temporarily use these settings, issue this command:
```
sudo ifconfig eth0 10.8.16.1
```

[SIZE="5"]Enable IP forwarding[/SIZE]
Port forwarding is turned off in ubuntu by default. But it is needed so that the Computer will forward pakets it receives. To enable port forwarding, issue the following command
```
gsku gedit /etc/sysctl.conf
```
and look for the following line
```
#net.ipv4.conf.default.forwarding=1
```
once that one is found, remove the # so that it reads to be
```
net.ipv4.conf.default.forwarding=1
```
These changes will take effect with the next reboot. if you want them to take effect right now, use these commands
```
sudo sysctl -w net.ipv4.ip_forward=1
```
**[Update]**
it has been reported multiple times that the sysctl.conf got ignored. You can check that issueing this command **after a reboot**:
```
sudo sysctl net.ipv4.ip_forward
```
if the answer is still 0. you will need to add a line to /etc/rc.local. open it to edit with
```
sudo gedit /etc/rc.local
```
and add this line BEFORE the exit 0 in the file
```
sysctl -w net.ipv4.ip_forward=1
```
then reboot and check with the above command if it still returns 0. **ONLY do this change if you have to, as this is an ugly hack to force setting...** 
**[/Update]**
[SIZE="5"]Configuring iptables (paket filter)[/SIZE]
In order to allow pakets to pass though the router, we need to add a couple of iptables rules to the filter so that everything may pass our machine. Also we need to rewrite the pakets so that they can find their way back to us.
open the file /etc/rc.local with
```
gksu gedit /etc/rc.local
```
and add the following lines 
```
/sbin/iptables -P FORWARD ACCEPT
/sbin/iptables --table nat -A POSTROUTING -o eth1 -j MASQUERADE
```

Doing it this way is neither elegant nor very secure, but it is basic and it should work. If you are worried about security issues, i suggest you read up in iptables and how to confugure the rules more secure than simply letting anything pass through.
again, these changes only take effect after a reboot. 
to make the changes take effect right now, use these commands
```
sudo iptables -P FORWARD ACCEPT
sudo iptables --table nat -A POSTROUTING -o eth1 -j MASQUERADE
```

[SIZE="5"]Configuring the client[/SIZE]
There are two ways to configure the client - one is a static, manual config. If you would like to do this, then give the client an ip-address in the network 10.8.16.0/24 (i.e. 10.8.16.2), the gateway 10.8.16.1 and a dns server from your computer (they can be found in the file /etc/resolv.conf)

If you have multiple client, or do not want to configure something staticially, you might want to look at setting up a *basic* dhcp server which issues network configurations to clients.
to install the server, type the following
```
sudo apt-get install dhcp3-server
```
this should install the dhcp-server on your machine. The start will fail, but that is nothing to worry about.
before the dhcp server itself can be configured, we need one more little bit of information. We need to know what dns servers are used so we can push then to the clients that will be configured via this server. to find out the currently used dns server, use this command
```
cat /etc/resolv.conf
```
and note down the ip addresses that are written at the nameserver statement

The next step is to configure the dhcp-server so it knows what ip-addresses to dish out and what settings.
for that, edit the file /etc/dhcp3/dhcpd.conf with this command
```
gksu gedit /etc/dhcp3/dhcpd.conf
```
save the content in a different file (for later reference or if you want to do more with it later on), and then replace it with the following basic setup:
```
ddns-update-style none;
option domain-name "mynetwork";
option domain-name-servers **Nameserver1, Nameserver2**;
option routers 10.8.16.1;

default-lease-time 42300;
max-lease-time 84600;
authoritative;

log-facility local7;

subnet 10.8.16.0 netmask 255.255.255.0 {
  range 10.8.16.50 10.8.16.150;
}

```
The Bold entries in the config file have to replaced by the nameserver ip addresses that you previously got. if you only have one, remove the second one.

the last thing to do before the server can be started is to tell it what interface to listen on. This can be configures in the file /etc/default/dhcp3-server.
open it with 
```
gksu gedit /etc/default/dhcp3-server
```
and edit the line with the INTERFACES="" to read
```
INTERFACES="eth0"
```

the dhcp-server will be automaticially started upon reboot. to manually start it now use this command
```
sudo /etc/init.d/dhcp3-server start
```

That is all you need for a basic setup of things. 
**Please be reminded that you need to always check the network devices in your computer aginst the ones in the config. If you configure blindly from this and your devices are swapped or named different, you can break you computers network entirely.**

---

### Post by rockinlinux on 2008-03-13
ok i did do that spaceteddy but it returns a 0 so it is not enabled...here is my file.

```
  #
# /etc/sysctl.conf - Configuration file for setting system variables
# See sysctl.conf (5) for information.
#

#kernel.domainname = example.com
#net/ipv4/icmp_echo_ignore_broadcasts=1

# the following stops low-level messages on console
kernel.printk = 4 4 1 7

# enable /proc/$pid/maps privacy so that memory relocations are not
# visible to other users.
kernel.maps_protect = 1

##############################################################3
# Functions previously found in netbase
#

# Uncomment the next line to enable Spoof protection (reverse-path filter)
#net.ipv4.conf.default.rp_filter=1

# Uncomment the next line to enable TCP/IP SYN cookies
#net.ipv4.tcp_syncookies=1

# Uncomment the next line to enable packet forwarding for IPv4
net.ipv4.conf.default.forwarding=1

# Uncomment the next line to enable packet forwarding for IPv6
#net.ipv6.conf.default.forwarding=1

```

---

### Post by neurostu on 2008-05-16
So I didn't use the walkthrough above to enable internet sharing, I used firestarter. I was able to get it so that my local machines can all ping each other but I don't get internet sharing from my server machine to the clients.  Anybody know what I might need to do?

---

### Post by neurostu on 2008-05-16
I was having a DNS issue. Firestarter worked great for me!

---

### Post by dmizer on 2008-10-29
/etc/sysctl.conf needs two lines for proper ipv4 forwarding:

```
net.ipv4.conf.default.forwarding=1
net.ipv4.conf.all.forwarding=1
```
That's why your sysctl.conf is getting ignored.

More information here: [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

---

