---
title: "Port Bonding on KVM with Bridge network"
date: 2016-11-10
forum: Networking &amp; Wireless
---

### Post by matthewmcwest on 2016-11-10
I have a new server with dual NICs.  I have set it up as a KVM virtual host and would like to bond the two NICs while also using a bridge so my VMs are exposed to the network.  I have set up the bonding module and tried the following /etc/network/interfaces setup:
```
# The loopback network interfaceauto lo
iface lo inet loopback


# This was an attempt to bond and bridge the nics


# The bonded interface
auto bond0
iface bond0 inet manual
  bond-mode 2
  bond-slaves em1 em2


auto br0
iface br0 inet static
  address x.y.0.4
  network x.y.0.0
  netmask 255.255.255.0
  broadcast x.y.0.255
  gateway x.y.0.1
  dns-nameservers x.y.0.1
  bridge_ports bond0
  bridge_stp off
  bridge_fd 0
  bridge_maxwait 0



```

Unfortunately this did not work.

---

### Post by TheFu on 2016-11-10
Are the switches capable of supporting this protocol and has that been enabled?
Did you load the Linux bonding module into the kernel and specify the options?
[http://www.cyberciti.biz/faq/ubuntu-linux-bridging-and-bonding-setup/](http://www.cyberciti.biz/faq/ubuntu-linux-bridging-and-bonding-setup/) has instructions for 16.04.

---

### Post by matthewmcwest on 2016-11-11
I was able to get bonding to work (without the bridge) so I know the broadcom gigabit integrated NICs will do it.  I did load the bonding module, but I'm not sure what you mean by specify the options.  I followed the instructions on the link you gave, but it still did not work.  Not sure what the next steps are.

---

### Post by TheFu on 2016-11-11
> **matthewmcwest said:**
> I was able to get bonding to work (without the bridge) so I know the broadcom gigabit integrated NICs will do it.  I did load the bonding module, but I'm not sure what you mean by specify the options.  I followed the instructions on the link you gave, but it still did not work.  Not sure what the next steps are.

What do the log files show?

---

### Post by matthewmcwest on 2016-11-11
I'm not sure which log file to look at.

---

### Post by TheFu on 2016-11-11
> **matthewmcwest said:**
> I'm not sure which log file to look at.

Teaching to fish ... "ubuntu log files"

All of them.  I tend to use egrep, but you can look at them anyway you want.

Please help us to help you. Saying something "doesn't work" doesn't really convey many details. The provided link had a number of commands to show progress of the steps.  Perhaps, if you ran those and posted both the command AND the output here, someone could help?

Descriptions aren't nearly as useful as showing the actual output, since we often don't really understand what we are seeing.

Make sense?

---

### Post by matthewmcwest on 2016-11-11
Great point.  I started looking through the syslog and playing around with the interfaces file.  I finally got it working.  Below is the interfaces file and the output of more /proc/net/bonding/bond0.  I know the interfaces file has a lot of commented stuff, but I was experimenting.  I noticed in the /proc/net/bonding/bond0 output that it says the speed is slow.  The NICs are connected to a Cisco Catalys 2960.  I'm not sure if I need to setup the ports on the switch for LACP.  I thought that Cisco's DTP would take care of this.

cat /etc/network/interfaces:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).


# The loopback network interface
#auto lo
#iface lo inet loopback


# This was an attempt to bond and bridge the nics


auto em1
iface em1 inet manual
  bond-master bond0


auto em2
iface em2 inet manual
  bond-master bond0


# The bonded interface
auto bond0
iface bond0 inet manual
#iface bond0 inet static
#  address 10.92.0.4
#  network 10.92.0.0
#  netmask 255.255.255.0
#  broadcast 10.92.0.255
#  gateway 10.92.0.1
#  dns-nameservers 10.92.0.1
  bond-mode 4
#  bond-slaves em1 em2
#auto em1
#iface em1 inet manual
#  bond-master bond0


#auto em2
#iface em2 inet manual
#  bond-master bond0


# This works


auto br0
iface br0 inet static
  address 10.92.0.4
  network 10.92.0.0
  netmask 255.255.255.0
  broadcast 10.92.0.255
  gateway 10.92.0.1
  dns-nameservers 10.92.0.1
  bridge_ports bond0
#  bridge_ports em1
  bridge_stp off
  bridge_fd 0
  bridge_maxwait 0


#auto br1
#iface br1 inet static
#  address 10.92.0.3
#  network 10.92.0.0
#  netmask 255.255.255.0
#  broadcast 10.92.0.255
#  gateway 10.92.0.1
#  dns-nameservers 10.92.0.1
#  bridge_ports em2
#  bridge_stp off
#  bridge_fd 0
#  bridge_maxwait 0




more /proc/net/bonding/bond0:


Ethernet Channel Bonding Driver: v3.7.1 (April 27, 2011)


Bonding Mode: IEEE 802.3ad Dynamic link aggregation
Transmit Hash Policy: layer2 (0)
MII Status: up
MII Polling Interval (ms): 0
Up Delay (ms): 0
Down Delay (ms): 0


802.3ad info
LACP rate: slow
Min links: 0
Aggregator selection policy (ad_select): stable


Slave Interface: em1
MII Status: up
Speed: 100 Mbps
Duplex: full
Link Failure Count: 0
Permanent HW addr: 10:98:36:a6:df:8b
Slave queue ID: 0
Aggregator ID: 1
Actor Churn State: none
Partner Churn State: churned
Actor Churned Count: 0
Partner Churned Count: 1


Slave Interface: em2
MII Status: up
Speed: 100 Mbps
Duplex: full
Link Failure Count: 0
Permanent HW addr: 10:98:36:a6:df:8c
Slave queue ID: 0
Aggregator ID: 2
Actor Churn State: churned
Partner Churn State: churned
Actor Churned Count: 1
Partner Churned Count: 1

---

### Post by matthewmcwest on 2016-11-11
I have set up the cisco switch for lacp.  It shows the port-channel have double the speed of a single port.  I also looked up the lacp rate: slow, and it defines how often lacp packets are exchanged.  I think it is working, but I am not completely sure.  I need to set up a real world test.  If you have any ideas on how to do this, let me know.  Thank you

---

### Post by matthewmcwest on 2016-11-11
I have set up iperf3 on the server and on 2 other machines on the same switch.  When I run iperf3 on both machines (using the server that I just set up bonding on as an iperf3 server), I only get about 95Mbps.  This shows that I was unsuccessful in my attempts to set up bonded and bridged NICs.  I'll try again next week.

---

