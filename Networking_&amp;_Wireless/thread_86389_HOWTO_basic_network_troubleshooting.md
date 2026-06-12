---
title: "HOWTO: basic network troubleshooting"
date: 2005-11-05
forum: Networking &amp; Wireless
---

### Post by greenway on 2005-11-05
Since solving simple network related problems often means going through the same cycle of routines most of the times, I took the effort of writing down the tools and method I use for solving these kind of issues. I hope there will be more who can benefit from this effort.

**Network failure guide, basic trouble shooting**

I wrote this guide for Ethernet based network structures, routed by an Unix based router/firewall. The network might be a small home network as well as a larger office network, as long as it is Ethernet based, the same rules will apply.

This guide is written for those with some basic knowledge about tcp/ip, networking and Unix based operating systems.

contents:

[U]Hardware configuration
Ping away!
Lost network connectivity
Slow or bad connectivity
Using telnet for testing network connectivity[/U]


_Hardware configuration_

The first you want to do is make sure that your NIC is conifgured correctly and that is activated. Use

	ifconfig (-h for all available parameters)

To check if your NIC is activated and configured properly: it should have a valid IP address and it's MAC (media access control) address should be available since hosts on the LAN need this address for locating each other. Also make sure it has valid interrupt (so it doesn't creates any conflicts with other hardware devices). If all of this properly set, you are good to go!

The second thing you want to do is making sure your network structure is set up correctly. A good starting point might be checking the cables on your network. Make sure you didn't use crossover cables where you need straight-through cables and the other way around. When connecting DCE's (data communication equipment) such as routers and switches to DTE (data terminal equipment) such as NICs you will need a straight-through cable. When connecting DTE to DTE or DCE to DCE you will need a crossover cable. If you will stick to the scheme below, you should be ok.

connection             type of cable
PC to PC                crossover
switch to switch      crossover
hub to hub             crossover
PC to modem         straight-through
PC to hub              straight-through
PC to switch           straight-through

Whenever you might experience connection problems, and you are not sure if you are using the wright type of cable, try switching between crossover and straight-through.

If your link light is off and you are absolutely sure about the type of cable you are using, it might be that both hosts operate with a different duplex. There is half duplex which basically means that this NIC is not able to send and receive bits and the same time. And then there is full duplex, meaning this NIC is able to send and receive bits and the same time. These days, the most NICs available will auto negotiate the duplex with the NIC on the other side, however this doesn't apply to older NICs so it might be a good idea to check, just to be sure.

The original command on Unix based systems is:

	mii-tool (-v will give you the most available info)

A newer version of this tool is:

	eththool <nic interface>

The last one is compatible with more NICs compared to the older one. Now make sure that both NICs (which you want to get to talk to each other) have negotiated the same duplex, eater full or half. And while you at it, make sure have negotiated the same speed as well (usually 10mb/s or 100mb/s). If you locate a problem here, you can try to use either mii-tool or ethtool to force a duplex and or network speed. Unfortunately, this feature is not always supported by NICs, so you would just have try and find out. Otherwise, back to the shop and get yourself a decent, Unix/Linux compatible piece or hardware!

When your link light is on on both hosts on your network, the connected devices are connected and have negotiated a duplex and network speed, at this point the NICs should be able to talk to one another. Time to move on to the next step.

_Ping away!_

No you are sure you NICs are able to communicate with each other,let's do so! I am sure you have heard about this great, although simplistic network testing tool which goes by the distinct name &#8220;ping&#8221;. Basically, what &#8220;ping&#8221; can do is sending a Internet Control Message Protocol (ICMP) Echo packet to any host on the whole wide internet and request a corresponding echo packet reply. But first let's put it to the test on your local network. What you want to do is try to reach any host on your network with the following syntax:

	ping 192.168.1.100 (or any valid ip on your LAN)

Your ping address can either be an ip address or a host name (at this point I would stick with the raw ip addresses since your probably not yet properly connected to the internet and DNS might not yet configured properly). In the above example, I have pinged my LAN's gateway (ctrl + c to stop pinging):

ING 192.168.1.100 (192.168.1.100) 56(84) bytes of data.
64 bytes from 192.168.1.100: icmp_seq=1 ttl=64 time=0.701 ms
64 bytes from 192.168.1.100: icmp_seq=2 ttl=64 time=0.603 ms
64 bytes from 192.168.1.100: icmp_seq=3 ttl=64 time=0.578 ms
64 bytes from 192.168.1.100: icmp_seq=4 ttl=64 time=0.652 ms
64 bytes from 192.168.1.100: icmp_seq=5 ttl=64 time=0.571 ms
64 bytes from 192.168.1.100: icmp_seq=6 ttl=64 time=0.594 ms

