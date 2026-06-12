---
title: "Connecting to KVM's from different subnet"
date: 2014-09-10
forum: Networking &amp; Wireless
---

### Post by mduffy2 on 2014-09-10
Instead of creating a new thread I'm going to add to this one as I have the same issue.  I have a 2 node network.  Remote is running Ubuntu desktop 14.04 and the server is running 14.04 also.  I can ping out from the VM to the internet and the desktop, but I cannot ping from the desktop to the VM.

  I have edited the /etc/network/interfaces file on the **server** as described:

```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto em1
iface em1 inet manual

auto br0
iface br0 inet static
bridge_ports em1
bridge_fd 9
bridge_hello 2
bridge_maxage 12
bridge_stp off
address 192.168.1.200
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1
dns-nameservers 75.75.75.75 75.75.76.76

********

Server ifconfig is:

br0       Link encap:Ethernet  HWaddr a0:48:1c:e8:54:15
          inet addr:192.168.1.200  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fdc5:1c33:9d67:0:a248:1cff:fee8:5415/64 Scope:Global
          inet6 addr: fdc5:1c33:9d67:0:ac72:e8cb:4d09:f7ee/64 Scope:Global
          inet6 addr: fe80::a248:1cff:fee8:5415/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4967 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3341 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:494179 (494.1 KB)  TX bytes:445735 (445.7 KB)

em1       Link encap:Ethernet  HWaddr a0:48:1c:e8:54:15
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7158 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3341 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1124496 (1.1 MB)  TX bytes:445735 (445.7 KB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:2220 errors:0 dropped:0 overruns:0 frame:0
         TX packets:2220 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:215554 (215.5 KB)  TX bytes:215554 (215.5 KB)

virbr0    Link encap:Ethernet  HWaddr fe:54:00:fc:29:2a
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:241 errors:0 dropped:0 overruns:0 frame:0
          TX packets:301 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:26990 (26.9 KB)  TX bytes:36508 (36.5 KB)

vnet0     Link encap:Ethernet  HWaddr fe:54:00:fc:29:2a
          inet6 addr: fe80::fc54:ff:fefc:292a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:241 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1294 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500
          RX bytes:30364 (30.3 KB)  TX bytes:90639 (90.6 KB)
```

And brctl shows:

```
bridge name    bridge id        STP enabled    interfaces
br0        8000.a0481ce85415    no        em1
virbr0        8000.fe54004fd365    yes        vnet0
```

What am I doing wrong?

Thanks for any assistance.

Mike

---

### Post by mduffy2 on 2014-09-11
I am new to Ubuntu.

**Setup: **I have a 2 node network. Laptop (192.168.1.x)  is running Ubuntu  desktop 14.04 and the server (192.168.1.200)  is also running 14.04. I  have configured bridge mode on the server per below.

  **Problem: **I can ping out from  the  KVM to the internet and to  the desktop, but I cannot ping from the  desktop to the VM.

  I have edited the /etc/network/interfaces file on the **server** as described:

**/etc/network/interfaces**

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto em1
iface em1 inet manual

auto br0
iface br0 inet static
bridge_ports em1
bridge_fd 9
bridge_hello 2
bridge_maxage 12
bridge_stp off
address 192.168.1.200
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1
dns-nameservers 75.75.75.75 75.75.76.76

********


[B]Server ifconfig is:
[/B]
br0       Link encap:Ethernet  HWaddr a0:48:1c:e8:54:15
          inet addr:192.168.1.200  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fdc5:1c33:9d67:0:a248:1cff:fee8:5415/64 Scope:Global
          inet6 addr: fdc5:1c33:9d67:0:ac72:e8cb:4d09:f7ee/64 Scope:Global
          inet6 addr: fe80::a248:1cff:fee8:5415/64 Scope:Link
UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4967 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3341 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:494179 (494.1 KB)  TX bytes:445735 (445.7 KB)

