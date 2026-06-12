---
title: "[SOLVED] Share internet between ubuntu boxes"
date: 2008-01-14
forum: Networking &amp; Wireless
---

### Post by iris-n on 2008-01-14
Hi all

I know that this is a pretty common request, but i seem to be stuck on some stupid error that i can't figure out.

The case is, i have a desktop ubuntu/xp with an wireless internet that I wish to share with my latpop, which is ubuntu solely. They are connected through a crossover cable.

I know they're seeing each other, 'cos there's a healthy NFS share working.

I already managed to set up the internet sharing between the xp and the latpop, but that's not ideal.

I already followed [_this_]("https://help.ubuntu.com/community/InternetConnectionSharing?highlight=%28sharing%29%7C%28internet%29") guide, to no effect.

Here's my interfaces :

```
auto lo
iface lo inet loopback


iface wlan0 inet static
address 189.43.135.190
netmask 255.255.255.248
gateway 189.43.135.185
wireless-essid SJNOVAERAE




iface eth0 inet static
address 192.168.0.1
netmask 255.255.255.0





auto eth0

auto wlan0
```

and my resolv.conf: ```
nameserver 200.251.179.13
nameserver 200.251.179.11
```

I hope someone can point me.
Thanks =)

---

### Post by sqrt2 on 2008-01-14
Assuming that you have a clean iptables setup (reboot to ensure that), all you need actually is
[indent]sudo iptables -A FORWARD -j MASQUERADE[/indent]
or -- alternatively, if your public IP address never changes, which it looks like --
[indent]sudo iptables -A FORWARD -j SNAT --to 189.43.135.190[/indent]
In case of a static IP adress, the second alternative is better, because masquerading can confuse services on the internal network, should you decide to provide services to the public. (However, you'll need additional iptables rules then.)

Also, you have to activate IP forwarding in the first place:
[indent]sudo sh -c "echo 1 > /proc/sys/net/ipv4/ip_forward"[/indent]
Be sure not to reboot here, because otherwise all settings will be lost.

Next, configure 192.168.0.1 as the gateway for the non-wirelessly connected computer. Connection sharing should work then.

---

### Post by iris-n on 2008-01-14
Thanks, it is static indeed.

However, it didn't worked, when i typed the ```
 sudo iptables -A FORWARD -j SNAT --to 189.43.135.190
```, it gave me ```
iptables: No chain/target/match by that name

```

And what you mean by not reboot? I will have to type these every time i want the internet?

---

### Post by sqrt2 on 2008-01-14
Ah, sorry, I wasn't concentrating. What I meant was
[indent]sudo iptables -t nat -A POSTROUTING -j SNAT --to 189.43.135.190[/indent]

You can save the IP forwarding setting by editing /etc/sysctl.conf as described in the HOWTO. To save the iptables settings, you can try adding
[indent]up iptables -t nat -A POSTROUTING -j SNAT --to 189.43.135.190[/indent]
to eth0 in /etc/network/interfaces.

---

