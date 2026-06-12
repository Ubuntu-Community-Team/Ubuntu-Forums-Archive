---
title: "resolv.conf is lost with every reboot"
date: 2008-06-02
forum: Networking &amp; Wireless
---

### Post by DaVinciXL on 2008-06-02
Since friday I have this odd problem (having nothing changed in the system except for installing the suggested ubuntu updates):
My computer has a fixed IP address, which under all circumstances has to remain so, and is connecting to the internet through a router. The computer is bound to this router via lan cable. This setup worked great since ubuntu 6.something straight up until last friday. Now, with every reboot, my Linux loses its /etc/resolv.conf, or better: after every reboot the file is empty (except for the well-known warning, not to change anything in this file).

When I go to the network managing tab of kcontrol and add my router as DNS and hit "save", everything is fine again.
The same goes for manually editing the resolv.conf.

However, after the next reboot the entry "nameserver 192.168.1.1" will be gone again.

Any ideas on how to fix this?
Any ideas on what might help to figure the real problem out?

Regards,
DaVinciXL

---

### Post by superprash2003 on 2008-06-02
read this [http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html)
 opendns server used here.. you can change if you wish

---

### Post by DaVinciXL on 2008-06-02
Thanks. I'll give that a try.

---

### Post by DaVinciXL on 2008-06-03
Didn't work out. Same problem as before... :(

---

### Post by Iowan on 2008-06-03
Post your **/etc/network/interfaces**.

---

### Post by DaVinciXL on 2008-06-03
```

auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0


iface eth0 inet static
address 192.168.1.101
netmask 255.255.255.0
gateway 192.168.1.1

auto eth0

```

---

### Post by Iowan on 2008-06-03
I should mention that I haven't used Kubuntu...
Check (where?) to see if "roaming" mode is selected - probably shouldn't be for a static IP.

---

### Post by DaVinciXL on 2008-06-12
Well... everything is configured just the way it should be now (worked for YEARS) - but after a reboot these settings are gone again and I don't know why.

I doesn't seem to have anything to do with the static IP. I configured my PC as DHCP client this afternoon and rebooted it. It got an IP address but the Nameserver was not set.
And yes, the DHCP server is configured correctly - works fine with several notebooks.

---

