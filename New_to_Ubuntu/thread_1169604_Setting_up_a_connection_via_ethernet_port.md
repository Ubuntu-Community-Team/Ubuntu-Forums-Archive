---
title: "Setting up a connection via ethernet port"
date: 2009-05-25
forum: New to Ubuntu
---

### Post by Andrieux on 2009-05-25
I can't figure out how to do this, so if anyone could simply tell me, or link me to a page that exists for the sole purpose of setting up a connection via ethernet port, and not a guide on every single way to connect to the internet on Ubuntu, I'd really appreciate it. I'm using Ubuntu 9.04.

Thanks...

---

### Post by dragos_iliescu_2005 on 2009-05-25
You need to specify more details about how intend to connect.
However, I'll try to give you the most simple case.
Open Network connection>>Wired. Double click on the "Auto eth0".
Select DHCP (automatic). It should work.

---

### Post by quadra on 2009-05-25
Hi, this is normally seamless. If your Ethernet interface is recognized, you should see a Network icon (on the top right panel by default).
Or go to Settings - Preferences - Network connections. 
Do you have a working router that assigns addresses on the network via DHCP?

Other problem may be a missing driver, if your ethernet card is non standard. I'd suggest you open a terminal and type
```

sudo lshw -C network
```

and paste the output here so experts may help

---

### Post by Andrieux on 2009-05-25
@dragos_iliescu_2005: That didn't work.

---

> **quadra said:**
> Hi, this is normally seamless. If your Ethernet interface is recognized, you should see a Network icon (on the top right panel by default).
Or go to Settings - Preferences - Network connections. 
Do you have a working router that assigns addresses on the network via DHCP?

Other problem may be a missing driver, if your ethernet card is non standard. I'd suggest you open a terminal and type
```

sudo lshw -C network
```and paste the output here so experts may help

Output:
```
andrew@ubuntu:~$ sudo lshw -C network
  *-network DISABLED      
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: fa:ed:6b:14:92:fc
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
andrew@ubuntu:~$
```

---

### Post by abn91c on 2009-05-25
make everything is connected properly, turn off the pc and modem/router, then reboot your router, wait 30 seconds, reboot PC if you dont get a connection then run this command in a terminal ```
sudo dhclient eth0
```

---

### Post by Andrieux on 2009-05-25
> **abn91c said:**
> make everything is connected properly, turn off the pc and modem/router, then reboot your router, wait 30 seconds, reboot PC if you dont get a connection then run this command in a terminal ```
sudo dhclient eth0
```

It didn't connect to the internet. =/.

> andrew@ubuntu:~$ sudo dhclient eth0
[sudo] password for andrew: 
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:e0:4d:0b:c5:21
Sending on   LPF/eth0/00:e0:4d:0b:c5:21
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
andrew@ubuntu:~$ I tried connecting with a 2Wire PC Port, which I use to connect on Windows, and I couldn't quite get it working with ndiswrapper. It says the driver is installed, the power light on the thing is on, but there is no internet connection.

> root@ubuntu:~/ndiswrapper-1.54/windriver# ndiswrapper -l
2wirepcp : driver installed
    device (1630:0011) present
root@ubuntu:~/ndiswrapper-1.54/windriver# 

---

### Post by quadra on 2009-05-25
Hi
From your "sudo lshw" post I see that you have only one network adaptor, "pan0" (=personal area network, something to do with Bluetooth, NOT what we need).

In a "healthy" configuration, there should be at least a network adaptor "eth0" (eth for ethernet). Example:

```
  *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: **eth0**
       version: 12
       serial: 00:21:9b:cc:73:d6
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.20 duplex=full firmware=N/A ip=192.168.1.64 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
```


So it seems Ubuntu has not found your network card.
I *think* it's not a driver issue, but the interface was not recognized at all.

Are you sure that nothing is disabled in BIOS?
(boot your PC and enter the BIOS). 
Maybe you could also find some extra information there, such as the type and manufacturer of your network interface card.

