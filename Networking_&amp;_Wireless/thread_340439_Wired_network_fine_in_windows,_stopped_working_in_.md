---
title: "Wired network fine in windows, stopped working in edgy?"
date: 2007-01-17
forum: Networking &amp; Wireless
---

### Post by MarkRobert on 2007-01-17
This morning I had to put a switch into my office to help with the amount of computers I needed to connect. Probably nothing to do with it but thought I'd mention it.

Anyhow, connected straight to network port in wall. Port works as it connects fine in winxp (dual boot)

Booting into ubuntu I have it set to get a ip address autmatically, but nothings happening. Was working fine this morning and I haven't installed anything on the computer or made any changes.

Here is what I get when i ifconfig eth0

eth0      Link encap:Ethernet  HWaddr 00:15:C5:B9:82:BA  
          inet6 addr: fe80::215:c5ff:feb9:82ba/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:177 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11989 (11.7 KiB)  TX bytes:2222 (2.1 KiB)
          Interrupt:18 

I also had a feisty cd so I booted into the live version and still the same, no connection. But windows on the same machine is fine. Any suggestions on what I can try?

I'm using a Dell Inspiron 6400. Network card is Broadcom 440x 10/100 Integrated Controller. 

Thanks for reading

---

### Post by deejaylinux on 2007-01-17
It seems like you have not configured your TCP/IP parameters. My ifconfig output is this:

eth0      Link encap:Ethernet  HWaddr 00:40:63:D7:E6:48
          inet addr:192.168.2.1  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::240:63ff:fed7:e648/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:247 errors:0 dropped:0 overruns:0 frame:0
          TX packets:134 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:21769 (21.2 KiB)  TX bytes:17304 (16.8 KiB)
          Interrupt:11 Base address:0xec00

Check your TCP/IP configuration again and try

Good luck

---

### Post by MarkRobert on 2007-01-17
It's set to dhcp, and I can see that it is enabled in networking. However when i open network tools and highlight eth0 and select configure, I get an error advising I can't access tge system configuration.

---

### Post by deejaylinux on 2007-01-17
Please post the contents in /etc/network/interfaces files.

If we look at this file, maybe we could detect the problem.

---

### Post by MarkRobert on 2007-01-17
Thanks, had a look through it previously and didn't see anything wrong, but just in case I rewrote the eth0 part and it's working fine again.

---

### Post by cesine on 2007-01-17
im also having trouble getting eth0 to run, could you post the /etc/network/interfaces anyway?

---

### Post by MarkRobert on 2007-01-17
Sure. Now that i've got home my wireless isn't connecting under ubuntu, but fine in windows. Doh!

Anyway, here's my version

> auto lo
iface lo inet loopback


iface eth0 inet dhcp

iface eth1 inet dhcp
wireless-essid xxxxxxxxxxxxxx
wireless-key xxxxxxxxxxxxxxxxxxxxxxx

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
























auto eth1

auto eth0

auto eth1

auto eth0


---

