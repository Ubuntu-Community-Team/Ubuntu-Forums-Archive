---
title: "Cannot connect to internet"
date: 2008-08-17
forum: Networking &amp; Wireless
---

### Post by focus310 on 2008-08-17
Hello:

I am unable to connect to the internet.

I ran lshw -C network and result show the following:
*-network
description: **Wireless interface**
product: **PRO/Wireless 3945ABG Network Connection**
vendor: Intel Corporation
physical id: 0
bus info: pci@0000:0b:00.0
logical name: wmaster0
version: 02
serial: 00:1f:3c:9b:7a:a7
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical wireless
configuration: broadcast=yes **driver=iwl3945 **ip=192.168.1.100 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g

I am guessing that my wireless card is being recognized.  I believe it can also my driver.

I then went to System > Administration > Network Settings.  I went to Wireless Connection under the Connections tab.   I entered my Network Name (ESSID), Password type - WEP key (hexadecimal) and the network password.  I also set Automatic configuration for DHCP under Connection Settings.  I click OK and go to Firefox.  I type a website address and all I get is Looking up www.<whatever>.com.

I am at a loss as to what to do.  This doesn't make any sense to me.

Can someone help me out?
Thanks.

---

### Post by coffeecat on 2008-08-17
From the information you give, it looks as though your laptop has connected to your router. From lshw -C network:

> **focus310 said:**
> ip=192.168.1.100

You have a local network IP address. Which is interesting because you imply that you did lshw -C network **before** you went into Network Settings. If you have a local IP address, the computer must have connected to the router. Did you try configuring the Network Manager applet (on the upper panel) first, because that was probably all you needed to have done? It usually isn't necessary to go into System > Administration > Network, particuarly with a well-supported wireless chipset such as Intel.

Anyway - to confirm that you are indeed connected to the router and that it is assigning you an IP address, post the output of:

```
ifconfig
```and

```
iwconfig
```Also, please post details of your router, because...

> **focus310 said:**
> all I get is Looking up www.<whatever>.com.

... if you are connected to the router, this suggests either a DNS problem or an IPv6 one.

IPv6 can be a issue with older routers or those with older firmware, and this leads either to very slow resolution of internet addresses or what you are getting. It's not a problem with Windows XP, because IPv6 is not enabled by default in XP.

A quick diagnostic test for IPv6: Open firefox and type 'about:config' (no quotes) in the address bar. Tell the childish 'Here be dragons' message to get lost and type 'ipv6' in the filter and you will get one line starting, 'network.dns.disableIPv6...' Double-click on false to change it to true. Close down firefox and restart. If you can now browse the internet, you have an IPv6 problem and you need to do something about the router or disable IPv6 in Ubuntu. If this doesn't make any difference, we need to look at other things.

---

