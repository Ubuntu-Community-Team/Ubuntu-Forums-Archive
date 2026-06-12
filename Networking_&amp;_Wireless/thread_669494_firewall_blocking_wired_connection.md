---
title: "firewall blocking wired connection"
date: 2008-01-16
forum: Networking &amp; Wireless
---

### Post by tuokor on 2008-01-16
I have wireless home network. There are three machines connected to te wireless router. First  is desktop computer with a wired connection. The second is a ubuntu server which is wireless and the third is my laptop. The problem is that I connected the server and the desktop computer with a wired connection. Now if I want to connect to the server via wired I have to stop the firestarter firewall or else it blocks everything. Ping says operation is not permitted and ssh won't connect. Via wireless everything works fine. I would really want to get the wired to work because I'm transfering large files between these computers and it is very slow with the wireless.

Thanks for advance

Here is my /etc/network/interfaces files from the server and the desktop

The server:
```

iface eth0 inet static
        address 192.168.12.2
        netmask 255.255.255.0


auto wlan0
iface wlan0 inet dhcp
wireless-essid XXXXXXXX
wireless-enc   s:XXXXXXXX
wireless-channel 11
wireless-mode   managed

```
The desktop
```

auto lo
iface lo inet loopback



iface eth1 inet static
address 192.168.12.3
netmask 255.255.255.0

auto eth1

```

The desktop has also eth0 interfaces which goes to the router and gets its ip via dhcp (it wasn't in the file probably because network manager deals that).

The firestarter isn't configured to block anything from going out.The server has open port for ssh.

---

