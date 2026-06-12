---
title: "Switching to STATIC from DHCP"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by zeeple on 2009-01-28
Hi.  I have a newly built machine which I would like to switch from using DHCP to static.  I tried doing this with the GUI but everytime I rebooted it it came back up DHCP. I read there is a bug with Network manager, so okay I am fine with doing it via cli.

The /etc/network dir lacks any ifcfg-eth0 that I can find, and there is no /etc/sysconfig to be found.  The first thing I need to do is change BOOTPROTO=dhcp to BOOTPROTO=static, but I cannot find where this is done in ubuntu.

Any takers?

---

### Post by glotz on 2009-01-28
Is this of any use? [https://help.ubuntu.com/community/StaticDnsWithDhcp](https://help.ubuntu.com/community/StaticDnsWithDhcp)

---

### Post by zeeple on 2009-01-28
> **glotz said:**
> Is this of any use? [https://help.ubuntu.com/community/StaticDnsWithDhcp](https://help.ubuntu.com/community/StaticDnsWithDhcp)

Unfortunately no, that is of no use to me.  I need to make the server NOT use dhcp, using the command line, and 'Network Configuration' in the GUI does not work.

---

### Post by ibutho on 2009-01-28
Edit /etc/network/interfaces and change the entry for your network device (e.g. eth0) from something like
```

auto eth0
iface eth0 inet dhcp

```
to something like
```

iface eth0 inet static
    address 192.168.1.2
    netmask 255.255.255.0
    gateway 192.168.1.1

```

---

### Post by zeeple on 2009-01-28
> **ibutho said:**
> Edit /etc/network/interfaces and change the entry for your network device (e.g. eth0) from something like
```

auto eth0
iface eth0 inet dhcp

```
to something like
```

iface eth0 inet static
    address 192.168.1.2
    netmask 255.255.255.0
    gateway 192.168.1.1

```

Thanks!  I got a similar answer from the great google in the sky.  I'll mark this one solved.

---

### Post by Devastator9 on 2009-01-28
> **ibutho said:**
> Edit /etc/network/interfaces and change the entry for your network device (e.g. eth0) from something like
```

auto eth0
iface eth0 inet dhcp

```
to something like
```

iface eth0 inet static
    address 192.168.1.2
    netmask 255.255.255.0
    gateway 192.168.1.1

```

I also have to edit the 
/etc/resolv.conf
add nameserver xxx.xxx.xxx
    nameserver xxx.xxx.xxx.

---

### Post by zabrab on 2012-12-07
One other different thing you could do
Still use HDCP
but reserve the IP address based on the MAC address
therefore therre would be no change on your side
just on the DHCP server side

---

### Post by nothingspecial on 2012-12-07
Old thread.

Closed.

---

