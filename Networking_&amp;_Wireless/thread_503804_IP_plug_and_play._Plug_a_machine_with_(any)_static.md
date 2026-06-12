---
title: "IP plug and play. Plug a machine with (any) static ip, dns, and gateway address to a"
date: 2007-07-18
forum: Networking &amp; Wireless
---

### Post by mson77 on 2007-07-18
[FONT="Courier New"]_[COLOR="Red"]IP plug and play. Plug a machine with (any) static ip, dns, and gateway address to a network and voila ! internet works.[/COLOR]_

Hi... this a topic at [[COLOR="Blue"]this sourceforge link[/COLOR]]("http://sourceforge.net/projects/ippnp/").

But there is no source code to download. And also... this "project" is very interesting because any user... with any IP configuration (even any static IP) gets access into the internet without any changes on his laptop. It should works in a local ethernet segment only because it should proxy arp performing some universal gateway to these users.

Also I found 02 payed hotspot product that use solution like this:
[LIST]
[*][[COLOR="Blue"]http://www.mikrotik.com/testdocs/ros/2.9/guide/specs.php[/COLOR]]("http://www.mikrotik.com/testdocs/ros/2.9/guide/specs.php")
[*][[COLOR="Blue"]http://www.nomadix.com/products/nse/[/COLOR]]("http://www.nomadix.com/products/nse/")
[/LIST]

> [FONT="Courier New"](from MIKROTIK product)
HotSpot - HotSpot Gateway with RADIUS authentication and accounting;** true Plug-and-Play access for network users;** data rate limitation; differentiated firewall; traffic quota; real-time status information; walled-garden; customized HTML login pages; iPass support; SSL secure authentication; advertisement support.[/FONT]


> [FONT="Courier New"]For End Users (from NOMADIX product)

    * **Get a problem-free connection to the service with Zero Configuration changes**
    * Gain access to local content and applications as part of an advanced service offering
    * Pay for services using a variety of mechanisms including credit card, scratch card or by signing up for a subscription-based service
[/FONT]


I am looking for solution like these above mentioned... Can I get some initial help from here?

Summary: I am looking for an open-source solution that provides something like [http://sourceforge.net/projects/ippnp/]("http://sourceforge.net/projects/ippnp/").
IP plug and play. Plug a machine with (any) static ip, dns, and gateway address to a network and voila ! internet works.


Very thanks,


mson77[/FONT]

---

### Post by spd106 on 2007-07-18
Have you read this [http://lists.freebsd.org/pipermail/freebsd-net/2007-May/014201.html](http://lists.freebsd.org/pipermail/freebsd-net/2007-May/014201.html)
My sentiments exactly.

The best we currently have are Avahi (Zeroconf, Bonjour etc) or UPnP. Neither of these do exactly what you describe, but are along the same lines.

Good Luck

---

### Post by mson77 on 2007-07-19
[FONT="Courier New"]Hello,


Regarding...

[quote=spd106][FONT="Courier New"]The best we currently have are Avahi (Zeroconf, Bonjour etc) or UPnP. Neither of these do exactly what you describe, but are along the same lines.[/FONT][/quote]

these topics that you have mentioned (quote) are related to the client/user machine. It means that the user has to have these software installed to be in a PnP environment.

What I am trying to tell and share here is at the opposite side: the server side.
My server with some <ippnp> feature... has to be able to provide a feature like "universal gateway".

I understard that this may be done... first by proxy-arping the client arp request for the client's gateway. Then this server (mine) should tell to the client that his gateway is with server_eth1 by proxy arping.

But I am looking for a ready made solution... from open source world.

Thanks,


mson77

heeeeeeeeeeeelp neededdddddddd

[/FONT]

---