[Edit:] However in your previous post, the eth0 is found [confused!]

[Edit2:] Oh I see, your 2Wire PC Port is some special USB network adapter yea? Then what I said is not really applicable. I'm not an expert with those adaptors, sorry

---

### Post by GabeQuashnofsky on 2009-05-25
I have a similiar question.
Thanks for all the answers.

---

### Post by quadra on 2009-05-25
I think we'd need more information about your hardware
[See my edits above]

Just an observation, before in your dhclient output, it said

No DHCPOFFERS received.

**IF** your (special?) eth0 Ethernet interface works fine hardware-wise, consider that a DHCP service is needed on your network. It assigns the three vital parameters to your network interface (IP address, subnet mask, gateway). 
As an alternative to DHCP, if you are familiar with IP network configuration, you may manually set those parameters (plus the DNS server) in the entry belonging to eth0 in System - Preferences - Network connections - Wired. But DHCP is usually easier.

---

### Post by Andrieux on 2009-05-25
> **quadra said:**
> I think we'd need more information about your hardware
[See my edits above]

Just an observation, before in your dhclient output, it said

No DHCPOFFERS received.

**IF** your (special?) eth0 Ethernet interface works fine hardware-wise, consider that a DHCP service is needed on your network. It assigns the three vital parameters to your network interface (IP address, subnet mask, gateway). 
As an alternative to DHCP, if you are familiar with IP network configuration, you may manually set those parameters (plus the DNS server) in the entry belonging to eth0 in System - Preferences - Network connections - Wired. But DHCP is usually easier.

What hardware information do you need? 

The ethernet port is on a Nvidia networking controller, which (I believe) is built into the motherboard. The USB port is a 2Wire PC Port. I have a Network Everywhere Fast Ethernet 10/100 Network Card lying around, as well. Should I go ahead and put that into a PCI slot and hope for a new outcome, or would that be unlikely?

---

### Post by quadra on 2009-05-25
Yea I see. Why not try the other network card.
I'd focus on the normal cards first (easier) and unplug the 2Wire PC USB thing.
What kind of router / broadband modem is there on the other end, and does it have DHCP enabled?

I'm still confused because your lshw output doesn't show eth0 (meaning "device not existing"). But in this case, dhclient output should say "No such device".
Can you verify that the outputs of *sudo lshw -C network* and *sudo dhclient eth0* are still the same as before?

Other useful command is *ifconfig eth0*. If the connection was OK, the output must show the IP address and subnet mask as in this example:

```
eth0      Link encap:Ethernet  HWaddr 00:21:9b:cc:73:d6  
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
```

More info about these commands: *man lshw, man dhclient, man ifconfig*

In short, 
1) the ethernet device eth0 needs to be there (use *sudo lshw*), 
2) there should be a DHCP service (use *sudo dhclient eth0*), otherwise manual config, 
3) the overall config must be OK (use *ifconfig eth0*)

---

### Post by Andrieux on 2009-05-25
Here:
> andrew@ubuntu:~$ sudo lshw -C network
[sudo] password for andrew: 
  *-network DISABLED      
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 12:2b:ae:4e:97:e5
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes> andrew@ubuntu:~$ sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:e0:4d:0b:c5:21
Sending on   LPF/eth0/00:e0:4d:0b:c5:21
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
> andrew@ubuntu:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:e0:4d:0b:c5:21  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Base address:0xe000 

andrew@ubuntu:~$ 

Here's /etc/network/interface; I don't if it helps with anything, but I read somewhere it has something to do with connecting to the internet. Idk though.

> auto lo
iface lo inet loopback

---

### Post by procras on 2009-05-25
To check if your ethernet port is recognised by the kernel check the messages log after booting.
$ dmesg | grep eth0
[    3.448829] eth0: VIA Networking Velocity Family Gigabit Ethernet Adapter