em1       Link encap:Ethernet  HWaddr a0:48:1c:e8:54:15
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7158 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3341 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1124496 (1.1 MB)  TX bytes:445735 (445.7 KB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:2220 errors:0 dropped:0 overruns:0 frame:0
         TX packets:2220 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:215554 (215.5 KB)  TX bytes:215554 (215.5 KB)

virbr0    Link encap:Ethernet  HWaddr fe:54:00:fc:29:2a
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:241 errors:0 dropped:0 overruns:0 frame:0
          TX packets:301 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:26990 (26.9 KB)  TX bytes:36508 (36.5 KB)

vnet0     Link encap:Ethernet  HWaddr fe:54:00:fc:29:2a
          inet6 addr: fe80::fc54:ff:fefc:292a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:241 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1294 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500
          RX bytes:30364 (30.3 KB)  TX bytes:90639 (90.6 KB)

  **Server brctl:**

bridge name    bridge id        STP enabled    interfaces
br0        8000.a0481ce85415    no        em1
virbr0        8000.fe54004fd365    yes        vnet0

**Desktop ifconfig**

eth0      Link encap:Ethernet  HWaddr 00:8c:fa:a6:9d:aa  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fdc5:1c33:9d67:0:35c8:5d50:c17c:5fba/64 Scope:Global
          inet6 addr: fdc5:1c33:9d67:0:28c:faff:fea6:9daa/64 Scope:Global
          inet6 addr: fe80::28c:faff:fea6:9daa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:732 errors:0 dropped:0 overruns:0 frame:0
          TX packets:732 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:37127 (37.1 KB)  TX bytes:37127 (37.1 KB)



Do I need to change my router config (Lynksys E1200) or is there a config change on the server that will enable the bridged server interface (em1 )to forward the packets to the VM's virtual interface?

Thanks for any assistance.

---

### Post by nerdtron on 2014-09-11
Can you edit you rpost with [noparse] ```
 
``` [/noparse] so that it is easier to read.
Let's have a couple more info to get a clearer picture here.
Also post the answer to following:
     
     Output of ifconfig on the desktop
   
     Do you have a dhcp server?
    
     what is the ifconfig output on the VM?
   
     what is the contents of /etc/network/interfaces on the VM?

      Is the server and the desktop connected to a switch?

For bridge to work, all machines, server, vm and desktop should have the same IP block. Like 192.168.1.2, 192.168.1.3, and 192.168.1.4 respectively. 
I'm thinking your VM is still NATted on the server so you can't ping from desktop to VM.

---

### Post by slickymaster on 2014-09-11
*Moved to the ***Virtualisation*** sub-forum*

---

### Post by mduffy2 on 2014-09-11
To add a bit to this.

1)  Added a static route on the router for the 192.168.122.x network using the server's IP (192.168.1.200) as the gateway.
2) Ran **tcpdump** on the server and pinged a VM (192.168.122.75) from my laptop. The ICMP request is in the dump but the message " ICMP 192.168.122.75 protocol 1 port 47807 unreachable".  The port number is different for the next request.

So the ping is getting to the server but it can't forward to the VM.

Also,  "**uvt-kvm ip test**" command yields 192.168.122.75.

Any ideas?

Thanks

Mike

---

### Post by mduffy2 on 2014-09-12
Nerdtron:  Thanks for the response.  I'm not sure how to designate the "code".  I tried the ```
 and the /code and did not work.

Yes, the VM's are on a different subnet,192.168.122.x, than the desktop and the server, 192.168.1.x.  The server has br0 set up to bridge between it and the VMs.

Below are the outputs you requested (not in code format).  I've bolded the commands.

[B]Desktop ifconfig:
[/B]
[CODE]eth0      Link encap:Ethernet  HWaddr 00:8c:fa:a6:9d:aa  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fdc5:1c33:9d67:0:28c:faff:fea6:9daa/64 Scope:Global
          inet6 addr: fe80::28c:faff:fea6:9daa/64 Scope:Link
          inet6 addr: fdc5:1c33:9d67:0:a506:f6b2:b5a6:dc19/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:5424 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5424 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:313729 (313.7 KB)  TX bytes:313729 (313.7 KB)
