---
title: "Can't connect wired to internet"
date: 2010-08-04
forum: New to Ubuntu
---

### Post by i.got.ur.back.no on 2010-08-04
Hi, i just installed ubuntu 10.4 LTS on my laptop and i when i tried to connect to the internet wired i couldn't. nothing happened! am i supposed to do something in the terminal or something? thx

---

### Post by sikander3786 on 2010-08-04
Hi.

Basically you don't need to do anything to access the internet unless you are behing a proxy server. A few basic questions

I suppose you are using ADSL. Is your LAN Card recognized by Ubuntu? There should be a Network Icon present in the top right corner of your screen in the system tray.

Is your PC a dhcp client? Is the gateway information correctly distributed by the dhcp server?

Regards.

---

### Post by dv3500ea on 2010-08-04
If you go to System -> Administration -> System Monitor
and click on the 'Resources' tab, can you see any activity under 'Network History'?

If you open a web browser (the default is firefox), what happens?

Is the 'wired' connection an ethernet connection or something else (eg. USB)?

Is it dialup or broadband?

---

### Post by i.got.ur.back.no on 2010-08-04
okay the answer to ur first question is that i don't see anything under Network History..
 
answer to ur second question is when i open firefox is says** Welcome to Ubuntu 10.4 LTS** and it just talks about ubuntu
 
Answer to the third question is that i have ethernet connnection
 
and fourth question i have mobile broadband

---

### Post by dv3500ea on 2010-08-04
When you try to go to a website (eg. google, what happens)?

When you click on the network indicator in the top right hand corner, what does it say underneath 'Wired Network'?

To get extra (advanced) information you can go to System -> Administration -> Network Tools.

To try to configure your connection, go to System -> Preferences -> Network Connections

---

### Post by cj13579 on 2010-08-04
Is this a new install? I did an install recently that didn't pick up my network card. However, the following solved it:

Add the following lines to: /etc/network/interfaces by doing:

```
sudo nano /etc/network/interfaces
```

and then add the following lines for DHCP

```

auto eth0
iface eth0 inet dhcp
```

or for a static IP

```
autho eth0
iface eth0 inet static
address 192.168.1.5
netmask 255.255.255.0
gateway 192.168.1.254
```

or whatever your IP to be

then

```
sudo /etc/init.d/networking restart
```

---

### Post by dineshs on 2010-08-05
If you are using mobile broadband you can configure it via Network manager
Right click on the double arrow icon on top right of the panel-click edit connections then-mobile broadband -add ......
But to what device your ethernet cable is plugged?What does
```
ifconfig -a
```say ?

---

