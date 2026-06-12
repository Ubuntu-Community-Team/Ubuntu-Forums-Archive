---
title: "How to define Device Name with Netgear fvs318v3 Router"
date: 2008-04-27
forum: Networking &amp; Wireless
---

### Post by jpmd on 2008-04-27
Hi, folks,

I have Ubuntu 7.10 running on a ten-year-old Gateway and everything seems to run fine -- Lighttpd (in lieu of Apache), Putty, and even Domino 7.02 server for playing around with Lotus Notes.

I have a wired network connected to a cable modem using DynDNS successfully.

The router is a Netgear FVS318v3.

One minor question:  How do I define the "Device name" in Ubuntu so Netgear displays it?

Here's a screen shot of the Netgear router's *Maintenance/Attached Devices* panel.

[IMG]http://www.widgetracing.com/images/advisor/netgear_devices.jpg[/IMG]

I've got Samba configured with a netbios name and server string, both of which appear when my WinXP boxes browse for shared directories and printers.

> # server string is the equivalent of the NT Description field
   # server string = %h server (Samba, Ubuntu)
   netbios name = GW-Ancient
   server string = GW-G6-450 - an ancient computer


I'm new to Ubuntu and to Linux in general, so I'm sure I'm just missing something obvious.

Thanks for your input!

John

---

### Post by magenine on 2009-04-22
$ sudo pico /etc/dhcp3/dhclient.conf

send host-name "**<hostname>**";

---

