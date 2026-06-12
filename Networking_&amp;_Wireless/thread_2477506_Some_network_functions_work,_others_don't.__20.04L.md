---
title: "Some network functions work, others don't.  20.04LTS"
date: 2022-07-27
forum: Networking &amp; Wireless
---

### Post by uacnt83982803 on 2022-07-27
This is a strange one.  The problem started earlier today.  After a restart of my system, I cannot access most network functions.  

Symptoms:
1. Browser won't connect to external sites (however, it will access the admin page of my router, and will (via that admin page) successfully retrieve the current firmware version (confirms that the router is on the current version).
2. Software updater hangs at Querying Software Sources, and then fails to download
3. I can remote into another Ubuntu PC on my LAN using the Remmina client, and everything works fine
4. When I'm remoted into that other PC, it can ping the problem PC and gets consistent clean responses, no errors
5. System monitor shows some active data send and receive.

What steps I've taken:
1. I have checked Network settings a dozen times.  Everything looks correct, and I've cycled everything.
2. Tried my home wifi, it connects fine but same symptoms
3. I booted from a Live Ubuntu USB stick and (using Try Ubuntu) the Firebox browser works fine.
4. Restarted my router, even though everything else on the network works perfectly fine
5. Restarted the problem PC numerous times

Other info of note:
1. I had installed a paid VPN about a week ago.  It was working perfectly, however just to rule it out as a problem I removed all of the packages associated with it (and rebooted several times).  No change.
2. Other PCs on the same LAN function fine.  I'm typing this on a Windows box.

Not sure what to try next.  Since the Live USB stick works fine, that seems to rule out any hardware issues.

Is this possibly a DNS (or lack thereof) issue?

Any help is appreciated!

---

