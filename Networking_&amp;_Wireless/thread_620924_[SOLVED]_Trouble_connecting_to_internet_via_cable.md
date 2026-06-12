---
title: "[SOLVED] Trouble connecting to internet via cable"
date: 2007-11-23
forum: Networking &amp; Wireless
---

### Post by ruru on 2007-11-23
I have just moved house and am now accessing internet over cable. My xubuntu box won't connect.
I know the card/drivers are OK as I was previously using pppoe without a problem. 
I know my new connection works as I am online with a mac laptop.

I am running xubuntu gutsy and want a wired connection over eth0. 
Below is a bit more info to get things started:

An excerpt from the output of **lshw -C bridge**
```

 *-bridge:0
       description: Ethernet interface
       product: MCP55 Ethernet
       vendor: nVidia Corporation
       physical id: 10
       bus info: pci@0000:00:10.0
       logical name: eth0
       version: a2
       serial: 00:18:f3:49:a6:ef
       size: 100000000
       capacity: 1000000000
       width: 32 bits
       clock: 66MHz
       capabilities: bridge pm msix msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.60 duplex=full ip=192.168.2.18 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s

```


Below, the output from **sudo /etc/init.d/networking restart**.
I wasn't sure if the stuff about pon/poff should be there. I actually uninstalled pppoeconf as I thought it could be getting in the way - as far as I understand (not much!) I shouldn't be using pppoe now.
```

 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth0.pid with pid 5648
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:18:f3:49:a6:ef
Sending on   LPF/eth0/00:18:f3:49:a6:ef
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.2.1 port 67
dsl-provider: ERROR while getting interface flags: No such device
/bin/sh: pon: not found
Failed to bring up dsl-provider.
There is already a pid file /var/run/dhclient.eth0.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:18:f3:49:a6:ef
Sending on   LPF/eth0/00:18:f3:49:a6:ef
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPOFFER from 192.168.2.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.2.1
bound to 192.168.2.19 -- renewal in 1562 seconds.

```

Any help would be much appreciated, I'm almost certain this is just some setting I've screwed up somewhere along the line, but troubleshooting network hardware is beyond me...

---

### Post by mellowd on 2007-11-23
It looks like you are connecting to a cable router as opposed to a cable modem. Am I right?

---

### Post by ruru on 2007-11-23
It's a Scientific Atlanta/Cisco EPC2203 Cable Modem (to quote the sticker on the base).

---

### Post by ruru on 2007-11-23
After two days of searching these forums, I came across a suggestion to unplug the ethernet cable, unplug power to the modem and wait 10 min.
Plug everything back in and it works!

Bizzarre. There must be a better way. But I'm happy and I guess this is solved...

---

### Post by mellowd on 2007-11-24
It depends. If you did one at a time we could have seen where the problem actually came from. That would've taken more time though. Sometimes it is nessecary to unplug the modem for a while. 1 minute should do it. In England here DSL exchanges get reset after 25 minutes if no connection is going through so we sometimes tell us customer to unplug for 30 minutes if we have exhausted all other options. this forces the exchange to use a new line for the connection. This is pretty rare though.

By unplugging the ethernet cable you'll force the pc to reset it's IP address and get a new one from the modem. This also refreshes the DNS and can help sometimes. 

If this happens again, try 1 and then the other. That way you'll be able to find out exactly what caused it.

---

### Post by ruru on 2007-11-24
I think this may be a misunderstanding on my part...
What i didn't make clear is that I was trying to connect with the laptop AND the desktop at the same time.
Having reset the modem (by unplugging), the linux box works fine - but the laptop won't get an IP address (I discovered this morning). The manual for the modem says that up to 31 computers can connect via a switch (I have a fast ethernet switch downstream of the modem now)  - but it seems to me I might need a router to do this?
As I said, networking is not my strong point! but I would dearly like to understand how to do this and I appreciate the help.

---

### Post by mellowd on 2007-11-24
> **ruru said:**
> I think this may be a misunderstanding on my part...
What i didn't make clear is that I was trying to connect with the laptop AND the desktop at the same time.
Having reset the modem (by unplugging), the linux box works fine - but the laptop won't get an IP address (I discovered this morning). The manual for the modem says that up to 31 computers can connect via a switch (I have a fast ethernet switch downstream of the modem now)  - but it seems to me I might need a router to do this?
As I said, networking is not my strong point! but I would dearly like to understand how to do this and I appreciate the help.

What kind of modem have you got?

From what you are saying above, a router may be more beneficial. A switch is a layer 2 device. IP is layer 3. What this means is that a switch doesn't look at IP addresses, it doesn't know anything about them. A switch works on your hardware MAC address, thats how it knows where to send data. A switch will not be able to seperate the laptop and desktop via IP. Essentially, a basic modem will see the switch and everything behind it as one device. This creates a problem giving out IP addresses.

Thinking about it now though, are your computers getting their addresses via dhcp? If so that would mean the modem had some sort of dhcp server in it which more than likely would mean it's pretty advanced. Could you let me know the make and model of both the modem and switch?

---

### Post by ruru on 2007-11-24
the modem model I posted above:
> 
It's a Scientific Atlanta/Cisco EPC2203 Cable Modem (to quote the sticker on the base).


And the switch is a Longshine LCS-FS6108.

Edit: Yes, the addresses are assigned by DHCP

---

### Post by mellowd on 2007-11-24
I've had a look a that modem online and it only has 1 ethernet port. This is the problem. That means the switch is directly connected to that and then shared out. This as I explained above won't work. 

You could buy a router and connect it to the modem like that, but thats too much equipment/mess.

If I were you, I would get rid of that modem and get a new cable modem/router. Make sure that router has multiple ethernet ports and possibly wireless as well if you use that. That one device will do all you need.

---

### Post by ruru on 2007-11-24
Hey, thanks for the help! This is as I was suspecting. I wanted to set up wireless anyway, so a new bit of kit was in the pipeline anyway. Is there anyting I should know before buying a cable modem? Are they all much the same?

One last question - I have two cable outlets in my flat. If I stick a modem on each, will that cause trouble? Or does the cable provider just want to deal with one IP address?

---

### Post by mellowd on 2007-11-24
More than likely they are split from the same cable. Therefore it'll conflict.

For a home setup I've used a netgear before and it worked perfectly for that purpose. The one I had, had a cable connecter, 4 ethernet ports and a wireless access point. So everything you would need

---

