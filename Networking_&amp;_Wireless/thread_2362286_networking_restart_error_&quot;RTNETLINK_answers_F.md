---
title: "networking restart error &quot;RTNETLINK answers: File exists&quot;"
date: 2017-05-26
forum: Networking &amp; Wireless
---

### Post by wduizer on 2017-05-26
Hi,

After editing the /etc/network/interface file to:
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

source /etc/network/interfaces.d/*

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.x.y
        netmask 255.255.255.0
        gateway 192.168.x.254
        dns-nameservers 192.168.z.z 192.168.z.z 

I tried to restart the interface in several ways. I tried ifdown ifup, /etc/init.d/networking restart and even a reboot of the machine.
When trying the reboot the machine will not restart....
When trying to restart the service it gives the error "RTNETLINK answers: File exists"
I have tried to flush the "ip addr flush dev eth0", but no help there....

the file is wright, and the location to. When i replace static with dhcp and hash out the rest o fth config it works fine.

I'm a bit lost here....

Can anyone help me?

greetz Wim

---

### Post by TheFu on 2017-05-26
IP addresses don't have letters. They have numbers between 1 and 254. x, y, z won't work.

Also, are you positive that eth0 is the correct device?  In 16.04 the device naming method changed.

---

### Post by wduizer on 2017-05-26
some numbers are replaced by letters, we don't want to spit out to much info over the web, and yes eth0 is the one and only device which is shown in the ifconfig result so it should be correct

---

### Post by TheFu on 2017-05-26
Posting non-routable IPs aren't a security risk.  

Is there any other network device running?  Perhaps wifi?  Some google results point to having multiple gateways specified.  

The output from **route** would be helpful. Please use 'code tags' so the output lines up and is easy to read.

---

### Post by wduizer on 2017-05-26
[table="width: 500"]
[tr]
	[td]Destination[/td]
	[td]Gateway[/td]
	[td]Genmask[/td]
	[td]Flags[/td]
	[td]MSS[/td]
	[td]Window[/td]
	[td]irtt[/td]
	[td]Iface[/td]
[/tr]
[tr]
	[td]Default[/td]
	[td]192.168.x.254[/td]
	[td]0.0.0.0[/td]
	[td]UG[/td]
	[td]0[/td]
	[td]0[/td]
	[td]0[/td]
	[td]eth0[/td]
[/tr]
[tr]
	[td]192.168.x.0[/td]
	[td]*[/td]
	[td]255.255.255.0[/td]
	[td]U[/td]
	[td]0[/td]
	[td]0[/td]
	[td]0[/td]
	[td]eth0[/td]
[/tr]
[/table]

---

### Post by TheFu on 2017-05-26
Here's mine on a chromebook running Ubuntu-lite 16.04. Yours has different columns?  **ip route** and **route** show different formats, neither matches yours.

```
$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         rt1             0.0.0.0         UG    0      0        0 br0
172.22.22.0     *               255.255.255.0   U     0      0        0 br0
192.168.122.0   *               255.255.255.0   U     0      0        0 virbr0
```

Don't know if the changes in columns or capitalization means anything or not.

---

### Post by chili555 on 2017-05-26
> I'm a bit lost here....

Can anyone help me?Probably not.

Half of the computers on the entire planet have 192.168. addresses. Knowing yours or mine is meaningless, unless, of course, we are being asked to help you troubleshoot and you decline to provide requested details which are most likely critical.

Here is how nervous I am about addresses:```
3: wlp3s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether 5c:c5:d4:0e:64:a6 brd ff:ff:ff:ff:ff:ff
    inet 192.168.0.120/24 brd 192.168.0.255 scope global wlp3s0
       valid_lft forever preferred_lft forever
    inet6 2602:306:b8c8:15f8:7999:cc4a:98cd:96c2/64 scope global noprefixroute dynamic 
       valid_lft 2591537sec preferred_lft 604337sec
    inet6 fe80::e28a:5920:5ed5:d892/64 scope link 
       valid_lft forever preferred_lft forever

```There ya go! Everything I have.

Please switch to DHCP as you said and then show us:```
route -n
ifconfig
```> dns-nameservers 192.168.z.z 192.168.z.z Is this the gateway or is another computer on the network configured properly as a DNS nameserver??

---

### Post by TheFu on 2017-05-26
If DHCP works, I'd switch back to that and compare the **route** and **ip a** outputs.
The only trick is that static IPs cannot be in the same range as the DHCP server managed IP range, but must be in the same subnet.

Post the working DHCP output if you'd like help.

---

### Post by wduizer on 2017-05-28
sorry about the paranoid approach but its recommended by my superiors. The DHCP scope is in the same subnet as the static ip i'm trying to set. The DHCP scope is set to give addresses above 192.168.x.10 and the static ip i'm configuring is 192.168.x.4, so that should not be the problem.
The gateway as shown in the route table 192.168.x.254. The dns nameservers are 192.168.z.z and 192.168.z.y so not the same as the gateway and even in a different subnet but working while using DHCP because its set as a ip-helper-address in our switch

---

### Post by chili555 on 2017-05-28
Now please change back to static as above and then run:```
sudo ifdown eth0 && sudo ifup -v eth0
```The -v for verbose should give us some clues as to what's going wrong.

Do you get an address at all?> ifconfig eth0

---

### Post by wduizer on 2017-05-28
root@GDHCP-01:/home/ubuntu# sudo ifdown eth0 && sudo ifup -v eth0
Killed old client process
Internet Systems Consortium DHCP Client 4.3.3
Copyright 2004-2015 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)


Listening on LPF/eth0/b8:27:eb:40:c3:f1
Sending on   LPF/eth0/b8:27:eb:40:c3:f1
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.x.4 port 67 (xid=0x41fd96fa)
RTNETLINK answers: No such process
RTNETLINK answers: Cannot assign requested address
Parsing file /etc/network/interfaces.d/50-cloud-init.cfg
Configuring interface eth0=eth0 (inet)
/bin/run-parts --exit-on-error --verbose /etc/network/if-pre-up.d
run-parts: executing /etc/network/if-pre-up.d/ethtool
run-parts: executing /etc/network/if-pre-up.d/ifenslave
+ [ inet = meta ]
+ IF_BOND_SLAVES=
+ [  ]
+ [  ]
+ [ -z  ]
+ exit
run-parts: executing /etc/network/if-pre-up.d/vlan


/sbin/dhclient -1 -v -pf /run/dhclient.eth0.pid -lf /var/lib/dhcp/dhclient.eth0.leases -I -df /var/lib/dhcp/dhclient6.eth0.leases eth0
Internet Systems Consortium DHCP Client 4.3.3
Copyright 2004-2015 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)


Listening on LPF/eth0/b8:27:eb:40:c3:f1
Sending on   LPF/eth0/b8:27:eb:40:c3:f1
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3 (xid=0x3bd7cd1d)
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3 (xid=0x3bd7cd1d)
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8 (xid=0x3bd7cd1d)
DHCPREQUEST of 192.168.x.10 on eth0 to 255.255.255.255 port 67 (xid=0x1dcdd73b)
DHCPOFFER of 192.168.x.10 from 192.168.y.y
DHCPACK of 192.168.x.10 from 192.168.y.y
bound to 192.168.x.10 -- renewal in 272501 seconds.
/bin/run-parts --exit-on-error --verbose /etc/network/if-up.d
run-parts: executing /etc/network/if-up.d/000resolvconf
run-parts: executing /etc/network/if-up.d/ethtool
run-parts: executing /etc/network/if-up.d/ifenslave
+ [ inet = meta ]
+ [  ]
run-parts: executing /etc/network/if-up.d/ip
run-parts: executing /etc/network/if-up.d/openssh-server
run-parts: executing /etc/network/if-up.d/upstart
Configuring interface eth0=eth0 (inet)
/bin/run-parts --exit-on-error --verbose /etc/network/if-pre-up.d
run-parts: executing /etc/network/if-pre-up.d/ethtool
run-parts: executing /etc/network/if-pre-up.d/ifenslave
+ [ inet = meta ]
+ IF_BOND_SLAVES=
+ [  ]
+ [  ]
+ [ -z  ]
+ exit
run-parts: executing /etc/network/if-pre-up.d/vlan
/bin/ip addr add 192.168.x.4/255.255.255.0 broadcast 192.168.x.255      dev eth0 label eth0
/bin/ip link set dev eth0   up
 /bin/ip route add default via 192.168.x.254  dev eth0 onlink
RTNETLINK answers: File exists
Failed to bring up eth0.



root@GDHCP-01:/home/ubuntu# ifconfig
eth0      Link encap:Ethernet  HWaddr b8:27:eb:40:c3:f1
          inet addr:192.168.x.10  Bcast:192.168.x.255  Mask:255.255.255.0
          inet6 addr: fe80::ba27:ebff:fe40:c3f1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:92650 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8322 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:104560607 (104.5 MB)  TX bytes:839417 (839.4 KB)

---

### Post by chili555 on 2017-05-28
> run-parts: executing /etc/network/if-pre-up.d/ifenslave
+ [ inet = meta ]
+ IF_BOND_SLAVES=
+ [ ]
+ [ ]
+ [ -z ]
+ exit
run-parts: executing /etc/network/if-pre-up.d/vlan
Is this some kind of bonding arrangement (about which I know nothing)?? I don't understand at all.

---

### Post by steeldriver on 2017-05-28
Maybe this will help?

[Custom Network Configuration With cloud-init]("http://lxd.readthedocs.io/en/latest/cloud-init/")

> Therefore, either when you create or copy a container it gets a newly rendered network configuration from a pre-defined template. cloud-init uses the network-config file to render /etc/network/interfaces.d/50-cloud-init.cfg when you first start a container. It will not react to any changes if you restart a container afterwards unless you force it.

 The default behavior is to use a DHCP client on a container's eth0 interface.
 **In order to change this you need to define your own network configuration using user.network-config key in the config dictionary which will override the default configuration (this is due to how the template is structured).**

---

