---
title: "Ubuntu Router Almost..  need help pls!"
date: 2008-01-06
forum: Networking &amp; Wireless
---

### Post by Me109 on 2008-01-06
Hi and thx in advance! I've used this forums alot to help me setup my network.. But I've finally hit a wall and am looking for help! :KS
[SIZE="3"]
[COLOR="DarkOrange"]Problem:   Ubuntu server (setup as router) is not serving internet[/COLOR][/SIZE]

This is my network diagram

[IMG]http://www.jamietelford.com/bintwo/network_03.gif[/IMG]

Setup
[LIST]
[*]Ubuntu 7.10 server
[*]LAMP
[*]SSH
[*]Printer Server
[*]SAMBA with SWAT
[*]DNS server
[*]TorrentFlux
[*]mediatomb
[/LIST]

Basically it all works..  i can ping google from ubuntu..  torrentflux works..   I can connect to SAMBA from VISTA. I can SSH from vista.. Apache works.. can surf the hosted sites. Mediatomb works.. PS3 can connect the uPnP server and stream AVI's

[COLOR="DarkOrange"]Vista Acquires an IP from the dhcp server on the ubuntu router..[/COLOR]
But get the error [COLOR="Red"]"cannot access primary DNS server"[/COLOR]
when trying to resolved the lack of an internet connection..

[IMG]http://www.jamietelford.com/bintwo/prob_01.gif[/IMG]

So I'm completely stumped on what next step I can take..  here's some of the conf files

[INDENT][INDENT]root@NAS:~# cat /etc/network/interfaces
[COLOR="RoyalBlue"]# The loopback network interface
auto lo
iface lo inet loopback

# The primary incoming (external) network interface
auto eth0
iface eth0 inet dhcp

# The primary outgoing (internal) network interface
auto eth1
iface eth1 inet static
address 192.168.0.1
network 192.168.0.0
netmask 255.255.255.0
broadcast 192.168.0.255[/COLOR]

root@NAS:~# cat /etc/dhcp3/dhcpd.conf
[COLOR="RoyalBlue"]default-lease-time 600;
max-lease-time 7200;

option subnet-mask 255.255.255.0;
option broadcast-address 192.168.1.255;
option routers 192.168.1.254;
option domain-name-servers 192.168.1.1, 192.168.1.2;
option domain-name "nas.net";

subnet 192.168.0.0 netmask 255.255.255.0{
range 192.168.0.10 192.168.0.100;
range 192.168.0.150 192.168.0.200;}[/COLOR]

root@NAS:~# cat /etc/bind/named.conf.options
[COLOR="RoyalBlue"]options {
        directory "/var/cache/bind";

        forwarders {
         218.186.1.38;
         202.156.1.58;
         218.186.1.28;
         };

        auth-nxdomain no;    # conform to RFC1035
        listen-on-v6 { any; };
};[/COLOR]

root@NAS:~# host [www.google.com](www.google.com)
[COLOR="RoyalBlue"]www.google.com is an alias for [www.l.google.com](www.l.google.com).
[www.l.google.com](www.l.google.com) has address 72.14.235.147
[www.l.google.com](www.l.google.com) has address 72.14.235.99
[www.l.google.com](www.l.google.com) has address 72.14.235.104[/COLOR][/INDENT][/INDENT]

So I'm hoping that someone can point me in the right direction! Thx!

---

### Post by solar george on 2008-01-06
Can any of the machines behind the router connect to the internet?

---

### Post by chrisgibbs on 2008-01-06
Gday,

Good informative post, Pic is most helpful too. Only thing that would make the pic better is having IP addresses on it (if only for the Ubuntu Router and the Cable modem).

In saying that I think your DHCP setup could be wrong, according to your descriptions.

My understanding of your setup is the following 

Cable Modem (192.168.1.254) -> (192.168.?.?) (EXTERNAL) Ubuntu Server (192.168.0.1) (INTERNAL) -> LAN CLIENTS

For this to work the DHCP conf needs to be setup with the same subnet as the INTERNAL address IE 192.168.0.0/255.255.255.0

Change the DHCP config to the following:

[INDENT]default-lease-time 600;
max-lease-time 7200;

option subnet-mask 255.255.255.0;
option broadcast-address 192.168.0.255;
option routers 192.168.0.1;
option domain-name-servers 192.168.0.1
option domain-name "nas.net";

subnet 192.168.0.0 netmask 255.255.255.0{
range 192.168.0.10 192.168.0.100;
range 192.168.0.150 192.168.0.200;}[/INDENT]

