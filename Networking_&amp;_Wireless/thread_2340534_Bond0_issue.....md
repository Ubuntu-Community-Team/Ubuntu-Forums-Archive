---
title: "Bond0 issue...."
date: 2016-10-19
forum: Networking &amp; Wireless
---

### Post by rkurnik on 2016-10-19
Hi...

I'd like to know if this is normal behavior for bonding interface.

Basically I wanted to test the bonded devices and I have the interfaces setup so thay are in the bounded group...  eth0 and eth1:

root@somemachine:/var/log$ cat /proc/net/bonding/bond0
Ethernet Channel Bonding Driver: v3.7.1 (April 27, 2011)


Bonding Mode: fault-tolerance (active-backup)
Primary Slave: eth0 (primary_reselect always)
Currently Active Slave: eth0
MII Status: up
MII Polling Interval (ms): 100
Up Delay (ms): 200
Down Delay (ms): 200


Slave Interface: eth0
MII Status: up
Speed: 10000 Mbps
Duplex: full
Link Failure Count: 0
Permanent HW addr: a0:36:9f:5e:6f:00
Slave queue ID: 0


Slave Interface: eth1
MII Status: up
Speed: 10000 Mbps
Duplex: full
Link Failure Count: 0
Permanent HW addr: a0:36:9f:5e:6f:02
Slave queue ID: 0


So I tested by taking down the eth0 interface with this command:
ifdown eth0

Then I brought it back up:
ifup eth0

But now with the interface restored my /proc/net/bonding/bond0 reads:
root@somemachine:~$ cat /proc/net/bonding/bond0
Ethernet Channel Bonding Driver: v3.7.1 (April 27, 2011)


Bonding Mode: fault-tolerance (active-backup)
Primary Slave: None
Currently Active Slave: eth1
MII Status: up
MII Polling Interval (ms): 100
Up Delay (ms): 200
Down Delay (ms): 200


Slave Interface: eth1
MII Status: up
Speed: 10000 Mbps
Duplex: full
Link Failure Count: 0
Permanent HW addr: a0:36:9f:5e:6f:02
Slave queue ID: 0


eth0 didn't make it back into the list after it came back up.  

Is this normal?  If so what's the best way to test failover to make sure it fails back and forth?

---

### Post by nathan-linux-sa on 2016-10-19
You are running bond mode 1, that states:

Mode 1 (active-backup)
This mode places one of the interfaces into a backup state and will only  make it active if the link is lost by the active interface. Only one  slave in the bond is active at an instance of time. A different slave  becomes active only when the active slave fails. This mode provides  fault tolerance.

Now, from the output, I cannot confirm if eth0 is down. What does your switch say? What does **ethtool eth0** say?

Depending on what you want to achieve with the bonding, you should maybe look at the alternative bonding modes, too:

[http://www.cloudibee.com/network-bonding-modes/](http://www.cloudibee.com/network-bonding-modes/)

---

### Post by rkurnik on 2016-10-19
OK, I will look at the alternatives but as you see in the first contents of [COLOR=#000000]/proc/net/bonding/bond0 that I posted contained both slaves eth0 (active) and eth1 (inactive)....  when I took the eth0 interface down and brought it back up eth0 did not make it back into the [/COLOR][COLOR=#000000]/proc/net/bonding/bond0 output.....  I would of though the output would of been like the first one showing eth1 as active and eth0 as inactive.

no?[/COLOR]

---

