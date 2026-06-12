---
title: "my network interface is lo, is this normal?"
date: 2008-06-12
forum: Networking &amp; Wireless
---

### Post by ghmercado on 2008-06-12
hi I just installed 8.04 LTS.

I think I may have a misconfigured network setup.

at System > Administration > Network Tools

There are two devices, IPv4 and IPv6

IPV4 ip address: 192.168.1.5, netmask / prefix: 255.255.255.0; broadcast 192.168.1.255
IPv6 shows the mac address of my network interface.

but when I click 'configure' ethernet interface eth0, I get the ff. error:

The interface does not exist
Check that it is correctly typed and that it is correctly supported by your system (ok).

however the internet works on my system, although it is using lo.

I was trying to setup up opendns but the instructions said I should write

```
sudo ifdown eth0 && sudo ifup eth0 
```

at the end. It doesn't work for me, not recognizing eth0.

Is this normal? What to do to use OpenDNS?

many thanks in advance

---

### Post by superprash2003 on 2008-06-12
to use opendns [http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html)

---

