---
title: "Wired network issues"
date: 2007-07-29
forum: Networking &amp; Wireless
---

### Post by Azzural on 2007-07-29
Hey I'm new to Linux and just installed Ubuntu 7.04,

The problem I'm having is that I put Ubuntu on an older computer that I had sitting around and it had no Ethernet plug so I had to go and buy one (the netgear fa311v2.)  So I installed the card and started the system and when i went into the network config and set everything up it wouldn't connect me to my wired internet, I cannot even get on to the router settings from it, even though I checked on another computer and it seems to have been given an ip address.

Thanks for your help.

---

### Post by spd106 on 2007-07-30
If the IP address you have looks like this 169.254.x.x, then it's a self-assigned address and probably won't work with your router. Try running the dhcp client from a terminal.
```
sudo dhclient eth0
```

If it times out then you seem to be unable to contact the router's dhcp server. Try checking the NIC configuration with this command.
```
sudo lshw -class network
```

Please post the results here.

---

### Post by Azzural on 2007-07-30
Hey thanks for the response,

when i type 

```
sudo dhclient eth0
```

```
There is already a pid file /var/run/dhclient.pid with pid 5487
killed old client process, removed Pid file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium .
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SI0CSIFFLAGS: Device or resource busy
SI0CSIFFLAGS: Device or resource busy
Listening on LPF/eth0/00:14:6c:8e:6a:b1
Sending on  LPF/eth0/00:14:6c:8e:6a:b1
Sending on  Socket/fallback
receive_packet failed on eth0: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
send_packet: Network is down
No CHCPOFFERS received.
No working leases in persistent database - sleeping.

```

and when i type 

```
sudo lshw -class network
```

    ```
*-network:0 DISABLED
            description: Wireless interface
            product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
            vendor: Broadcom Corporation
            physical id: d
            bus info:pci@1:0:d.0
            logical name: eth1
            version: 02
            serial: 00:11:50:95:aa:20
            width: 32 bits
            clock: 33MHz
            capabilities: bus_master ethernet physical wireless
            configuration: broadcast=yes driver=bcm43xx driververson=2.6.2-15 gener
ic latency=64 link=no multicast=yes wireless=IEEE 802.11b/g
            resources: iomemory:f4100000-f4101fff
    *-network:1 DISABLED
            description: Ethernet interface
            product: RTL-8139/8139c/8139C+
            vendor: Realtek Semiconductor Co., Ltd.
            physical id: e
            bus info: pci@01:0e.0
            logical name: eth0
            version: 10
            serial: 00:14:6c:8e:6a:b1
            size: 100MB/s
            capacity: 100MB/s
            width: 32 bits
            clock: 33MHZ
            capabilites: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 1
00bt 100bt-fd autonegotiation
            configuration: autonegotiation=on broadcast=yes drivers=8139too driververs
ion=0.9.28 duplex=full latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes
 port=MII speed=100MB/s
            resources:ioport:3000-30ff iomemory:f4120ff
```

---

### Post by spd106 on 2007-07-30
Ok, for some reason your interfaces are disabled. Network Manager should be overseeing their operation, so try clicking on the nm-applet and make sure it's enabled.

You can also try restarting network manager with this command.
```
sudo /etc/dbus.d/event.d/25NetworkManger restart
```

If that's not working, then try this and see if the status changes.
```
sudo ifup eth0
```

---

### Post by Azzural on 2007-07-31
When i type

```
sudo /etc/dbus.d/event.d/25NetworkManger restart
```

i get 

```
sudo: /etc/dbus.d/event.d/25NetworkManger: command not found
```

and when i type

```
 sudo ifup eth0
```

```
ifup: interface eth0 already configured
```

oh and "Enable Networking" is on

---

### Post by spd106 on 2007-07-31
Sorry I should have checked that command instead of typing from memory. It should be this (I cut and pasted this one), though it probably won't help.
```
sudo /etc/dbus-1/event.d/25NetworkManager restart
```

Try running this more direct command, then dhclient again
```
sudo ifconfig eth0 up
```
```
sudo dhclient eth0
```

It might also be useful to post the output of this
```
ifconfig eth0
```

---

### Post by Azzural on 2007-07-31
```
sudo ifconfig eth0 up
```
```
SIOCSIFFLAGS: Device or resource busy
```



```
sudo dhclient eth0
```
```
There is already a pid file /ver/run/dhclient.pid with pid 5766
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFFLAGS: Device or resource busy
SIOCSIFFLAGS: Device or resource busy
Listening on LPF/eth0/00:14:c:8e:6a:b1
Sending on  LPF/eth0/00:14:c:8e:6a:b1
Sending on  Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
send_packet: Network is down
receive_packet failed on eth0: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
send_packet: Network is down
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```



```
ifconfig eth0
```
```
eth0          Link encap:Ethernet       HWaddr 00:14:6C:8E:6A:B1
                 Broadcast MULTICAST   MTU:1500   Metric:1
                 RX packets:0 errors:0 dropped:0 overruns:0 frame:0
                 TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
                 collisions:0 txqueuelen:1000
                 RX bytes:0 (0.0 b)   TX bytes:0 (0.0 b)
                 Base address:0x4000              
```

if you need anything else just tell me and ill post  it :P

---

### Post by bomanizer on 2007-07-31
Ok, now this is really weird... I've had similar problems with wired networking. My wireless is a-OK, but for some reason the wired is not, for example I get "unknown host" when I try to ping a random host (like, ping [www.yahoo.com](www.yahoo.com)). Same with browsers, "host not found", etc..
I tried the suggested commands, but they dont help. For some reason it crossed my mind to check my firewall settings, so I did "sudo /etc/init.d/firestarter start" and it returned with a failure!! Ok, then I switched to wireless and after that firestarter started ok... WEIRD!

edit: the weirdness continues. My Gf has a XP laptop and It's connecting to the same router/modem just fine, but the live-cd is unable to connect with wired connection!! WEIRD! It seems that there's something very wrong with my laptop.

---

### Post by davegp on 2007-08-09
Hi all,

I've been noticing something similar to this discussion with my laptop under Ubuntu Feisty.
When the system comes back from hibernating whichever network device that is not connected is removed from NetworkManager's list of available options. For example

I reboot and have options for wired and wireless under NetworkManager. 
I choose a wireless connection and then hibernate. 
When I come out of hiberntion, NetworkManager no longer lists an option for wireless connection. 
The only way that I have been able to restore it is by a reboot. 
Restarting the nm-applet doesn't work; restarting X (Ctrl-Alt-Bksp) doesn't work.

When I check with ifconfig, I see that eth0 now refers to my wireless connection

Is the problem that NetworkManager assigns eth0 to wireless and this prevents wired from being assigned as eth0 when you plug in an ethernet cable?

davegp

---

### Post by sonydod on 2007-08-09
I got same issue, wired network cant grab an IP, it would be nice to know a resolution.
Updated some DVD software it froze when i did a reboot i could no longer connect.

---

### Post by czepluch on 2007-08-16
I've got kind of the same problem, but it says that im connected to the wired connection but i cant use the internet in any way.

Help would be nice here

---

### Post by Michael.1 on 2007-08-17
Hi, I also got the same problem after I installed latest updates. It was a week ago, and since that time I can't connect to the wired network from Ubuntu on my laptop. It can't get proper IP from DHCP. Instead, it shows 0.0.0.0. And the manual assignment of IP etc doesn't work too :(  However, the network works fine in Windows on the same machine.

---

