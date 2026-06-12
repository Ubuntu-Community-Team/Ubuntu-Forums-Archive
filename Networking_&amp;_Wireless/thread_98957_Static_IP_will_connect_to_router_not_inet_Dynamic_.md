---
title: "Static IP will connect to router not inet/ Dynamic IP will connect to all"
date: 2005-12-04
forum: Networking &amp; Wireless
---

### Post by basementjack on 2005-12-04
I have been searching this forum and google, but I cannot see why my wireless laptop will not connect with static IP, when dynamic IP works....
These are my configurations:

**DHCP**
```

mapping hotplug
        script grep
        map eth3

## The primary network interface
iface eth3 inet dhcp
        ## wireless-* options are implemented by the wireless-tools package
        wireless-essid XXX
        wireless-key XXXXXXXXXXXXX

```

**Static**
```

mapping hotplug
        script grep
        map eth3

## The primary network interface
iface eth3 inet static
        address 192.168.1.3
        netmask 255.255.255.0
        ## wireless-* options are implemented by the wireless-tools package
        wireless-essid XXX
        wireless-key XXXXXXXXXXXXX

```

I checked that my Router's DHCP IP-range is from 100 to 149, so that's not it...
I checked that with a cable static IP and dhcp works just fine, so my Router does support it...

Does anybody have a good idea?..

---

### Post by ranf on 2005-12-04
Why do you want it to be static?

Can you ping your router (I assume it is something like 192.168.1.1)?
Can you ping google.com by IP:
```
ping 64.233.187.99
```

If that works you will just have to take care about name resolution:
```
sudo gedit /etc/resolv.conf
```
`nameserver <IP of your router>' should work just fine.

---

### Post by inhetep on 2005-12-04
Hi, 

u need to define a gateway address. The address is the ip of your router mostlikely

192.168.1.1

add the following line to your interfaces file 

```
gateway 192.168.1.1
```
 
below your line

```
wireless-key XXXXXXXXXXXXX
``` .

Then to ping your router

```
ping 192.168.1.1
```

 If this works try to 
```
ping www.google.com
```.
If it works u are set. 
If this doesn't work and a ping to googles
IP works (see post before), u need to check the resolv.conf

if no nameserver line exist 

add the line
  
```
nameserver 192.168.1.1 
```

if this is your router

or the nameserver of your provider simply google it using your dhcp config again and add

```
nameserver xxx.xxx.xxx.xxx #DNS  IP of provider  
```

then everything should work.

---

### Post by basementjack on 2005-12-05
[QUOTE=ranf]Why do you want it to be static?[/QUOTE]

Because I am setting up network between my laptop and my desktop... Seems easier with static ip's..

[QUOTE=inhetep]
add the following line to your interfaces file

gateway 192.168.1.1

below your line

wireless-key XXXXXXXXXXXXX
[/QUOTE]

How on earth did you find out that the gateway-line has to be below one's wireless-key-line? - It Worked! :)

And any idea why gateway was not need when I tried a static ip with a cable?..

---

### Post by inhetep on 2005-12-05
It doesn't matter where to put it (well it has to be associated with the interface). It is was only easier to explain. :-\"  

> And any idea why gateway was not need when I tried a static ip with a cable?..

I have got no idea.:confused:  I would assume your cable modem handles the connection setup.

---

### Post by basementjack on 2005-12-06
Well it worked.. :O Thanks..

---

