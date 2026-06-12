---
title: "Firestarter problem - device not ready"
date: 2007-05-25
forum: Networking &amp; Wireless
---

### Post by e^(i*pi) on 2007-05-25
I am attempting to set up my firewall using firestarter, but I have ran into an problem.  Whenever I finish going through the wizard and try to start the firewall I get a message that says:

Failed to start the firewall
the device eth0 is not ready

I opened up my networking tool and found that my connection is coming through a device labeled loopback interface(lo).  That doesn't show up on firestarter though.  Whenever I look through possible devices all I find are eth0, wifi0, and ath0.  Does anyone have any ideas about what may be going on.

---

### Post by emilio_77 on 2007-05-28
Similar problem after last kernel update (2.6.20-16-generic).

my error msg is

---

failed to start the firewall

the device ppp0 is not ready

please check your network device settings and make sure your internet connection is active

---

my wired network connection works properly

---

### Post by jeremy12 on 2007-05-28
I to had this issue it has to do with your nic not having a IP, if eth0 or ppp0 is your internet connection make sure its set to DHCP

if it is your local card make sure it has a static ip set

"ifconfig" will show all enabled devices
'ifconfig -a' will show ALL Cards regardless of status

To enable your eth0 you can either enable it by assigning an IP and running "ifconfig eth0(or ppp0) up" or by telling your DHCP client to get an IP and assign it to eth0, but just assigning your self might be easier

example of a /etc/network/interfaces

```
auto lo
iface lo inet lookpack

iface eth0 inet dhcp

auto eth0

iface eth1 inet static
address 192.168.0.1
network 182.168.0.0
netmask 255.255.255.0
broadcast 192.168.0.255

auto eth1
```

if this is all right then it MIGHT be a issue with restarting your cable modem or whatever you use at the same time as your server and that talking with eth0 and assigning its ip so the firewall is just seeing it as busy but i dunno about that

---

