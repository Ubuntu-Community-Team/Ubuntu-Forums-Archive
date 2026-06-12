---
title: "OpenDNS messes with local network browsing?"
date: 2007-09-03
forum: Networking &amp; Wireless
---

### Post by LordMau on 2007-09-03
I've finally tracked down the issue on my way my feisty box was unable to browse my network shares. Ever since my box was dapper I had always overridden my dns server using opendns. I lost my ability to browse shares by edgy and just let it slide and worked around it. However with the stability of fusesmb I now needed dependable access to the shares.

After many misses I nailed it down to my use of opendns. Removing it finally let me see my shares. But still I do prefer to still use during web browsing. I wonder how to achieve this though without sacrificing network browsing.

To break it down:

[LIST]
[*]While using opendns
[LIST=1]
[*]I followed the instuction at the opendns site to add their dns servers
[*]I added wins to the nsswitch.conf file as such the "hosts" line is:
```
"hosts:      dns files mdns wins"
```
[*]Browsing via fusesmb (in thunar) or using pyneighbor I am able to see the workgroup and computer names, but unable to drill down further;
[*]smbtree is unable list the shares like above. I notice that it also parses a 203.xxx.xxx.xxx ip to resolve a local computer;
[/LIST]
[/LIST]

[LIST]
[*]While using opendns and removing the dns line at nsswitch.conf
[LIST=1]
```
"hosts:      files mdns wins"
```
[*]Browsing via fusesmb (in thunar) or using pyneighbor I am able to see the workgroup and computer names, AND the first level of shares, but unable to drill down further;
[*]smbtree is able list the shares like above including the 1st teir of shares but no further. ;
[/LIST]
[/LIST]

[LIST]
[*]While using opendns and removing wins at nsswitch.conf
[LIST=1]
```
"hosts:      dns files mdns"
```
[*]no browsing possible;
[*]smbtree is unable list the shares like above. I notice that it also parses a 203.xxx.xxx.xxx ip to resolve a local computer;
[/LIST]
[/LIST]

[LIST]
[*]Removing opendns
[LIST=1]
[*]I followed the instuction at the opendns site to add their dns servers
[*]nsswitch.conf file includes wins and dns on the "hosts" line is:
```
"hosts:      dns files mdns wins"
```
[*]Browsing via fusesmb (in thunar) or using pyneighbor is successfull, all shares are visible at all levels;
[*]smbtree also list all shares. it doesn't refer to that 203.xxx.xxx.xxx url anymore;
[/LIST]
[/LIST]

Hope that clarifies things. I hope there's a way to use opendns and browse local shares. Or is this problem with opendns use just me so far? TIA.

---

### Post by noob12 on 2007-09-03
Would suggest moving dns later in your sequence (after wins and mdns).  For feisty desktop, I'm using this line:
```

hosts:          files mdns4_minimal [NOTFOUND=return] wins dns mdns4

```

---

### Post by LordMau on 2007-09-03
> **noob12 said:**
> Would suggest moving dns later in your sequence (after wins and mdns).  For feisty desktop, I'm using this line:
```

hosts:          files mdns4_minimal [NOTFOUND=return] wins dns mdns4

```

I actually did move those around but to no effect.

I'm curious with your hosts line though, what do those other lines do (notfound=return and mdns4_minimal)?

---

### Post by noob12 on 2007-09-03
The NOTFOUND=return clause means that resolution will not continue of the resolution module preceding it returns a NOTFOUND result.  The mdns4_minimal module performs a reduced version of the mdns4 lookup, but I would have to lookup the details.  It is the portion that should  precede a dns lookup.  I think the default feisty line is exactly what I have but excluding wins.

Note that when you change order you should reboot.  I don't think changes affect already running processes.

---

### Post by ppietryga on 2007-09-03
It's just a quick thought after reading the 'man nsswitch.conf'.
Maybe you should have something like:
```

hosts: dns (NOTFOUND=continue) files mdns wins

```

---

### Post by LordMau on 2007-09-03
I see, my nsswitch.conf does not have those items, probabaly since it was an edgy upgrade instead of a fresh feisty install.

I'll try again those suggestions with a reboot, though I should note that as described in the first post I immediately saw a difference in browsing when I deleted either the wins item or the dns item without rebooting nor even restarting the network.

Update later. Thanks

---

