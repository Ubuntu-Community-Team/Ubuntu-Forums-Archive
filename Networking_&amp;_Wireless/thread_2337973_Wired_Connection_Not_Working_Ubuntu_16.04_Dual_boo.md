---
title: "Wired Connection Not Working Ubuntu 16.04 Dual boot with windows 10"
date: 2016-09-23
forum: Networking &amp; Wireless
---

### Post by tarikneaj on 2016-09-23
[COLOR=#111111][FONT=Ubuntu]I dual booted my computer yesterday. Everything works fine except the internet connection keeps disconnecting. It never actually connects. It goes offline constantly.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Ive read multiple threads and nothing worked. Here are some info -

[I]ifconfig -a

[/I][/FONT][/COLOR]
```
eno1  Link encap:Ethernet  HWaddr 14:dd:a9:7e:5e:a8  
      inet6 addr: fe80::b5a8:8559:5f56:d0ff/64 Scope:Link
      UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
      RX packets:96 errors:0 dropped:0 overruns:0 frame:0
      TX packets:377 errors:0 dropped:0 overruns:0 carrier:0
      collisions:0 txqueuelen:1000 
      RX bytes:7730 (7.7 KB)  TX bytes:69310 (69.3 KB)
      Interrupt:20 Memory:f7100000-f7120000 

lo    Link encap:Local Loopback  
      inet addr:127.0.0.1  Mask:255.0.0.0
      inet6 addr: ::1/128 Scope:Host
      UP LOOPBACK RUNNING  MTU:65536  Metric:1
      RX packets:3645 errors:0 dropped:0 overruns:0 frame:0
      TX packets:3645 errors:0 dropped:0 overruns:0 carrier:0
      collisions:0 txqueuelen:1 
      RX bytes:269510 (269.5 KB)  TX bytes:269510 (269.5 KB)
```

[I]sudo lshw -c network


[/I]```
[I]*-network               
       description: Ethernet interface
       product: Ethernet Connection (2) I218-V
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eno1
       version: 05
       serial: 14:dd:a9:7e:5e:a8
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.6-k duplex=full firmware=0.1-4 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:27 memory:f7100000-f711ffff memory:f7138000-f7138fff ioport:f040(size=32)
[/I]
```[I]

cat /etc/network/interfaces

```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo 
iface lo inet loopback


auto eno1 
iface eno1 inet dhcp

```

Any help is appreciated!

Edit: [/I]I might want to add that eth0 device does not exist for me.

Edit: I did what the first response said and changed from eth0 to eno1 in /network/interfaces. Did not work.

---

### Post by jeremy31 on 2016-09-23
I would change the /etc/network/interfaces file to 
```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo 
iface lo inet loopback


auto eno1
iface eno1 inet dhcp
```

As you have no eth0 device

---

### Post by tarikneaj on 2016-09-23
I did that, fixed nothing hower.

---

### Post by jeremy31 on 2016-09-23
Were you able to connect while installing Ubuntu 16.04?

---

### Post by tarikneaj on 2016-09-23
Im not exactly sure what you mean by "while installing ubuntu 16.04" since I didnt have the option to use my internet while installing it. But it did work perfectly fine beforehand, in windows 10. This is only a problem on ubuntu.

---

### Post by jeremy31 on 2016-09-23
If you boot to the USB/DVD you installed Ubuntu with, choose Try without installing and see if you can connect there

---

### Post by tarikneaj on 2016-09-23
I just did this, Still no internet connection at all with the "try without installing".

---

### Post by jeremy31 on 2016-09-23
Any error messages from ```
dmesg | egrep 'eno1|e1000e'
```

---

### Post by tarikneaj on 2016-09-23
This is what I get - 

dmesg | egrep 'eno1|e1000e
```

[    0.669594] e1000e: Intel(R) PRO/1000 Network Driver - 3.2.6-k
[    0.669595] e1000e: Copyright(c) 1999 - 2015 Intel Corporation.
[    0.675618] e1000e 0000:00:19.0: Interrupt Throttling Rate (ints/sec) set to dynamic conservative mode
[    0.841948] e1000e 0000:00:19.0 eth0: registered PHC clock
[    0.841950] e1000e 0000:00:19.0 eth0: (PCI Express:2.5GT/s:Width x1) 14:dd:a9:7e:5e:a8
[    0.841951] e1000e 0000:00:19.0 eth0: Intel(R) PRO/1000 Network Connection
[    0.841985] e1000e 0000:00:19.0 eth0: MAC: 11, PHY: 12, PBA No: FFFFFF-0FF
[    0.842993] e1000e 0000:00:19.0 eno1: renamed from eth0
[   11.558057] IPv6: ADDRCONF(NETDEV_UP): eno1: link is not ready
[   13.047783] e1000e: eno1 NIC Link is Up 100 Mbps Full Duplex, Flow Control: Rx/Tx
[   13.047786] e1000e 0000:00:19.0 eno1: 10/100 speed: disabling TSO
[   13.047813] IPv6: ADDRCONF(NETDEV_CHANGE): eno1: link becomes ready

```

I should maybe mention that I have 2 different ethernet connections. One Called Wired Connection 1, which is the only one I can use. Second one called "ifupdown (eno1)" which cannot be edited, used or deleted

---

### Post by SeijiSensei on 2016-09-23
This sounds like a hardware problem.  Got another Ethernet cable you can try?  Also try using a different port on your router.

What happens if you replace the entry in /etc/network/interfaces with a static configuration like this:
```

auto eno1
iface eno1 inet static
address 192.168.1.100
netmask 255.255.255.0
gateway 192.168.1.1
dns-servers 8.8.8.8 8.8.4.4

```
You'll obviously need to use an address within your local subnet and the router's IP as your gateway.  

I'm a bit puzzled as to what happened to eno0.  Does this new systemd method of defining interfaces break the *nix standard and start numbering at one rather than zero?  Have you tried replacing "eno1" with "eno0"?  Any luck?

---

### Post by Shane_Lewis on 2016-09-24
"If you boot to the USB/DVD you installed Ubuntu with, choose Try without installing and see if you can connect there"

I have a similar problem to the OP, but internet died work with the installation media running. Then it works fine without the DVD until I boot into Linux after running Windows. What's going on here? How do I fix it permanently?

Sorry, posting from mobile, and the quote functionality isn't cooperating.

---

