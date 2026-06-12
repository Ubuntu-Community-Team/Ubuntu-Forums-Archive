---
title: "Manually set nameserver with a static IP?"
date: 2006-08-08
forum: Networking &amp; Wireless
---

### Post by kirtfitzpatrick on 2006-08-08
My question is:
How do I set my nameserver when I connect to the network using a static IP?

I have seen many threads that tell me to set my /etc/resolve.conf to readonly.  But this will not work for me since I need to connect to a VPN for work and there is an internal DNS server there that I need to use when I am connected.  Also when I am in a coffee shop on the weekends I don't want to have to backup my /etc/resolve.conf file and change the permissions to get the nameservers from that network.  I am fine with specifying the nameserver manually for static IP, but there must be some way to automate this.  Is there a way to hook into a script that I can write when the interface goes up and down?

I have a fresh install Ubuntu 6.06 LTS and a static IP on my local wireless network.  I connect to my WEP access point through DHCP or static IP just fine.  When using DHCP the DNS is set automatically to the router 192.168.0.1 which is what I want and it works great and I have no problems.  However, When I switch to static (Assume a reboot, I haven't used DHCP in over a month) I do not get a nameserver set automagically.  When I edit the /etc/resolve.conf file manually and set the router as the nameserver after I am connected, once again, everything is fine.  I have no problems writing a script to append to that file manually but how do I run that script whenever the interface is brought up (at boot or via ifup).


# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

allow-hotplug eth1
auto eth1



# wireless - head - static
iface eth1 inet static
    wireless-ap any
    wireless-essid head
    wireless-nick LifeSupport
    wireless-enc XXXXXXXXXX
    address 192.168.0.70
    netmask 255.255.255.0
    gateway 192.168.0.1
    hostname lifesupport
    mtu 1450


# wireless - King's Coffee
# iface eth1 inet static
    # hostname lifesupport
    # address 192.168.1.189
    # netmask 255.255.255.0
    # gateway 192.168.1.254
    # mtu 1450
    # wireless-nick LifeSupport
    # wireless-essid King's Coffee Shop
    # wireless-ap 00:12:88:AF:FA:A1
    # wireless-ap any
    # wireless-channel 9
    # wireless-rate 54M

# hardline
# iface eth0 inet dhcp

# vpn
# iface tunnel inet ppp
        # provider XXXXXXXXXX

---

### Post by KLineD on 2006-08-09
Bumping this up because I have the same problem.

I have my wireless router with dhcp, the thing is that the same router gets assigned as nameserver, which I don't want because it's considerably slower than the asdl modem that also get's picked up as nameserver.

So everytime I log in I have to comment out the line in resolv.conf that sets the router ip's as nameserver.

---

