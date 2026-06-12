---
title: "trouble connecting windows pc to server"
date: 2015-10-03
forum: Networking &amp; Wireless
---

### Post by ash_law on 2015-10-03
Hi All,

I have a simple server which was previously installed with suse linux enterprise server (but as costs got higher it had to go); so I have installed the latest version of ubuntu server 15.04 and have installed the gui desktop.

I am running BT fibre with the HomeHub 4 and I have 1 windows box attached to the server via ethernet (2 x NIC cards).

The internet works fine on the server but all attempts to get the internet / network / server talking to windows / vice versa have failed.

when i load up the network app on the server for the server NIC - it gives me the hardware address; ipv4 address; ipv6 address and the default route but when I click on options for this NIC it says "error editing connection. did not find connection with UUID '(null').

I would prefer the windows box to be auto dhcp but even adding static addresses does not work.

The NIC that is attatched to the windows box on the server shows only a hardware address and options brings up editing wire connection.

Any ideas what I need to install or do please?

---

### Post by TheFu on 2015-10-03
15.04 support ends in January. It is less-than-idea choice for a server.  14.04 is the current LTS release which gets 5 yrs of support.  15.10 will be released in a few weeks and will be supported until May-ish 2016. [https://www.ubuntu.com/info/release-end-of-life](https://www.ubuntu.com/info/release-end-of-life) explains. 

Server networking needs to be managed by editing the /etc/network/interface file.  Please post that.
For the Windows machine - I'd use "dhcp reservations" - which is set by the DHCP server on the network.  Most home routers support this mode: [http://blog.jdpfu.com/2011/07/18/use-your-router-to-centralize-your-network-device-management](http://blog.jdpfu.com/2011/07/18/use-your-router-to-centralize-your-network-device-management) explains. This way, all your devices, even portable ones, have static IPs when at home. That is very convenient.

For other troubleshooting from Linux, copy/paste the output from:
* ifconfig
* route
* sudo lshw -C network
back here within "code tags" (so things line up and are easy to read). Adv Reply has a button for this.

Network connectivity troubleshooting Guide: [http://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking](http://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking)

Also - you didn't say which protocols you wanted these machines to use.  ssh? http? sftp? something else?

---

### Post by ash_law on 2015-10-04
Hi,

source /etc/network/interfaces.d/*

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp


ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:40:f4:59:3b:4d  
          inet addr:192.168.1.91  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::240:f4ff:fe59:3b4d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:101518 errors:0 dropped:0 overruns:0 frame:0
          TX packets:53787 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:142745343 (142.7 MB)  TX bytes:4257614 (4.2 MB)

eth1      Link encap:Ethernet  HWaddr 00:19:66:0b:d5:2c  
          inet6 addr: fe80::219:66ff:fe0b:d52c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:583 errors:0 dropped:0 overruns:0 frame:0
          TX packets:43 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:108922 (108.9 KB)  TX bytes:7016 (7.0 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:468 errors:0 dropped:0 overruns:0 frame:0
          TX packets:468 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:57499 (57.4 KB)  TX bytes:57499 (57.4 KB)

route:

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         BThomehub.home  0.0.0.0         UG    0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0

lshw -C network:

 *-network               
       description: Ethernet interface
       product: DP83815 (MacPhyter) Ethernet Controller
       vendor: National Semiconductor Corporation
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: eth0
       version: 00
       serial: 00:40:f4:59:3b:4d
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii fibre 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=natsemi driverversion=2.1 duplex=full ip=192.168.1.91 latency=32 link=yes maxlatency=52 mingnt=11 multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:19 ioport:d800(size=256) memory:deeff000-deefffff memory:deee0000-deeeffff


The server is going to be used as back up and file storage from the windows box; is an extra firewall for the windows box; is how the internet gets to the windows box; is a mail server. I do not require remote access to the server - in fact this could be disabled.

regards,

---

### Post by TheFu on 2015-10-04
It would help if you please edited the post above and used "**code tags**" so things line up, as *previously requested*.  We are used to seeing output in specific ways.

a) DHCP on a 'server' is a waste of time. Make it static ... after you read through the rest here and try ... 
b) Can the Win machine ping 192.168.1.91?
c) having ssh access to the "server" really would be helpful for you, but whatever. That is "remote access" in the Unix world - not some remote desktop thingy, though you can have a remote desktop only accessible through an ssh connection.
d) for what you've said is the desired purpose, you'll need a more complex network setup (firewall, proxy). Both NICs will need to be connected somewhere and will need to be on different subnets (or routing will be ugly/hard).

IMHO.

I don't see anything wrong with the network that is working (eth0).  Eth1 isn't configured at all, so no surprises there either. 

You want the linux machine to be:
* router
* firewall
* mail server
* ssh server
* possibly VPN and web-proxy server.
Is this correct?

---

### Post by ash_law on 2015-10-04
Hi, sorry about the code tags being missing,

static is the way to go then.

The windows box transmit fails when pinging that address. so no, it can't ping it.

ssh for definite - and after more reading on ssh it does make sense.



You want the linux machine to be:
* router
* firewall
* mail server
* ssh server
* possibly VPN and web-proxy server.
Is this correct? 		

all of the above.

i own a business and work from home - in the early days of no server - we got hacked - so the need for an extremely secure server.

{previously i used suse and although very good and easy to set up - it became terribly expensive; i then moved on to untangle which sufficed until no when i wanted something more from the server.)

regards,

---

### Post by steeldriver on 2015-10-04
Is there a particular reason you need to set up a point-to-point connection between the Windows machine and the server? Since you have a HomeHub router, it would be much simpler just to plug both of them into that - then you won't need to worry about configuring multiple interfaces / routing between them.

---

### Post by ash_law on 2015-10-04
Hi steeldriver,

1. security

2. the router is in the lounge - connected to it is a bt powerline adaptor which connects to the server in another room; also connected to the router is the tv, bt vision box and a media centre.

3. previously we have been hacked and there is some sensitive company data that I would like kept private.

regards,

---

### Post by TheFu on 2015-10-04
Have you figured out how the hack occurred?  Adding a Linux machine isn't likely to change anything enough unless you get really, really, serious about security - usability-impacting - serious. 

Basically, if the habits don't change that allowed the hack, it won't help.

---

### Post by ash_law on 2015-10-04
Hi,

we were hacked over 4 years ago - at the time i had 1 x windows box connected to a router.

since being hacked I changed isp and installed a linux server to add the extra level of security, etc. It seems like it did the job.

Now after utilising suse and untangle, i now use the best server software on the market (or so I have been told) - ubuntu.

regards,

Hi,

In interfaces does the dns nameservers addresses have to be attached to both the NIC's or just the one (primary (internet to server) or secondary (server to windows box)?

> **TheFu said:**
> It would help if you please edited the post above and used "**code tags**" so things line up, as *previously requested*.  We are used to seeing output in specific ways.

a) DHCP on a 'server' is a waste of time. Make it static ... after you read through the rest here and try ... 
b) Can the Win machine ping 192.168.1.91?
c) having ssh access to the "server" really would be helpful for you, but whatever. That is "remote access" in the Unix world - not some remote desktop thingy, though you can have a remote desktop only accessible through an ssh connection.
d) for what you've said is the desired purpose, you'll need a more complex network setup (firewall, proxy). Both NICs will need to be connected somewhere and will need to be on different subnets (or routing will be ugly/hard)


Ok. The server is set up on the router with a static IP. ETH1 is now set up and working and I can ping the ip addresses.

However I still do not have internet or network access on the Windows Box.

Could you point me in the direction of what I should do and/or what information do you require from me?

best regards,

---

### Post by steeldriver on 2015-10-06
Since this is basically an internet connection sharing setup, AFAIK you need to configure the Ubuntu box as a gateway i.e. enable IP forwarding and create appropriate NAT rules via iptables... ?

[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

---

### Post by ash_law on 2015-10-07
has dhcp server been removed from 15.04? everytime i try to install it, it fails.

I have installed webmin and it is in the un-used modules section and will not let me install it.

i understand if dhcp3 - server isn't current but isc-dhcp-server will not install either.

Hi Ubuntu Gurus,

Having been a windows techie for years and having only dabbled with unix/linux the last couple of weeks have been a massive learning curve. I appreciate that there is a huge amount of information about ubuntu server on forums such as these and various other sites also but for some reason I am unable to connect the windows box to the ubuntu server.

I have gone through [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing) and set it up as per with a few changes in the ip addresses for my system but although I can see the server from the windows box I still cannot connect to the internet.

I have now re-installed ubuntu server - installed via dos dhcp server - installed desktop - uninstalled network manager as I intend to setup the network via iptables and have installed webmin.

I have also previously gone through the webmin setup that internet shares but to no avail.

I know both the nics in the server work as do both the nics in the windows box (although only one is used).

I am running BT Infinty - although this should not cause a problem.

(previously I have had untangle and suse linux enterprise server setup and running perfectly as a server (file server, gateway, etc) without issue)).

Any ideas anyone?

---

