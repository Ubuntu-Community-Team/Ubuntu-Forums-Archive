---
title: "primary interface?"
date: 2005-09-06
forum: Networking &amp; Wireless
---

### Post by one_ro on 2005-09-06
Hi guys,

On a laptop with Kubuntu 5.04 which used to have an running internet connection, I changed back and forth between home/job network settings and here I am stumped all of a sudden...
Basically, what I don't understand comes from here:

```
$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 vmnet1
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 vmnet8
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 vmnet1
```

which AFAIK it should be

```
$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 vmnet1
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 vmnet8
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 eth0
```

That is, my primary network card should be eth0 (not vmnet1). The vmnet entry comes from a VMware station I have installed. The status:
- I can ping the gw
- I can ping myself
- I cannot ping anything else
- [COLOR=Red]sudo ifdown eth0[/COLOR] and [COLOR=Red]sudo ifup eth0[/COLOR] gives:
[COLOR=Blue]SIOCADDRT: Network is unreachable[/COLOR]

Is there a special procedure to make eth0 default?
TIA,
Adrian

---

### Post by kirsche on 2005-09-07
did your try to stop the vmware services?
or try to run the vmware-config.pl again?

---

### Post by mlomker on 2005-09-07
I'd agree with trying vmware-config.pl again.  I personally don't configure the NAT and localnet bindings and just use the shared NIC approach (the VM's get their own IP address).  There won't be any additional entries in your routing table if you go that way.

You can manually fix your problem using **route** commands, but it'd be a PITA to do it on every boot.

---

