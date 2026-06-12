---
title: "[SOLVED] Secondary IP address (alias) problems"
date: 2008-05-12
forum: Networking &amp; Wireless
---

### Post by Peppery on 2008-05-12
Hi there,

I recently upgraded (clean install) my Eee PC to Hardy from Gutsy. At my school, to get internet access two IP addresses are required. Under Gutsy, I had my ath0 connection configured with a 192.168.1.200 address and used "ifconfig ath0:0 10.97.192.200 netmask 255.255.255.0 up" to connect fine.
However, under Hardy, I ran the above command and try and ping an IP and I get an "connect: network unreachable" error message. ifconfig lists both IP addresses as it should, and the first "connection" can ping local addresses fine. If I change the first IP to the external IP I can ping outgoing addresses fine, but that isn't very helpful as the DNS server (among other things) is on the private connection. :(

The only thing that I can think of that would have changed anything is that under Hardy I'm using the [Wicd]("http://wicd.sourceforge.net/") network manager to manage my wireless connections as I found the supplied Gnome applet one rather hopeless.

Any advice would be appreciated. Thanks.

---

### Post by Aearenda on 2008-05-12
I don't use WiCD - are you sure it can handle aliases (multiple ip addresses)? I would disable it and just use /etc/network/interfaces to configure things until we know its working, then try to get WiCD to manage it afterwards. 

Do you have the gateway address set the same way as before? Maybe WiCd is guessing it wrong. Please post the output from 'route' and the contents of /etc/resolv.conf and /etc/network/interfaces, as they stand when you are trying to connect at school.

The gateway address should point to a router - is the Internet routed via the 10.97.192.0 network or the 192.168.1.0 network? 

Or: you could set the DNS address to a public DNS server on the internet (such as OpenDNS), so you don't need the internal one.

---

### Post by Peppery on 2008-05-12
I'm not sure if Wicd can handle aliases, I configure the alias with ifconfig so I'm not sure why it wouldn't specifically. I'm open for suggestion for another (wireless) network manager that'll let me do settings per AP (GNOME's netwok-manager applet didn't work so well for me).

I'll have a look tomorrow and get back to you with those command/file outputs.

Yes - the gateway is the same as before. It's all the same settings as before as DHCP isn't available.

The internet is routed via the 10.x network, and is pointing at a router. I know that works because changing the static IP in Wicd works fine. 

I've tried setting it to a public DNS server, but the firewall seems to block anything that doesn't go out on 80 or 443. I still need access to the private one, for printing and the such.

---

### Post by Peppery on 2008-05-12
```
harrison@eeepc:~$ cat /etc/resolv.conf 
nameserver 192.168.1.1
harrison@eeepc:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

harrison@eeepc:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.97.192.0     *               255.255.255.0   U     0      0        0 ath0
192.168.1.0     *               255.255.255.0   U     0      0        0 ath0

```

---

### Post by wirelessmonkey on 2008-05-12
Your routing isn't right... try:
route add default gw 10.97.192.1

restart networking using 
sudo /etc/init.d/networking restart

If it doesn't change, you can remove the route using

sudo route del default


Best of Luck

---

### Post by Aearenda on 2008-05-12
I agree with wirelessmonkey - you have no default gateway, so your pc does not know what to do with non-local packets!

---

### Post by Peppery on 2008-05-13
Thanks, that works perfectly. I thought it would be something simple like that. :)

---