If your ethernet port is recognised your should be able to configure it using
$ ifconfig eth0 up
$ ifconfig eth0 IPADD
WHERE IPADD is the address you want it to have. The system will set the netmask for you usually. 
You may need to add a route command check your routes with 
$ route -n
Add the default gateway with
$ route add default gw 192.168.1.254 eth0
Where 192.168.1.254 is the IP address of your default gw.

If that works set up your dns resolvers by editing /etc/resolv.conf

---

### Post by quadra on 2009-05-25
Hi procras, thanks for helping
Not everything is clear to me, but one problem seems that there is no working DHCP service ("No DHCPOFFERS received."), so your eth0 is UP but it has no IP address.
Andrieux, would you simply like to have a default simple ethernet setup, with connection to the internet? Then, best is check if DHCP is enabled on your router/modem.
Otherwise, the above commands (IPADD, route) will be helpful for advanced manual config.

To clarify:
- What router/modem (manufacturer / type) do you use for your LAN and internet connection, and does it provide DHCP
- What entries do you see in System - Preferences - Network connections - Wired

---

### Post by Andrieux on 2009-05-26
> **quadra said:**
> Hi procras, thanks for helping
Not everything is clear to me, but one problem seems that there is no working DHCP service ("No DHCPOFFERS received."), so your eth0 is UP but it has no IP address.
Andrieux, would you simply like to have a default simple ethernet setup, with connection to the internet? Then, best is check if DHCP is enabled on your router/modem.
Otherwise, the above commands (IPADD, route) will be helpful for advanced manual config.

To clarify:
- What router/modem (manufacturer / type) do you use for your LAN and internet connection, and does it provide DHCP
- What entries do you see in System - Preferences - Network connections - Wired

Modem: 2Wire Homeportal 1100; how do I check if it provides DHCP?
There aren't any entries in Network Connections anymore, and it won't let be add any.

---

### Post by procras on 2009-05-26
According to [http://www.shopping.com/xPF-2Wire-HomePortal-1100]("http://www.shopping.com/xPF-2Wire-HomePortal-1100") this is an ADSL router which features a DHCP server. Many routers have the option to turn off the DHCP server in the web interface.

Ensure you have plugged an ethernet cable (cat 5e) from your ethernet card on your PC into the router. Ensure this is not a patch cable with crossed wires, some routers wont allow patch (cross over cables). Your ethernet port should show some lights when it is connected. Ensure that you have plugged the cable into the correct RJ-45 socket on the router (look for a label saying ethernet or LAN). Any traffic between the PC and the router should usually be visible as flashing lights on the modem.

Check the manual that comes with the router of if lost look on internet to find out the IP address range it uses often 
192.168.0.[0-255]
or 
192.168.1.[0-255]
or
10.X.Y.[0-255]
The router's IP address is usually something like
192.168.1.254
You need this address if you want to ping the router or connect to its administration software.

When the cables are plugged in look for flashing.
Configure your ethernet address 
$ sudo ifconfig eth0 X.Y.Z.A
$ sudo route add default gateway P.Q.R.S eth0

and then ping your router etc.

According to [http://http://support.2wire.com/?page=view&article=25&text=manual&cat=&sort=]("http://http://support.2wire.com/?page=view&article=25&text=manual&cat=&sort=")
This routers default settings are.

Static: 192.168.1.1 - .63
Dynamic: 192.168.1.64 - .250
Reserved: 192.168.1.251-.253
Subnet: 255.255.255.0
Default Gateway: 192.168.1.254
DNS: 192.168.1.254
CIDR: 192.168.1.0/24 

You could use192.168.1.1 for the network card on your PC and try to ping the modem at 192.168.1.254

---

### Post by andrawloo on 2009-07-06
I have the same problems. The NetWorkManager keep sayiing: device not manage and nothing else I can do. 
 
It seems that the net devices are disappeared.
 
I 'm use Ubuntu9.04, but I have repair it by cleared the /etc/networtk/interfaces and reboot.

---

