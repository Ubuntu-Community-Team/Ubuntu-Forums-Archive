---
title: "changing eth speed"
date: 2007-02-17
forum: Networking &amp; Wireless
---

### Post by wshieh on 2007-02-17
Hello,

newbie question:

I'm trying to change the eth speed to 10Mbps by using

ethtool -s eth1 speed 10 duplex full autogen **off**

ethtool eth1 shows:
speed: 10Mb/s

but mii-tool eth1 shows:
eth1: 10Mbit ,  full duplex, no link

and the link is dead and I can't use it

if I go 
ethtool -s eth1 speed 10 duplex full autogen **on**

ethtool eth1 shows:
speed: 100Mb/s

mii-tool eth shos:
eth1: negotiated 100baseTx-FD, link ok

How can i set it to 10Mb/s ?

Thanks!

---

### Post by sdide on 2007-02-17
Hey,

If the other end is forced at 100Mbps, it doesn't help forcing your end to 10Mbps - that will 
just create "No link". When you set autoneg on, you negotiate to 100Mbps, which tells me that the other end (whatever that is), is set at 100Mbps.

To force 10Mbps, you need to make the other end either autonegotiate, or set it to 10Mbps.

---

### Post by Floppyjoe on 2007-02-17
This is probably a dumb question but why are you trying to slow it down from 100Mb/s to 10Mb/s?
Is the internet going to fast for you?:D

---

### Post by wshieh on 2007-02-17
the other end is connected to a switch

---

### Post by wshieh on 2007-02-17
> **Floppyjoe said:**
> This is probably a dumb question but why are you trying to slow it down from 100Mb/s to 10Mb/s?
Is the internet going to fast for you?:D

just doing some experiment :)

---

### Post by sdide on 2007-02-17
Hey, 

are you the administrator of that switch? 
Do you know what kind of switch it is?

---

### Post by wshieh on 2007-02-17
I have access to it. It is a cisco switch.

I configured the port to full duplex 10mb/s on this end.

I actually have 4 ethernet cards on this web server, now all of them are connected to the switch, both ends of the 4 eth are now set to 10mb/s.

There is another client with 1 eth connect to the same switch, the speed of this link is set to 100mb/s.

Now I got another problem: when I try to download big files from the server to the client, the links are experiencing some problem (i can see the cisco switch ports flashing orange lights on 3 of the ports).... and on the switch, when i turn on debug ethernet-controller address, it shows some message like this:

ADDR_FLAP:  FastEthernet0/3 relearning X addrs per min

---

### Post by sdide on 2007-02-18
Yes, 

3 of the ports would be in blocking state if you are bridging the 4 NICs to the server and have spanning tree protocol turned on (which I strongly recommend, and which is default for all VLANs on Cisco equipment.).

The addressflapping must be because the switch sees the same MAC address on different ports.

---

### Post by wshieh on 2007-02-18
How can I avoid the addressflapping? .. the 4 nics are slaves of a bond, so they all appear to have the same address
If I turn off STP, will it cause more problem?
thanks~

---

### Post by sdide on 2007-02-19
Hey. 
I need more info to answer questions about your setup.

How are the NICs configured on the server, what switch is it, and what is the configuration on the 4 ports on the switch?

---

### Post by wshieh on 2007-02-19
> **sdide said:**
> Hey. 
I need more info to answer questions about your setup.

How are the NICs configured on the server, what switch is it, and what is the configuration on the 4 ports on the switch?

Switch: Cisco Catalyst 3500 Series XL
Port 1,3,5,7 are connected to the server, 11 is connected to the client

Port    Name               Status       Vlan     Duplex Speed   Type
------- ------------------ ------------ -------- ------ ------- ----
Fa0/1                      connected    1          Full      10 100BaseTX/FX
Fa0/3                      connected    1          Full      10 100BaseTX/FX
Fa0/5                      connected    1          Full      10 100BaseTX/FX
Fa0/7                      connected    1          Full      10 100BaseTX/FX

Fa0/11                     connected    1          Full     100 100BaseTX/FX


on the server, the 4 nics:
# ethtool eth0
Settings for eth0:
        Supported ports: [ MII ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  Not reported
        Advertised auto-negotiation: No
        Speed: 10Mb/s
        Duplex: Full
        Port: MII
        PHYAD: 1
        Transceiver: external
        Auto-negotiation: off
        Supports Wake-on: g
        Wake-on: d
        Link detected: yes

# ethtool eth1
Settings for eth1:
        Supported ports: [ MII ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Half 1000baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Half 1000baseT/Full
        Advertised auto-negotiation: Yes
        Speed: 10Mb/s
        Duplex: Half
        Port: Twisted Pair
        PHYAD: 1
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: g
        Wake-on: d
        Current message level: 0x000000ff (255)
        Link detected: yes

# ethtool eth2
Settings for eth2:
        Supported ports: [ MII ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Half 1000baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Half 1000baseT/Full
        Advertised auto-negotiation: Yes
        Speed: 10Mb/s
        Duplex: Half
        Port: Twisted Pair
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: umbg
        Wake-on: g
        Current message level: 0x00000007 (7)
        Link detected: yes

# ethtool eth3
Settings for eth3:
        Supported ports: [ MII ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Half 1000baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Half 1000baseT/Full
        Advertised auto-negotiation: Yes
        Speed: 10Mb/s
        Duplex: Half
        Port: Twisted Pair
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: umbg
        Wake-on: d
        Current message level: 0x00000007 (7)
        Link detected: yes


Somehow I can't change eth1,2,3 to Full Duplex if I set the speed to 10Mb/s. 
If I set speed 10, full duplex autoneg off, the links cannot be established.

---

