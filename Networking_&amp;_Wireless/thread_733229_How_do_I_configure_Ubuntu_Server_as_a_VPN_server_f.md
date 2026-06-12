---
title: "How do I configure Ubuntu Server as a VPN server for virtual machines"
date: 2008-03-23
forum: Networking &amp; Wireless
---

### Post by ubuntogenius on 2008-03-23
This may be a slightly long winded question, but I want to make sure I include all the necessary info.

I am trying to set up a virtual LAN which is only accessible via a VPN connection.  Here is the setup so far...

I have placed a server in a co-location facility.  The OS on the server is Ubuntu Server 6.0.6 LTS.  I did a standard LAMP installation.  Next I installed VMware Server and created a few virtual machines.  All the VMs are Windows Server 2003 and they are all running Apache 2.0 and FileZilla FTP Server.  The VMs all work fine, as does the host server.

Currently the host server and each of the VMs has a public IP address (ie: they are all Internet facing).  I can connect to the host via HTTP, HTTPS, SSH, and FTP.  I can connect to the VMs via HTTP, FTP and RDP.  But, I see this setup as flawed from a security perspective - I would prefer to hide the VMs from the Internet by assigning private IP addresses and using the Linux host as a kind of proxy.

What I would like to do is setup a VPN server on the host so that the only way anyone can get to the VMs is via a VPN tunnel.  The exception to this would be HTTP.  I would like to configure Apache on the host to use Named Virtual Hosts to forward HTTP traffic to the appropriate VM.  This config I have done before so I know it works.  Where I am having trouble is the VPN side of things.

I have installed Poptop ([http://www.poptop.org/](http://www.poptop.org/)), which is a PPTP server solution for Linux.  It seems to work fine in the sense that I can create a new VPN connection on my WIndows PC, and connect to the host server.  When I do an ipconfig on the my Windows PC I get a new PPP connection and IP address:

PPP adapter MyServer VPN:

   Connection-specific DNS Suffix  . :
   IPv4 Address. . . . . . . . . . . : 10.28.101.100
   Subnet Mask . . . . . . . . . . . : 255.255.255.255
   Default Gateway . . . . . . . . . : 0.0.0.0

When my Windows PC has a VPN connection active and I do an ifconfig on the host, I get this:

ppp0      Link encap:Point-to-Point Protocol
             inet addr:10.28.101.1  P-t-P:10.28.101.100  Mask:255.255.255.255
             UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1396  Metric:1
             RX packets:32 errors:0 dropped:0 overruns:0 frame:0
             TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
             collisions:0 txqueuelen:3
             RX bytes:2447 (2.3 KiB)  TX bytes:98 (98.0 b)

I tried giving each of the VMs a private IP address, for example, 10.28.101.10, 10.28.101.11, etc.  But my Windows PC was unable to ping any of the VMs either by IP address or host name.

In the Poptop config file (/etc/pptpd.conf), I have configured the local IP and remote IPs as follows:

localip 10.28.101.1
remoteip 10.28.101.100-200

I suppose I have a number of questions:

1.  Is my proposed design feasible?  Is it possible to "hide" the VMs from the Internet and only allow access via VPN (except for HTTP)?
2.  Is there a problem with my configuration on either the host or the VMs?  For example, should I use NAT or Bridged networking on the VMs?  Currently I am using Bridged because each VM is using a static public IP address.
3.  Is there a better (or alternative) solution?  I am happy to use a different VPN server product.  My preference is to use one that supports the built in MS VPN client so my customers don't need to install a VPN client (eg: Cisco).

Any help would be greatly appreciated.

Cheers,

---

### Post by farahbod on 2008-03-25
[COLOR="Blue"]1. Is my proposed design feasible? Is it possible to "hide" the VMs from the Internet and only allow access via VPN (except for HTTP)?
[/COLOR]
Yep, but i think you need to set some things up on the server. All packets come from client should go the bridged network and all packets back from the VM should go through the PPP link. Check for proxyarp in the pptpd configuration. Also check for packet forwarding:
```
#cat /proc/sys/net/ipv4/ip_forward
```
There should be 1, if not run this:
```
#echo 1 > /proc/sys/net/ipv4/ip_forward
```

[COLOR="Blue"]2. Is there a problem with my configuration on either the host or the VMs? For example, should I use NAT or Bridged networking on the VMs? Currently I am using Bridged because each VM is using a static public IP address.[/COLOR]

Bridge's ok. However you can isolate those VMs on a private network with host(ubuntu).

[COLOR="Blue"]3. Is there a better (or alternative) solution? I am happy to use a different VPN server product. My preference is to use one that supports the built in MS VPN client so my customers don't need to install a VPN client (eg: Cisco).[/COLOR]

Maybe.
But pptpd works fine!


[COLOR="Blue"]I would like to configure Apache on the host to use Named Virtual Hosts to forward HTTP traffic to the appropriate VM. This config I have done before so I know it works.[/COLOR]

How did you do that?! ;-)

---

