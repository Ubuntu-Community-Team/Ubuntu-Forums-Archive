---
title: "Network Link speed (revisited)"
date: 2005-09-06
forum: Networking &amp; Wireless
---

### Post by Gigalo on 2005-09-06
I realise that there may be other posts with a solution to my problem.  Unfortunately, I seem to be unable to find any references to the information that I seek.

I have an Intel D865Perl board, with built on Gigabit lan.  I have an Intel 16 port switch at 10/100.  The onboard network seems to work fine with the switch, in terms of negotiating 100BaseTX, as I can tell by the led lighting on the switch.

What I require is instruction on what hex codes to use with my network hardware in order to set it to full-duplex mode at 100BaseTX.

I have tried several things already, including

'sudo ifconfig eth0 media 100BaseTX'

The response:

'port: SIOCSIFMAP: Operation not supported'

Be assured, eth0 IS valid and up, as this message is being sent through that device.

The relavent lspci output for my network hardware is as follows:

0000:02:01.0 Ethernet controller: Intel Corp. 82547EI Gigabit Ethernet Controller (LOM)

Thank you for any assistance in this matter.

---

### Post by Gigalo on 2005-09-06
I FOUND A SOLUTION!!!!

Now, I just have to find out how to make it stick.

I found the command ethtool.

With this nifty little tool, I ended up turning autonegotiation of the network settings OFF, and set the link to 100BaseT, full-duplex manually.

Can anyone tell me if this change will stick past a reboot, and if not, what do I need to do to make it stick.

The code is as follows (for my setup, of course):

ethtool -s eth0 speed 100 duplex full autoneg off

Thanks.

Michael

---

### Post by joshuapurcell on 2005-09-15
I'm interested in finding out how to make my network card always stay at full duplex after reboot as well. The autonegotiation on my switch does not work, so I find myself constantly using ethtool to change the duplex and autonegotiation at startup manually.

In Red Hat you can edit /etc/sysconfig/network-scripts/ifcfg-eth0 with this line:
ETHTOOL_OPTS="speed 100 duplex full autoneg off"

There are two files that I'm guessing could work in the same way here:
/etc/network/interfaces
/etc/network/options

I've looked at the man page for interfaces and it says nothing about giving ethtool options, and there is no man page for /etc/network/options. Any ideas?

---

### Post by Gigalo on 2005-09-16
Joshua, I ended up hacking the change in place by just placing the appropriate ethtool line in the file /etc/rcS.d/S75sudo.  I placed

ethtool -s eth0 speed 100 autoneg off duplex full

as the second to last line (right before "exit 0")

That has me up and running right at boot.

I know that it isn't really reccommended to do that, but it works.  At least for the short term, and until I can find a different solution, it will work.

Michael.

---

### Post by joshuapurcell on 2005-09-20
I found out how to get this to work at bootup through using the /etc/network/interfaces file. Here's what my file looks like:```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
iface eth0 inet dhcp




**up sudo ethtool -s eth0 autoneg off speed 100 duplex full**
auto eth0
```
The important part is the ethtool line, and it only worked for me when I had it above the "auto eth0" portion of the file for some weird reason. Also, adding sudo to the command helped to get rid of an error I recieved when running the **ifup** command from my normal username, but I don't think it would be needed at startup (haven't tested that out).

---

### Post by mlomker on 2005-09-20
> 
iface eth0 inet dhcp
**up sudo ethtool -s eth0 autoneg off speed 100 duplex full**
auto eth0

The important part is the ethtool line, and it only worked for me when I had it above the "auto eth0" portion of the file for some weird reason. 


That's because it has to be listed under the proper interface, in this case eth0.  I'd actually recommend changing that to **pre-up**, but if it works for you then that's cool.

---

### Post by joshuapurcell on 2005-09-21
[QUOTE=mlomker]That's because it has to be listed under the proper interface, in this case eth0.  I'd actually recommend changing that to **pre-up**, but if it works for you then that's cool.[/QUOTE]
I'll try pre-up and see how it does, and if it doesn't work I'll just change back. Also, I didn't like having sudo in there... and it seems to work properly without it at startup. Thanks for the help.

---

### Post by mlomker on 2005-09-21
> I didn't like having sudo in there... and it seems to work properly without it at startup.

Everything in your startup scripts run as root already.

---

### Post by tflanders on 2006-06-11
[QUOTE=joshuapurcell]I found out how to get this to work at bootup through using the /etc/network/interfaces file. Here's what my file looks like:```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
iface eth0 inet dhcp




**up sudo ethtool -s eth0 autoneg off speed 100 duplex full**
auto eth0
```
The important part is the ethtool line, and it only worked for me when I had it above the "auto eth0" portion of the file for some weird reason. Also, adding sudo to the command helped to get rid of an error I recieved when running the **ifup** command from my normal username, but I don't think it would be needed at startup (haven't tested that out).[/QUOTE]

**I couldn't get any of the above things to work so I reverted back to /etc/rc.local and made it like the below config.**

My file:

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
/usr/sbin/ethtool -s eth1 speed 100 duplex full autoneg off
/etc/init.d/networking restart
exit 0

---