--- 192.168.1.100 ping statistics ---
6 packets transmitted, 6 received, 0% packet loss, time 5003ms
rtt min/avg/max/mdev = 0.571/0.616/0.701/0.052 ms


Now, this output can give quite some useful information: first of all and the most important at this time is that we can connect to this host. As you will see in the statistics, 6 packets transmitted and 6 packets received meaning the hosts reacting to our requests by sending back some sort of message (this could be corresponding IMCP Echo packets or other kind of replies). 

There might be sometimes at which you would like ping to all available hosts on the network, this can be done with the following command:

	ping -b network address

This might come in handy when checking which hosts are connected to the LAN and which ones are not. Furthermore, I have used ping's broadcast function several times to get a network started when for some reason on a fresh network, hosts don't see each other's MAC addresses. In this case broadcasting on the network made the broadcasting host's MAC address available to all hosts connected to the network. 

There also might be situations in which your ping will be not be as successful as the one above. For example you might get the following output:

PING 192.168.1.75 (192.168.1.75) 56(84) bytes of data.
From 192.168.1.98 icmp_seq=1 Destination Host Unreachable
From 192.168.1.98 icmp_seq=2 Destination Host Unreachable
From 192.168.1.98 icmp_seq=3 Destination Host Unreachable

--- 192.168.1.75 ping statistics ---
6 packets transmitted, 0 received, +3 errors, 100% packet loss, time 5000ms
, pipe 3

This message is triggered by the router which knows the hosts you were trying to ping is part of valid network but it cannot be reached. There might be several reasons for this:
the host you are trying to connect to, might be turned down or disconnected from the network
the host's NIC might have the wrong duplex set, see &#8220;Hardware configuration&#8221;
You might have used wrong cables for connecting this host to the network, see &#8220;Hardware configuration&#8221;
In the case of a wireless network, your SSID or encryption keys might be incorrect

Basically whenever you are able to ping to hosts on your LAN, your LAN is working properly. But what if my connection is ok (worked through &#8220;Hardware configuration&#8221; without any problems) but ping is not happening for me? Take a look in the next section for a possible answer.

_Lost network connectivity_

So your hardware is set up properly but you are still unable to let the hosts talk with each other. This problem might have it's roots in MAC addresses (media access control). MAC addresses are hard coded hexadecimal number by which any NIC can uniquely be identified. These addresses are used for reaching hosts on local networks. Whenever you are trying to reach a hosts on your network, the hosts from which you are trying to reach the other one, must know the right MAC address. When looking up the MAC addresses known to the machine on which you are logged on, use the following command:

	arp (-h for correct syntax and parameters)

When using arp on my laptop, I get the following output:

Address                  HWtype  HWaddress           Flags Mask           Iface
192.168.1.103            ether   00:0E:A6:8C:AB:C1   C                     eth0
192.168.1.100            ether   00:0E:A6:61:BD:D6   C                     eth0

The local machine only holds on to the MAC address(es) of the NIC(s) with which it directly communicates. So on any given moment, an workstation in your LAN connected to the internet will only know the MAC address of the gateway and not of the other workstations in the LAN, unless they have been talking to each other recently. When output your arp table and it presents incomplete MAC addresses, this is most probably your issue. You can resolve this problem by first trying to ping broadcast to the entire LAN, usually this will make hosts connected pick up your MAC address. If this doesn't do the trick, try entering the MAC address manually into the arp table.

To do so, you will first need the MAC address of the NIC, this can be found with ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:00:B4:4B:0A:FD
          inet addr:192.168.1.98  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::200:b4ff:fe4b:afd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10677 errors:0 dropped:0 overruns:0 frame:18
          TX packets:9447 errors:0 dropped:0 overruns:0 carrier:0
          collisions:65 txqueuelen:1000
          RX bytes:9653849 (9.2 MiB)  TX bytes:949368 (927.1 KiB)
          Interrupt:3 Base address:0x300
The MAC address is the hexadecimal number followed by &#8220;Hwaddr&#8221;. Now you know the address, you can enter it into the arp table using the arp command:

	arp -s hostname MAC_address

_Slow or bad connectivity_

Whenever you are experiencing slow or bad connectivity, you might want to use ifconfig or ethtool for error reporting. Let's look again at ifconfig's output:

eth0      Link encap:Ethernet  HWaddr 00:00:B4:4B:0A:FD
          inet addr:192.168.1.98  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::200:b4ff:fe4b:afd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9152 errors:0 dropped:0 overruns:0 frame:18
          TX packets:8182 errors:0 dropped:0 overruns:0 carrier:0
          collisions:65 txqueuelen:1000
          RX bytes:9045646 (8.6 MiB)  TX bytes:817706 (798.5 KiB)
          Interrupt:3 Base address:0x300

The highlighted lines represents errors occurred during transmission and reception of bits from your network.

To get a more detailed error report, you can use the ethtool command:

	ethtool -S <NIC>

This might give a report like:

NIC statistics:
     rx_packets: 1669993
     tx_packets: 627631
     rx_bytes: 361714034
     tx_bytes: 88228145
     rx_errors: 0
     tx_errors: 0
     rx_dropped: 0
     tx_dropped: 0
     multicast: 0
     collisions: 0
     rx_length_errors: 0
     rx_over_errors: 0
     rx_crc_errors: 0
     rx_frame_errors: 0
     rx_fifo_errors: 0
     rx_missed_errors: 0
     tx_aborted_errors: 0
     tx_carrier_errors: 0
     tx_fifo_errors: 0
     tx_heartbeat_errors: 0
     tx_window_errors: 0
     tx_deferred: 0
     tx_single_collisions: 0
     tx_multi_collisions: 0
     tx_flow_control_pause: 0
     rx_flow_control_pause: 0
     rx_flow_control_unsupported: 0
     tx_tco_packets: 0
     rx_tco_packets: 0

Possible causes for network error:
collisions- happens when two NICs on the LAN are attempting to send data at the same time, although is a typical part of ethernet operation, it can slow the network down dramatically, a general rule of thump is that it should be below 0,1% of frames send. There single collisions after which a frame goes through and multiple collisions where several attempts are needed for a frame to come trough.
CRC errors &#8211; indicates that a frame goes through but is damaged along the way. When this kind errors occur in the absence of a high rate collisions,this usually indicates electrical noise. In this case you should inspect you cables and routers/switches.
frame errors: usually indicates a bad NIC.
FIFO and overturn errors: The number of times that the NIC was unable of handing data to its memory buffers because the data rate the capabilities of the hardware. This is usually a sign of excessive traffic.
length errors: The received frame length was less than or exceeded the Ethernet standard. This is most frequently due to incompatible duplex settings.
carrier errors: Errors are caused by the NIC card losing its link connection to the hub or switch. Check for faulty cabling or faulty interfaces on the NIC and networking equipment.

_Using telnet for testing network connectivity_

Whenever you want to test connectivity on a host at a specific port, telnet is the way to go! By default telnet connects to TCP port 23 but you can specify any you port to want, syntax:

	telnet 192.168.1.100 80

This telnet command connects to my LAN gateway on the HTTP port. telnet can be used for testing connectivity on remote hosts or the local host (by connecting to the loopback interface(127.0.0.1) or the NIC's ip address). Below you will find a example of a successful connection:

Trying 192.168.1.102...
Connected to 192.168.1.102.
Escape character is '^]'.
SSH-1.99-OpenSSH_3.4p1
^]
telnet> quit
Connection closed.

A established connection can be closed by the key combination Ctrl + ]. Besides a successful connection there are two more possible scenario's: &#8220;connection timed out&#8221; and &#8220;connection refused&#8221;.
Trying 216.10.100.12...
telnet: connect to address 216.10.100.12: Connection timed out

