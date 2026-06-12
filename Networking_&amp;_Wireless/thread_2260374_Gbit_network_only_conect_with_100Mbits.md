---
title: "Gbit network only conect with 100Mbit/s"
date: 2015-01-11
forum: Networking &amp; Wireless
---

### Post by Azyx on 2015-01-11
Have Ubuntu 14.04

My homenetwork interface is from lshw -html is:

```
[TABLE="class: node"]
[TR]
[TD="class: first"]id:[/TD]
[TD="class: second"]network[/TD]
[/TR]
[TR]
[TD="class: first"]description:[/TD]
[TD="class: second"]Ethernet interface[/TD]
[/TR]
[TR]
[TD="class: first"]product:[/TD]
[TD="class: second"]MCP73 Ethernet[/TD]
[/TR]
[TR]
[TD="class: first"]vendor:[/TD]
[TD="class: second"]NVIDIA Corporation[/TD]
[/TR]
[TR]
[TD="class: first"]physical id:[/TD]
[TD="class: second"]f[/TD]
[/TR]
[TR]
[TD="class: first"]bus info:[/TD]
[TD="class: second"]pci@0000:00:0f.0[/TD]
[/TR]
[TR]
[TD="class: first"]logical name:[/TD]
[TD="class: second"]eth0[/TD]
[/TR]
[TR]
[TD="class: first"]version:[/TD]
[TD="class: second"]a2[/TD]
[/TR]
[TR]
[TD="class: first"]serial:[/TD]
[TD="class: second"]00:21:85:93:20:c4[/TD]
[/TR]
[TR]
[TD="class: first"]size:[/TD]
[TD="class: second"]1Gbit/s[/TD]
[/TR]
[TR]
[TD="class: first"]capacity:[/TD]
[TD="class: second"]1Gbit/s[/TD]
[/TR]
[TR]
[TD="class: first"]width:[/TD]
[TD="class: second"]32 bits[/TD]
[/TR]
[TR]
[TD="class: first"]clock:[/TD]
[TD="class: second"]66MHz[/TD]
[/TR]
[TR]
[TD="class: first"]capabilities:[/TD]
[TD="class: second"]pm msi bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation[/TD]
[/TR]
[TR]
[TD="class: first"]configuration:[/TD]
[TD="class: second"][TABLE]
[TR]
[TD="class: sub-first"] autonegotiation[/TD]
[TD]=[/TD]
[TD]on[/TD]
[/TR]
[TR]
[TD="class: sub-first"] broadcast[/TD]
[TD]=[/TD]
[TD]yes[/TD]
[/TR]
[TR]
[TD="class: sub-first"] driver[/TD]
[TD]=[/TD]
[TD]forcedeth[/TD]
[/TR]
[TR]
[TD="class: sub-first"] driverversion[/TD]
[TD]=[/TD]
[TD]0.64[/TD]
[/TR]
[TR]
[TD="class: sub-first"] duplex[/TD]
[TD]=[/TD]
[TD]full[/TD]
[/TR]
[TR]
[TD="class: sub-first"] ip[/TD]
[TD]=[/TD]
[TD]192.168.0.2[/TD]
[/TR]
[TR]
[TD="class: sub-first"] latency[/TD]
[TD]=[/TD]
[TD]0[/TD]
[/TR]
[TR]
[TD="class: sub-first"] link[/TD]
[TD]=[/TD]
[TD]yes[/TD]
[/TR]
[TR]
[TD="class: sub-first"] maxlatency[/TD]
[TD]=[/TD]
[TD]20[/TD]
[/TR]
[TR]
[TD="class: sub-first"] mingnt[/TD]
[TD]=[/TD]
[TD]1[/TD]
[/TR]
[TR]
[TD="class: sub-first"] multicast[/TD]
[TD]=[/TD]
[TD]yes[/TD]
[/TR]
[TR]
[TD="class: sub-first"] port[/TD]
[TD]=[/TD]
[TD]MII[/TD]
[/TR]
[TR]
[TD="class: sub-first"] speed[/TD]
[TD]=[/TD]
[TD]1Gbit/s[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[TR]
[TD="class: first"]resources:[/TD]
[TD="class: second"][TABLE]
[TR]
[TD="class: sub-first"] irq[/TD]
[TD]:[/TD]
[TD]43[/TD]
[/TR]
[TR]
[TD="class: sub-first"] memory[/TD]
[TD]:[/TD]
[TD]fcf77000-fcf77fff[/TD]
[/TR]
[TR]
[TD="class: sub-first"] ioport[/TD]
[TD]:[/TD]
[TD]c880(size=8)[/TD]
[/TR]
[TR]
[TD="class: sub-first"] memory[/TD]
[TD]:[/TD]
[TD]fcf7e800-fcf7e8ff[/TD]
[/TR]
[TR]
[TD="class: sub-first"] memory[/TD]
[TD]:[/TD]
[TD]fcf7e400-fcf7e40f[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]

```

Network manager says it and the switch indicator says 100Mbit/s.

I have tested with different cables (Cat6 and cat 5e), to other computers who have Gbits-connections, but this networdcard just connect to 100Mbit/s. See attached screen shoot.

Thanx to all tips to help fix this problem.

Edit. lspci get this for the Ethernet Card:

[CODE][04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)
/CODE]

---

### Post by TheFu on 2015-01-12
What router/switch is it connected into? vendor and model please.
I assume you've swapped the ports around and retested?

---

### Post by Azyx on 2015-01-12
> **TheFu said:**
> What router/switch is it connected into? vendor and model please.
I assume you've swapped the ports around and retested?

Yes now I have.Model  tekComm-805AG\8A (0503)

But now it worked :) Cat 5E does not always manage 1Gbit :(  Also seems to be some kind of memory or stuff in the switch...

Thanx.

---

### Post by TheFu on 2015-01-12
CAT5e has plenty of capacity to support GigE connections. Using CAT6 only provides more headroom that isn't needed and a thicker cable.  It is likely the connector on 1 side of that cable has failed in some way.

---

### Post by Azyx on 2015-01-23
Seems to be a problem with the [COLOR=#a52a2a]**tekComm-805AG\8A (0503)**[/COLOR]. It indicate connection, but the computers sometimes does not get an IP (trying to connect all the time), but if I bypass the gigabit switch it get an IP address. Very frustrating, work sometimes, sometimes it's enought to power off and on the Gbit-switch. There some get 100Mbit onetime and 1Gbit another time in the indicator, and sometimes it indicate connection, but the **[COLOR=#a52a2a]Zyxel nbg-418n[/COLOR]** can not deliver IP-connection at all (the client can't connect)

Are there some  technical limitation to connect a switch [COLOR=#a52a2a]**tekComm-805AG\8A (0503) **[/COLOR]after a broadband-router **[COLOR=#a52a2a]Zyxel nbg-418n[/COLOR]** that have the DHCP-server? mac-adresses and stuff should  go thrue the the switch with no problems or?

---

