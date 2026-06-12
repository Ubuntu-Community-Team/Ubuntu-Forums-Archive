---
title: "Bonding multiple mobile hotspots &amp; connectivity"
date: 2015-03-27
forum: Networking &amp; Wireless
---

### Post by charish2 on 2015-03-27
Hi all,

I have a fairly unique set up that I'm trying to get working and haven't found much info on it. I have two mobile hotspots connected via USB (eth1 and eth2) that I've bonded together in /etc/network/interfaces. I've managed to get the bond interface up and running partially, but there's an issue with connectivity, e.g. I can't even run a dig or nslookup to any domain. Since these are hotspots, there's not much that can be changed configuration-wise for their networks --- I say this because both hotspots have LAN IPs of 192.168.0.1 and I'm thinking that might be an issue. And DHCP's been disabled on both hotspots as well.

This is my current bonding configuration for the hotspots:

```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


auto eth1
iface eth1 inet manual
	bond-master bond0


auto eth2
iface eth2 inet manual
	bond-master bond0


auto bond0
iface bond0 inet static
	address 192.168.0.168
	gateway 192.168.0.1
	netmask 255.255.255.0
	bond-mode 0
	bond-miimon 100
```

Is there something that I'm missing within the bonding configuration or even something else entirely different?  Any help would be greatly appreciated.

Thanks!

---

### Post by tgalati4 on 2015-03-28
Resolving names with /etc/resolv.conf use to be easy.  But now there is a service that maintains the DNS resolvers, so it is complicated and may or may not work correctly with your Use Case.

```
cat /etc/resolv.conf
man resolvconf
```

First, I would include some dns-nameserver stanzas in your *interfaces* file:  [http://unix.stackexchange.com/questions/71062/ubuntu-how-to-configure-dns-servers-in-etc-network-interfaces-correctly-for-re](http://unix.stackexchange.com/questions/71062/ubuntu-how-to-configure-dns-servers-in-etc-network-interfaces-correctly-for-re)

Basic networking docs:  [https://help.ubuntu.com/lts/serverguide/network-configuration.html](https://help.ubuntu.com/lts/serverguide/network-configuration.html)

When you don't use DHCP, you lose name resolution, unless you specify it manually.

---

### Post by charish2 on 2015-03-30
Even with adding the dns-nameserver and dns-search parameters in the bonding stanza, it's a no-go.

However, after some digging, I think I found a more basic issue: for some reason, the bond interface itself isn't coming up (at least not fully, I think) and I can't ping the gateway. After adding the bond interface, it doesn't show up on ifconfig; I have to manually do a "sudo ifup bond0" to try and bring it up but get

```
charish@charish-ThinkPad-T430:~$ sudo ifup bond0
RTNETLINK answers: File exists
Failed to bring up bond0
```

Now, three things I noticed after issuing the ifup:

1) bond0 does appear in "ifconfig"
2) It does not, however, appear in the Network Manager GUI (it shows the individual modems, but greyed out with the message "device not managed"). But, going under "Edit connections", I can see that the bonded connection is there.
3) The output from the bond0 file
```
charish@charish-ThinkPad-T430:~$ cat /proc/net/bonding/bond0
Ethernet Channel Bonding Driver: v3.7.1 (April 27, 2011)


Bonding Mode: load balancing (round-robin)
MII Status: up
MII Polling Interval (ms): 100
Up Delay (ms): 0
Down Delay (ms): 0
```

According to some other posts that I Googled for, based on the above output for /proc/net/bonding/bond0, it almost looks as if the slaves haven't joined the bonded interface. Am I correct in that assertion?

---

### Post by tgalati4 on 2015-03-31
Well, understand that NetworkManager and manual configuration (using /etc/network/interfaces) will constantly be at odds with one another.  What is the value of:

```
cat /etc/NetworkManager/NetworkManger.conf
```

>        managed=false | true
              Controls  whether  interfaces  listed  in  the  'interfaces' file are managed by NetworkManager.  If set to true, then interfaces listed in
              /etc/network/interfaces are managed by NetworkManager.  If set to false, then any  interface  listed  in  /etc/network/interfaces  will  be
              ignored by NetworkManager. Remember that NetworkManager controls the default route, so because the interface is ignored, NetworkManager may
              assign the default route to some other interface.  When the option is missing, false value is taken as default.



---

### Post by michi1983 on 2015-04-01
Could you just post an output of ```
ifconfig
```?

greetz

---

