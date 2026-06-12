---
title: "confuguring TCP/IP"
date: 2009-05-01
forum: New to Ubuntu
---

### Post by hashi856 on 2009-05-01
I need to configure my TCP/IP. I've looked at the man and info pages, I checked google, and I can't find a good source to teach me how to configure it.

---

### Post by victorbrca on 2009-05-01
Can you be a bit more specific on what you need? Maybe explain what you are trying to do!! 

Cheers,

Vic.

---

### Post by spiderbatdad on 2009-05-01
/etc/resolv.conf is where you set your dns query server...on one line each like so:
```
nameserver xx.xxx.xxx.xx
nameserver xx.xxx.xxx.xx
```
In /etc/network/interfaces you can specify how you want to connect...as in auto dhcp or static. For example:
```
#auto eth0
iface eth0 inet static
address xx.xxx.xx.x
netmask xxx.xxx.xxx.x
network xxx.xxx.xx.x
broadcast xx.xx.xxx.xx
gateway xx.xxx.x.xx

```

---

### Post by Iowan on 2009-05-01
A couple of networking links for you...
[http://www.debianadmin.com/ubuntu-networking-for-basic-and-advanced-users.html]("http://www.debianadmin.com/ubuntu-networking-for-basic-and-advanced-users.html")
[https://help.ubuntu.com/8.04/serverguide/C/network-configuration.html]("https://help.ubuntu.com/8.04/serverguide/C/network-configuration.html")

---

### Post by hashi856 on 2009-05-03
> **victorbrca said:**
> Can you be a bit more specific on what you need? Maybe explain what you are trying to do!! 

Cheers,

Vic.

Ok here's the deal. I don't know most of the terms that have to do with what I'm trying to accomplish, so I'm just gunna try to explain it in the most basic layman's terms...

I'm in the army, and I'm deployed to Afghanistan. There is a place her where I can connect my laptop to the internet, but the TCP/IP setting have to be input manually, exactly like in the attached picture. As you can probably tell, the picture is of Windows, not Linux. I need to know where and how to input that exact information on Ubuntu.

---

### Post by arapa on 2009-05-03
Are you connecting by plugging a cable into your laptop or by using your wireless card?

By default Ubuntu puts a Network Manager applet up by the clock on the top toolbar. This tool allows you to set your IP information using a graphical interface (GUI). (right click > edit connections).

---

### Post by hashi856 on 2009-05-03
> **arapa said:**
> Are you connecting by plugging a cable into your laptop or by using your wireless card?

Plugging in a cable

---

### Post by jespdj on 2009-05-03
Do you see a networking icon in the top right of the screen? Click on it with the right mouse button and select "Edit Connections...".

In the dialog that appears, select the tab "Wired", click on your network connection and click the "Edit..." button. Enter your password in the dialog that appears. Then click the "IPv4" tab, where you can enter the information in approximately the same way as in Windows.

See the attached screenshot. (Note, this is with Ubuntu 9.04).

---

### Post by llemm on 2009-05-03
> **hashi856 said:**
> Ok here's the deal. I don't know most of the terms that have to do with what I'm trying to accomplish, so I'm just gunna try to explain it in the most basic layman's terms...

I'm in the army, and I'm deployed to Afghanistan. There is a place her where I can connect my laptop to the internet, but the TCP/IP setting have to be input manually, exactly like in the attached picture. As you can probably tell, the picture is of Windows, not Linux. I need to know where and how to input that exact information on Ubuntu.



To Manually assign an IP address

ifconfig eth0 <ipaddress that you want> netmask <subnetmask> 

In xp subnet is automatically assigned based on your IP address in Linux its Manual

to add a default gateway

route add default gw <gateway address> eth0

---

### Post by arapa on 2009-05-03
If the IPv4 settings says 'Automatic (DHCP)' on the dropdown switch to 'Manual'.

Then click the '+Add' button to bring up the box to enter the network settings.

Add both your primary and secondary DNS servers in the box separated by a comma (ie. 88.202.19.129, 4.2.2.2)

The Windows terminology is a little different but they mean the same thing:

Address = IP address
Netmask = Subnet mask
Gateway = Default gateway

---

### Post by Skrynesaver on 2009-05-03
From the desktop, right click on the network manager icon in your top panel, click on edit connections, in the Wired tab, select eth0 and click edit, in the ipv4 settings tab, change from DHCP to manual.
Add the settings.

---

