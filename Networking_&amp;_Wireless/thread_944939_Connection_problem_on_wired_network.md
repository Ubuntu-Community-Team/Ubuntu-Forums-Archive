---
title: "Connection problem on wired network"
date: 2008-10-11
forum: Networking &amp; Wireless
---

### Post by xfred on 2008-10-11
Hi

I've had my desktop set up with a wired connection to a netgear DG834G ADSL modem/router for a while now and not had any problems.  Even yesterday it was working fine.  However today I find that I can't connect to the network: it just stays in a perpetual state of "trying to connect".

Now I'm almost certain that the problem isn't the router, as I'm typing this message using my laptop connected wirelessly to it, and the settings seem ok (dhcp enabled, ranges 192.168.0.2 -> 192.168.0.254), and I don't recall changing anything on the desktop, though clearly something must have changed.

Here's the result of running ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:1d:7d:01:69:8a  
          inet6 addr: fe80::21d:7dff:fe01:698a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:722 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:90008 (87.8 KB)
          Interrupt:219 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2155 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2155 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:109788 (107.2 KB)  TX bytes:109788 (107.2 KB)

```

Here's the syslog (or what I hope is the relevant part, anyhow):
```
Oct 12 13:07:07 middle-earth dhclient: DHCPRELEASE on eth0 to 192.168.0.1 port 67
Oct 12 13:07:07 middle-earth dhclient: send_packet: Network is unreachable
Oct 12 13:07:07 middle-earth dhclient: send_packet: please consult README file regarding broadcast address.
Oct 12 13:07:08 middle-earth NetworkManager: <info>  Activation (eth0) cancellation handled. 
Oct 12 13:07:08 middle-earth NetworkManager: <info>  Activation (eth0): cancelled. 
Oct 12 13:07:08 middle-earth NetworkManager: nm_device_is_802_3_ethernet: assertion `dev != NULL' failed
Oct 12 13:07:08 middle-earth NetworkManager: nm_device_is_802_11_wireless: assertion `dev != NULL' failed
Oct 12 13:07:09 middle-earth dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Oct 12 13:07:09 middle-earth kernel: [ 1144.498779] r8169: eth0: link up
Oct 12 13:07:09 middle-earth kernel: [ 1144.501647] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Oct 12 13:07:09 middle-earth NetworkManager: <info>  Will activate wired connection 'eth0' because it now has a link. 
Oct 12 13:07:09 middle-earth NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth0'. 
Oct 12 13:07:09 middle-earth NetworkManager: <info>  Will activate connection 'eth0'. 
Oct 12 13:07:09 middle-earth NetworkManager: <info>  Device eth0 activation scheduled... 
Oct 12 13:07:09 middle-earth NetworkManager: <info>  Activation (eth0) started... 
Oct 12 13:07:09 middle-earth NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Oct 12 13:07:09 middle-earth NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Oct 12 13:07:09 middle-earth NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Oct 12 13:07:09 middle-earth NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Oct 12 13:07:09 middle-earth NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Oct 12 13:07:09 middle-earth NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Oct 12 13:07:09 middle-earth NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Oct 12 13:07:09 middle-earth NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Oct 12 13:07:09 middle-earth NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Oct 12 13:07:09 middle-earth kernel: [ 1144.533425] r8169: eth0: link down
Oct 12 13:07:11 middle-earth avahi-daemon[5499]: Registering new address record for fe80::21d:7dff:fe01:698a on eth0.*.
Oct 12 13:07:11 middle-earth NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction. 
Oct 12 13:07:11 middle-earth NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Oct 12 13:07:11 middle-earth NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth0 
Oct 12 13:07:11 middle-earth NetworkManager: <info>  SWITCH: terminating current connection 'eth0' because it's no longer valid. 
Oct 12 13:07:11 middle-earth NetworkManager: <info>  Deactivating device eth0. 
Oct 12 13:07:11 middle-earth NetworkManager: <info>  Activation (eth0): cancelling... 
Oct 12 13:07:11 middle-earth NetworkManager: <info>  Activation (eth0) cancellation handler scheduled... 
Oct 12 13:07:11 middle-earth NetworkManager: <info>  Activation (eth0): waiting for device to cancel activation. 
Oct 12 13:07:11 middle-earth dhclient: DHCPRELEASE on eth0 to 192.168.0.1 port 67
Oct 12 13:07:11 middle-earth dhclient: send_packet: Network is unreachable
Oct 12 13:07:11 middle-earth dhclient: send_packet: please consult README file regarding broadcast address.
Oct 12 13:07:11 middle-earth kernel: [ 1146.788625] r8169: eth0: link up
Oct 12 13:07:11 middle-earth kernel: [ 1146.823055] r8169: eth0: link down
Oct 12 13:07:12 middle-earth NetworkManager: <info>  Activation (eth0) cancellation handled. 
Oct 12 13:07:12 middle-earth NetworkManager: <info>  Activation (eth0): cancelled. 
Oct 12 13:07:12 middle-earth avahi-daemon[5499]: Withdrawing address record for fe80::21d:7dff:fe01:698a on eth0.
Oct 12 13:07:12 middle-earth NetworkManager: nm_device_is_802_3_ethernet: assertion `dev != NULL' failed
Oct 12 13:07:12 middle-earth NetworkManager: nm_device_is_802_11_wireless: assertion `dev != NULL' failed
Oct 12 13:07:12 middle-earth NetworkManager: <info>  Will activate wired connection 'eth0' because it now has a link. 
Oct 12 13:07:12 middle-earth NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth0'. 
Oct 12 13:07:12 middle-earth NetworkManager: <info>  Will activate connection 'eth0'. 
Oct 12 13:07:12 middle-earth NetworkManager: <info>  Device eth0 activation scheduled... 
Oct 12 13:07:12 middle-earth NetworkManager: <info>  Activation (eth0) started... 
Oct 12 13:07:12 middle-earth NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Oct 12 13:07:12 middle-earth NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Oct 12 13:07:12 middle-earth NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Oct 12 13:07:12 middle-earth NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Oct 12 13:07:12 middle-earth NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Oct 12 13:07:12 middle-earth NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Oct 12 13:07:12 middle-earth NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Oct 12 13:07:12 middle-earth NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Oct 12 13:07:12 middle-earth NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Oct 12 13:07:12 middle-earth NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth0 
Oct 12 13:07:12 middle-earth dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Oct 12 13:07:13 middle-earth NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction. 
Oct 12 13:07:13 middle-earth NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Oct 12 13:07:13 middle-earth NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth0 
Oct 12 13:07:13 middle-earth NetworkManager: <info>  SWITCH: terminating current connection 'eth0' because it's no longer valid. 
Oct 12 13:07:13 middle-earth NetworkManager: <info>  Deactivating device eth0. 
Oct 12 13:07:13 middle-earth NetworkManager: <info>  Activation (eth0): cancelling... 
Oct 12 13:07:13 middle-earth NetworkManager: <info>  Activation (eth0) cancellation handler scheduled... 
Oct 12 13:07:13 middle-earth NetworkManager: <info>  Activation (eth0): waiting for device to cancel activation. 
Oct 12 13:07:13 middle-earth dhclient: DHCPRELEASE on eth0 to 192.168.0.1 port 67
Oct 12 13:07:13 middle-earth dhclient: send_packet: Network is unreachable
Oct 12 13:07:13 middle-earth dhclient: send_packet: please consult README file regarding broadcast address.
Oct 12 13:07:14 middle-earth kernel: [ 1149.026131] r8169: eth0: link up
Oct 12 13:07:14 middle-earth kernel: [ 1149.028993] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Oct 12 13:07:14 middle-earth kernel: [ 1149.073973] r8169: eth0: link down
Oct 12 13:07:14 middle-earth NetworkManager: <info>  Activation (eth0) cancellation handled. 
Oct 12 13:07:14 middle-earth NetworkManager: <info>  Activation (eth0): cancelled. 
Oct 12 13:07:14 middle-earth NetworkManager: nm_device_is_802_3_ethernet: assertion `dev != NULL' failed
Oct 12 13:07:14 middle-earth NetworkManager: nm_device_is_802_11_wireless: assertion `dev != NULL' failed
Oct 12 13:07:14 middle-earth NetworkManager: <info>  Will activate wired connection 'eth0' because it now has a link. 
Oct 12 13:07:14 middle-earth NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth0'. 
Oct 12 13:07:14 middle-earth NetworkManager: <info>  Will activate connection 'eth0'. 
Oct 12 13:07:14 middle-earth NetworkManager: <info>  Device eth0 activation scheduled... 
Oct 12 13:07:14 middle-earth NetworkManager: <info>  Activation (eth0) started... 
Oct 12 13:07:14 middle-earth NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Oct 12 13:07:14 middle-earth NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Oct 12 13:07:14 middle-earth NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Oct 12 13:07:14 middle-earth NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Oct 12 13:07:14 middle-earth NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Oct 12 13:07:14 middle-earth NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Oct 12 13:07:14 middle-earth NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Oct 12 13:07:14 middle-earth NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Oct 12 13:07:14 middle-earth NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Oct 12 13:07:14 middle-earth NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth0 
```

Any ideas?

---

### Post by akira86 on 2008-10-11
Hello
give us the answer of :
cat /etc/network/interfaces

(hide your wifi key before posting ;-p)

---

### Post by prshah on 2008-10-11
> **xfred said:**
> 
Here's the result of running ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:1d:7d:01:69:8a  
          inet6 addr: fe80::21d:7dff:fe01:698a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:722 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:90008 (87.8 KB)
          Interrupt:219 Base address:0xc000 

```

