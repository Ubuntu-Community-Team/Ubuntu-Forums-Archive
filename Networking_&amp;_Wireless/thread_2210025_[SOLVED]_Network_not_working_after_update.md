---
title: "[SOLVED] Network not working after update"
date: 2014-03-08
forum: Networking &amp; Wireless
---

### Post by claudio-bonora on 2014-03-08
Hello to all, 
after a software update on Ubuntu 12.04LTS, the LAN network is not working.
IThe network card is the Intel NIC I217-LM. 
I tried compiling and installing the Intel e1000e driver compatible with my card but without success. Even running kernel with earlier or later (currently on Linux 3.8.0-37), the result has not changed. 
Do you have any ideas on how we can solve this problem? 
Thanks in advance

---

### Post by varunendra on 2014-03-08
Welcome to the forums claudio-bonora!

Please open a terminal (Ctrl-Alt-T) and run the following commands -
```
uname -mr
sudo lshw -numeric -C network -sanitize
```

And do you have any other means to connect this system to internet?

---

### Post by claudio-bonora on 2014-03-08
Hi and thanks!

Temporarily I tether with my phone via usb and it works just well

The outputs for the commands are:

```
reception@ServerUfficio:~$ uname -mr
3.8.0-37-generic x86_64

```

```
reception@ServerUfficio:~$ sudo lshw -numeric -C network -sanitize
  *-network               
       description: Ethernet interface
       product: Ethernet Connection I217-LM [8086:153A]
       vendor: Intel Corporation [8086]
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 04
       serial: [REMOVED]
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.1.4-k duplex=full firmware=0.13-4 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:44 memory:f7c00000-f7c1ffff memory:f7c3d000-f7c3dfff ioport:f080(size=32)

```

As I can see the adapter is recognized but doesn't work

---

### Post by varunendra on 2014-03-09
> **claudio-bonora said:**
> ```

       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.1.4-k duplex=full firmware=0.13-4 latency=0 **[COLOR="#0000CD"]link=yes[/COLOR]** multicast=yes port=twisted pair speed=100Mbit/s
```

So you are physically connected, is everything on the logical side good? That is-

Is DHCP enabled and working properly?
How have you configured your network in Ubuntu?

The e1000e driver is already included in the kernel and you shouldn't have needed to compile it manually in the first place. I have almost never seen a problem with these cards that use this driver. So the prime suspects for me are external factors (bad cable, bad contact, improper DHCP configuration, stuck router firmware etc.) and/or internal configuration problems.

Accordingly, please check/try -

[INDENT][LIST=1]
[*]Make sure the cable and contacts are good. If possible, try replacing the cable with a tested one.
[*]Make sure DHCP is working properly and its pool is not already saturated (all the IPs in DHCP range already been assigned).
[*]Try rebooting the router - Power it off > wait for 4 minutes (usually 20-30 seconds are sufficient, but just to be sure) > Power it on again. Do the same on the computer.
[*]Try manually assigning an available IP temporarily to test if it is internal configuration issue. This is how -
[/LIST]
```
sudo ifconfig eth0 down
sudo ifconfig eth0 *[COLOR="#0000CD"]192.168.1.100[/COLOR]*
```
..where the IP *[COLOR="#0000CD"]192.168.1.100[/COLOR]* is just an example and should be replaced by a valid and available IP on your network. Check if it was accepted with -
```
ifconfig
```
Then try pinging your router -
```
ping -c4 192.168.1.1
```
..again, assuming your router's IP is 192.168.1.1. If not, change it with whatever it is.[/INDENT]

Please try these and post back your confirmation about each of the above points - what you tried and what was the response.

If everything above already looks good, and still there is no connection, please install '**ethtool**' -
```
sudo apt-get install ethtool
```
and post back its report -
```
sudo ethtool eth0
```

Apart from above confirmations/output, please also check your system's BIOS and let me know if you see a feature called "IOMMU" in there. Although the status "link=yes" indicates that is probably not an issue, but just to confirm.

---

### Post by claudio-bonora on 2014-03-13
Thank you for the help but I changed the cable and now it works, so it was a cable related issue.

---

