---
title: "WOL not working on select ports"
date: 2019-01-04
forum: Networking &amp; Wireless
---

### Post by wcnackers on 2019-01-04
I have a motherboard my company designed that uses Intel Dual Skylake or Cascade Lake Processors.  The PCH is an Intel Lewisburg C600 series and the board has 1-dual Intel i350 ethernet controller, 1-quad Intel i350 ethernet controller and 1 Intel i210 controller.

The problem I am having is that WOL works on port 0 of the dual controller, port 0 of the quad controller and on the single i210 port.  It does not work on port 1 of the dual i350 or on ports 1, 2 or 3 of the quad controller.

For example, the port names for the dual i350 are enp2s0f0 and enp2s0f1.  When I type [COLOR=#ff0000]"sudo ethtool enp2s0f0"[/COLOR], I get [COLOR=#ff0000]"Supports Wake-on: pumbg, Wake-on: g"[/COLOR]  But when I type [COLOR=#ff0000]"sudo ethtool enp2s0f1"[/COLOR] I get [COLOR=#ff0000]"Support Wake-on: d, Wake-on: d"[/COLOR].  I then try to enable WOL on the port by typing [COLOR=#ff0000]"sudo ethtool -s enp2s0f1 wol g"[/COLOR], but it returns "Cannot set new wake-on-lan settings:  Operation not supported.  not seeting wol".  

I have tried this on Ubuntu 16.04 and 18.04 with the same results.  And I know the hardware works because WOL works on all ports when I run Windows 10.  So I am sure there is something I am not doing correctly but for the life of me, I can't figure it out.

Any help will be much appreciated.  Thanks!

WCN

---

