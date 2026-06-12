---
title: "problem with etc/network/interfaces setup"
date: 2007-08-01
forum: Networking &amp; Wireless
---

### Post by tuprox on 2007-08-01
I'm trying to setup a router with 2 NIC's.  I did an install of 6.06 and it was behind a Belkin router that had DHCP enabled.  I want to set this computer to take the place of the belkin router, so I need to figure out what IP's to use. I'd like to stick with the traditional 192.168.1.1 (gateway) for now.  
this is what my /etc/network/interfaces file looks like:

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
```

I have no wireless card so I guess I can leave the ath0 alone?

This is what I'm supposed to input from the Tutorial [here:]("http://ubuntuforums.org/showthread.php?t=376283")
```
 # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

#MY BROKEN INTERFACE (3com on-board)
#auto eth0
#iface eth0 inet dhcp
#pre-up iptables-restore < /etc/iptables.conf

# Gateway 
# You should set this to DHCP if your cable/DSL ISP provides it.
# the "pre-up" command brings up the iptables "firewall"
# it is just set to static for testing purposes.  see eth0 for DHCP setup.
auto eth1
iface eth1 inet static
address 192.168.1.17
netmask 255.255.255.0
gateway 192.168.1.1
pre-up iptables-restore < /etc/iptables.conf

#Wireless Setup
auto ath0
iface ath0 inet manual
wireless-mode master
# CHANGE ME!!! to your own ESSID
wireless-essid pivotpoint

#Bridge interface
auto br0
iface br0 inet static
    address 10.1.1.1
    network 10.1.1.0
    netmask 255.255.255.0
    broadcast 10.1.1.255
    bridge-ports eth2 ath0
```

I'm confused as to what the "Bridge interface" does and Also, they have a NIC in the machine that is broken and they did not enter data for this.  What should the addresses be for my 2nd NIC?

---

### Post by PaulFr on 2007-08-01
The tutorial you reference bridges wireless traffic (ath0) to and from a local Ethernet LAN (eth2) and also routes all this traffic to an external Ethernet WAN (eth1). See the key comments from that tutorial about the setup being discussed```
interface setup
    my eth0 is broken and on-board so I had to add a card [YMMV]
    eth1 is the WAN interface (gateway)
    eth2 is the LAN interface
    ath0 is the wireless card
    br0 is the bridged connection of ath0 and eth2
```What is your scenario ? Since you want to replace your current Belkin router, you should know what IP addresses are on its **multiple** interfaces. 192.168.1.1 would most probably be the address on one side, what is it on the other side ? Is that DHCP or do you have a static IP address there as well ?

As an example, I assume your network to be of the type >    [192.168 m/cs] <--> [192.168.1.1 i/f] [Router machine] [External i/f] <-> [Next step (cable modem)]

1. The eth0 section gives an example of an interface that gets its IP address through DHCP. Uncomment if you use DHCP to get your interface IP address from the next device (another gateway, cable modem, ISP, etc.). Assume you have a cable modem that is configured as a DHCP server, i.e. it hands out IP addresses to client machines that make such DHCP requests. Then your eth0 interface would read ```
auto eth0
    iface eth0 inet dhcp
```
2. If on the other hand, if your cable modem is not set up for DHCP, then you need to find out its IP address and netmask (say it is 192.168.100.1 and netmask is 255.255.255.0), then your entry should read```
auto eth0
    iface eth1 inet static
    address 192.168.100.2
    netmask 255.255.255.0
    gateway 192.168.100.1
```So your router machine should have a different **address** but which should be on the same subnet as your cable modem. It should have an entry for your cable modem as your default router so that all packets go to your router.

3. The eth1 section gives an example of an interface that sets its IP address statically. So for your 192.168.1.1 internal interface which you want to be static, you would put ```
auto eth1
    iface eth1 inet static
    address 192.168.1.1
    netmask 255.255.255.0
```
4. Please comment out any unnecessary interface sections by putting **#** before those lines. So the bottom part of your interfaces file should read```
# auto ath0
# iface ath0 inet dhcp

# auto wlan0
# iface wlan0 inet dhcp
```

5. I would suggest you omit the iptables line for now - first get your routing working properly, then add your firewall rules.

Hope this helps.

---

