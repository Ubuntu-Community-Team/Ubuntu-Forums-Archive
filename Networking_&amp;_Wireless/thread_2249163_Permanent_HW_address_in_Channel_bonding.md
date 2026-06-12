---
title: "Permanent HW address in Channel bonding"
date: 2014-10-20
forum: Networking &amp; Wireless
---

### Post by h.hittini on 2014-10-20
Hi,

I have a machine running Ubuntu Server 10.0.4 with kernel 2.6
I'm using ifenslave-2.6 for channel bonding; I have two wireless interfaces and I'm facing an issue with ASUS-N53 USB; it's ra0 interface
The permanent mac address is 00:00:00:00:00:00 as you can see below
```
hosam@Dell-XPS:~$ cat /proc/net/bonding/bond0 
Ethernet Channel Bonding Driver: v3.5.0 (November 4, 2008)


Bonding Mode: load balancing (round-robin)
MII Status: up
MII Polling Interval (ms): 100
Up Delay (ms): 0
Down Delay (ms): 0


Slave Interface: ra0
MII Status: up
Link Failure Count: 0
Permanent HW addr: 00:00:00:00:00:00


Slave Interface: wlan0
MII Status: up
Link Failure Count: 0
Permanent HW addr: 00:08:54:a0:0d:f2

```
However, when I use ifconfig I find that it has a mac address
```
hosam@Dell-XPS:~$ ifconfig ra0 | grep HWaddr
ra0       Link encap:Ethernet  HWaddr 60:a4:4c:ec:6d:58  

```
The mismatch is causing a huge issue for me, the interface is not receiving data because the mac address is not valid
How to overcome that?

Thank you
------------------------------------------------------------------------------------------------------------------------------------
Update 1:
According to this website [http://www.linuxfoundation.org/collaborate/workgroups/networking/bonding#Network_configuration](http://www.linuxfoundation.org/collaborate/workgroups/networking/bonding#Network_configuration)
The slave interfaces should have their mac address configured to be same as the bonding interface address
As you can see in the following, ra0 mac address wasn't changed
```

hosam@Dell-XPS:~$ ifconfig | grep HW
bond0     Link encap:Ethernet  HWaddr 00:08:54:a0:0d:f2  
ra0       Link encap:Ethernet  HWaddr 60:a4:4c:ec:6d:58  
wlan0     Link encap:Ethernet  HWaddr 00:08:54:a0:0d:f2 

```

---

### Post by davit2 on 2014-10-20
Hi,
# ifconfig bond0 hw ether 00:11:22:33:44:55

 or
 # ip link set bond0 address 00:11:22:33:44:55

---

### Post by h.hittini on 2014-10-20
> **davit2 said:**
> Hi,
# ifconfig bond0 hw ether 00:11:22:33:44:55

 or
 # ip link set bond0 address 00:11:22:33:44:55

I tried both and I'm getting "Operation not supported"

---

### Post by davit2 on 2014-10-20
try it
sudo ifconfig bond0 hw ether 00:11:22:33:44:55

---

### Post by davit2 on 2014-10-20
To make the custom MAC address persistent, you need to modify the  bond interface configuration file /etc/sysconfig/network/ifcfg-bond0 for  all cluster nodes.
 Add the following line at the end
 LLADDR=00:11:22:33:44:55'
 When VCS starts up/restarts, the bond interface config will be reset.  To skip the bond reconfig in the startup. You need to comment out the  line in /opt/VRTSnasgw/scripts/preonline.sh on all the nodes.
 # $NASGW_SCRIPTS_DIR/bondconfig.sh reconfig
  
 Please be awared that by commenting out the line above, there will be  no node(s) can be added/deleted in the cluster as the bond information  can't be synchronized.
  
 Then restart the bond interface
 # service network restart bond0

---

### Post by h.hittini on 2014-10-20
> **davit2 said:**
> try it
sudo ifconfig bond0 hw ether 00:11:22:33:44:55
Please have a look at Update 1
I tried changing the mac address of ra0 and I got "Operation not permitted"
I tried changing the mac address of bond0, I didn't get an error but the address wasn't changed
However, I believe the issue is with ra0's mac address, not the bonding interface

---

### Post by h.hittini on 2014-10-20
> **davit2 said:**
> To make the custom MAC address persistent, you need to modify the  bond interface configuration file /etc/sysconfig/network/ifcfg-bond0 for  all cluster nodes.
 Add the following line at the end
 LLADDR=00:11:22:33:44:55'
 When VCS starts up/restarts, the bond interface config will be reset.  To skip the bond reconfig in the startup. You need to comment out the  line in /opt/VRTSnasgw/scripts/preonline.sh on all the nodes.
 # $NASGW_SCRIPTS_DIR/bondconfig.sh reconfig
  
 Please be awared that by commenting out the line above, there will be  no node(s) can be added/deleted in the cluster as the bond information  can't be synchronized.
  
 Then restart the bond interface
 # service network restart bond0
There is no such file
```
hosam@Dell-XPS:~$ ls /etc | grep sys
rsyslog.conf
rsyslog.d
sysctl.conf
sysctl.d
```

---

