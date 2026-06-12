---
title: "Renaming interfaces eth0 or lo or wlan0 to something else."
date: 2011-07-17
forum: New to Ubuntu
---

### Post by darthgarlic on 2011-07-17
How do I rename eth0 to something more descriptive? If I rename eth0 to howard_the_wonder_llama for example will that screw up other programs or processes because they look for them by name/? Will the new name show up in an ifconfig request?

I have already tried editing /etc/udev/rules.d/70-persistent-net.rules with no noticeable change.

---

### Post by HermanAB on 2011-07-17
The names are assigned in /etc/udev/whatever/70-persistent-network-rules or some such.  Just go and trawl through /etc/udev and you will figure it out.

---

### Post by darthgarlic on 2011-07-17
I found it and used nano to rename eth0 to wired_ethernet, after rebooting the interface failed to work. I changed the name back and now it works. I guess I answered my own question as far as being able to change the name and have it work.

---

### Post by ercferret18 on 2011-07-17
maybe you could use a shell variable:)

$ethernet or something like that

---

### Post by khanx on 2011-08-11
There should be a simple solution to this...

---

### Post by CatKiller on 2011-08-11
Why? You can call your connection anything you want. Changing the device name doesn't make any sense - in the same way that you wouldn't try to change the device name of /dev/sda1, you'd just give that partition a label.

---

### Post by haqking on 2011-08-11
[http://www.science.uva.nl/research/air/wiki/LogicalInterfaceNames](http://www.science.uva.nl/research/air/wiki/LogicalInterfaceNames)

[http://linux.die.net/man/8/ifrename](http://linux.die.net/man/8/ifrename)

i think also you can use udev to rename interfaces ?

man udev

---

### Post by grahammechanical on 2011-08-11
Have you tried using Network Manager Edit Connections to change the connection name? It will let you do it. And although I cannot say for certain we might find that in 11.10 get get labels like Wired Connection 1. It is like that in my 11.10 Alpha 2.

Whatever you call the connection it still has to match up to eth0, eth1 and wlan0 because these are the labels that the system uses. Network manager ought to do the matching up or we would not be able to give a name to the connection.

Regards.

---

### Post by haqking on 2011-08-11
> **grahammechanical said:**
> Have you tried using Network Manager Edit Connections to change the connection name? It will let you do it. And although I cannot say for certain we might find that in 11.10 get get labels like Wired Connection 1. It is like that in my 11.10 Alpha 2.

Whatever you call the connection it still has to match up to eth0, eth1 and wlan0 because these are the labels that the system uses. Network manager ought to do the matching up or we would not be able to give a name to the connection.

Regards.


Connection name and Interface name are completely different

My interface Wlan0 has about 20 connection names based on the connection but the interface name remains the same

I beleive you can rename the interfaces names with ifrename [http://linux.die.net/man/8/ifrename](http://linux.die.net/man/8/ifrename)

---

### Post by YesWeCan on 2011-08-11
I wanted to make sure each interface card had a fixed name. I was having trouble because on each reboot the names got shuffled up for some reason.

I read the /etc/udev/rules.d/README and did what it said.
I copied 70_persistent-net.rules to 80_persistent-net.rules
Then I edited 80 and only changed the names within the "".
```
# This file was manually generated
# Changed the default names for each ethernet interface
#
# You can modify it, as long as you keep each rule on a single
# line, and change only the value of the NAME= key.

# PCI device 0x10ec:0x8139 (8139too)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:0a:cd:19:c1:87", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="[COLOR="Red"]eth3[/COLOR]"

# PCI device 0x10de:0x0057 (forcedeth)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:14:85:2d:2c:54", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="[COLOR="red"]eth2[/COLOR]"

# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:25:22:9f:be:af", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="[COLOR="red"]eth1[/COLOR]"

# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:25:22:9f:be:ae", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="[COLOR="red"]eth0[/COLOR]"
```

and this works just fine.
It might be that the name cannot be longer than some length perhaps. Try it with a shorter name just to get it working.

---

### Post by JKyleOKC on 2011-08-11
Everyone seems to be overlooking the fact that the interface's device name occurs in a number of places, and if you change the actual device name itself, you have to track down ***ALL*** of those places and make the same change to each.

As YesWeCan noted, you can force consistent device naming by proper setup of the udev rules; I have a system with three network adapters in it, and use this to force the adapters to always have the same names.

However, device names appear in several files of the /etc directory, and several more in the /dev directory, as well as being configured into the network manager applet and possibly several other user-configuration files.

The best bet is to use udev to force consistent naming, if you have more than one adapter, and then create environment variables to establish human-friendly versions, such as WiredNet=eth0 or WirlessNet=wlan0. You can then type "ifconfig $WiredNet" to determine the settings. You can add the commands to create those variables in your hidden .bashrc file and they will then show up each time you log in.

---

