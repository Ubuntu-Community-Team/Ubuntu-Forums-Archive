---
title: "Can't get return for ifdown - Problem with eth0?"
date: 2007-06-15
forum: Networking &amp; Wireless
---

### Post by Halfling Rogue on 2007-06-15
Hey there, I'm running Dapper Drake 6.06 on a pentium IBM Thinkpad A20m, with a [Linksys WMP11v4 802.11b]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_g-l/#l") PCI wireless card. I've been following the instructions on [this page]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper") and made it as far as "[2.5.2.3. ]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#head-558430826c18c7a080e3eb11984fc8138cc2a4f2")Loading the new driver module" before running into problems.

ndiswrapper -l returns "neti2120  driver present, hardware present", and ifconfig and iwconfig both have wlan0 in the list (along with lo, eth0, irda0, and sit0).

But when I tried sudo ifdown wlan0 I get "ifdown: interface wlan0 not configured", and sudo ifup wlan0 returns "SIOCADDRT: File exists
Failed to bring up wlan0".

The troubleshooting on the page says it might be because of eth0, so I ran sudo killall dhclient and got "dhclient: no process killed". sudo ifconfig eth0 down got me no return at all.

Help?

---

### Post by kevdog on 2007-06-16
Do you need all those interface names (along with lo, eth0, irda0, and sit0)?

What does your /etc/network/interfaces file look like along with /etc/iftab??

---

### Post by Halfling Rogue on 2007-06-16
Not sure it matters either way. My other laptop (same version of Dapper, same wireless card, a ThinkPad 390E) has all of them except eth0 and works just fine.

Interfaces looks like this:

```
#The loopback network interface
auto lo
iface lo inet loopback

iface wlan0 inet static
address 192.168.1.4
netmask 255.255.255.0
gateway 192.168.1.1
```

Iftab reads:

```
eth0 mac 00:90:27:97:c9:da arp 1
```

---

### Post by Halfling Rogue on 2007-06-16
Pinging the router and the laptop itself gets responses; no idea why it isn't working.

---

### Post by Halfling Rogue on 2007-06-16
Never mind! Turns out I hadn't specified a DNS Server. Works fine now.

---

