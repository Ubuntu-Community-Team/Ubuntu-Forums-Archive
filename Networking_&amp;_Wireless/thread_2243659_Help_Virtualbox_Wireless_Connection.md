---
title: "Help: Virtualbox Wireless Connection"
date: 2014-09-10
forum: Networking &amp; Wireless
---

### Post by NoFriends on 2014-09-10
Hi All, 

I have installed Ubuntu 14.04 LTS using Oracle Virtualbox.

My main system is running Windows 7.

I run the command

[B]iwconfig

[/B]and the outut i get is the following:

[B]lo        no wireless extensions.
eth0    no wireless extensions.

[/B]because of this when i run the below:

[B][COLOR=#000000][FONT=Consolas]airmon-ng start wlan0

[/FONT][/COLOR][/B][COLOR=#000000][FONT=Consolas]I should get information under interface, chipset & driver
if the command has worked, but not information shows up at this point.

If anyone could advise that would be great.


My main issue is how do i fix this:

[/FONT][/COLOR][B]lo no wireless extensions.
eth0 no wireless extensions.[/B]

---

### Post by SeijiSensei on 2014-09-10
The guest operating does not communicate directly with your wireless router.  Instead it uses a virtualized Ethernet interface to communicate with the Win7 host, which forwards the traffic to the router.  

Read this part of the VB documentation for details: [https://www.virtualbox.org/manual/ch06.html](https://www.virtualbox.org/manual/ch06.html)

If you open a terminal in the Ubuntu guest and type the command "ifconfig" do you see an "eth0" entry with an IP address like 10.8.0.2?  That's the virtual networking device that communicates with the host.  Try the command "ping 8.8.8.8" which is the address of Google's DNS server.  Do you see replies?

---

