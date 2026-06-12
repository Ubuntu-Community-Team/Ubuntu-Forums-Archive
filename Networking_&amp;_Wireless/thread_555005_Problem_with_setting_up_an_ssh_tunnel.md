---
title: "Problem with setting up an ssh tunnel"
date: 2007-09-19
forum: Networking &amp; Wireless
---

### Post by Biochem on 2007-09-19
I want to create a SSH tunnel between my laptop and my home network. But I  want to keep the client default route so I can access local resources. I followed the following instruction up to the point for the automation with ifup/down.
[https://help.ubuntu.com/community/SSH_VPN](https://help.ubuntu.com/community/SSH_VPN) 

However when I try to connect I receive the following message:
```
 sudo ifup tun0
Password:
Warning: Permanently added the RSA host key for IP address 'xxx.xxx.xxx.xxx' to the list of known hosts.
Enter passphrase for key '/root/.ssh/id_rsa': 
ifdown: interface tun0 not configured
RTNETLINK answers: File exists
run-parts: /etc/network/if-up.d/avahi-autoipd exited with return code 2
mount error 113 = No route to host
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)
Usage: inet_route [-vF] del {-host|-net} Target[/prefix] [gw Gw] [metric M] [[dev] If]
       inet_route [-vF] add {-host|-net} Target[/prefix] [gw Gw] [metric M]
                              [netmask N] [mss Mss] [window W] [irtt I]
                              [mod] [dyn] [reinstate] [[dev] If]
       inet_route [-vF] add {-host|-net} Target[/prefix] [metric M] reject
       inet_route [-FC] flush      NOT supported
Failed to bring up tun0.

```The /etc/network/interfaces config on my client is:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

# this is the home vpn

iface tun0 inet static
        pre-up ssh -p 26 -f -w 0:0 dynamic.domain.net 'ifdown tun0; ifup tun0'
        pre-up sleep 20
        address 192.168.123.1
        pointopoint 192.168.0.100
        netmask 255.255.255.0
        up route add -net 192.168.0.0 netmask 255.255.255.0 gw 192.168.123.1 tun0
        up route add gabriellapointe.homeip.net gw 192.168.0.100 eth0
        down route del -net 192.168.0.0 netmask 255.255.255.0 gw 192.168.123.1 tun0
        down route del gabriellapointe.homeip.net gw 192.168.0.100 eth0
```and on my server:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

iface eth0 inet static
address 192.168.0.100
netmask 255.255.255.0

auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth1 up # line maintained by pppoeconf
provider dsl-provider


auto eth0



iface eth1 inet ipv4ll

auto eth1

## This is a ssh vpn tunnel with the laptop

 iface tun0 inet static
        pre-up sleep 5
        address 192.168.0.100
        pointopoint 192.168.123.1
        netmask 255.255.255.0
        up arp -sD 192.168.123.1 eth0 pub

```The server is directly  connected to the internet and also serves as a gateway and local DHCP.
eth0 is lan
eth1 is wan

And I have no problem connecting with ssh without tunnel

Any Idea what I did wrong?

---

### Post by Biochem on 2007-09-22
Anyone?

---

### Post by bgturk on 2007-09-26
I am trying to do the same thing however I am getting stuck even earlier, on this:

 sudo ssh -w 0:0 1.2.3.4

I can't login as root into the remote machine for some reason.

---

### Post by Conradle on 2007-09-27
**bgturk,**
Have you checked your config file to see if root login is disabled?

/etc/ssh/sshd_config

---

### Post by Biochem on 2007-09-27
bgturk,
Since I'm using key authentification, aside from enabling root login, I also had to put my pub key in /root/.ssh.

---

### Post by bgturk on 2007-09-28
> **Conradle said:**
> **bgturk,**
Have you checked your config file to see if root login is disabled?

/etc/ssh/sshd_config
Yes, I have. This does not seam to be the cause of the problem. 
On this blog it is mentioned that:
> 
One issue the community documentation doesn't address is: how to log in to the machine at work as root? Since the default situation in ubuntu is to have the root password scrambled. One option is to set a password for root using:

sudo passwd

Personally, I prefer using ssh's public key authentication mechanism. First, generate a key:

home $ sudo ssh-keygen -t rsa -b 2048 -f /root/.ssh/id_vpn

[http://wouter.horre.be/node/62](http://wouter.horre.be/node/62)

However, I have just given up on this VPN SSH option as it seems to be too completed, besides it does not allow remote logins of window clients into my home SSH box anyway.
 
My purpose for wanting to use this was to make my laptop appear on my home network while I am at the university, where bittorrent is  diallowed. But for this, simple port forwarding of the releavnt bittorrent ports will do. Full VPN tunneling would have been cool but it is not really worth the trouble.

---