I would also recommend setting the EXTERNAL interface as a static IP address (Makes configuration changes easier later IE port forwarding)

What does the command `netstat -r` output on the ubuntu router please?

Is the Ubuntu Router able to successfully ping an Internet address and also able to successfully do DNS lookups? [edit] Dont worry about this..... Just read the post again [/edit]

Cheers,

---

### Post by Me109 on 2008-01-06
> **solar george said:**
> Can any of the machines behind the router connect to the internet?

No not at this stage

> Good informative post, Pic is most helpful too. Only thing that would make the pic better is having IP addresses on it (if only for the Ubuntu Router and the Cable modem).

Thx.. I figure try and provide as much info as possible.. thx for the suggestion...


OK..  I've modified dhcpd.conf as you suggested and this has successfully rectified the "cannot access primary DNS server"  problem.. thumbs up to you!

so now a new problem.. it seems that the DNS server isnt resolving anything

[IMG]http://www.jamietelford.com/bintwo/prob_02.gif[/IMG]

which I confirmed through command prompt... pinged both IP and name..

as requested here is the output from 'netstat -r'

```
root@NAS:~# netstat -r
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.0.0     *               255.255.255.0   U         0 0          0 eth1
59.189.176.0    *               255.255.248.0   U         0 0          0 eth0
default         cm1.delta176.ma 0.0.0.0         UG        0 0          0 eth0
```

The IP address at the External NIC is resolved via DHCP from my ISP at this stage.. you can see the IP above..

anyhow I'm not sure about why the DNS server is not doin its thing..  so thx again for any help on this one!

---

### Post by solar george on 2008-01-06
> which I confirmed through command prompt... pinged both IP and name..
Thats not a DNS problem then.

Have you got NAT setup on the router.

---

### Post by chrisgibbs on 2008-01-06
Soalr George is correct.

NAT will need to be setup. I just figured that the cable modem would be performing the NAT.

---

### Post by Me109 on 2008-01-06
> **solar george said:**
> Thats not a DNS problem then.

Have you got NAT setup on the router.


Ahhhhh..  this is starting to connect all the dots for me...   So this is IP Masquerading right?

I'm going to try this setup..

