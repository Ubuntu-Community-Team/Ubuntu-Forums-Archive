---
title: "Strange network card problem"
date: 2008-08-28
forum: Networking &amp; Wireless
---

### Post by TeknoPhil on 2008-08-28
Hello experts!
My network card is working fine on Hardy (8.04) Desktop.

On Hardy server, it's working 25% of the time ... I don't know why but sometime I boot and it's fine, otherwise not. Really strange.

I just did a fresh install of Ubuntu Server (8.04) on a brand new computer (Intel D945GC Mini-ITX board)

If this can help, the LAN subsystem consists of the following:
&#8226; Intel 82801GB ICH7
&#8226; Realtek RTL8102EL device for 10/100 Mbits/sec Ethernet 

When it's not working, I'm able to ping localhost, but not my router.

Here's more information:

/etc/network/interfaces
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.115
netmask 255.255.255.0
gateway 192.168.1.1

```

/etc/resolv.conf
```

nameserver 192.168.1.1

```

/etc/hosts (wall-e is the name of the server)
```

127.0.0.1  localhost
127.0.0.1  wall-e 

```

My cable is fine. Bios setting are defaults ...

Thanks a lot for the help!

---

### Post by TeknoPhil on 2008-08-30
For those who might get into the same problem, here's more information (external links):

[[COLOR="Red"]RTL8102EL / Ubuntu 8.04 intermitent failure[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/240470")


This is a know bug. Seems like Ubuntu server v.7.10 will work with this board.

In my case, I brought a cheap PCI network card and disabled the onboard NIC. It's working like a charm.

---

