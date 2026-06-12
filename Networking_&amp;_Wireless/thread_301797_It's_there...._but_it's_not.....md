---
title: "It's there.... but it's not...."
date: 2006-11-17
forum: Networking &amp; Wireless
---

### Post by jlipoth on 2006-11-17
I am trying to install a D-link WNA-2330 into my laptop.  I started by doing and OEM install and it appeared to detect it.  It even asked me for a wep password!  I was super excited!  When I finished the install, I booted up the computer and opened up the Network setting....   ...It wasn't there!  I looked at some of the trouble shooting documentation and I know this much.

[COLOR="DarkRed"]

sudo lshw

     *-network UNCLAIMED
          description: Ethernet controller
          product: AR5212 802.11abg NIC
          vendor: Atheros Communications, Inc.
          physical id: 1
          bus info: pci@04:00.0
          version: 01
          width: 32 bits
          clock: 33MHz
          capabilities: cap_list
          resources: iomemory:52000000-5200ffff irq:185[/COLOR]

and


[COLOR="DarkRed"]lspci -v

04:00.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
        Subsystem: D-Link System Inc Unknown device 3a1a
        Flags: medium devsel, IRQ 185
        Memory at 52000000 (32-bit, non-prefetchable) [disabled] [size=64K]
        Capabilities: <access denied>
[/COLOR]

I also tried typing iwconfig, but I didn't see it there.  I'm assuming that 's pretty much the same as looking at the network settings to see if it's there.  I'm very new to Ubuntu and I think I may be in over my head; but if I can get this to work, I will be one step farther away from having to use windows.  I really don't want to go back to windows. :(](*,)   Thanks

---

### Post by jlipoth on 2006-11-17
I'm abandoning this installation and returning the D-Link to the store because I got my internal one work!  I took a second try at the broadcom wireless tutorial and it worked great!

---

