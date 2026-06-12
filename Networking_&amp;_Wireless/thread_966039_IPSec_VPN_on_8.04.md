---
title: "IPSec VPN on 8.04?"
date: 2008-11-01
forum: Networking &amp; Wireless
---

### Post by the real omni on 2008-11-01
I'm trying to connect to my corporate intranet from home via VPN.

The VPN is set up using IPSec with DES/MD5 enc.

I've looked into VPNC and OpenVNC. Neither of those solutions work - VPNC is specific to Cisco VPN routers and OpenVNC will only connect to OpenVNC servers.

Can anyone provide me with instructions to get a non-cisco IPSec VPN configured on 8.04?

Thanks

---

### Post by the real omni on 2008-11-02
bump

---

### Post by the real omni on 2008-11-05
bump

---

### Post by paschadee on 2009-03-29
Key search terms: ubuntu intrepid ibex ipsec openswan vpn kvpnc networkmanager huawei e220 

I imagine this applies for most versions of Ubuntu. If not, bite me. I'm running 8.10.

I installed the kde-vpn-client  - [http://home.gna.org/kvpnc/](http://home.gna.org/kvpnc/) - which simplifies the use of a whole bunch of different tools. This tool works in gnome too. 

```
sudo apt-get install kvpnc
```

PPTP connections worked fine, and OpenVPN connections worked fine - these are also easily configurable in NetworkManager->VPN Connections. This tool includes some nice wizards to get you going. But because some options in IPSEC can be a bit tricky, even the latest version of the kvpnc tool (at writing, 0.9.1) couldn't manage properly some openswan options that I needed and I didn't have the time to slice up config options I know that work and punch them into a GUI, I went the manual (but automate-able route).

I found good info here:
[http://ubuntuforums.org/showthread.php?p=1781442](http://ubuntuforums.org/showthread.php?p=1781442)
[http://searchenterpriselinux.techtarget.com/tip/0,289483,sid39_gci1286413,00.html](http://searchenterpriselinux.techtarget.com/tip/0,289483,sid39_gci1286413,00.html)

I chose the OpenSWAN implementation since this is what my company uses, and we use the relatively more secure X509 certificate authentication and not PSK (pre-shared-key aka passwords). My setup is my laptop, and one of those Huawei E220 modems for mobile broadband so my IP is dynamic at worst. To get that working, I installed the driver download from here:
[https://forge.betavine.net/frs/?group_id=12&release_id=14](https://forge.betavine.net/frs/?group_id=12&release_id=14) and added my ISP connection under NetworkManager. Got the idea from here:
[http://henrikan.wordpress.com/2008/04/03/telia-3g-med-huawei-e220-och-ubuntu-710/](http://henrikan.wordpress.com/2008/04/03/telia-3g-med-huawei-e220-och-ubuntu-710/)

Pre-requisites: openswan, vpn server X509 public certificate from each server you want to tunnel to, your X509 private/public certificate pair which each vpn server is aware of.

```
sudo apt-get install openswan
```

That done, set up your local connection in ```
/etc/ipsec.conf
``` The options provided below are independent of local IP, route and interface, so should work carte-blanche.

```

# right: remote
# left: local

version 2
config setup
    klipsdebug=none
    plutodebug=none
    plutostderrlog=/var/log/ipsec.log
    nat_traversal=yes

#set some default options that both connections below will use.
#in this example we will use X509 certificates for authentication.
conn %default
    authby=rsasig
    leftrsasigkey=%cert
    rightrsasigkey=%cert
    type=tunnel
    leftcert="/etc/ipsec.d/certs/myprivatecert.pem"
    keyingtries=1
    #keylife=1200s
    #ikelifetime=1200s
    #leftcert= this needs to be YOUR PRIVATE X509 certificate that 
         #the vpn servers are aware of

#name the connection...
conn Stockholm
    auto=start
    left=%defaultroute
    rightcert="/path/to/this/vpn/servers/public/certificate.crt"
    right=1.2.3.4
    rightsubnet=10.48.0.0/16
    #left=%defaultroute. this is auto-determined at connect time. 
    #right=remote=public IP address or host-name of the vpn server with openswan
    #rightsubnet=the subnet of the internal network you want to connect to

#name the connection...
conn London
    auto=start
    left=%defaultroute
    rightcert="/path/to/this/vpn/servers/public/certificate.crt"
    right=fw-london.somecorp.com
    rightsubnet=193.188.23.0/24

#some other important options to follow...

# disable opportunistic encryption
conn block
    auto=ignore

conn private
    auto=ignore

conn private-or-clear
    auto=ignore

conn clear-or-private
    auto=ignore
conn clear
    auto=ignore

conn packetdefault
    auto=ignore
```

Feel free to copy and paste the above options and modify to get things working your way. The above options are fairly common, e.g. NAT. 

Finally, to bring the tunnels up, you need to 
```
sudo /etc/init.d/ipsec restart
```

This should say something like
```
ipsec_setup: Stopping Openswan IPsec...
ipsec_setup: Starting Openswan IPsec 2.4.12...

```

The output of ```
route
``` produces the following:

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.64.64.64     *               255.255.255.255 UH    0      0        0 ppp0
193.180.23.0    *               255.255.255.0   U     0      0        0 ppp0
10.48.0.0       *               255.255.0.0     U     0      0        0 ppp0
link-local      *               255.255.0.0     U     1000   0        0 ppp0
default         10.64.64.64     0.0.0.0         UG    0      0        0 ppp0

```

From this you can see the two routes from the rightsubnet= options are now set. i.e. the two rows beginning 193.180. and 10.48.

To close the tunnels you need to:
```
sudo /etc/init.d/ipsec stop
```

If you want to automate the tunnels to go up and down upon connect of various network interfaces, check out this post which should give you a good example to follow. [http://ubuntuforums.org/showthread.php?t=430312](http://ubuntuforums.org/showthread.php?t=430312) Look at the scripts to go in 
```
/etc/network/if-up.d
```
and
```
/etc/network/if-down.d
```
and place (links to) scripts here.

I can't adequately explain half of this stuff, but it works for me. ipsec options will be radically different depending on scenario - your mileage will vary. If it doesn't work for you - you're on your own.

---

