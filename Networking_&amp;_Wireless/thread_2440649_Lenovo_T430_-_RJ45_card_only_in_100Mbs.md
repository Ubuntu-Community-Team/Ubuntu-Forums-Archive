---
title: "Lenovo T430 - RJ45 card only in 100Mbs"
date: 2020-04-13
forum: Networking &amp; Wireless
---

### Post by chlowden on 2020-04-13
Hello
I am recently having an issue where I can NO LONGER get my LENOVO T430 to connect at 1Gbs on ethernet cables.
I have tried on many cables, many ethernet wall ports but I cannot go above 100Mbs. The same cables etc work fine on other machines

The machine has an Intel e1000e driver and I have installed the latest version.
```
user1@user1-t430:~$ sudo lshw -C network
[sudo] password for user1: 
  *-network                 
       description: Ethernet interface
       product: 82579LM Gigabit Network Connection (Lewisville)
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: enp0s25
       version: 04
       serial: 28:d2:44:26:94:85
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.6.0-NAPI duplex=full firmware=0.13-3 ip=192.168.0.19 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:30 memory:f2500000-f251ffff memory:f253b000-f253bfff ioport:5080(size=32)

```

I have tried forcing 1gbits using both 
```
nm-connection-editor
```

```
sudo ethtool -s enp0s25 speed 1000 duplex full autoneg off
```

Both have the same result of turning off the service. In the system prefs, the Wired config becomes greyed out and I have restart to machine to get the network connection working again.
This did work not so long ago and I cannot see what has changed.

```
user1@user1-t430:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.4 LTS
Release:    18.04
Codename:    bionic

```

Any thoughts would be most welcome.
Thank you

---

### Post by chlowden on 2020-04-18
I have change the router and the machine still only offers 100mbs. is there a way to check the hardware?

---

### Post by chlowden on 2020-04-25
I installed the Ubuntu hard drive into a 2nd T340 where the ethernet  port works in gigabit and with the Ubuntu systems was also limited to  100Mbs so this does not seem to be a hardware issue.

---

### Post by coffeecat on 2020-04-25
Hello, sorry you have not had any replies. I've moved this thread from the *Hardware* sub-forum to *Networking & Wireless* in the hope that one of our members interested in network hardware will be able to help. This sub-forum is not exclusively for wireless cards.

Good luck!

---

### Post by CelticWarrior on 2020-04-25
> **chlowden said:**
> I installed the Ubuntu hard drive into a 2nd T340 where the ethernet  port works in gigabit and with the Ubuntu systems was also limited to  100Mbs so this does not seem to be a hardware issue.

Indeed, it does not seem to be an hardware issue. To confirm you can boot a live session to see how it behaves with a different OS.

---

### Post by chlowden on 2020-05-08
Thank you Celtic for your confirmation. After booting of a Ubuntu USB stick, the gigabit showed up. 

In a desperate attempt I thought that maybe a system jerk might break / repair something. I hard crashed the portable, disconnected the mains supply, took out the battery (not the rom battery) and made and ate lunch. 2 hours later, I put the battery back and reconnected the mains supply , BUT DID NOT CONNECT THE ETHERNET CABLE. The machine was already in airplane mode. I restarted the machine, checked that the ifconfig and sudo lshw -C  to be sure that there was no network connection and then reconnected the ethernet cable. 
MIRACLE : the machine  sees 1Gbs.

But not really. It slipped back to 100kbs after about 10 mins.

But I think I have the culprit. I suspect that the female RJ45 socket on the portable is "tired", dirty or whatever but not making consistently good connections.
So many blame the cabling, but check the socket condition too! wiggle the cable in the socket and waiting to see if the connection breaks.

---

