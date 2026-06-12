---
title: "dsl-300t and wgr614 in pppoa mode"
date: 2007-08-25
forum: Networking &amp; Wireless
---

### Post by mrgrapefruit on 2007-08-25
My ISP uses PPPoA. The D-Link DSL-300T connects to the internet just fine and passes the public address to whatever device connects to it (i.e. if you plug it straight into eth0, ubuntu can connect just fine).

The problem starts when trying to get the Netgear WGR-614 v4 to work with this. It picks up the public address (which it sets to the same as the gateway address which I believe is correct) and everything looks fine, but then when it tries to connect to the internet it fails. I initially thought it might just be DNS resolution, but when I got the DNS address from my ISP and manually entered it, it didn't help. I can't set the DSL-300T to bridge mode (a config which I know worked before) because the WGR-614 can only handle PPPoE.

The annoying thing is my Apple AirPort Extreme can use the DSL-300T just fine, it just doesn't have any ethernet ports to allow my ubuntu box access at the same time.

I'd be grateful for any suggestions other than 'buy new equipment', as I'm a student...

---

