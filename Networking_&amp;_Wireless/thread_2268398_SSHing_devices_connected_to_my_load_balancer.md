---
title: "SSHing devices connected to my load balancer"
date: 2015-03-08
forum: Networking &amp; Wireless
---

### Post by max94 on 2015-03-08
[COLOR=#333333][FONT=UbuntuRegular]I have three computers set up like this:
[/FONT][/COLOR][IMG]http://i.stack.imgur.com/UCgGM.png[/IMG]d[COLOR=#333333][FONT=UbuntuRegular]But I am having issues understanding how to setup the [/FONT][/COLOR]/etc/network/interfaces[COLOR=#333333][FONT=UbuntuRegular] for each device so that they can all be SSHd[/FONT][/COLOR][COLOR=#333333][FONT=UbuntuRegular]I have tried this:
[/FONT][/COLOR]
Load Balancer:
    Eth1 (Local)
        address 192.168.1.10
        netmask 255.255.255.0
        network 192.168.0.0
        gateway 192.168.1.254 #hub
    Eth0
        address 192.168.0.10
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255 #hub

RPi1:
    address 192.168.0.20
    netmask 255.255.255.0
    network 192.168.1.0
    broadcast 192.168.0.10 #Load Balancer Eth0
    gateway 192.168.1.10 #Load Balancer Eth1
RPi2:
    address 192.168.0.30
    netmask 255.255.255.0
    network 192.168.1.0
    broadcast 192.168.0.10 #Load Balancer Eth0
    gateway 192.168.1.10 #Load Balancer Eth1
[COLOR=#333333][FONT=UbuntuRegular]I am testing whether they are connected to the internet by trying to ssh into them but I can only successfully ssh into the Load Balancer. Can you spot anything that may be causing the issue?[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]I have also tried sshing like this:[/FONT][/COLOR]
ssh -t 192.168.1.10 ssh 192.168.0.20 
[COLOR=#333333][FONT=UbuntuRegular]But it is not working[/FONT][/COLOR]

---

