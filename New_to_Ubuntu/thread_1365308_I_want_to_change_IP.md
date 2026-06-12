---
title: "I want to change IP"
date: 2009-12-27
forum: New to Ubuntu
---

### Post by 0864045 on 2009-12-27
Hi.. Distinguished brotherhood:

How do I change the IP in the Linux system..?

Thank you very much..

---

### Post by mapes12 on 2009-12-27
Could you explain more about your configuration please and why you need to change an IP address?

Generally, Private IP addresses are managed by your router via DHCP but you can configure static IP addresses if required. Your Public IP address will be assigned to you by your ISP, either dynamically (most popular) or rarely, a static address. You cannot change your Public IP address without your ISP reconfiguring it for you.

---

### Post by diablo75 on 2009-12-27
I believe it is in System>Administration>Networking (I might be wrong).

Once you open that, you'll see several tabs that designate different devices types you can manage from here (Wired, Wireless, etc.).  By default your network device is told to run with DHCP, hence the "Auto Eth" names you'll see.  In the panel you are able to edit or create profiles for your devices.  This makes the most sense if you use a Wireless adapter in several locations (work, coffee shop, home, all of which have different addressing schemes perhaps, different encryption methods, etc.).  For Wired devices, the same sort of priciples apply.  You might want a static IP to be used at home, but DHCP to be enabled somewhere else.

Anyway, for starts you can just select the Auto Eth or similar profile name from the device tab of your choosing and edit it's profile so that your IP is no longer assigned by the router you're connecting to, and setup your own static IP instead.

---

### Post by 0864045 on 2009-12-27
Is not there a special code to change the IP>>or a specific way of applications..?

This is what I mean my question..

Thank you..

---

### Post by mlentink on 2009-12-27
It is not at all clear to me what you mean by your question. 
The easiest is to change the IP adress in the NetworkManager applet, which you can find in your notification area. It is the small icon that shows whether you are connected or not.  Right-click it and select 'edit connections'.

If you know what you are doing, you can also edit the interfaces file directly
```
gksudo gedit /etc/network/interfaces[COLOR=#663300][/COLOR]
```
in this file, find and delete the line that connects by DHCP:
```
iface eth0 inet dhcp
```
then replace it by what you want (example):
```
iface eth0 inet static
        address 192.168.1.101
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.254
```
Note that this is an ***example***, I do not know your actual networking setup!

then make the changes take effect by opening a terminal and:
```
$ sudo /etc/init.d/networking restart
```

---

### Post by 0864045 on 2009-12-27
> **mlentink said:**
> It is not at all clear to me what you mean by your question. 
The easiest is to change the IP adress in the NetworkManager applet, which you can find in your notification area. It is the small icon that shows whether you are connected or not. Right-click it and select 'edit connections'.
 
If you know what you are doing, you can also edit the interfaces file directly
```
gksudo gedit /etc/network/interfaces
```
in this file, find and delete the line that connects by DHCP:
```
iface eth0 inet dhcp
```
then replace it by what you want (example):
```
iface eth0 inet static
        address 192.168.1.101
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.254
```
Note that this is an ***example***, I do not know your actual networking setup!
 
then make the changes take effect by opening a terminal and:
```
$ sudo /etc/init.d/networking restart
```
 
 
I want to change the IP in a manner known as ternimal or applications

---

### Post by mlentink on 2009-12-27
I just gave you both the application method (through NetworkManager applet) as well as the method through terminal.

It seems you might benefit by first reading about the basics of Ubuntu.

See:
[https://help.ubuntu.com/](https://help.ubuntu.com/)

---

### Post by The Secret on 2009-12-27
[LIST=1]
[*]Stop dreaming - not everything can be done via GUI. Most of the solutions will require you to edit configuration files manually.
[*]Do you have a dynamic IP ?
[/LIST]

---

### Post by 3rdalbum on 2009-12-27
> **0864045 said:**
> Hi.. Distinguished brotherhood:

How do I change the IP in the Linux system..?

Thank you very much..

Your ISP determines your IP address.

So the answer is no, you can't change your IP address unless you call your ISP.

---

### Post by mlentink on 2009-12-27
> **3rdalbum said:**
> Your ISP determines your IP address.

So the answer is no, you can't change your IP address unless you call your ISP.

Sorry. This is only true in te situation of a single PC connected directly to the internet. In many if not most situations however, the computer would be connected to a LAN, which would be connected to the internet through a router. Within a LAN it is entirely possible to choose whatever IP-adres you would see fit. Obviously, not all of them would work.

The OP has, as yet, not been able to make clear what it is exactly that he wants to achieve. Before he does, we will not be able to provide definitive answers.

---

