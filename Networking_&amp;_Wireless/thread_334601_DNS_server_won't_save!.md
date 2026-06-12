---
title: "DNS server won't save!"
date: 2007-01-09
forum: Networking &amp; Wireless
---

### Post by kvonb on 2007-01-09
I recently got wireless working on my spare computer.  It works fine although it seems to take a minute or so after booting to start working, but that is another story .

The main problem is that Menu->System->Administration->Networking->DNS refuses to save whatever I put in there!

Each time I boot up, there is an entry of 0.0.0.0 in the DNS box, I have to type it back in again.

I've tried the "save as location" option, but it still loses it.

I did notice that it never asks me for a password when I first start the networking tool, maybe that is an issue?

If I knew which file to edit I would be happy to just put it in there.

Here is my /etc/network/interfaces file:

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

#auto ath0
#iface ath0 inet dhcp

auto wlan0
iface wlan0 inet static
address 192.168.1.4
netmask 255.255.255.0
broadcast 192.168.1.255
gateway 192.168.1.1
dns-nameservers 192.168.0.1
#iface wlan0 inet dhcp
wireless-essid MYHOME
wireless-mode ad-hoc
```Once I type in 192.168.0.1 as my DNS server, the net works perfectly!

Regards, Kev :)

---

### Post by teaker1s on 2007-01-09
if you set static ip then dns will stay DCHP you can sort by looking at thread link below
[http://ubuntuforums.org/showthread.php?t=282034&highlight=stabilise+dns]("http://ubuntuforums.org/showthread.php?t=282034&highlight=stabilise+dns")

good luck:mrgreen:

---

### Post by kvonb on 2007-01-09
Thanks for the link, I tried it and it didn't work.

So after wasting hours on this I decided to lobotomise the stupid thing and removed dhcp client!

It now works fine :).

Maybe a re-install will fix it, but for now it is working.

For reference, this is what I did:

Open Synaptic, search for "dhcp", right click on "dhcp3-client" and select "remove completely", also the same for "dhcp3-common".  It complains that it will also remove "ubuntu-minimal" however this did NOT negatively affect my machine.  Apply and exit when finished.

Next

```
sudo gedit /etc/resolv.conf
```

....and add your nameserver, save and exit.

Reboot and enjoy :)

---

### Post by teaker1s on 2007-01-09
glad you fixed it:mrgreen: , I personally despise dhcp as you always get problems with lease time even if it changes only daily with some machines](*,)

---