Here's the syslog (or what I hope is the relevant part, anyhow):
```

Oct 12 13:07:09 middle-earth NetworkManager: <info>  Will activate wired connection 'eth0' because it now has a link. 
Oct 12 13:07:09 middle-earth kernel: [ 1144.533425] r8169: eth0: link down
Oct 12 13:07:11 middle-earth avahi-daemon[5499]: Registering new address record for fe80::21d:7dff:fe01:698a on eth0.*.
Oct 12 13:07:11 middle-earth NetworkManager: <info>  SWITCH: terminating current connection 'eth0' because it's no longer valid. 
Oct 12 13:07:11 middle-earth kernel: [ 1146.788625] r8169: eth0: link up
Oct 12 13:07:11 middle-earth kernel: [ 1146.823055] r8169: eth0: link down
Oct 12 13:07:14 middle-earth kernel: [ 1149.026131] r8169: eth0: link up
Oct 12 13:07:14 middle-earth kernel: [ 1149.073973] r8169: eth0: link down

```

Looks like your wired connection is failing; check the cable. I doubt that it's a computer issue; most likely the cable is shorting somewhere, which is why the link keeps going down (and up again).

You can also [disable ipv6]("http://ubuntuforums.org/showpost.php?p=5580701&postcount=2"), since it doesn't seem as though you are using it.

