---
title: "PLEASE?!? - Another HIF Bridge Static IP problem (w/ Winbind &amp; Win2KAdvSvr guest)"
date: 2008-07-26
forum: Networking &amp; Wireless
---

### Post by innovate2000 on 2008-07-26
Fellow Ubuntuers, Linux guru's and other "citizens of the world"

I have set up several SMB file servers that authenticate with Windows Active Directory servers - all is good there. I also have set up several Ubuntu/Kubuntu (host) Vbox workstations (Ubuntu Desktop Host, XP guest) with NAT networking and these too authenticate with Windows Active Directory servers. I am now trying to create Win2KAdvSvr VM servers on Ubuntu 8.04 server hosts so I can reclaim some of the physical hardware. The servers need to be seen from the network, be forwardable (static IP), have Microsoft Active Directory interactivity, as well as connect to other network shares and be connectable from the network - just as they are now as standalone servers. Optimally I'd like IIS (5.x) to be able to look to a shared folder as it's project file source (I've sucessfully gotten SQL Server 2K5 to do it (T1807)).

_Configuration_
Host: Ubuntu 8.04 server (**Static IP**)
Guest: Windows 2000 Advanced Server (**Static IP**)

So far, I've tried several methods for setting up bridging, first the method dictated in the VirtualBox manual, then several others I've found online. None seem to work fully. The closest I got was that both host & guest had Internet connectivity, but the guest could not see the "real" network (no DNS resolution) or communicate with the GC (AD server). I really need this. If I set up the VM with NAT and DHCP (guest), I can sometimes see the network. In **all **cases, the guest could ping the computers by name or IP (with this configuration) - but if I try to run "net use z: \\computername\share (or \\ip address\share)" I get error 67 network name not found. When I expanded "My Network Places" all I get is the VirtualBox shared folders node and the "Directory" node - and when I expand this node, I don't get anything.

Here is the original /etc/network/interfaces that I was using:
```

# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

# The primary network interface
auto eth0
iface eth0 inet manual

# Network Bridge Interface
auto br0
iface br0 inet static
address 10.13.0.3
network 10.13.0.0
netmask 255.255.255.0
broadcast 10.13.0.255
gateway 10.13.0.49
bridge_ports eth0 tap0

# Virtual Network Interfaces
auto tap0
iface tap0 inet manual
tunctl_user babalou
uml_proxy_arp 10.13.0.3
uml_proxy_ether eth0

```

So - I did more research. One article ([http://forums.virtualbox.org/viewtopic.php?t=1175](http://forums.virtualbox.org/viewtopic.php?t=1175)) prompted me to think that the permanent tap interface might be resolved before Winbind and that might be causing the problem. So, I removed the permanent tap interface and went to dynamic tap interface. I backed up the /etc/network/interfaces file and created this one:
```

# The loopback network interface
auto lo
iface lo inet loopback

# Network Bridge Interface
auto br0
iface br0 inet static
address 10.13.0.3
network 10.13.0.0
netmask 255.255.255.0
broadcast 10.13.0.255
gateway 10.13.0.49
bridge_ports eth0
#bridge_ports all

# The primary network interface
auto eth0
iface eth0 inet manual

```

You can see I've tried both ```
bridge_ports eth0
``` and ```
bridge_ports all
```. Neither made any improvement. I  then created the following scripts to be run in the Start/End Application Vbox fields:

setuptap.sh
```
 #!/bin/bash 
 # Create an new TAP interface for the user
 interface=`VBoxTunctl -b -u babalou` 
 if [ -z "$interface" ]; then 
 exit 1 
 fi 
 # Write the name of the interface to the standard output. 
 echo $interface 
 # Bring up the interface. 
 kdesudo /sbin/ifconfig $interface up 
 # And add it to the bridge. 
 kdesudo /usr/sbin/brctl addif br0 $interface 

```

killtap.sh
```

#!/bin/bash 
 # Remove the interface from the bridge.  
 kdesudo /usr/sbin/brctl delif br0 $2
 # And use VBoxTunctl to remove the interface. 
 /usr/bin/VBoxTunctl -d $2

```

The start/end scripts run without error. YAY! or so I thought.
I also thought I was on the right page when I saw this article ([http://www.montanalinux.org/node/561](http://www.montanalinux.org/node/561)) - but no matter what I do - the guest has no connectivity at all (no from/to ping either). I've been working this issue for **over a month** - have read a LOT (big believer in RTFM first before posting) but somehow have still missed the mark.

The following is the result of lshw -C network:
```

  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 5
       bus info: pci@0000:01:05.0
       logical name: eth0
       version: 10
       serial: 00:00:00:00:00:00 (NOT REAL MAC)
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full latency=32 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: br0
       serial: 00:00:00:00:00:00 (NOT REAL MAC)
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A ip=10.13.0.3 link=yes multicast=yes


```

In the new interfaces file, I even tried creating the bridge with a dynamic ip just in case my settings were incorrect - 
```

auto br0
iface br0 inet dhcp
bridge_ports all

```
to no avail - it still didn't work. BUT the host (Ubuntu 8.04 server) has maintained connectivity - I have not lost connectivity on the host.

I have uninstalled/reinstalled Win2KAdvSvr SEVERAL times as well as the Guest Additions (until I figured out that the GA's did not impact networking). The only thing I have not done is totally reinstall Ubuntu. I'd rather not go there if I don't have to (using MD RAID5). If anyone can make any suggestion point me in a positive direction, I would be very greatful. I have been trying to resolve this for so long that it has literally given me nightmares. This doesn't seem like it should be a hard problem. 

PLEASE ANYONE?!?

---

### Post by innovate2000 on 2008-08-01
[SOLVED!]
The issue was that I was using Windows 2000 Advanced Server as guest. Once I changed to Windows 2000 Server - all it working as expected.

---

