---
title: "Network Bridging"
date: 2007-08-05
forum: Networking &amp; Wireless
---

### Post by explosive on 2007-08-05
This is the setup I have:

(All IP address' are assigned manually - DHCP is disabled on the router).

```

WIRELESS-ROUTER                 PC
                                PC
                                PC ---[x-over cable]---PC

```

I have 3 PC's connected wirelessly to my router, 1 of which is running Ubuntu (7.04 server edition). I have another PC (running Ubuntu 7.04 desktop edition) connected to this one via a crossover Ethernet cable. I wish to get internet access on the PC connected via crossover cable. 

I understand that I need to use network bridging and I have installed bridge-utils on the wirelessly connected PC. I am not sure of the settings that I should now be putting in my /etc/network/interfaces files on either PC. All the example that I have seen use DHCP and I need to use a manually assigned IP.

---

### Post by explosive on 2007-08-06
*bump*

---

### Post by explosive on 2007-08-08
*bump again*

Anyone got any ideas? I could really do with a hand with this...

---

### Post by spd106 on 2007-08-08
There's some information [here]("https://help.ubuntu.com/community/NetworkConnectionBridge") and more [here]("https://help.ubuntu.com/community/BridgingNetworkInterfaces").
Post back with any problems and we will try to assist.

Good luck

---

### Post by explosive on 2007-08-09
Right, I've had a go and I'm having some problems:

This is my /etc/network/interfaces file on the bridging PC:
> 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface (connects to net)
auto wlan0
iface wlan0 inet static
	address 10.20.251.200
	netmask 255.255.255.0
	network 10.20.251.0
	broadcast 10.20.251.255
	gateway 10.20.251.75
	
	# wireless-* options are implemented by the wireless-tools package
	#wireless-mode managed
	#wireless-essid z765treg
	
	#wpa stuff
	wpa-driver wext
	wpa-ssid ********
	wpa-ap-scan 1
	wpa-proto RSN
	wpa-pairwise CCMP
	wpa-groupwise CCMP
	wpa-key-mgmnt WPA-PSK
	wpa-psk *************************************


	# dns-* options are implemented by the resolvconf package, if installed
	dns-nameservers 212.159.6.9 212.169.6.10

#Ethernet card - used to link to other PC
auto eth0
iface eth0 inet manual

#Bridge
auto br0
iface br0 inet static
	bridge_ports eth0 wlan0
	address 10.20.251.201
	netmask 255.255.255.0



I now can't connect to the internet at all on the bridging PC (I have tried the commands specified in the wiki page but when I try and ping I just get a host unreachable message).

I also don't know what settings I should be using on the PC that is going to be connected to the bridge. What do I set the ip address and gateway to?

---

### Post by Paris Heng on 2007-08-10
> **explosive said:**
> Right, I've had a go and I'm having some problems:

This is my /etc/network/interfaces file on the bridging PC:


I now can't connect to the internet at all on the bridging PC (I have tried the commands specified in the wiki page but when I try and ping I just get a host unreachable message).

I also don't know what settings I should be using on the PC that is going to be connected to the bridge. What do I set the ip address and gateway to?



Hi, do u able to bridge ur eth0 and wifi0 ??? success anyway?

Please reply.

---

### Post by explosive on 2007-08-10
No it doesn't work at all - thats what I just said! :)

---

### Post by Paris Heng on 2007-08-11
> **explosive said:**
> No it doesn't work at all - thats what I just said! :)


ICIC, dunno who can help us!!...haih, i now doing on the wireless interface with the Ethernet.

---

### Post by explosive on 2007-08-11
*bump*

---

### Post by RandomJoe on 2007-08-11
Do you *need* to use bridging?  That is not necessary just to get network access.

Bridging makes both segments of physical connection look like a single connection.  While that does have its uses - I have that setup between a VPN connection and my office LAN so remote users' systems act like they are physically on the office network - it can be a bit of a pain to set up.

To get net access from your server, all you need is to enable IP routing on the machine in the middle.  I usually use Slackware for this, so I can't say for sure this is all you'll need...

The simplest form (with no firewalls in use, and no need for masquerading) is just to run the following on the machine in the middle:
```
sudo echo "1" > /proc/sys/net/ipv4/ip_forward
```

This tells the kernel to forward packets between the different interfaces on your system.  You would then tell the server to use the machine in the middle as a gateway, and packets should flow.

If you have a firewall on the box in the middle, you would of course have to configure that appropriately.

---

### Post by explosive on 2007-08-14
I have had a go at setting the system up as you said but it is still not working.

The machine in the middle is the "server". It is connected to the Internet via a wireless connection and its Ethernet port is connected to the other PC via a crossover cable.

The server machines /etc/network/interfaces:
> 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface (connects to net)
auto wlan0
iface wlan0 inet static
	address 10.20.251.200
	netmask 255.255.255.0
	network 10.20.251.0
	broadcast 10.20.251.255
	gateway 10.20.251.75
	
	#wpa stuff
	wpa-driver wext
	wpa-ssid z765treg
	wpa-ap-scan 1
	wpa-proto RSN
	wpa-pairwise CCMP
	wpa-groupwise CCMP
	wpa-key-mgmnt WPA-PSK
	wpa-psk ****************************************************


	# dns-* options are implemented by the resolvconf package, if installed
	dns-nameservers 212.159.6.9 212.169.6.10

auto eth0
iface eth0 inet static
address 10.20.251.201
netmask 255.255.255.0


The other PC's /etc/network/interfaces:
> 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 10.20.251.202
netmask 255.255.255.0
gateway 10.20.251.201

dns-nameservers 212.159.6.9 212.159.6.10


I have run 
> sudo echo "1" > /proc/sys/net/ipv4/ip_forward
on the server machine as you suggested but I am still not getting network access on the other PC (The server can still access the network).

---

### Post by explosive on 2007-08-15
*bump*

---

### Post by Paris Heng on 2007-08-18
> **RandomJoe said:**
> Do you *need* to use bridging?  That is not necessary just to get network access.

Bridging makes both segments of physical connection look like a single connection.  While that does have its uses - I have that setup between a VPN connection and my office LAN so remote users' systems act like they are physically on the office network - it can be a bit of a pain to set up.

To get net access from your server, all you need is to enable IP routing on the machine in the middle.  I usually use Slackware for this, so I can't say for sure this is all you'll need...

The simplest form (with no firewalls in use, and no need for masquerading) is just to run the following on the machine in the middle:
```
sudo echo "1" > /proc/sys/net/ipv4/ip_forward
```

This tells the kernel to forward packets between the different interfaces on your system.  You would then tell the server to use the machine in the middle as a gateway, and packets should flow.

If you have a firewall on the box in the middle, you would of course have to configure that appropriately.



Hi,

I ahve try the :-

```
sudo echo "1" > /proc/sys/net/ipv4/ip_forward
```

I am disable the ipv6 as well.

But things don't just get done, the **ath0 (my wireless interface) **become unrecognized and invalid when i try another approach which is Routing. 

And when i add a route to ath0 :-

**route add -net 192.168.1.1 netmask 255.255.244.0 dev ath0**

**it give unrecognized interface for ath0!!!**

Any ideas on routing?

---

### Post by paultatum on 2007-09-03
Hi,
I use slackware and kubuntu. Started using kubuntu recently, and i'm going to bridge it also. On slackware, I have a startup script that does the following:

# create a bridge
/sbin/modprobe 8139too
/sbin/modprobe via-rhine

/sbin/brctl addbr br0
/sbin/brctl addif br0 eth1
/sbin/brctl addif br0 eth2

/sbin/ifconfig eth1 0.0.0.0
/sbin/ifconfig eth2 0.0.0.0

/sbin/ifconfig br0 192.168.0.1 netmask 255.255.255.0 up

So now we just have to work out how to get ubuntu to do the same.....

Paul Tatum.

PS eth0 on this machine is the internet connection, and eth1 and eth2 are connections using direct cables with crossover plugs to form my lan of 3 machines.

---

### Post by HermanAB on 2007-09-03
You can set up a NAT router and DHCP to serve machines behind the Ubuntu box.  As a minimum you need to do this:

# Bring the ethernet ports up
ifconfig eth0 1.2.3.4 netmask 255.255.255.0 up
ifconfig eth1 4.3.2.1 netmask 255.255.255.0 up

# Enable IP forwarding
echo 1 > /proc/sys/net/ipv4/ip_forward

# Create a NAT firewall
iptables -I FORWARD -i eth0 -o eth1 -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -I FORWARD -i eth1 -o eth0 -j ACCEPT
iptables -t nat -I POSTROUTING -o eth0 -j MASQUERADE

Cheers,

H.

---

