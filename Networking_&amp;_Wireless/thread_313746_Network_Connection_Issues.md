---
title: "Network Connection Issues"
date: 2006-12-06
forum: Networking &amp; Wireless
---

### Post by ziadoz on 2006-12-06
I'm a newbie to Linux and having some teething problems connecting my new Ubuntu setup to the internet. I'm running a Netgear DG834Gv2 (ip: 192.168.0.2, dhcp enabled) router and connecting the machine with Ubuntu on it via ethernet. I've enabled the network card in the networking options in Ubuntu, but I still can't ping anything or open any web pages in Firefox.

Thanks in advance for any help. :)

---

### Post by gitargr8 on 2006-12-06
Open up your terminal program and run the following commands:

```

$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:08:74:04:B9:4C
          inet addr:10.194.193.145  Bcast:10.194.193.255  Mask:255.255.254.0
          inet6 addr: fe80::208:74ff:fe04:b94c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:291537 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3592 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:63695889 (60.7 MiB)  TX bytes:532783 (520.2 KiB)
          Interrupt:11 Base address:0x2c00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:112 (112.0 b)  TX bytes:112 (112.0 b)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
$ sudo ifconfig eth0 up
$ sudo dhclient eth0

```

Change eth0 to whatever your network connection may be.

~Ryan

---

### Post by ziadoz on 2006-12-06
EDIT: Got it working, thanks a lot. :)

---

### Post by ziadoz on 2006-12-10
Is there anyway I can make these commands run on boot? Because I seem to have to do them everytime I reboot my machine in order to get a connection.

---

### Post by gitargr8 on 2006-12-10
There is a way to do this, I know it has something to do with your /etc/network/interfaces file, you can try searching the forum, or perhaps someone more knowledgeable than I can respond.

---

### Post by dbott67 on 2006-12-10
Normally, all interfaces should be enabled automatically in the **/etc/network/interfaces** file.

For example, my file looks like this:
```
dbott@edgy:~$ cat /etc/network/interfaces
[COLOR="Red"]auto lo[/COLOR]
iface lo inet loopback

[COLOR="Red"]auto eth0[/COLOR]
iface eth0 inet dhcp

[COLOR="Red"]auto eth1[/COLOR]
iface eth1 inet dhcp

[COLOR="Red"]auto eth2[/COLOR]
iface eth2 inet dhcp

[COLOR="Red"]auto ath0[/COLOR]
iface ath0 inet dhcp
[COLOR="Red"]
auto wlan0[/COLOR]
iface wlan0 inet dhcp

```

Notice the [COLOR="Red"]auto[/COLOR] in front of each interface.  This tells the OS to enable the interface upon startup.

If you can post your interfaces file, we can make sure it looks okay.  Enter the following command at the terminal and paste the output here:
```
cat /etc/network/interfaces
```

-Dave

---

### Post by ziadoz on 2006-12-10
I got the following:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

iface eth1 inet dhcp

```

eth1 is the device thats not connecting until i run:

```

dhclient eth1

```

I changed it to:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp

```

When I reboot it seems to work. Is this what I was supposed to change?

---

### Post by dbott67 on 2006-12-10
> **ziadoz said:**
> 
I changed it to:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp

```

When I reboot it seems to work. Is this what I was supposed to change?

Exactly! :)

---

### Post by ziadoz on 2006-12-10
> **dbott67 said:**
> Exactly! :)

Thanks for all your help guys. :)

---

### Post by linuxhhp on 2006-12-10
I will show u the simple way to resolve the problem.
First install the Network Manager and KNetwork MAnager.
Go to Networking and disable all the connection.
Restart your pc or laptop.
Knetworkmanager will search the networks itself.
Select the right network.
Provide approproiate security key when needed
Thats it you are connected.

---

