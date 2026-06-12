---
title: "Multi-Homed IP Aliases within the Same Subnet"
date: 2008-02-08
forum: Networking &amp; Wireless
---

### Post by rvjcallanan on 2008-02-08
I have a very unusual Ubuntu 6.06 LTS Server Edition configuration requirement.

I use this box as an Imaging Server i.e. a repository for disk images which can be pushed to (and pulled from) the server using special purpose network boot disks on the client side. These network boot disks use a DHCP address if available but will fall back to a ZeroConf/LinkLocal/APIPA address in the 169.254.*.* range if a DHCP Server is not available.

In order to match the addressing requirements of the client, my Imaging Server is assigned a static IP address in the local subnet range but has a "fallback" address alias of 169.254.0.113 (within the ZeroConf range not used by the client). This configuration has been a great success and has been working reliably for some time now.

Having recently added a second subnet to my network, I needed to convert my Imaging Server into a multi-homed system by adding a second NIC. Unfortuately, my fallback addresses will no longer work because the aliases for each NIC are within the same subnet and the server IP layer is obviously confused. 

I have provided an exerpt from /etc/network/interfaces below. The eth0 entries worked fine in the single-homed case.

I do not want to use a bridging or bonding solution as the two subnets must be distinct at Layer 2.

I need a Layer 3/routing solution which will only come into play when the fallback adresses are used. 

Any expert help would be appreciated.

Here are relevant entries from my /etc/network/interfaces file:

auto eth0
iface eth0 inet static
    address 192.168.3.13
    netmask 255.255.255.0
    network 192.168.3.0
    broadcast 192.168.3.255
    gateway 192.168.3.1
    dns-nameservers 192.168.3.1

auto eth0:0
iface eth0:0 inet static
    address 169.254.0.113
    netmask 255.255.0.0
    network 169.254.0.0
    broadcast 169.254.255.255

auto eth1
iface eth1 inet static
    address 192.168.4.13
    netmask 255.255.255.0
    network 192.168.4.0
    broadcast 192.168.4.255

auto eth1:0
iface eth1:0 inet static
    address 169.254.0.213
    netmask 255.255.0.0
    network 169.254.0.0
    broadcast 169.254.255.255

---

### Post by rvjcallanan on 2008-02-11
Okay, I am looking at an ARP filter and bonding solution, see similar thread at:

[http://ubuntuforums.org/showthread.php?p=4309143#post4309143]("http://ubuntuforums.org/showthread.php?p=4309143#post4309143")

---

### Post by netztier on 2008-02-11
> **rvjcallanan said:**
> 
I need a Layer 3/routing solution which will only come into play when the fallback adresses are used. 

Any expert help would be appreciated.


I think you are trying to fix a cartwheel to a 24ton truck. 

Suggestion that will lead to a properly "networked" solution:
 
[LIST]
[*]leave the client networks separated at Layer 2, as you said it was required.
[*]get a router (e.g. a Linux PC), or a real hardware router to interconnect the two networks.
[*]if the DHCP service is not reliable, hit it's admin over the head with a large trout until it does, or run your own (maybe on the Linux PC acting as router?)
[*] use static adressing for the server in the *single* subnet where it lives.
[*] avoid non-routeable 169.254.0.0 /16 addresses by all means. They are meant to be link-local and.. well - are nothing but a networking kludge.
[/LIST]

In short: leave routing/networking intelligence to devices built or configured for the job, and let the servers be servers.  Where I work, we spent months to rot those multihomed servers out of the network. We did not make many new friends amongst the server teams during that phase. But we gained a lot of application stability and troubleshooting's become a lot easier since. 

What you are aiming at (fiddling with ARP etc) will lead to even more complications on the server side. Having multiple NICs within one subnet is already asking for trouble (to be solved by properr adapter teaming or bonding), but having the same subnet number (169.254.0.0 /16) on two distinct broadcast domains is dropping a match into a box of fireworks labelled "routing table".

regards

Marc

---

### Post by rvjcallanan on 2008-02-11
Marc,

Thank you for your prompt reply and wonderfully subtle metaphors :) but, to coin a well-known phrase, never judge a kludge by it's cover...

My Imaging Server is a very special exception to your otherwise valid observations. It needs to be accessible via ALL subnets on my network but cannot make any assumption about the presence or otherwise of a DHCP server. 

For example:

1. I may be imaging (or restoring) the DHCP server itself (which will be off-line during the imaging process)

2. I may be imaging (or restoring) a server on a subnet on which no DHCP server is present (all static addresses). 

3. I may be imaging (or restoring) a machine using a direct/cross-over cable or a spare switch, as would happen in lab preparation, etc.

My imaging client disks will use a DHCP address if available, otherwise they will fall back to a Zeroconf address. This behaviour was originally prompted by the requirement to be able to use an XP laptop and cross-over patch lead as an Imaging server when "on the road" (XP will fall back to APIPA/Zeroconf address in the absence of DHCP).

Fortunately, I have control of the "dynamic" range of Zeroconf addresses used by the client. Therefore I can confidently assign a "static" fall-back Zeroconf address outside this range to the Imaging Server (we are not using ZeroConf anywhere else).

I might also point-out that adding DHCP Server functionality to the Imaging Server itself is not an option as it would conflict with my normal DHCP server. Let me also emphasise that the Imaging Server must also be generally accessible on both subnets for admin tasks, file transfers, etc.

This is general-purpose solution has proven itself over time in the SINGLE-HOMED case. 

Unfortunately, the DUAL-HOMED scenario poses a problem because the fallback Zeroconf IP aliases are, by definition, on the same subnet.

I have actually obtained a working solution for the MULTI-HOMED case using arp-filter and will post details as soon as I have it fully tested.

This solution has short-comings in the general case but works for me because all image/restore connections are initiated by the client. The main shortcoming, which is observable using the server ping command, is that ARP broadcasts on the Zeroconf subnet are always transmitted on the first NIC in the routing table. You can use the ping -I option to overcome this (in the case of ping, that is).

For a 100% foolproof solution, you would need a round-robin ARP broadcast mechanism across the two interfaces but, as far as I can see, this can only be achieved with bonding/port trunking which may not be desirable for reasons already stated.

If there are any bonding/port trunking experts out there who can find a way of achieving this while keeping my normal subnets isolated then I am all ears :)

Regards,

Vincent

---

### Post by rvjcallanan on 2008-02-23
This was finally solved with a bridging solution, see:

[http://sourceforge.net/mailarchive/message.php?msg_name=003b01c86cf8%246dff8290%24c704a8c0%40HPN01X](http://sourceforge.net/mailarchive/message.php?msg_name=003b01c86cf8%246dff8290%24c704a8c0%40HPN01X)

Many thanks for help

---