```

[B]VM ifconfig

[/B]```
eth0      Link encap:Ethernet  HWaddr 52:54:00:a6:95:a2  
          inet addr:192.168.122.75  Bcast:192.168.122.255  Mask:255.255.255.0
          inet6 addr: fe80::5054:ff:fea6:95a2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:82859 errors:0 dropped:4 overruns:0 frame:0
          TX packets:3905 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14442186 (14.4 MB)  TX bytes:307015 (307.0 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

[B]Server ifconfig

[/B]```
br0       Link encap:Ethernet  HWaddr a0:48:1c:e8:54:15  
          inet addr:192.168.1.200  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fdc5:1c33:9d67:0:e4f8:e07a:ec7d:f6e5/64 Scope:Global
          inet6 addr: fdc5:1c33:9d67:0:a248:1cff:fee8:5415/64 Scope:Global
          inet6 addr: fdc5:1c33:9d67:0:94da:89ef:2cdd:866c/64 Scope:Global
          inet6 addr: fe80::a248:1cff:fee8:5415/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:65969 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29556 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:39643654 (39.6 MB)  TX bytes:2453285 (2.4 MB)

em1       Link encap:Ethernet  HWaddr a0:48:1c:e8:54:15  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:136261 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29556 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:59319884 (59.3 MB)  TX bytes:2453285 (2.4 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:194 errors:0 dropped:0 overruns:0 frame:0
          TX packets:194 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15856 (15.8 KB)  TX bytes:15856 (15.8 KB)

virbr0    Link encap:Ethernet  HWaddr fe:54:00:3c:71:f3  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11274 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21695 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:726577 (726.5 KB)  TX bytes:31499696 (31.4 MB)

vnet0     Link encap:Ethernet  HWaddr fe:54:00:a6:95:a2  
          inet6 addr: fe80::fc54:ff:fea6:95a2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3934 errors:0 dropped:0 overruns:0 frame:0
          TX packets:82935 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:310933 (310.9 KB)  TX bytes:14446488 (14.4 MB)
```

[B]VM's /etc/network/interfaces

[/B]```
# The loopback network interface
auto lo
iface lo inet loopback

# Source interfaces
# Please check /etc/network/interfaces.d before changing this file
# as interfaces may have been defined in /etc/network/interfaces.d
# NOTE: the primary ethernet device is defined in
# /etc/network/interfaces.d/[B]eth0
[/B]# See LP: #1262951
source /etc/network/interfaces.d/*.cfg
```
[B]
VM's /etc/network/interfaces.d/

[/B]```
# The primary network interface
auto eth0
iface eth0 inet dhcp
```

Yes, the server and desktop are connected on a switch.  I added a static route to 198.162.122.x using the gateway of the server's IP, 192.168.1.200 and using tcpdump I see the pings (ICMP) packets from the desktop on the server but the 

[B]server tcpdump output from desktop ---> VM ping
[/B]

```
10:12:24.540909 IP mduffy-Satellite-C55-A > 192.168.122.75: ICMP echo request, id 9906, seq 65, length 64
E..T.R@.@.HU...e..zK....&..AH..T.....<...................... !"#$%&'()*+,-./01234567
10:12:24.540972 IP ubuntuserver > mduffy-Satellite-C55-A: ICMP 192.168.122.75 protocol 1 port 6826 unreachable, length 92
```

The ping is finding the server but the port is unreachable. So I looked at the server's Iptables and see in the FORWARD section the "reject-with icmp-port-unreachable"
message.  Could that be the problem?

**sudo iptables -L --line-numbers**

```
Chain INPUT (policy ACCEPT)
num  target     prot opt source               destination         
1    ACCEPT     udp  --  anywhere             anywhere             udp dpt:domain
2    ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:domain
3    ACCEPT     udp  --  anywhere             anywhere             udp dpt:bootps
4    ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:bootps

Chain FORWARD (policy ACCEPT)
num  target     prot opt source               destination         
1    ACCEPT     all  --  anywhere             192.168.122.0/24     ctstate RELATED,ESTABLISHED
2    ACCEPT     all  --  192.168.122.0/24     anywhere            
3    ACCEPT     all  --  anywhere             anywhere            
4    REJECT     all  --  anywhere             anywhere             reject-with icmp-port-unreachable
5    REJECT     all  --  anywhere             anywhere             reject-with icmp-port-unreachable

Chain OUTPUT (policy ACCEPT)
num  target     prot opt source               destination         
1    ACCEPT     udp  --  anywhere             anywhere             udp dpt:bootpc
```

---

### Post by mduffy2 on 2014-09-12
Nerdtron:

It was iptables blocking ping on the FORWARD table.  I changed the table to ACCEPT ALL and pings are working. I've got connectivity.

Is the default iptable to block pings?

Regards

Mike

---

### Post by slickymaster on 2014-09-12
@mduffy2:
I've edited all your posts in this thread, adding code tags to all because output code posted as plain text loses its formatting and parts of it sometimes turn into smileys making it difficult to read and understand. The [use of code tags]("http://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168") makes the post clean, compact and more appealing, thus getting more attention from readers.

---

### Post by nerdtron on 2014-09-12
> **mduffy2 said:**
> Nerdtron:

It was iptables blocking ping on the FORWARD table.  I changed the table to ACCEPT ALL and pings are working. I've got connectivity.

Is the default iptable to block pings?

Regards

Mike

Hmmm.. not sure why you already have iptables in place? If you are troubleshooting network setting like this, you should disable any firewall first and try to establish connectivity. You should confirm first that you can have ping back and forth on the desktop and the VM and the SERVER.

Anyway I found an issue here.
The VM is still using the NAT IP it is given.. Although the server has configured the correct bridge interface. The **VM is NOT CONFIGURED TO USE THE BRIDGE INTERFACE**.

Are you using the Virt-Manager GUI? Shutdown the VM and then configure it's network interface to use the bridge interface. See my screenshot below
[ATTACH=CONFIG]256404[/ATTACH]

Then boot your VM again. Now try ifconfig on the VM and you should see that it has an IP range similar to the Server and the Desktop with 192.168.1.xx

---

### Post by bapoumba on 2014-09-13
Consolidated posts from the same OP on the same subkect (some posts moved from another thread).

---

