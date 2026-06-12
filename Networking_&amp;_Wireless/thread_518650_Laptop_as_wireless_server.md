---
title: "Laptop as wireless server?"
date: 2007-08-06
forum: Networking &amp; Wireless
---

### Post by Toufik on 2007-08-06
Is it possible to use my laptop as a wireless server in order to share datas with another laptop that will be connected with it? The purpose is not to share an internet connection but only to be able to easily share files between two laptops.

Thanks

some specs: sony laptop with feisty fawn and centrino as wifi chip

---

### Post by Toufik on 2007-08-07
Bump

---

### Post by spd106 on 2007-08-07
I think what you need is an ad hoc network. This will allow you to connect to other PCs in a wireless peer to peer network. This wiki page will guide you through the steps, I have found that network manager doesn't work very well, so you will probably have to use the iwconfig etc terminal commands. 
[https://help.ubuntu.com/community/WifiDocs/Adhoc](https://help.ubuntu.com/community/WifiDocs/Adhoc)

For file sharing just use samba, you can select which directories to share quite easily by right-clicking them. The first time it will prompt you to install the samba software (don't bother with NFS). Access shares through the Places menu under Network and click through the Windows Network shortcut or simply enter the path to it directly, smb://*hostname*.local/sharename 
e.g the archives directory on my laptop called johnny5 is at smb://johnny5.local/archives

For more information see [https://help.ubuntu.com/community/ComprehensiveSambaGuide](https://help.ubuntu.com/community/ComprehensiveSambaGuide)

---

### Post by Toufik on 2007-08-07
Well, after a few more hours of googling, I've finally found 1 (one!) how-to ... in French: 

[http://blog.theclimber.be/index.php?post/2007/05/29/Faire-un-relais-wifi-sur-Ubuntu](http://blog.theclimber.be/index.php?post/2007/05/29/Faire-un-relais-wifi-sur-Ubuntu)

For my purpose (not bridging between private network and internet), here is the description in English:

1) configure wifi interface
2) install a dhcp server in order to connect to that interface automatically
(the two last points are for bridging)
3) Install a DNS server to resolve the address names
4) Install a NAT (really the bridging between intranet and internet)

1) Configuration of wifi interface:
First you need to remove network-manager as it will always try to override your changes!
```
sudo apt-get remove network-manager
```

* eth0 : interface connected to internet
* eth1 : wifi interface where to connect the subnetwork

edit this file: /etc/network/interfaces
```

auto lo
iface lo inet loopback

# Primary network interface : eth0 (interface towards internet)
auto eth0
iface eth0 inet dhcp

# Second network interface : eth1
# wifi
iface eth1 inet static
        address 192.168.157.1
        network 192.168.157.0
        netmask 255.255.255.0
        broadcast 192.168.157.255
        pre-up ifconfig eth1 up
        pre-up ifconfig eth1 down
        pre-up ifconfig eth1 up
        pre-up ifconfig eth1 down
        pre-up iwconfig eth1 essid "TUX-wifi"
        pre-up iwconfig eth1 mode ad-hoc
        pre-up ifconfig eth1 up
auto eth1

```

2) Install DHCP server
```
sudo apt-get install dhcp3-server
```

Edit this file: /etc/default/dhcp3-server
```
INTERFACES="eth1"
```

Edit this file: /etc/dhcp3/dhcpd.conf
```

# The ddns-updates-style parameter controls whether or not the server will
# attempt to do a DNS update when a lease is confirmed. We default to the
# behavior of the version 2 packages ('none', since DHCP v2 didn't
# have support for DDNS.)
ddns-update-style ad-hoc;

# option definitions common to all supported networks...
option domain-name "tux-master.lan";
option domain-name-servers 192.168.157.1;
log-facility local7;

# Configuration of specific interface
subnet 192.168.157.0 netmask 255.255.255.0 {
  range 192.168.157.50 192.168.157.200;
  option domain-name-servers 192.168.157.1;
  option domain-name "tux-master.lan";
  option routers 192.168.157.1;
  option broadcast-address 192.168.157.255;
  default-lease-time 600;
  max-lease-time 7200;
}

```

Restart your network:

```
sudo /etc/init.d/networking restart
sudo /etc/init.d/dhcp3-server restart
```

Should work now!

---

### Post by Toufik on 2007-08-07
We answer at the same time :)

Indeed the Ad-hoc mode is the solution but it is nowhere stated clearly.

For the files, scp will be good enough :)

It's a pity that network manager is not able to configure private network on demand (like in M$ or OSX)

---

