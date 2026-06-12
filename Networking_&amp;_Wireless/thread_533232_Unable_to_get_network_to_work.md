---
title: "Unable to get network to work"
date: 2007-08-23
forum: Networking &amp; Wireless
---

### Post by Khuong on 2007-08-23
I am new to Ubuntu and a novice on Linux.  I configured a static IP address.  "ifconfig -a" shows the network card as "up" and with the valid IP and gateway.  However, I'm unable to ping my default gateway.  I even try to ping my loopback address "172.0.0.1" and am unsuccessful.  Did I forget to do a step?  Do I need to enable network services or something?  
BTW - the network link light is on and I'm confident that the router/switch is good (I tried a known good port on the switch).

---

### Post by Jose Catre-Vandis on 2007-08-23
Please report the output of:
```
ifconfig
```
and if wireless
```
iwconfig
```

Also does it connect if you allow dhcp, as opposed to static IP, and is your router set to allow static IPs within the range of the Ip you set?

What is your network card?

---

### Post by Khuong on 2007-08-23
static IP should is within the range.  DHCP does not work either.  My other computer works fine (Windows Vista).  This computer used to be a Windows XP box, but, I recently converted it to Ubuntu.  So, I know the NIC works fine.  I'm wondering if it's a driver issue.  Ifconfig shows the interface as up.  Media = Ethernet.  however, the strange thing is I can't even ping my loopback: 127.0.0.1 as though the protocol stack was not loaded.

any suggestion on where else to look?  I appreciate your help.

---

### Post by Jose Catre-Vandis on 2007-08-25
Is it wired or Wireless NIC?

Do you have any security (WEP/WPA) if wireless?

Please report the output of ifconfig/iwconfig so we can see what is happening?

What do you mean by Media=Ethernet?

Are you using Ubuntu 7.04?

Do you have the Network Manager applet running ( do you have a little icon of two monitors in the tray?) If so what does this say is happening?

---

