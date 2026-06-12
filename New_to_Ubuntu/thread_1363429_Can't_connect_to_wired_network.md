---
title: "Can't connect to wired network"
date: 2009-12-24
forum: New to Ubuntu
---

### Post by rajwraith on 2009-12-24
I tried out Ubuntu 9.10 live CD. Everything worked ok. But just like 9.04, 9.10 can't connect to my wired network. I applied all the necessary settings ( IP address, subnet mask, MAC Address and stuff). I clicked apply but the network manager keeps reverting to "Auto Ethernet" instead of "Auto eth0" where my custom settings are. My motherboard is a Asus P5KPL-AM. 
I faced the same problem with my Ubuntu 9.04. Is it my motherboard? Or is it a ubuntu bug?
Please help me here, I really want to use and spread ubuntu.

---

### Post by Temposs on 2009-12-24
It's usually easier to not specify your network settings, and let DHCP take care of it. In 99% of cases, if the hardware is compatible with Ubuntu, you shouldn't have to specify anything to connect to a wired network.

---

### Post by rajwraith on 2009-12-24
My ISP requires the custom settings. So I have to use them.

---

### Post by Ocxic on 2009-12-24
in a terminal type "route" to make sure your getting a default route. without one, you won't be able to connect. 
```

ikrel@xilti:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.2.0        *               255.255.255.0   U     1      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         10.0.2.1        0.0.0.0         UG    0      0        0 eth0       <--------default route
ikrel@xilti:~$ 

```

To add one type "sudo route add default gw 1.2.3.4" replace 1.2.3.4  with your own gatway. I've found my network manager does not set this for some reason and i have to manually add it from time to time

Also make sure you remove auto connect from the settings in network manager for other connections

---

### Post by Iowan on 2009-12-24
Is Auto Ethernet set to "Connect automatically"?
Is Auto eth0?

(Ouch... I'm getting redundant again...)

---

### Post by chuina on 2009-12-24
I set default gateway from this file /etc/networking/interfaces

chuina@desktop:~$ sudo gedit /etc/network/interfaces
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
    address 192.168.10.1
    network 192.168.10.0
    netmask 255.255.255.0
    broadcast 192.168.10.255
    gateway 10.0.0.1
```

My gateway here is 10.0.0.1.

---

### Post by rajwraith on 2009-12-25
how do i set the MAC address? and the DNS server settings?

---

### Post by rajwraith on 2009-12-25
btw, thanks for your help guys. Really appreciate the effort :)

---

### Post by allenbradley on 2009-12-25
MAC address is machine-specific (Unless you _have_ to change it). You can change other settings by using the GUI route as well. Right click on the network manager on the top right corner of your screen ( If it is not there, fire up a terminal and type in nm-applet ). Now click on Edit Connections. Now, choose the wired connection (generally, Auto eth0) and edit. Now click on the tab IPv4 setting and choose Manual from the drop down box. Now, you can easily add all the information you want. Of course, all this assumes you have GNOME and X. Otherwise, ocxic and chuina probably have better advice. Is it still not storing these settings? 

I know I am being redundant, but just to make sure.

---

### Post by rajwraith on 2009-12-25
I know how to do that already. But as I said before, it's not working. I applied all the custom settings to "Auto eth0" in Network Manager. Everytime I try to connect, it keeps reverting back to "Auto Ethernet" (which is created automatically without my knowledge) which doesn't have all the custom settings. I even tried changing the name from "Auto eth0" to "Auto Ethernet", that didn't work.
Strange thing is, I've used the internet doing the same exact things in 9.04. Then I changed my motherboard and that was the last of my days with Ubuntu. I reinstalled 9.04 but the problem persisted. Thought 9.10 would change things but...
Anyway, thanks.

---

### Post by Iowan on 2009-12-25
You *should* be able to uncheck the "Connect automatically" box on Auto eth0. (*should* and *can* may be different)

---

### Post by rajwraith on 2009-12-29
I can but when i right click on the network icon,I get "Auto Ethernet", and not "Auto eth0". How can I directly connect to "Auto eth0"?

---

### Post by Temposs on 2009-12-29
When I right-click on the network icon, click "Edit Connections", under the Wired tab I have "Auto eth0". Is this different from what you have?

---

### Post by rajwraith on 2009-12-30
yep

---

### Post by rajwraith on 2010-01-01
one thing, i've been only testing through the live CD. should i install ubuntu first and then try?

---

