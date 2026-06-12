---
title: "Power on Computer over Ethernet cable"
date: 2015-07-23
forum: Networking &amp; Wireless
---

### Post by penuel1310 on 2015-07-23
Hey guys, how can I power on a computer over Ethernet cable?
(see diagram)

I want to power on Computer 2 by using Computer 1 over Ethernet cable. I can power off Computer 2, cause I can login to Computer 2 from Computer 1 via SSH. But how do I power on the computer over Ethernet cable? 
I'm just interested about knowing if it's possible or not, If so then how?
Something to do with wake-on-LAN or ether-wake??

---

### Post by Lars Noodén on 2015-07-23
Yes, that would be wake-on-lan and works only on the same LAN.  The details of turning it on vary a little depending on the card you have on the target.  , 

[https://help.ubuntu.com/community/WakeOnLan](https://help.ubuntu.com/community/WakeOnLan)

---

### Post by tgalati4 on 2015-07-24
I have some older Dell PowerEdge servers that have Power-on-LAN as well as Wake-on-LAN.  You typically activate it in BIOS and then send an *ethtool* command activate the network card.  On the Dells, you have to put the *ethtool* command in /etc/rc.local so that it gets set at every boot.  On other computers the setting is sticky.  

Send the magic packet (WoL) using any method.  If the machine is powered off, it will boot from a cold condition.  If the machine is asleep, then it will wake.

So Power-on-LAN needs 3 things to work properly:

1.  A BIOS that supports it.  The power-on circuitry is often controlled by the BIOS through ACPI and interrupt conditions.
2.  A network card that can be set to listen to magic packets.  Most, but not all, network cards support WoL.
3.  An *ethtool* setting to sets the network card to listen for magic packets.

An alternative is to purchase a powerstrip with an ethernet port that performs the same thing.

---

### Post by penuel1310 on 2015-07-27
My Ethernet card supports Wake-On-LAN, but the BIOS does not have any Wake-On-LAN option or anything similar. What can I do? Any solution for that?

---

### Post by tgalati4 on 2015-07-27
Try leaving the PCI slot powered that hosts the network card while the computer is shut down.  Install *acpitool* and examine:

```
sudo apt-get install acpitool
acpitool -w
```

Use the -W switch to keep part of the bus awake during sleep.

When you shut your computer down completely, you should see network activity flashes on the back of the network connection.  That way PoL and WoL will work when the computer is either asleep or shut down.  If no network activity, then no WoL.  

Not all computers support PoL so you will have to continue to research.

---

