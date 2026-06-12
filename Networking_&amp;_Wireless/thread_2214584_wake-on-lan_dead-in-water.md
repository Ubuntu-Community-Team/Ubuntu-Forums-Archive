---
title: "wake-on-lan dead-in-water?"
date: 2014-04-02
forum: Networking &amp; Wireless
---

### Post by clayton3 on 2014-04-02
I'm trying to set-up an old t420 as a media server for the house. I'd like to enable WOL because, you know, energy. In Bios we're all set, I think WOL was on by default. However I'm afraid that the NIC won't do it. Here's the details:

```
00:19.0 Ethernet controller: Intel Corporation 82579LM Gigabit Network Connection (rev 04)

```

and the kicker:
```
Settings for eth0:
    Supported ports: [ TP ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Full 
    Supported pause frame use: No
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Full 
    Advertised pause frame use: No
    Advertised auto-negotiation: Yes
    Speed: 1000Mb/s
    Duplex: Full
    Port: Twisted Pair
    PHYAD: 2
    Transceiver: internal
    Auto-negotiation: on
    MDI-X: off
Cannot get wake-on-lan settings: Operation not permitted
    Current message level: 0x00000007 (7)
                   drv probe link
    Link detected: yes


```

Is there anything to do? Do I have to open the computer and hardwire a connection? Is that really a thing on a laptop?

---

### Post by chili555 on 2014-04-02
Ooooh! Opening the computer and having wires dangling is tempting, but let's see if we can figure out a tidier way. Doesn't your device use the driver e1000e? Check:```
lsmod | grep e10
```If so, here is a document that may help us: [https://www.kernel.org/doc/Documentation/networking/e1000e.txt](https://www.kernel.org/doc/Documentation/networking/e1000e.txt)> Enabling Wake on LAN* (WoL)
  ---------------------------
  WoL is configured through the ethtool* utility. For instructions on
  enabling WoL with ethtool, refer to the ethtool man page.

  WoL will be enabled on the system during the next shut down or reboot.
  For this driver version, in order to enable WoL, the e1000e driver must be
  loaded when shutting down or rebooting the system.
So what does ethtool report about your device? My similar device says:```
sudo ethtool eth0
<snip>
Supports Wake-on: pumbg
	Wake-on: g
```And the manual page says:> wol p|u|m|b|a|g|s|d...
              Sets  Wake-on-LAN  options.   Not all devices support this.  The
              argument to this option is a  string  of  characters  specifying
              which options to enable.

              p   Wake on PHY activity
              u   Wake on unicast messages
              m   Wake on multicast messages
              b   Wake on broadcast messages
              a   Wake on ARP
              g   Wake on MagicPacket™
              s   Enable SecureOn™ password for MagicPacket™
              d   Disable  (wake  on  nothing).  This option
                  clears all previous options.So it appears that my Intel ethernet is set to wake on MagicPacket but could be set to PHY, unicast, multicast, broadcast or MagicPacket with something like:```
sudo ethtool -s eth0 wol u
```I suspect you could drop that into /etc/rc.local without the sudo, of course.

I am frankly on uncharted ground here. I have never attempted WOL.

---

