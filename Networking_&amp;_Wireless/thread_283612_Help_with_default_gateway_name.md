---
title: "Help with default gateway name"
date: 2006-10-24
forum: Networking &amp; Wireless
---

### Post by urrimus on 2006-10-24
Hallo.
I have a small problem.
I want to install Unicore6 system to my PC.
Installing was good, but now i have to configure GPE client for Unicore. Server install and configuration was done how it was written in readme, and now i have to set default gateway name to GPE klient:
From Readme:


[B]** Client side registry settings:

In the GPE app client, edit the registries ("File/Preferences/Registries") 
to include

[https://host:port/DEMO_NJS/axis/services/RegistryService](https://host:port/DEMO_NJS/axis/services/RegistryService)  (Unicore/GS registry)
[https://host:port/XNJS/services/Registry](https://host:port/XNJS/services/Registry)                  (FZJs UAS registry)

where "host" and "port" refer to the gateway hostname and port (8080 by
default).[/B]


i have to set gateway hostname, and i have to set full network path of my PC.
If i execute route command, this gives


[B]Destination Gateway Genmask Flags Metric Ref Use Iface
85.196.200.0    *               255.255.252.0   U     0      0        0 eth0
default         ubr1-200-1.tart 0.0.0.0         UG    0      0        0 eth0[/B]


and i can't find full gateway name, can anybody help me where i can read it from?

And one more question, if i have to set gateway hostname, this must be with my ubuntu user name and/or computer name or not?

Thank you,
Urmas.

---

