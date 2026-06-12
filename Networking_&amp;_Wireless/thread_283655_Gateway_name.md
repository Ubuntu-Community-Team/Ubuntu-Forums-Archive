---
title: "Gateway name"
date: 2006-10-24
forum: Networking &amp; Wireless
---

### Post by urrimus on 2006-10-24
Hallo.
I have a small problem.
I want to install Unicore6 system to my PC.
Installing was good, but now i have to configure GPE client for Unicore. Server install and configuration was done how it was written in readme, and now i have to set default gateway name to GPE klient:
From Readme:
urmas

** Client side registry settings:

In the GPE app client, edit the registries ("File/Preferences/Registries")
to include

[https://host:port/DEMO_NJS/axis/serv...egistryService](https://host:port/DEMO_NJS/axis/serv...egistryService) (Unicore/GS registry)
[https://host:port/XNJS/services/Registry](https://host:port/XNJS/services/Registry) (FZJs UAS registry)

where "host" and "port" refer to the gateway hostname and port (8080 by
default).


i have to set gateway hostname, and i have to set full network path of my PC.
If i execute route command, this gives


Destination Gateway Genmask Flags Metric Ref Use Iface
85.196.200.0 * 255.255.252.0 U 0 0 0 eth0
default ubr1-200-1.tart 0.0.0.0 UG 0 0 0 eth0


and i can't find full gateway name, can anybody help me where i can read it from?

And one more question, if i have to set gateway hostname, this must be with my ubuntu user name and/or computer name or not?

Thank you,
Urmas.

---

### Post by Jussi Kukkonen on 2006-10-24
> **urrimus said:**
> Hallo.
i have to set gateway hostname, and i have to set full network path of my PC.

Go to *System->Administration->Network Settings*, click on properties of the connection in use and you will see your "IP address" and  "Gateway address". That's the info you want.

> And one more question, if i have to set gateway hostname, this must be with my ubuntu user name and/or computer name or not?

This does not make much sense. Can you elaborate what you mean?

---

### Post by urrimus on 2006-10-24
Thanks, Jussi!
Much Better.
Earlier were Cannot get target systems .... Unknown Host
but now Cannot get target systems .... Connection Refused

Maybe it is nesersarry to disable Firewall or maybe my provider doesn't allow such things like Unicore Server work (don't believe really)?

And how to disable firewall if it is possible?

And about computer name, think that this is not necessary.

Thanks,
Urmas.

---

