---
title: "Setting up LAN"
date: 2015-04-09
forum: Networking &amp; Wireless
---

### Post by josh124 on 2015-04-09
Hello folks,

I am trying to setup a small LAN that consists of a Dell Server and an ASA (the LAN will eventually touch the interwebs). I have ubuntu server 14.04 loaded on the server.  

I have the server connected to the ASA via serial so i can configure it through telnet (the shell) - but i am at a loss on where to start.  

*i am very new to ubuntu/linux, so go easy :)

---

### Post by elliotbeken on 2015-04-09
You need an application called Minicom, see below link to the help page

[https://help.ubuntu.com/community/Minicom](https://help.ubuntu.com/community/Minicom)

hope this helps

---

### Post by SeijiSensei on 2015-04-09
Does the device have Ethernet ports, presumably ones designed to connect to machines behind it?  If so, I'd connect the Ubuntu machine to one of the Cisco's "LAN" ports, then reboot the Ubuntu machine and see if you get an IP address via DHCP.  If so, you can talk to the device over the network rather than the serial cable.  

When the Ubuntu machine boots up, open a terminal window and type the command "ifconfig".  You should see an entry for eth0, the machine's primary Ethernet interface, and its IP address information if any.  It will look something like this:
```

eth0      Link encap:Ethernet  HWaddr 2c:27:d7:b2:a5:38  
          inet addr:192.168.1.21  Bcast:192.168.100.255  Mask:255.255.255.0
          inet6 addr: fe80::2e27:d7ff:feb2:a538/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:40572223 errors:0 dropped:149 overruns:0 frame:0
          TX packets:38052314 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:37088446905 (37.0 GB)  TX bytes:36492043522 (36.4 GB)

```

If you type the command "route -n", you'll see how your machine communicates with others on the network and upstream:
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0

```
My machine uses Ethernet broadcasts on eth0 to talk to other machines on my network subnet, 192.168.1.0-255, and uses the same method to communicate with machines whose addresses begin with 169.254, an address block used by Windows machines by default.  Any other traffic (destination 0.0.0.0) it sends to a "gateway" router with the address 192.168.1.1.  That's a router connected to the Internet.  If your device is set up to work as a gateway, you'll see its address instead.

You can then talk to the ASA device with the command "telnet ip.addr.of.gateway" like "telnet 192.168.1.1" in my case.

If your device has enough Ethernet ports to support all your users, you need only plug their machines into the device as well.  For more users, you would need an [Ethernet switch]("http://www.newegg.com/Switches/SubCategory/ID-30") that you would "daisy chain" to the back of the ASA device.

---