[https://help.ubuntu.com/community/InternetConnectionSharing]("https://help.ubuntu.com/community/InternetConnectionSharing")

or

[https://help.ubuntu.com/7.10/server/C/ip-masquerading.html]("https://help.ubuntu.com/7.10/server/C/ip-masquerading.html")

I've actually tried a script previously from another post in this forum..  but its not working..  

thx again.. will post a result later 2nite..

---

### Post by Me109 on 2008-01-07
I can't for the life of me figure out how to do this..  

there is no real clear answer given on any forum post on setting up iptables and masquerading..  

I tried simple examples

```
iptables --flush
iptables -t nat --flush
iptables --delete-chain
iptables --table nat --delete-chain
iptables --table nat --append POSTROUTING --out-interface eth0 -j MASQUERADE
iptables --append FORWARD --in-interface eth1 -j ACCEPT
echo 1 > /proc/sys/net/ipv4/ip_forward
```

and many others.. but got no where...


I went back to this 'how to'

[[COLOR="RoyalBlue"]Setting up an Ubuntu Wired/Wirless Router[/COLOR]]("https://help.ubuntu.com/community/Router")

and tried the firewall code provided...

```
IPTABLES=/sbin/iptables
AWK=/usr/bin/awk
IFCONFIG=/sbin/ifconfig


# External (Internet-facing) interface
EXTIF="eth0"

# External IP address (autmatically detected)
EXTIP="`$IFCONFIG $EXTIF | $AWK /$EXTIF/'{next}//{split($0,a,":");split(a[2],a," ");print a[1];exit}'`"
 
# Internal interface
INTIF="eth1"

# Internal IP address (in CIDR notation)
INTIP="192.168.0.1/32"

# Internal network address (in CIDR notation)
INTNET="192.168.0.0/24"

# The address of anything/everything (in CIDR notation)
UNIVERSE="0.0.0.0/0"


echo "External: [Interface=$EXTIF] [IP=$EXTIP]"
echo "Internal: [Interface=$INTIF] [IP=$INTIP] [Network:$INTNET]"

echo
echo -n "Loading rules..."

# Enabling IP forwarding
echo 1 > /proc/sys/net/ipv4/ip_forward


# Clear any existing rules and set the default policy to DROP
$IPTABLES -P INPUT DROP
$IPTABLES -F INPUT 
$IPTABLES -P OUTPUT DROP
$IPTABLES -F OUTPUT 
$IPTABLES -P FORWARD DROP
$IPTABLES -F FORWARD 
$IPTABLES -F -t nat

# Delete all User-specified chains
$IPTABLES -X

# Reset all IPTABLES counters
$IPTABLES -Z

###################################################
# INPUT: Incoming traffic from various interfaces #
###################################################

# Loopback interface is valid
$IPTABLES -A INPUT -i lo -s $UNIVERSE -d $UNIVERSE -j ACCEPT


# Local interface, local machines, going anywhere is valid
$IPTABLES -A INPUT -i $INTIF -s $INTNET -d $UNIVERSE -j ACCEPT


# Remote interface, claiming to be local machines, IP spoofing, get lost
$IPTABLES -A INPUT -i $EXTIF -s $INTNET -d $UNIVERSE -j REJECT


# External interface, from any source, for ICMP traffic is valid
$IPTABLES -A INPUT -i $EXTIF -p ICMP -s $UNIVERSE -d $EXTIP -j ACCEPT


# Allow any related traffic coming back to the MASQ server in.
$IPTABLES -A INPUT -i $EXTIF -s $UNIVERSE -d $EXTIP -m state --state ESTABLISHED,RELATED -j ACCEPT


# Internal interface, DHCP traffic accepted
$IPTABLES -A INPUT -i $INTIF -p tcp --sport 68 --dport 67 -j ACCEPT
$IPTABLES -A INPUT -i $INTIF -p udp --sport 68 --dport 67 -j ACCEPT


# External interface, HTTP/HTTPS traffic allowed
$IPTABLES -A INPUT -i $EXTIF -m state --state NEW,ESTABLISHED,RELATED -p tcp -s $UNIVERSE -d $EXTIP --dport 80 -j ACCEPT
$IPTABLES -A INPUT -i $EXTIF -m state --state NEW,ESTABLISHED,RELATED -p tcp -s $UNIVERSE -d $EXTIP --dport 443 -j ACCEPT

# External interface, SSH traffic allowed
$IPTABLES -A INPUT -i $EXTIF -m state --state NEW,ESTABLISHED,RELATED -p tcp -s $UNIVERSE -d $EXTIP --dport 22 -j ACCEPT


# Catch-all rule, reject anything else
$IPTABLES -A INPUT -s $UNIVERSE -d $UNIVERSE -j REJECT


####################################################
# OUTPUT: Outgoing traffic from various interfaces #
####################################################

# Workaround bug in netfilter
$IPTABLES -A OUTPUT -m state -p icmp --state INVALID -j DROP

# Loopback interface is valid.
$IPTABLES -A OUTPUT -o lo -s $UNIVERSE -d $UNIVERSE -j ACCEPT


# Local interfaces, any source going to local net is valid
$IPTABLES -A OUTPUT -o $INTIF -s $EXTIP -d $INTNET -j ACCEPT


# local interface, MASQ server source going to the local net is valid
$IPTABLES -A OUTPUT -o $INTIF -s $INTIP -d $INTNET -j ACCEPT


# outgoing to local net on remote interface, stuffed routing, deny
$IPTABLES -A OUTPUT -o $EXTIF -s $UNIVERSE -d $INTNET -j REJECT


# anything else outgoing on remote interface is valid
$IPTABLES -A OUTPUT -o $EXTIF -s $EXTIP -d $UNIVERSE -j ACCEPT


# Internal interface, DHCP traffic accepted
$IPTABLES -A OUTPUT -o $INTIF -p tcp -s $INTIP --sport 67 -d 255.255.255.255 --dport 68 -j ACCEPT
$IPTABLES -A OUTPUT -o $INTIF -p udp -s $INTIP --sport 67 -d 255.255.255.255 --dport 68 -j ACCEPT


# Catch all rule, all other outgoing is denied and logged. 
$IPTABLES -A OUTPUT -s $UNIVERSE -d $UNIVERSE -j REJECT


###########################
# Packet Forwarding / NAT #
###########################

# ----- Begin OPTIONAL FORWARD Section -----

#Optionally forward incoming tcp connections on port 1234 to 192.168.0.100
#$IPTABLES -A FORWARD -i $EXTIF -o $INTIF -p tcp --dport 1234 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
#$IPTABLES -A PREROUTING -t nat -p tcp -d $EXTIP --dport 1234 -m state --state NEW,ESTABLISHED,RELATED -j DNAT --to 192.168.0.100:1234

# ----- End OPTIONAL FORWARD Section -----


# Accept solicited tcp packets
$IPTABLES -A FORWARD -i $EXTIF -o $INTIF -m state --state ESTABLISHED,RELATED  -j ACCEPT

# Allow packets across the internal interface
$IPTABLES -A FORWARD -i $INTIF -o $INTIF -j ACCEPT

# Forward packets from the internal network to the Internet
$IPTABLES -A FORWARD -i $INTIF -o $EXTIF -j ACCEPT

# Catch-all REJECT rule
$IPTABLES -A FORWARD -j REJECT

# IP-Masquerade
$IPTABLES -t nat -A POSTROUTING -o $EXTIF -j SNAT --to $EXTIP


echo " done."
```

And this didnt work....   


sorry guys I just can't make head or tail of this one..

---

### Post by mips on 2008-01-07
Have a look at: [http://ubuntuforums.org/showthread.php?t=111972](http://ubuntuforums.org/showthread.php?t=111972)

---

### Post by Me109 on 2008-01-08
> **mips said:**
> Have a look at: [http://ubuntuforums.org/showthread.php?t=111972](http://ubuntuforums.org/showthread.php?t=111972)

Hi Mips..  thanks for that link..  I've actually tried your script before (modified)  but still get nothing...

when i input


```
root@imacit:~# netstat -M
netstat: no support for `ip_masquerade' on this system.
```


I'm actually beginning to wonder if my initial setup is flawed..

---

### Post by mips on 2008-01-08
> **Me109 said:**
> Hi Mips..  thanks for that link..  I've actually tried your script before (modified)  but still get nothing...

when i input


```
root@imacit:~# netstat -M
netstat: no support for `ip_masquerade' on this system.
```


I'm actually beginning to wonder if my initial setup is flawed..

I'm going to assume you are using Ubuntu 7.10?
Then I'm going to tell you there is a bug in 7.10!
Then I will tell you not to worry as there is a fix!
[https://bugs.launchpad.net/ubuntu/+bug/178064](https://bugs.launchpad.net/ubuntu/+bug/178064)
[https://help.ubuntu.com/community/InternetConnectionSharing](https://help.ubuntu.com/community/InternetConnectionSharing)

Edit the "**/etc/sysctl.conf**" file and add the following lines :
```
net.ipv4.conf.default.forwarding=1
net.ipv4.conf.all.forwarding=1
```

---

### Post by Me109 on 2008-01-08
Thx mate 4 your help.. I actually made these amendments to the sysctl.conf some time ago..   I'm still playing with no dice..  I have no idea WTF is going on with this install of server..

I'm going to do some trouble shooting and trace the ip back from my connected PC to the DNS server on the Ubuntu box.. see if I can find out where the request is getting stuck.. 

so I'm not sure if its the bug in 7.10  ( i'm running x64 server)  my dhcp and bind settings..  IP Tables setup.. or something else entirely..

sigh.. if only it worked!

Thx again for your input!  cheers..

---

### Post by Me109 on 2008-01-08
ok.......

now i'm *think* i'm onto something

ok here's my connection

internet --> buffalo router --> ubuntu router -->  PC

(note the water cow is only in this loop so I can easily come to forum and post)

I run tracert [www.google.com](www.google.com) from the PC

```
tracert www.google.com

Tracing route to www.l.google.com [72.14.235.104]
over a maximum of 30 hops:

  1    <1 ms    <1 ms    <1 ms  buffalo.setup 
  2    10 ms    12 ms     9 ms  cm1.delta168.maxonline.com.sg
  3  1203 ms    19 ms     8 ms  172.20.16.65
  4    84 ms    97 ms   302 ms  172.26.16.1
  5   460 ms    97 ms    94 ms  172.20.9.209
  6    29 ms    13 ms    28 ms  203.116.6.37
  7   365 ms    40 ms   114 ms  203.118.3.228
  8   125 ms   695 ms   619 ms  pos9-0.br01.hkg05.pccwbtn.net [63.218.145.189]
  9   557 ms    64 ms    58 ms  ge12-1.br01.hkg04.pccwbtn.net [63.218.114.178]
 10   274 ms    75 ms    47 ms  google.ge13-5.br01.hkg04.pccwbtn.net [63.218.61.46]
 11   744 ms   565 ms   858 ms  64.233.175.209
 12   122 ms    64 ms    67 ms  209.85.250.88
 13    69 ms   126 ms   104 ms  209.85.250.103
 14   710 ms  1098 ms   892 ms  209.85.250.107
 15    71 ms    83 ms    76 ms  209.85.250.97
```


So I'm not sure what this means?  I guess that since I can trace google like this and the fact that tracert resolves the IP of google for the trace..  confirms that the DNS server /lookup on my Ubuntu router is in fact working?

So I'm back to looking at this IP tables / Masquerading problem or 7.10 bug..    :(

---

### Post by ICberg7 on 2008-01-30
Did you do the tracert from the server machine or from a device connected to it (on the inside of your network)?

I actually found a few "problems" in both the script located at
[http://ubuntuforums.org/showthread.php?t=111972](http://ubuntuforums.org/showthread.php?t=111972) (it's designed for a three-NIC setup)
as well as the internet connection sharing page located at
[http://help.ubuntu.com/community/InternetConnectionSharing](http://help.ubuntu.com/community/InternetConnectionSharing) (there are some typographical errors and missing steps),
so I had to make some modifications between the two in order to get a functional DHCP/NAT/DNS forwarder.


As you mentioned before, you've done the /etc/sysctl.conf fix (it only requires un-commenting a the
```
net.ipv4.conf.default.forwarding=1
```
line and adding ```
net.ipv4.conf.all.forwarding=1
``` right below it.


You were able to netstat -r earlier, so your problem with netstat -M might either be a syntax error or the fact that you're not root when you do it (sometimes *nix systems get funky when you don't sudo something that's supposed to be done by the root).

My solution does not use the dnsmaq or ipmasq tools indicated at [http://ubuntuforums.org/showthread.php?t=91370&highlight=ubuntu+server+nat+setup](http://ubuntuforums.org/showthread.php?t=91370&highlight=ubuntu+server+nat+setup) the bottom of [http://help.ubuntu.com/community/InternetConnectionSharing?highlight=%28network%29%7C%28connection%29%7C%28sharing%29](http://help.ubuntu.com/community/InternetConnectionSharing?highlight=%28network%29%7C%28connection%29%7C%28sharing%29), so if you've installed them, I'd recommend you ```
sudo apt-get remove dnsmasq ipmasq
``` to get rid of them, as they may be causing you difficulties.

**(Everything below assumes that eth1 is your external/ethernet in device and that eth0 is your internal/ethernet out device, because this is how my system is set up. Change the text below to fit your configuration)**

Before I forget, double-check and make sure that according to your DHCP configuration, everything is on the same subnet (192.168.1.x, for example), including your server machine, gateway (called the routers option in dhcpd.conf), and DNS sever.
Since your server machine is handling DNS requests (forwarding them onto your ISP's DNS), and routing functions, the ip address listed in dhcpd.conf file for these services should be that of your server.

To verify the ip address of your server, use the ifconfig command (no arguments).
To change the ip address of your server, use 
```
sudo ifconfig eth0 192.168.1.1
```
and replace 192.168.1.1 with the proper IP address.


Since it looks like your computer is plugging into a separat hardware router (the buffalo device), make sure that your linux server (and attached intranet) are on a separate subnet than the "internal" side of the buffalo device.
For example, if your buffalo router's internal IP address is set to 192.168.0.1 and your linux server is on the same subnet (192.168.0.x) or even the same address (192.168.0.1 specifically), you're going to have problems, despite the fact that both networks are on opposide sides of your linux router. It just makes masquerading and packet forwarding all screwy.
I'd recommend ofsetting the subnets and using 192.168.0.x and 192.168.1.x.


If all of this accurate, and you're still having issues, and bind9 and the dhcp server are both functional (restart the machine and watch the monitor for any errors if you have any doubt), then I'd recommend re-establishing your NAT setup.


Try running these commands:

```
sudo iptables -t NAT --flush
``` flush all chains in the NAT table of the iprouting database

```
sudo iptables -A FORWARD -i eth1 -o eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT
``` Accept all inbound packets that are part of a connection that is already established
```
sudo iptables -A FORWARD -i eth0 -o -eth1 -j ACCEPT
``` Accept all outbound packets
```
sudo iptables -A FORWARD -j LOG
``` Log all forwards
And here's the kicker, the most important command:
```
sudo iptables -t net -A POSTROUTING -o eth1 -j MASQUERADE
```
Direct all outbound traffic to the eth1 device and perform NAT masquerading on the packets.


If this doesn't get you fixed up, let us know.

---