### Post by TheFu on 2022-07-27
Determine what the problem is first.
[https://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking](https://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking) has some steps. Run each, in order and report which work and which failed.

---

### Post by uacnt83982803 on 2022-07-28
Thank you.  Here are the results of these tests:

1. IP is 192.168.1.100.  This matches what I see in my pfSense router's DHCP lease table; it shows there as Online.
2. Router is 192.168.1.1 (the pfSense's IP)
3. Cannot ping publically-known IPs such as 8.8.8.8 - ping just sits there, no results or errors.  I have to cancel using CTRL-Z.
4. dmesg | grep enp3s0f1 returns:
    r8169 Renamed from eth0
    r8169 Link is down
    r8169 Link is up - 1Gbps/Full - flow control off
    IPV6: ADDRCONF (NETDEV_CHANGE): enp3s0f1: link becomes ready

5. ```
sudo lshw -C net
```
finds the interface, no errors indicated
6. ifconfig - not found, need to install net-tools
7. ```
more /etc/resolv.conf:
```
```

    nameserver 127.0.0.53
    options edns0  trust-ad

```
8. route - not found, need to install net-tools

---

### Post by mIk3_08 on 2022-07-28
> **uacnt83982803 said:**
> This is a strange one.  The problem started earlier today.  After a restart of my system, I cannot access most network functions.  

Symptoms:
1. Browser won't connect to external sites (however, it will access the admin page of my router, and will (via that admin page) successfully retrieve the current firmware version (confirms that the router is on the current version).
2. Software updater hangs at Querying Software Sources, and then fails to download
3. I can remote into another Ubuntu PC on my LAN using the Remmina client, and everything works fine
4. When I'm remoted into that other PC, it can ping the problem PC and gets consistent clean responses, no errors
5. System monitor shows some active data send and receive.

What steps I've taken:
1. I have checked Network settings a dozen times.  Everything looks correct, and I've cycled everything.
2. Tried my home wifi, it connects fine but same symptoms
3. I booted from a Live Ubuntu USB stick and (using Try Ubuntu) the Firebox browser works fine.
4. Restarted my router, even though everything else on the network works perfectly fine
5. Restarted the problem PC numerous times

Other info of note:
1. I had installed a paid VPN about a week ago.  It was working perfectly, however just to rule it out as a problem I removed all of the packages associated with it (and rebooted several times).  No change.
2. Other PCs on the same LAN function fine.  I'm typing this on a Windows box.

Not sure what to try next.  Since the Live USB stick works fine, that seems to rule out any hardware issues.

Is this possibly a DNS (or lack thereof) issue?

Any help is appreciated!

Please run the script on this give url page below and post the information or pastebin link in this thread. 
```
https://github.com/UbuntuForums/system-info
```
This command will show all the results of this command```
sudo lshw -C network
```to complete all the info about your system just do the command above. Regards and cheers.

---

### Post by uacnt83982803 on 2022-07-28
So I downloaded the script and ran it.  The results (one line) you can see near the top of this Terminal capture  Nothing else seemed to happen with the script.  

Also this is the results of the lshw command:

```

[B]me@me-Aspire-E5-576:~$ script
Script started, file is typescript
[/B]
```


```

me@me-Aspire-E5-576:~$ sudo lshw -C network
[sudo] password for me: 

```

```

  *-network DISABLED        
       description: Wireless interface
       product: QCA9377 802.11ac Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlp2s0
       version: 31
       serial: 70:c9:4e:b5:03:d3
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath10k_pci driverversion=5.4.0-122-generic firmware=WLAN.TF.2.1-00021-QCARMSWP-1 latency=0 link=no multicast=yes wireless=IEEE 802.11
       resources: irq:132 memory:b1000000-b11fffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0.1
       bus info: pci@0000:03:00.1
       logical name: enp3s0f1
       version: 12
       serial: d8:c4:97:5d:c0:cc
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 duplex=full firmware=rtl8411-2_0.0.1 07/08/13 ip=192.168.1.100 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:19 ioport:3000(size=256) memory:b1204000-b1204fff memory:b1200000-b1203fff
  *-network:0
       description: Ethernet interface
       physical id: 1
       logical name: pvpnksintrf0
       serial: 1e:c1:cd:8f:29:5a
       capabilities: ethernet physical
       configuration: broadcast=yes driver=dummy driverversion=1.0 ip=100.85.0.1
  *-network:1
       description: Ethernet interface
       physical id: 2
       logical name: ipv6leakintrf0
       serial: a2:13:d6:92:b4:6c
       capabilities: ethernet physical
       configuration: broadcast=yes driver=dummy driverversion=1.0

```

me@me-Aspire-E5-576:~$ ^C
me@me-Aspire-E5-576:~$

---

### Post by TheFu on 2022-07-28
> **uacnt83982803 said:**
> Thank you.  Here are the results of these tests:


Can it ping the router by IP or not?
If it not, then look at crappy realtek drivers for the issue.
If so, check your router ports - try a different port.  Seems odd that it is getting a DHCP response, if it cannot ping the router.

I cannot help with realtek.  Stopped using stuff from them a few years ago after too much frustration.  $25 extra for Intel NICs is well worth it to me to avoid frustration over things that should "just work."

---

### Post by TheFu on 2022-07-28
Please edit all the posts above to wrap terminal commands + output in forum 'code tags'.  Having columns line up makes for much easier reading.  Always do this. Please.

---

### Post by uacnt83982803 on 2022-07-28
Yes, it can ping the router by IP, zero errors.  

Understood on the Intel NICs, but as this is a laptop I don't really have the option to change it.  Also, remember that when booted from a Live USB stick, everything works perfectly.

---

### Post by uacnt83982803 on 2022-07-28
Code blocks - thanks for the reminder.  Done.  And sticky note affixed to the laptop to remind me.

---

### Post by TheFu on 2022-07-28
> **uacnt83982803 said:**
> Yes, it can ping the router by IP, zero errors.  

Understood on the Intel NICs, but as this is a laptop I don't really have the option to change it.  Also, remember that when booted from a Live USB stick, everything works perfectly.

If you can ping the router, but not addresses on the internet AND all other devices work AND this computer works when using the Try Ubuntu flash boot,
then ....
the problem is likely due to a VPN or routing table screw up. Remove any VPN completely.  Reset the routing back to the defaults, which are very simple.  Should be 2 entries only.  Something like this:
```
$ ip route |column -t
default         via  172.22.22.1  dev    ens3    proto  static
172.22.22.0/24  dev  ens3         proto  kernel  scope  link    src  172.22.22.3
```

---

### Post by uacnt83982803 on 2022-07-28
I think I'm tracking with you.  I did remove all of the VPN's software packages the yesterday, but it appears there are some holdovers.

```

me@me-Aspire-E5-576:~$ ip route show

```

returns:
```

default via 192.168.1.1 dev enp3s0f1 
default via 100.85.0.1 dev pvpnksintrf0 proto static metric 98 
default dev wlp2s0 scope link metric 1003 linkdown 
100.85.0.0/24 dev pvpnksintrf0 proto kernel scope link src 100.85.0.1 metric 98 
169.254.0.0/16 dev wlp2s0 proto kernel scope link src 169.254.8.176 linkdown 
169.254.0.0/16 dev pvpnksintrf0 scope link metric 1000 
192.168.1.0/24 dev enp3s0f1 proto kernel scope link src 192.168.1.231

```

Edit: I figured out how to add and delete these.  So, I booted the machine on the Try Ubuntu live usb and recorded how the IP Routes are defined on that system (since it works).  I then restarted and edited the route table on the system, and have it exactly as it appears when running off the live USB.

However, as soon as I reboot it reverts back to pointing to the VPN again.  I checked in /etc/networkmanager (I think it was) and in there are 4 files - one for my wifi, one for my wired network, and 2 for the VPN.  I cannot delete those 2 files for the VPN.

From what I've read, those settings (for the routing table) are stored in several places.  Isn't there some way to push what is currently "Live" (the way I have it and ip route | column -t displays) overwriting all the other places that try to save it?

---

### Post by uacnt83982803 on 2022-07-29
Fixed it.  I ran:

```

nmcli Connection

```

Saw the vpn connections and deleted them.

After a reboot, I checked and all looked good, tested and the problem is resolved.

---

