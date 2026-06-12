---
title: "Got wireless working but need to disable WEP"
date: 2006-10-04
forum: Networking &amp; Wireless
---

### Post by greyash99 on 2006-10-04
I finally got my broadcom card working, but I need to know how to disable WEP securtiy.  The computer that manages that is a windows box.  I know how to change the WEP key but I don't know how to disable it.

---

### Post by wieman01 on 2006-10-04
Am I right in that you are connected to a router? You should disable WEP there **first**, then make the necessary changes in:
> sudo gedit /etc/networking/interfaces
Either post the contents so that we can help you OR search for a line that says "wireless-key" and uncomment it with a #. The restart the network:
> sudo /etc/init.d/networking restart

---

### Post by greyash99 on 2006-10-04
```

auto lo
iface lo inet loopback


iface eth0 inet dhcp


auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp



iface eth1 inet dhcp
address 192.168.0.13
netmask 255.255.255.0
wireless-essid jones
wireless-key 12345





















auto eth1

auto eth0

```

---

### Post by wieman01 on 2006-10-04
So if you have disabled WEP in the router, this should be your "interfaces" file assuming the you have DHCP enable (no static leases):
> auto lo
iface lo inet loopback

iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
wireless-essid [COLOR="Red"]jones[/COLOR]
Then restart the network:
> sudo /etc/init.d/networking restart

---

### Post by greyash99 on 2006-10-07
How do I disable WEP?  The computer that manages that is running windows.

---

### Post by wieman01 on 2006-10-07
> **greyash99 said:**
> How do I disable WEP?  The computer that manages that is running windows.
Hang on a minute... Is the Windows machine handling your wireless network? So it's connected to the DSL modem / Internet and has got a wireless card in order to act as an AP?

The "interfaces" file would look like this:
> auto lo
iface lo inet loopback

iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
wireless-essid [COLOR="Red"]jones[/COLOR]
wireless-key [COLOR="Red"]your_wep_key[/COLOR]
The restart the network:
> sudo /etc/init.d/networking restart

---

### Post by greyash99 on 2006-10-07
Ok this is how it works:
router/modem/cable thingy is connected to Windows box
Windows box manages the network
Windows box just controls WEP it doesn't have a wireless card
other Windows box works just fine with WEP code

Thanks for helping me so far.........

---

### Post by wieman01 on 2006-10-07
Ok, usually the router controls the network but this is not the point at this anyway. Can you try my suggested solution? What does your WEP key look like (if I may ask)?

---

### Post by greyash99 on 2006-10-07
Yeah I tried.  Idk wireless didn't work too well in Windows either......my WEP key is ASCII at least as far as I know :12345

---

### Post by wieman01 on 2006-10-07
> **greyash99 said:**
> Yeah I tried.  Idk wireless didn't work too well in Windows either......my WEP key is ASCII at least as far as I know :12345
Then perhaps try this:
> auto lo
iface lo inet loopback

iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
wireless-essid jones
wireless-key [COLOR="Red"]s:123456[/COLOR]
"s:" indicates that this is a string (ASCII) rather than hexadecimal.

---

### Post by wieman01 on 2006-10-07
And by the way: Whenever you have any kind of output, please post it so as to let us know...

---

