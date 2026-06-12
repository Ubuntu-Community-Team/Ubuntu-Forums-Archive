---
title: "Automatic dhcp"
date: 2009-04-19
forum: New to Ubuntu
---

### Post by Veehmot on 2009-04-19
I have to manually write the command "sudo dhcpclient" to auto configure eth0.

Is there a faster way? I have ifupdown installed, but I cant get this to work in Networks Manager, there is always a network device called 'lo' that is read only, so I don't know how to add a new network device and establish an automatic dhcp.
I tried adding one manually, and setting Auto DHCP in settings, but that doesn't work.

---

### Post by nandemonai on 2009-04-19
Use ifconfig -a to list all your network interfaces and copy the MAC address for eth0 (HWaddr). Then create a new connection in Network manager and be sure to paste that into the MAC Address bit along with any other settings you may want.

That _should_ do it.

---

### Post by Veehmot on 2009-04-19
Nope, that doesn't do it. Now the connection 'lo' is gone in Network Configuration, and there is my connection, but it says it has errors.
I followed your instructions, copy paste the mac address and leave the dhcp settings to auto.

---

### Post by Iowan on 2009-04-19
What's in */etc/network/interfaces*?

---

### Post by Veehmot on 2009-04-19
[size=4]**/etc/network/interfaces**[/size]
```
auto lo
iface lo inet loopback


auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider

auto eth0
iface eth0 inet manual
```

---

### Post by kukibird1 on 2009-04-19
In  a terminal run 
 sudo service networking stop and sudo service  Networkmanager stop

In /etc/network/interfaces file add  only the following 

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

restart the networking and Network manager services.

---

### Post by Veehmot on 2009-04-19
Yup, that made the trick, thank you!!

Do you mind helping me with this one?

[Pidgin can't connect: PPoE + DHCP + Router]("http://ubuntuforums.org/showthread.php?t=1130270")

---

