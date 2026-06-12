---
title: "ip configuration"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by vagelism on 2009-01-19
Hello to all.

I need to know how to apply an ip , mask ,gateway ,and dns
manual to an interface "not permanetly"

just to configure my wireless access point.
PLESE STEP BY STEP CONFIGURATION.
I AM TOTALLY NEW TO LINUX.

Thank you

---

### Post by Iowan on 2009-01-19
Check the **man** page for **iwconfig**.
(In a terminal, type **man iwconfig**)

---

### Post by vagelism on 2009-01-19
> **Iowan said:**
> Check the **man** page for **iwconfig**.
(In a terminal, type **man iwconfig**)

i did but i do not understand many things..
can you make me an example?
thank you

---

### Post by gsocker on 2009-01-19
Do you need to configure it via an ethernet cable or over the wireless interface? 
The steps are a little different.

---

### Post by vagelism on 2009-01-20
> **gsocker said:**
> Do you need to configure it via an ethernet cable or over the wireless interface? 
The steps are a little different.

lets say via ethernet....I belive will be much easier.
Thank you.

---

### Post by gsocker on 2009-01-20
OK. Click on the network icon and  disable networking to keep NetworkManager from causing problems. Look at your access point manual and find out what it's default address is - typically 182.168.0.50(D-Link) or 192.168.0.230(Netgear). 
Open Terminal.
Run:```
sudo ifconfig eth0 ip vvv.xxx.yyy.zzz
```, where v,x, and y are copied from the AP's default address and zzz is between 1 and 254 but **NOT** the same as the access point. You should not need to worry about the other settings as they will default to reasonable values.

Fire up your browser and try to load the access point's address.

---

### Post by DGortze380 on 2009-01-20
sudo ifconfig [interface] [ip address] netmask [netmask]

should be sufficient to configure an access point.

Changes will go away after a reboot, or you can run the command: /etc/init.d/networking restart

example: sudo ifconfig eth0 192.168.0.2 netmask 255.255.255.0

---

### Post by vagelism on 2009-01-21
> **DGortze380 said:**
> sudo ifconfig [interface] [ip address] netmask [netmask]

should be sufficient to configure an access point.

Changes will go away after a reboot, or you can run the command: /etc/init.d/networking restart

example: sudo ifconfig eth0 192.168.0.2 netmask 255.255.255.0

what if I need to add a gateway?
thank you...

---

### Post by hyper_ch on 2009-01-21
edit your /etc/network/interfaces file and add something like this:

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
allow-hotplug eth0
iface eth0 inet static
address 192.168.1.5
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1

```

In that case 192.168.1.x is the private network used. .1 is the router and .5 is the static IP given to that machine.

Then also edit your /etc/resolv.conf and add
```

nameserver 192.168.1.1

```
or the according IP of the router.

Then restart networking:
```

sudo /etc/init.d/networking restart

```

and you should have assigned a static ip.

Maybe you have to change eth0 to eth1 or something... that depends how your network card is identified.

---

### Post by DGortze380 on 2009-01-21
> **vagelism said:**
> what if I need to add a gateway?
thank you...

You shouldn't need to, the default should be fine.

If you do, follow the directions above to edit /etc/network/interfaces

Just remember to make a back-up, as changes to that file are permanent.

---

