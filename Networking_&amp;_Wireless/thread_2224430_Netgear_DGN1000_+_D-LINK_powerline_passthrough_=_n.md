---
title: "Netgear DGN1000 + D-LINK powerline passthrough = nothing"
date: 2014-05-16
forum: Networking &amp; Wireless
---

### Post by furio95 on 2014-05-16
Hello.
I am currently stuck and banging my head on the keyboard because of internet deprivation, and I beg for help of any kind (but possibly technical).

I have a [NETGEAR DGN1000]("http://support.netgear.it/product/DGN1000") modem which appars to be working perfectly, since I can connect with all of my WiFi devices with no issues. I route the connection through my power line using a [D-LINK DHP-P309AV]("http://www.amazon.it/D-Link-DHP-P309AV-Adattatori-PowerLine-Passthrough/dp/B00B713KJO/ref=sr_1_2/277-5909250-6352264?ie=UTF8&qid=1400240058&sr=8-2&keywords=d-link+dhp-p309av") (that's what it says on the box).
My machine is on the other end of the D-LINK thingy and connected with an Ethernet cable. Windows 7 automatically detected the net and connected and works fine, but Ubuntu 14.04 does not see it. The Network Manager applet says "device not supported" ("dispositivo non gestito" in Italian, which is my first language) and "sudo pppoeconf" finds nothing.

My knowledge of Ubuntu does not go far beyond the Software Center, so I have no idea what to do to get the Internet back online.
My command-line skills include folder navigation and copy-pasteing commands.
Please do not force me to use Windows, it's bad for my health.

Thank you in advance, 
Riccardo

---

### Post by furio95 on 2014-05-19
Problem solved!

In terminal:
```
[COLOR=#555555][FONT=Monaco]sudo gedit /etc/network/interfaces[/FONT][/COLOR]
```
Opened this file:
```
[COLOR=#555555][FONT=Monaco]# interfaces(5) file used by ifup(8) and ifdown(8)[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]auto lo[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]iface lo inet loopback[/FONT][/COLOR]

[COLOR=#555555][FONT=Monaco]auto dsl-provider[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]iface dsl-provider inet ppp[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]provider dsl-provider[/FONT][/COLOR]

[COLOR=#555555][FONT=Monaco]auto eth0[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]iface eth0 inet manual[/FONT][/COLOR]
```
And edited it this way:
```
[COLOR=#555555][FONT=Monaco]# interfaces(5) file used by ifup(8) and ifdown(8)[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]auto lo[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]iface lo inet loopback[/FONT][/COLOR]

[COLOR=#555555][FONT=Monaco]#auto dsl-provider[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]#iface dsl-provider inet ppp[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]#pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]#provider dsl-provider[/FONT][/COLOR]

[COLOR=#555555][FONT=Monaco]#auto eth0[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]#iface eth0 inet manual[/FONT][/COLOR]
```

Rebooted and it worked like a charm.

---