Please post the output of ```
sudo mii-tool eth0 && sleep 10 && sudo mii-tool eth0 && sleep 10 && sudo mii-tool eth0 && sleep 10 && sudo mii-tool eth0 && sleep 10 && sudo mii-tool eth0 && sleep 10
```

---

### Post by xfred on 2008-10-12
OK, I got called away yesterday, but on logging in this morning it seems that the problem has righted itself overnight, which makes me suspect you were right in suspecting the cable as the temperature has dropped significantly overnight.  Anyhow, I'll locate a spare cable for diagnostics if the problem resurfaces.

> **prshah said:**
> You can also [disable ipv6]("http://ubuntuforums.org/showpost.php?p=5580701&postcount=2"), since it doesn't seem as though you are using it.

Please post the output of ```
sudo mii-tool eth0 && sleep 10 && sudo mii-tool eth0 && sleep 10 && sudo mii-tool eth0 && sleep 10 && sudo mii-tool eth0 && sleep 10 && sudo mii-tool eth0 && sleep 10
```

Unfortunately like I said I got called away yesterday, and today I only get the uninformative result:

eth0: no autonegotiation, 10baseT-HD, link ok
eth0: no autonegotiation, 10baseT-HD, link ok
...

> **akira86 said:**
> Hello
give us the answer of :
cat /etc/network/interfaces

(hide your wifi key before posting ;-p)

auto lo
iface lo inet loopback

---

### Post by prshah on 2008-10-13
> **xfred said:**
> 
eth0: no autonegotiation, 10baseT-HD, link ok
eth0: no autonegotiation, 10baseT-HD, link ok


No autonegotiation, and 10Mbps link? Somethings not working; it can be on either end (router, computer) or with the cable, so you need to eliminate it one-by-one; you should start with the cable.

Check if the copper is exposed (uninsulated) on either end near where the wires enter the RJ45 (plastic) plug. If you can see the copper, that's where the trouble is; you need to either replace the cable or get a new pair of RJ45 plugs, a network crimper, chop off the old plugs, and replace them.

However, if you subscribe to the if-it-aint-broke-dont-fix-it category, you can leave well enough alone.. until the next time!

---

