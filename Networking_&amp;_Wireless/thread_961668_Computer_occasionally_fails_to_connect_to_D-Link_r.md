---
title: "Computer occasionally fails to connect to D-Link routers"
date: 2008-10-28
forum: Networking &amp; Wireless
---

### Post by haboegi on 2008-10-28
Dear community members

I'm stuck with a quite acute problem.
My laptop, a HP Compaq 6710b, randomly fails to connect to every d-link router I try connect to. "Randomly" means that I cannot predict at boot time whether it will be able to make a connection or not: sometimes it is able to and I can simply go on with my work as I should and sometimes I get no result at all. There is no intermediate situation...
I don't seem to have this problem with other routers than d-link. It does not matter whether I connect to a wired or a wireless network.
WHEN my Ubuntu Hardy fails to connect:
[LIST]
[*]I get the error "Address not found" when opening my browser
[*]Every other internet program (Opera, wget,...) encounters the same problem
[*]I can ping my router, but no other internal addresses (192.168.x.x)
[*]I cannot ping external addresses (google, etc.)
[/LIST]
Allow me to mention that I didn't use to have this problem before. It used to work normally without further difficulties until a few weeks ago.
Note: when booting from a Hardy live cd, it always works! :confused:

Would somebody please care to help me?
Thanks in advance!

---

### Post by haboegi on 2008-11-01
It's me again.
The upgrade to Ubuntu 8.10 has solved this issue.
But now I've got another one: My laptop (type: see above)
is able to detect any wireless network around but mine at home.
Th networks around are either unencrypted or WEP-protected.
Mine is WPA2-protected (AND is emitting its SSID). But it never
appears in the list. Connection also fails when I try to force it
to connect mannually via the network applet...

The same problem occurs when running the live cd. So it's no
configuration problem on my production system:
the new Ubuntu just somehow fails to detect my network.

Any Ideas?
Note: I have a Linksys WRT150N router...

---

