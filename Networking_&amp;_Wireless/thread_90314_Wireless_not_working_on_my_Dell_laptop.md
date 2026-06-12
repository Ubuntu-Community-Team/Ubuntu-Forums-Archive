---
title: "Wireless not working on my Dell laptop"
date: 2005-11-14
forum: Networking &amp; Wireless
---

### Post by sambusek on 2005-11-14
Hi all.
I've a problem with my wireless connection.
After a successfull installation of the "dell truemobile 1300" wireless card, a wireless "wlan0" connection was added in the network list.
I tried to configure my wireless connection, but - even if the signal is 100% - I can't manage to connect with my belkin access point.

The access point data are:
IP address: 192.168.2.1
Subnet mask: 255.255.255.0
Local domain name: Belkin
Wan mac address: xx-xx-xx-xx-xx-xx
Wireless channel: 11
SSID: belkin54g
I use a 13 hex digit 128-bit wep password.

Well: my access point doesn't see my computer and my computer doesn't connect to the access point. Why?!? I've inserted all the data, and on ubuntu they appear like this:

INTERNET PROTOCOL (IPv4)
[LIST]
[*]Address: 192.168.2.1 (my access point address)
[*]Broadcast: 192.168.2.255
[*]Subnet mask: 255.255.255.0
[/LIST]

NETWORK DEVICE
[LIST]
[*]Type: Ethernet
[*]Address: (my laptop mac address)
[/LIST]

So: what's wrong?!?
Note that I've written my 128 bit password in a continuous form (without any "-" between the couples of numbers and letters): is it right?

If anyone has suggestion, please tell me

Thank you!
Mauro

---

### Post by mlomker on 2005-11-14
I'd try it without encryption to confirm that the card is working.

---

### Post by erikringmar on 2006-01-08
Hi,

I'm not much of an expert, but I got my card to detect the network when I turned the ethernet off.  Don't know why it would work this way though.

good luck,

Erik

---

