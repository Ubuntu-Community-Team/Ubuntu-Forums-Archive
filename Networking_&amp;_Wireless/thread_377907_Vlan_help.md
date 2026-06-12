---
title: "Vlan help"
date: 2007-03-06
forum: Networking &amp; Wireless
---

### Post by jonathan.lees on 2007-03-06
I run a school network, I purchased some switches that support VLAN's and I'd like to use this feature. I'd like to use Ubuntu as a router to save on some costs but not sure where to start. 

I'm planning on 3 Vlans to begin with. Does this mean that my Ubuntu router will need a NIC for each VLAN and then a NIC for a connection to my Servers?

Can anyone point me in the right direction.
thanks

---

### Post by dbauer3851 on 2007-03-06
Don't quote me on this but I'm fairly certain that ubuntu supports 802.1q VLAN trunking.  I know it loads a dot1q module when the default install options are used.

---

### Post by netztier on 2007-03-06
> **jonathan.lees said:**
> 
I'm planning on 3 Vlans to begin with. Does this mean that my Ubuntu router will need a NIC for each VLAN and then a NIC for a connection to my Servers?



You're nearly there. :-)

[COLOR="Silver"]DISCLAIMER: I can't tell you *how* to configure this on the ubuntu router, for I haven't done this. But I can tell you *what* can be a solution.
[/COLOR]

The general rule when running VLANs is: "one IP subnet per VLAN", i.e 

```
[FONT="Courier New"]
VLAN 10 192.168.1.0 /24
VLAN 20 192.168.2.0 /24 
VLAN 30 192.168.3.0 /24[/FONT]
```

What the router for these subnets needs is one IP interface in each of these VLANs. It is common use to use the first or last IP address in the subnet for the router. In our example this would be the .1 or the .255 each. Now what you can do is put three NICs in the ubuntu router and make each one's switchport a member of the corresponding VLAN. For example:

```
[FONT="Courier New"]
VLAN 10 has Ports 1-16,    Port  1 connects to NIC 1 of the Ubuntu router.
VLAN 20 has Ports 17-32,   Port 17 connects to NIC 2 of the Ubuntu router.
VLAN 30 has Ports 33-48,   Port 33 connects to NIC 3 of the Ubuntu router.[/FONT]
```

(Port's dont' necessarily have to be assigned block-wise, this can be done port-by-port).

Well, for three VLANs, this might be ok, but what if it's ten, or twelve? Doing it like this becomes uneconomical, a waist of switchports and NICs & cabling will start to become expensive.


What you can do is this: define one port (preferrably a gigabit port) as 802.1q Trunk and have it carry all three VLANs plus what is called the "default VLAN", which is in most cases VLAN 1. Very often vendors suggest that you shouldn't actually use VLAN1 to carry application traffic; in a simple environment, this is not relevant, but as your LAN grows, there can arise some issues. 

Then you define the gigabit NIC in the Ubuntu router also as 802.1q -Port. Now you can create a logical sub-interface per VLAN and assign the corresponding addresses to each subinterface.

Result: we have one IP interface per VLAN again, with different subnets each. They just happen to use one common physical interface.

Your servers don't need separate links to the router. Just connect them to a switch port that is in the VLAN you want them to be in and give them an IP address from the corresponding subnet.

Take care of the default route: your router's IP stack can have only one default route or "gateway" statement in /etc/network/interfaces, and this'll have to be the IP address of the  
router giving access to the internet - such as your xDSL or cable broadband router, or your ISP's router if you connect the cable modem directly to the Ubuntu Router. Should you do the latter, I suggest using a separate NIC for that purpose, to separate "internal" and "external" traffic.

Oh, and one thing: Say, you want to have the VLANs spread across the switches, i.e. VLANs 10 and 20 have member ports on Switch 1 and 2, while VLAN 30 is spread over all three of  them, you'll have to configure the ports (use gigabit ports if available) for the inter-switch-links also as 802.1q trunk ports. The advantage of only having to use one port for an inter-switch-link is the same as for the router: you save ports and cables. 

best regards

Marc

---

### Post by netztier on 2007-03-07
> **jonathan.lees said:**
> 
Can anyone point me in the right direction.


I found this to be an excellent starting point: [http://www.linuxjournal.com/article/7268](http://www.linuxjournal.com/article/7268)

In a nutshell: 
[LIST]
[*]load the **8021q** module
[*]before the (sub)interface comes up, somehow run the command **vconfig add ethX <VLAN number>**, for example with some init-scripts or pre-up statements in /etc/network/interfaces.
[*] add an **iface ...** statement per subinterface to /etc/network/interfaces [/LIST]

[SIZE="1"][COLOR="Blue"]*Edit:* the **vconfig** program is part of the package named ***vlan*** from the main repositories.[/COLOR][/SIZE]

The example given in the article says that on Debian, it can be done without running the vconfig command, and that vconfig was only needed for non-Debian distributions. I'd give it a try and if it fails, add the vconfig statements afterwards. I'll try some of this myself when I find some spare time and a 802.1q capable switch


best regards

Marc

---

### Post by jonathan.lees on 2007-03-07
Thanks Marc, an excellent response, I really appreciate it. It seems I really need to think things through carefully. At the moment I use DHCP to dish out IP's, if I subnet will I need a DHCP server in each subnet?

---

### Post by netztier on 2007-03-07
> **jonathan.lees said:**
> Thanks Marc, an excellent response, I really appreciate it. It seems I really need to think things through carefully. At the moment I use DHCP to dish out IP's, if I subnet will I need a DHCP server in each subnet?

Not necessarily.

Correct in your assumption is that there needs to be one "device" per subnet (and thus per VLAN) that is listening for the DHCPDISCOVER and DHCPREQUEST messages of the clients asking for IP addresses. These are broadcast packets and cannot leave the subnet. 

You can run the DHCP server for all subnets right on the Ubuntu router and configure it to listen to the interfaces where clients will be active. Make sure that it doesn't listen to unwanted interfaces, particularly ones that go (directly) to the Internet - if there are any.

If you want to keep your DHCP service where it is (i.e. in one of the VLANs), someone needs to help those DHCP broadcast messages across the router boundary.

Enter: the **DHCP Relay Agent**. This is a service that needs to be present in each IP subnet where DHCP is meant to serve addresses. It picks up the DHCP broadcast messages, alters a few flags and bits in the packet and forwards it as unicast to the DHCP server(s) it has been configured to know. The DHCP server(s) can detect this message as coming from a relay agent and can determine the correct DHCP scope/pool to offer an address from. They send their DHCPOFFER back to the relay agent wich then sends it back to the client.

So what you do is:

[LIST]
[*]configure your DHCP server with one scope/pool per VLAN
[*]make sure that the DHCP options such as subnet masks, default router and DNS servers match each subnet's properties.
[*]run a DHCP relay service on the Ubuntu router that listens on the interfaces connected to the DHCP-enabled VLANs/subnets [SIZE="1"](but not in the subnet where the DHCP itself server is)[/SIZE], and that forwards the DHCP messages to the IP address of the DHCP server(s).
[/LIST]

In the universe repositories, there are three  software packages called **dhcp-relay**, **dhcp3-relay** and **dhcp-helper**. Reading their descriptions, I think that dhcp-helper is easiest to use, install and configure, but you'll have to find out which one best suits your needs

best regards

Marc

---

### Post by jonathan.lees on 2007-03-07
I thought dhcp relays might come into it. I can't use DHCP on the Ubuntu router since I have a Windows domain and need to use their DHCP for DNS updates. Anyway thanks again for your time, it's definatly food for thought.

---

