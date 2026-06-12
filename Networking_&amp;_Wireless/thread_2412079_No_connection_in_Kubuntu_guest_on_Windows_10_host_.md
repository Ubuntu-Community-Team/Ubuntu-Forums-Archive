---
title: "No connection in Kubuntu guest on Windows 10 host after changing from DSL to cable ro"
date: 2019-02-07
forum: Networking &amp; Wireless
---

### Post by qphysics2 on 2019-02-07
[COLOR=#333333][FONT=&quot]Greetings,[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]I have been struggling with this issue for about a year and have had no success in finding a solution.[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]I have VirtualBox running on Windows 10 with two guest VMs set up, Kubuntu and Sage. Kubuntu worked fine until I switched from DSL to cable. As soon as the old router was gone and the new one replaced it, I have no internet connection on the Kubuntu guest. [/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]I've tried adjusting connection settings on host, guest, and VB tools...can't get a connection established.[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]I just deleted my old VirtualBox install, and made sure that the Host-Only adapter was uninstalled in Network Settings...and installed 6.0...and that didn't fix it.[/FONT][/COLOR]

[COLOR=#333333][FONT=&quot]I've included a screenshot of ipconfig along with the VirtualBox network settings, a text file of the Windows 10 output of ifconfig.[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]Can anyone see what got broken, or more likely didn't get updated properly when I changed routers? [/FONT][/COLOR]

[COLOR=#333333][FONT=&quot]Thanks everyone![/FONT][/COLOR]

---

### Post by qphysics2 on 2019-02-07
Never mind...about two minutes after I posted this I was looking at the output of ifconfig and decided to check /etc/network/interfaces. Sure enough, changing everything from eth0 to enp0s3 followed by a restart fixed everything.

---

