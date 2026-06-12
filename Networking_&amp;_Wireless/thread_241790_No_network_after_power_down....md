---
title: "No network after power down..."
date: 2006-08-22
forum: Networking &amp; Wireless
---

### Post by und3rtug4 on 2006-08-22
Hi there...

One of my servers had a sudden power down, and when power it back up, i had no networking...

It load the networking on startup, and displays [ok]...

... But still no network...

I thought: "Maybe the sudden power down mess up my ethernet card"...
...But it didnt, when i do ```
sudo lspci
``` it detects my ethernet card.

Well, then i went check the /etc/network/interfaces file, it seems ok!

When i type ```
sudo ifconfig
```, it only detects the loopback interface, no eth0!

I tryed to reload my network by typing ```
sudo /etc/init.d/networking force-reload
```, and it displays [ok]...

... but then i try to ping my router or somother host, and it displays "Network unreachable".

Anyone got any idea of whats going on???

Thanks in advance..

Regards...

---

### Post by amohanty on 2006-08-22
Are you using dhcp?

If so check to make sure that dhclient is running:
**ps aux | grep dhclient**

If its not running, try (I am not a 100% sure of the syntac):
**dhclient eth0**
if that doesnt work try:
**dhclient -s <your dhcp server ip> eth0**

HTH
AM

---

### Post by und3rtug4 on 2006-08-22
No...

... i'm using static ip!

And my interface configurations on /etc/network/interfaces for eth0 seem ok!

I'm just not been able to solve this out...
... and it's quite frustrating!

Regards

---

### Post by amohanty on 2006-08-22
what happens if you try:
**sudo ifup -v --force eth0**

AM

---

### Post by und3rtug4 on 2006-08-23
I get this:

```

Configuring interface eth0=eth0 (inet)
run-parts --verbose /etc/network/if-pre-up.d
run-parts: executing /etc/network/if-pre-up.d/wireless-tools

ifconfig eth0 10.0.0.4 netmask 255.255.255.0 broadcast 10.0.0.255        up

route add dfault gw 10.0.0.1 eth0
SIOCADDRT: File exists

```

---

### Post by amohanty on 2006-08-23
Is your router IP: 10.0.0.1?

The SIOCADDRT: File exists means the interface was already up and it probably snt able to bind to that address. Try:
[B]sudo ifdown -v --force eth0
sudo ifup -v --force eth0[/B]

HTH
AM

---

### Post by und3rtug4 on 2006-08-23
Yes, my router IP is 10.0.0.1!

All the configuration are correct!

It's now working ok...

... i think it was somekind of hardware problem, since all i have done was open it up, plug the ethernet card out and plug it back in...

When i reboot the system, it was working...

... it still dont know the exact reason for this to happen...](*,) 

Regards...

---

### Post by amohanty on 2006-08-23
Its possible the card wasnt seated properly or a bump or something jarred it loose. If it was working before there doesnt seem to be any good reason for it to fail, unless of course your box is not protected by a surge protector which may have spiked your card along with other stuff. I would suggest waiting for it to happen again, or trying to reliably reproduce the problem on a dumy box.


HTH
AM

---

### Post by und3rtug4 on 2006-08-23
Yep, i'm gonna wait to see how the ethernet card behave's!
I have a electric spikes protector protecting my servers, it it's never 100% safe!

Anyway, thanks for the help amohanty!

Regards!

---

