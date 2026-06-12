---
title: "ICS wont work! Please help!"
date: 2008-11-20
forum: Networking &amp; Wireless
---

### Post by Fist Maker on 2008-11-20
Hello, I'm new to Ubuntu and I'm having trouble setting up a Network, I've tried using firestarter and following steps to set up NAT and DHCP/ipv4 in the terminal, but I cant seem to get internet from my Linux Box to my Xbox 360. My Setup is: LinuxBox with Internet(Working) to Hub/Switch to Xbox 360. I show No activity in firestarter when I set it up in eth1. My Linux box has eth0 set with internet, and eth1 is my other nic card to route it all out. I've tried to manually configure I.P.'s from eth1 and my Xbox, but either my I.P test fails or My DNS fails. I really would like to get my Xbox live back, but I'm not even sure what the next step is. I've downloaded and configured Firestarter, ipmasq and dnsmasq and configured to what the tutorials have asked to no avail either. The network worked when I had XP on this computer, so I'm not sure what else to do here. Please Help!

---

### Post by cariboo on 2008-11-20
The netblock on you second network adapter has to be different for the adapter connected to the internet. For example if you external ip address is:

```
192.168.1.100
```

then your internal ip address should be:

```
192.168.2.100
```

To set static ip address you have to edit /etc/network/interfaces eg:

```
sudo nano /etc/network/interfaces
```

edit the interfaces file to look something like this:

```
/etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
    address 192.168.1.200
    netmask 255.255.255.0
    broadcast 192.168.1.255
    gateway	192.168.1.1

# Secondary network interface
auto eth1
iface eth1 inet static
    address   192.168.2.100
    netmask   255.255.255.0
    broadcast 192.168.2.255
    gateway   192.168.1.200 

```

Note: you have to use the ip address of the external nic as the gateway for the internal nic.

Jim

---

### Post by Fist Maker on 2008-11-20
Thank you for the reply, but I am very new at this and I'm confused on what to do. I've been given alot of different instructions on what to do, So now I'm not sure what to put where. Can you explain a little bit further? I have everything set up for DHCP, so I'm not sure what I.P. to put where.

---

### Post by cariboo on 2008-11-20
I added some extra to my post see above.

Jim

---

### Post by Fist Maker on 2008-11-20
Ty again for clairifying. I'm abit scared to touch my eth0. (would DIE without my internet). Am I able to copy/paste exactly what you have typed into that file?

---

### Post by Fist Maker on 2008-11-20
Here is my ifconfig:

eth0      Link encap:Ethernet  HWaddr 
          inet addr:24.16.179.165  Bcast:24.16.183.255  Mask:255.255.248.0
          UP BROADCAST RUNNING MULTICAST  MTU:576  Metric:1
          RX packets:4345094 errors:0 dropped:0 overruns:1 frame:0
          TX packets:574769 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:749030409 (749.0 MB)  TX bytes:43084735 (43.0 MB)
          Interrupt:21 Base address:0x6000 

eth1      Link encap:Ethernet  HWaddr 
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:18ff:fe9e:5801/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3683 errors:0 dropped:0 overruns:0 frame:0
          TX packets:94 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1053996 (1.0 MB)  TX bytes:7200 (7.2 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:966 errors:0 dropped:0 overruns:0 frame:0
          TX packets:966 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:47628 (47.6 KB)  TX bytes:47628 (47.6 KB)

---

### Post by Fist Maker on 2008-11-20
I've also followed this procedure:
Procedure to follow

1. Get bridge-utils through Synaptic. This is the software we'll use to create the Network Bridge.

sudo aptitude install bridge-utils

Now, keep in mind to either print this out or not exit your browser, because in this next step we'll stop the Networking Services to change them.

2. Open a terminal, and type

sudo /etc/init.d/networking stop

Keep the terminal open.

3. Now we're going to edit our interfaces file:

gksu gedit /etc/network/interfaces

Replace whatever is there with:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet manual

auto eth1
iface eth1 inet manual

auto br0
iface br0 inet dhcp
bridge_ports eth0 eth1

Save the changes.

4. Now we'll restart the Network Services

sudo /etc/init.d/networking start

I'm not sure if this will affect anything either

---

### Post by Fist Maker on 2008-11-20
Ok. I have no idea what to do next. I cant get into the #ubuntu chat with IRC, as I cannot register for some reason. So I have no other options but here on the forums. Someone please provide me an option here. I switched over from XP and windows, and I really like this system, but I need to be able to share my internet. If anyone out there can help it would be very appreciated. I'd HATE to have to go back to XP.

---

### Post by geo21 on 2008-11-21
Hello.
i want to share my internet connection with another computer in my home, but i have internet acces on  eth1 and on eth0 i wanna share it. my ip is given by the main server on dhcp mode. please , anyone could help me with some  scripts or commands? thank you in advance. i forgot to type here what  version of ubuntu i have : 8.04

---

### Post by Iowan on 2008-11-21
[Here]("https://help.ubuntu.com/community/Internet/ConnectionSharing") is a help page on connection-sharing.

---

