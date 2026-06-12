---
title: "NetworkManager doesn't update resolv.conf"
date: 2007-01-14
forum: Networking &amp; Wireless
---

### Post by katanacb on 2007-01-14
Hello there,

I'm running Edgy Eft and am using NetworkManager to manage all of my connections to the internet (and vpn via the vpnc plugin to networkmanager)  Everything works like a charm except that networkmanager doesn't update resolv.conf with DNS entries it receives. 

The interfaces *do* get an IP address (and I can see them if I run ifconfig), but DNS information is just never updated.  Interestingly enough I get the following message in /var/log/daemon.log:

 <information>^IDHCP returned name servers but system has disabled dynamic modification! 

Of course the big question is, how to I enable dynamic modification of DNS information?  I've looked around, and installed resolvconf per some suggestions, but it still doesn't work.         ](*,) 

This happens specifically with wireless (on eth1) and vpnc (which creates a network device called tun0).  It works fine on the wired ethernet adapter eth0 (as long as I don't try to vpn).  I've seen a lot of other posts from people that get the same message but I haven't found any resolution to the problem.

Any ideas?  I can manually update resolv.conf but that is tedious since I'm on a laptop and move back and forth between networks all day long.

BTW this worked fine in dapper, so I'm really puzzled as to what changed between the 2 releases as it relates to networkmanager and configuration files.

--Chris

---

### Post by katanacb on 2007-01-25
*Bump*

---

### Post by Joenoob on 2007-01-25
Hi,

you'll be pleased to know that I am plagued with the same problem, I used a dsl-g604 dsl router and it is so daft it can't remember isp dns addresses.


Have you tried 'echo nameserver aaa.bbb.ccc.ddd /etc/resolv.conf'  with the same again for your secondary DNS? It's ugly, but so what?

Cheers

---

### Post by olejorgen on 2007-01-26
Not sure if it's exacly the same problem, but vpnc-connect fucks up my old dns here. (edgy) I don't think this happend on dapper.

> you'll be pleased to know that I am plagued with the same problem, I used a dsl-g604 dsl router and it is so daft it can't remember isp dns addresses.
Have you tried using the gateway as a dns adress?

---

### Post by finlay.thompson on 2007-02-08
I am having the same trouble !

I have a new laptop Toshiba Satellite M110, and everything "just worked", which is cool

I love the NetworkManager, so easy, and I am using the openvpn plugin. Again all this is really cool.

However: the dns settings don't get set correctly by the network manager. I also installed resolvconf, which I don;t think is the correct tool. There is something up with the network manager that has broken the DNS.

Just a thought, perhaps its the vpn plugin that is causing the trouble.

I also noticed the line:
<information>^IDHCP returned name servers but system has disabled dynamic modification! 

in the daemon.log.

Clearly that is the problem, whatever that means!

I would really appreciate a solution to this problem.

fin

---

### Post by finlay.thompson on 2007-02-08
just subscribing

---

### Post by frediE on 2007-02-08
Having the same issue.  When I use Network Manager to connect a VPN connection the DNS information is not being updated.

I checked the Network Settings (network-admin) and it just has the DNS from the wireless network.

As a workaround I just remove the DNS Server from the DNS tab and add my internal DNS server but that's a PIA.

**My VPN DNS server does not change so if there is a way to have it 'always' be the third option I wouldn't mind that either (as a workaround).  Anyone know how to do that???

Ultimately a solution to this would be great.

---

### Post by puyi on 2007-03-04
fin,

I have been unable to get my openvpn plugin to work. Do you mind sharing your settings?

I tried initiating OpenVPN from the command line (sudo openvpn --config /etc/openvpn/####.conf --log openvpn.log) but I experience at lest 50% packet loss.

> **finlay.thompson said:**
> I am having the same trouble !

I have a new laptop Toshiba Satellite M110, and everything "just worked", which is cool

I love the NetworkManager, so easy, and I am using the openvpn plugin. Again all this is really cool.

However: the dns settings don't get set correctly by the network manager. I also installed resolvconf, which I don;t think is the correct tool. There is something up with the network manager that has broken the DNS.

Just a thought, perhaps its the vpn plugin that is causing the trouble.

I also noticed the line:
<information>^IDHCP returned name servers but system has disabled dynamic modification! 

in the daemon.log.

Clearly that is the problem, whatever that means!

I would really appreciate a solution to this problem.

fin

---

### Post by Burnout on 2007-04-25
Is this bug filed? I'm also suffering from this problem.

---

### Post by frediE on 2007-05-08
well you can't say persistence pays off...

I **removed resolvconf** and it fixed the issue!!!!!

i read the def of the resolvconf package and ...sets itself up  as the intermediary between programs...
and i thought to my self... why can't NetworkManager to it by itself?  well, finds out it can.  it seems to be working perfectly now.  and surprisingly when i cat resolve.conf it tells the truth....

cat /etc/resolv.conf 
# generated by NetworkManager, do not edit!

---

### Post by Burnout on 2007-05-10
I installed the resolvconf package and it worked.

apt-get install resolvconf

Shouldn't it be a depency?

---

### Post by cez801 on 2007-05-26
I'm not sure which one of these posts to follow. The first post says they removed resolvconf and it worked and the second says they installed resolvconf and it worked.

I am on Fiesty Fawn, and by default the resolvconf is not installed. Without that package I can access my VPN at work OK, but I do not get any DNS resolution (in the meantime I have just updated my etc/hosts with the important server IP addresses).
I tried to install the resolvconf package, but then my VPN connection stopped working completely, so I have removed that.

So my question is it possible to connect to via VPN and get the DNS working on Feisty Fawn? And how can I do it?

Thanks.

---

### Post by quannum on 2007-06-04
I've got it working by installing resolvconf. It broke my VPN initially, but after rebooting it all worked.

I'm running Fesity btw.

---

### Post by ultim8 on 2007-06-04
I have the same problem.  I use openvpn to connect to work while at home, using the network-manager-openvpn plugin.  When vpn is not connected I can access any website fine.  When the vpn is connected, I can access my works website (and any internal work sites), but I can't access anything else via hostname (like [www.google.com](www.google.com)).

I tried quannum's suggestion of installing resolvconf with no luck (yes I rebooted).  It fixed the problem that I could connect to google (or any other website) while the vpn was on.  But I *could not* connect to any of my works internal sites via hostname.  So, I uninstalled resolvconf and I'm back to my original problem.

I'm running feisty.

---

### Post by clandestiny on 2008-03-30
I'm not an expert, but I'm usually willing to try anything.  I didn't get networkmanager working, but I did get resolvconf working with openvpn and wrote up everything I could think of.  It follows immediately, for the benefit of anyone who can use it.

*************************

[CENTER]DYNAMIC DNS CHANGES WITH OPENVPN ON UBUNTU CLIENT[/CENTER]


* resolvconf vs. networkmanager
* resolvconf background
* resolvconf installation and configuration
* Static DNS information for primary network interface
* resolvconf support for OpenVPN
* Final note on network adapter precedence and unusual names


1. resolvconf vs. networkmanager

I'm not sure to what extent networkmanager (aptitude related names 
network-manager, network-manager-gnome, network-manager-kde, 
knetworkmanager) can interfere with dynamic adjustment via 
resolvconf.  My original resolv.conf claimed to have been created by 
network-manager (which is a tool to aid in dhcp, wireless, pptp, and 
possibly even vpn in a desktop environment).  Since I'm not doing any 
network maintenance or configuration within the desktop environment, 
I removed all components of network-manager.  I suppose it is 
possible that it could peacefully coexist with resolvconf, but I made 
no such attempt.

I had installed the network-manager-openvpn package while 
network-manager was still installed on my ubuntu client, but DNS 
settings were never modified in connecting to or disconnecting from 
the vpn, so I pursued this avenue instead.


2. resolvconf background

During one of my upgrades from dapper through gutsy, the upgrade 
process had installed resolvconf, which had replaced my static 
resolv.conf with a symbolic link to a file dynamically generated at 
boot- and network-start time.  As I did not have the basic 
configuration set at that time, it acted to wipe out my usable 
resolv.conf and totally screw DNS, so I had removed resolvconf and 
replaced my static resolv.conf until now.  I've now done the basic 
research to make resolvconf usable and convenient.


3. resolvconf installation and configuration

Use aptitude to install the resolvconf package.  It's very simple and 
without immediate effect, except that /etc/resolv.conf will now 
become a symbolic link to /var/run/resolvconf/resolv.conf or 
/etc/resolvconf/run/resolv.conf.  I have both on my system at this 
moment, and they're both identical right down to the timestamp.  
It seems that it doesn't matter which way it's linked, as long as 
it's working.  You might want to explore the man pages on resolvconf 
and resolv.conf, as quite some complexity is possible to achieve by 
tweaking things in specific ways.

This dynamic file is generated by resolvconf automatically at network 
start.  If you use DHCP to bring up your primary network interface, 
everything should be automatic, and you may well not need to do any 
specific configuration to effect your default setup.  I, on the other 
hand, have my ubuntu machines statically set, so I needed to take an 
extra step to set the defaults.


4. Static DNS information for primary network interface

Find your primary network interface in /etc/network/interfaces.  It 
may look something like this:

```
    iface eth0 inet static
        address 192.168.0.2
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1

```
Assuming you have two nameservers, at 192.168.0.25 and 192.168.0.50, 
and your internal domain is considered to be foo.com, you would want 
to add the following two lines to the interface configuration:

```
        dns-search foo.com
        dns-nameservers 192.168.0.25 192.168.0.50

```
Once this is done, resolvconf will dynamically populate resolv.conf 
with the appropriate DNS information for eth0 every time the 
interface is brought up.


5. resolvconf support for OpenVPN

You will need two scripts (known as the "up" and "down" scripts for 
your OpenVPN connection) to handle what resolvconf needs to know.  
Sample "up" script:

```
	#!/bin/sh

	DEV=$1
	KEYPFX="foreign_option_"
	VPNDOMAIN="attheoffice.com"

	set | sed -n -e "1i search $VPNDOMAIN" \
	      -e "/^$KEYPFX/ s/^$KEYPFX.* DNS \(.*\)'/nameserver \1/p" \
		  | resolvconf -a $DEV

	resolvconf -u

```
Replace the value of VPNDOMAIN appropriately.  In the above example, 
once DNS has been modified for this connection, it allows you to 
attempt to access a host called "test" and automagically transforms 
the reference into "test.attheoffice.com" -- a useful feature.

Sample "down" script:

```
	#!/bin/sh

	DEV=$1

	resolvconf -d $DEV

	resolvconf -u

```
These scripts should be located in /etc/openvpn or wherever the .conf 
for the particular OpenVPN connection is located.

-----

To engage these scripts, you need to edit your vpn connection's .conf 
file and add this to the bottom:

```
	up /etc/openvpn/my-up-script-filename.sh
	plugin /usr/lib/openvpn/openvpn-down-root.so /etc/openvpn/my-down-script-filename.sh

```
(Adjust script filenames and locations accordingly.)

The plugin for the "down" script is necessary if your config file is 
designed to downgrade privileges (recommended -- look for statements 
in your config file keyed with the words "user" and "group".  If, for 
whatever reason, you choose to run (and continue) an OpenVPN 
connection as root, the second line above should just be:

```
    down /etc/openvpn/my-down-script-filename.sh

```
These scripts will run as you connect and disconnect the vpn to 
interleave DNS information received from the connection into your 
existing resolv.conf and remove it again on disconnect.

The above scripts were based on broader scripts I found through 
google that took into account intercepting DOMAIN and WINS 
information from the vpn server -- I opted to make the domain static, 
and WINS isn't governed by the resolver in linux, so I've ignored it.


6. Final note on network adapter precedence and unusual names

You'll find a file at /etc/resolvconf/interface-order.  Based on the 
entries in this file, to the extent you have more than one network 
interface active at the same time, this determined whose DNS 
information precedes whose.  As vpn will most likely use tap/tun, 
those should precede your default adapter type in this file.

(Note:  My default setup is to run eth0 as a leaf of a bridge (br0), 
so I can easily create dynamic tap/tun's for other purposes and 
bridge them into my Internet connection.  Adapter type "br*" was NOT 
in the interface-order file, and I needed to add it just prior to 
eth*.)

---

### Post by stream303 on 2008-03-31
A quick note since I'm not vpn savvy, but have had my share of dns issues. :)

I found that placing my isp's primary and backup dns server addresses inside the router's setup page to be the most helpful thing I've ever done, especially in mixed-os environments that use common windows-centric soho routers.  I tend to favor the dns addresses at OpenDNS.com anyway.

I'm not sure how this would affect vpn users, but since doing this with the routers, I have never had any resolv.conf problems when it comes to Linux.  (I've been editing dhclient, resolv.conf since my NetBSD days to overcome some low-end routers oddities, and got tired of that. :)

---

