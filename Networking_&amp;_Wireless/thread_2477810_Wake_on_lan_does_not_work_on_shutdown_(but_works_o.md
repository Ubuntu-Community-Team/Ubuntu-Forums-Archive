---
title: "Wake on lan does not work on shutdown (but works on suspend)"
date: 2022-08-08
forum: Networking &amp; Wireless
---

### Post by alduxo007 on 2022-08-08
Hi everyone

I am having the hardes time to make wake on lan work on shut down. Everything works fine on suspend. It works good on shut down when i wake on lan but use only windows also. 
The result of this command :
```
 sudo ethtool eno1 
```

is:

```
Supported ports: [ TP    MII ]        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
        Supported pause frame use: Symmetric Receive-only
        Supports auto-negotiation: Yes
        Supported FEC modes: Not reported
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
        Advertised pause frame use: Symmetric Receive-only
        Advertised auto-negotiation: Yes
        Advertised FEC modes: Not reported
        Link partner advertised link modes:  10baseT/Half 10baseT/Full
                                             100baseT/Half 100baseT/Full
                                             1000baseT/Full
        Link partner advertised pause frame use: Symmetric Receive-only
        Link partner advertised auto-negotiation: Yes
        Link partner advertised FEC modes: Not reported
        Speed: 1000Mb/s
        Duplex: Full
        Auto-negotiation: on
        master-slave cfg: preferred slave
        master-slave status: slave
        Port: Twisted Pair
        PHYAD: 0
        Transceiver: external
        MDI-X: Unknown
        Supports Wake-on: pumbg
        Wake-on: g
        Link detected: yes



```


Seems like the network card goes to total shutdown and does not receive to the magic packet....
For some ubuntu users that were having my problem the solution was:

```
NETDOWN=no
```

at [I]/etc/default/halt

[/I]But in Lubuntu there is not halt file on that location...

Any idea ?

---

### Post by TheFu on 2022-08-08
> Wake on lan does not work on shutdown (but works on suspend) 
Uh .... working as designed?  I'd never expect a powered off system to have any power use.

When a system is shutdown (S5 state), it doesn't wake on LAN.  After all, when a computer is shutdown, there shouldn't be any power used.  If you want to wake from standby, which does have power feeding to specific chips (and likely NICs), then use that.  Hibernation is deprecated in Ubuntu, but that might have a power state that feeds a bit of power to the NIC for WoL needs, but that would likely be extremely driver, motherboard and configuration specific, since The reason to use hibernation instead of standby is for lower power use - basically indefinite freezing of the OS state.

Here's a kernel document for the different power states: [https://www.kernel.org/doc/Documentation/power/states.txt](https://www.kernel.org/doc/Documentation/power/states.txt)  I don't see anything in that document specific to powering on-board NIC devices.

I suspect the drivers are more complete for your NIC under Windows then they are under Linux.  Do you have any specific documentation from the NIC vendor showing how to get WoL supported under Linux?

---

