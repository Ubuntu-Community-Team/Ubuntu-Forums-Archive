---
title: "problem with Sitecom wl-173 router"
date: 2008-08-25
forum: Networking &amp; Wireless
---

### Post by giuliopulina on 2008-08-25
Hi, I have a strange problem with the Sitecom wl-173 router, connected to an ADSL modem: after setting up correctly an unencrypted wireless network (with DHCP enabled), I can get an IP address but internet connection doesn't work. 
I've tried to use Wifi Radar and NetworkManager and the behaviour is the same. In addition, internet connection works wery well with Windows XP, and the router firewall is disabled.
Can you help me?

Giulio

---

### Post by Crafty Kisses on 2008-08-25
Post the results of:
```
lshw -C network
```

---

### Post by giuliopulina on 2008-08-25
> **Codename said:**
> Post the results of:
```
lshw -C network
```

I'll post you this evening (I'm not at home)! Thanks in advance :)

---

### Post by giuliopulina on 2008-08-25
The output is here: 

*-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 02
       serial: 00:13:02:2e:e5:12
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=192.168.0.117 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg
  *-network
       description: Ethernet interface
       product: NetLink BCM5789 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 21
       serial: 00:16:36:4e:5f:95
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 firmware=5789-v3.49a latency=0 link=no module=tg3 multicast=yes port=twisted pair

My internet connection downloads only the first bytes of the pages, and then it stops in waiting state.

---

### Post by coffeecat on 2008-08-25
When you get a problem like this - Windows XP can access the Internet and Linux can't through the same router - it's always worth checking that it's not an IPv6 issue.

Try this quick diagnostic test: open firefox in Ubuntu and type 'about:config' (no quotes) in the address bar. Click the warning away. Type 'ipv6' (again, no quotes) in the filter. You'll have one line starting 'network.dns,disableIPv6'. Change the false value to true. Now close down firefox and restart. If you can now browse the net, then you have a problem with IPv6 but you haven't fixed it, because Synaptic, update manager and any other app that needs to connect to the net will be affected.

Anyway, try this and if IPv6 is the problem, I'll suggest some possible fixes.

---

### Post by giuliopulina on 2008-08-25
> **coffeecat said:**
> When you get a problem like this - Windows XP can access the Internet and Linux can't through the same router - it's always worth checking that it's not an IPv6 issue.

Try this quick diagnostic test: open firefox in Ubuntu and type 'about:config' (no quotes) in the address bar. Click the warning away. Type 'ipv6' (again, no quotes) in the filter. You'll have one line starting 'network.dns,disableIPv6'. Change the false value to true. Now close down firefox and restart. If you can now browse the net, then you have a problem with IPv6 but you haven't fixed it, because Synaptic, update manager and any other app that needs to connect to the net will be affected.

Anyway, try this and if IPv6 is the problem, I'll suggest some possible fixes.

I've tried yesterday, but unfortunately it's not that :( ipv6 is disabled in firefox and also blacklisted.
Anyway, why is wireless interface named wmaster0? I thought it was wlan0!

---

### Post by coffeecat on 2008-08-25
> **giuliopulina said:**
> I've tried yesterday, but unfortunately it's not that :( ipv6 is disabled in firefox and also blacklisted.

Ah well. It was worth a try.

> **giuliopulina said:**
> Anyway, why is wireless interface named wmaster0? I thought it was wlan0!

I believe it depends on the wireless chipset and driver. With my Intel 2200BG wireless on my laptop, it comes up as eth1. :?

**Edit:** another thought. Have you tried setting up your Ubuntu machine with a static IP address? You'll have to put the subnet mask, gateway and DNS server addresses in by hand, of course.

---

### Post by giuliopulina on 2008-08-25
> **coffeecat said:**
> Ah well. It was worth a try.



I believe it depends on the wireless chipset and driver. With my Intel 2200BG wireless on my laptop, it comes up as eth1. :?

**Edit:** another thought. Have you tried setting up your Ubuntu machine with a static IP address? You'll have to put the subnet mask, gateway and DNS server addresses in by hand, of course.

I'm going to try, as soon as I reboot to Ubuntu for the n-th time :)

---

### Post by giuliopulina on 2008-08-26
i've tried, but the internet connection doesn't work.

---

### Post by coffeecat on 2008-08-26
I'm really out of ideas, but it might be worth trying a ping test to see whether this is a name resolution problem, or whether the Sitecom router is preventing your Ubuntu machine from connecting to the internet for some reason, even though it as assigning an IP address. The usual one to try is Google, but Google's numerical address changes every so often so rather than me suggesting the address, find the current one in Windows. In Windows, open a command prompt and type:

```
ping www.google.com
```.. and note the numerical (of the form 000.111.222.333) address that is returned. Now open a terminal in Ubuntu and try the same code (with google.com) and also with the numerical address.

If 'ping [www.google.com]("http://www.google.com")' doesn't work and 'ping *numerical address*' does, then it must be a name resolution problem. If neither work - well I don't know.

---

### Post by giuliopulina on 2008-08-26
> **coffeecat said:**
> I'm really out of ideas, but it might be worth trying a ping test to see whether this is a name resolution problem, or whether the Sitecom router is preventing your Ubuntu machine from connecting to the internet for some reason, even though it as assigning an IP address. The usual one to try is Google, but Google's numerical address changes every so often so rather than me suggesting the address, find the current one in Windows. In Windows, open a command prompt and type:

```
ping www.google.com
```.. and note the numerical (of the form 000.111.222.333) address that is returned. Now open a terminal in Ubuntu and try the same code (with google.com) and also with the numerical address.

If 'ping [www.google.com]("http://www.google.com")' doesn't work and 'ping *numerical address*' does, then it must be a name resolution problem. If neither work - well I don't know.

thank you again, but I just tried and the ping command in Ubuntu works both with URL and numerical address:
ping [www.google.it](www.google.it)
PING [www.l.google.com](www.l.google.com) (209.85.135.99) 56(84) bytes of data
64 bytes from mu-in-f99.google.com (209.85.135.99): icmp_seq=1 ttl=242 time=107 ms (and so on...)
pinging the numerical address produces the same result.

I'm going to contact Sitecom customer care, perhaps somebody had the same problem. :(

---

### Post by giuliopulina on 2008-08-26
I noticed that internet connection works for some websites (for example, [www.tgcom.it](www.tgcom.it)), while for others sites it stops (for example, [www.libero.it](www.libero.it)). In fact, when I ping img1.iol.it I don't receive any reply.
Can it be an MTU problem? I tried to set MTU to a lower value but the situation didn't change.

---

### Post by Nod Nolan on 2009-08-22
I've been searching for the solution for this for the last 24 hours.

I could connect to the router, but the router would not connect to the net.

It seems the problem has been resolved after I unchecked the "Turbo Mode" and "WMM" buttons in the Advanced wireless settings menu.

---