Trying 192.168.1.100...
telnet: connect to address 192.168.1.100: Connection refused

Usually when a &#8220;timed out&#8221; scenario occurs, you will get this message after a certain amount of time has passed. This is usually due to a non-existing or non connected host or due to a firewall which is blocking (NOT rejecting) the telnet session.

The &#8220;connection refused&#8221; scenario is usually caused by the fact that there is no server listening on the port you are trying to reach (the port is closed) or to a firewall which is rejecting the telnet session.

---

### Post by mgor on 2005-11-05
great howto, but i've got two "steps" i'd think should be included:
1) name resolution problems. check /etc/resolv.conf and see if they're pingable, etc. 
2) traceroute to see how far you get.

---

### Post by greenway on 2005-11-05
Yeah, I was considering including those issues as well. However, I was aiming only at LAN configuration. If I would include thos issues and direct the guide more to setting up a internet connection, in my opinion issues as NAT, ip forwarding and firewalls should also be included. At the moment I am writing an article for The Linux Documentation Project about setting up a decent, shared internet connection. When finished, I will post it here as well.

---

### Post by mgor on 2005-11-06
ah, okey.
maybe you should change the title to 'basic LAN network troubleshooting' then? just a thought :-)

---

### Post by jerremy-tamlin on 2006-09-13
Thanks for the great HOWTO.

I was wondering if you could answer a question about telnet?

My Uni uses telnet to grant access to the wider Internet (outside the Uni's LAN which you have to pay for) I don't know exactly how they do this but you must log in via telnet. On windows you simply telnet to gateway.myuni.edu.au and you will be asked for your student number and password. Then you have browser access to the internet.

However on Ubuntu (which is all I have now) I can log in using telnet just as I would on windows but it doesn't grant the browser access. How do I make firefox etc. go through the telnet connection?

Thanks for your help.

---

