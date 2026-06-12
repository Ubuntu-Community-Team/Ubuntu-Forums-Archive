---
title: "Wireless connection droped periodic"
date: 2008-11-25
forum: Networking &amp; Wireless
---

### Post by mehrdadm on 2008-11-25
Hi there,
I was upgraded My Kubuntu 8.04 (with mixed KDE 4.1.2) to Kubuntu 8.10, 2 days ago!

yesterday, wireless connection to my ADSL/Access Point dropped periodic and get connected again.
today my connection dropped and it cannot connect again! even Wired Connection! and my laptop cannot connect to network!
after that, i ask for it on Kubuntu IRC channel, and they say remove /etc/network/interface file, and restart system.
so, it connected again. but just for a while!
and after that I have to restart NetworkManager service to get connect again! and after a while my connection dropped and cannot connect until i restart NetworkManager service.

My system is Dell Inspiron 6400 Laptop.

Is there any idea?

---

### Post by Ayuthia on 2008-11-25
If you are also having problems with the wired connection, can you turn off KNetworkManager (right click on the network icon in the panel and select quit) and try the following in the Konsole:
```
sudo dhclient eth0
```

This is mainly to test and see if KNetworkManager is having problems with the connection or if it is something else.

---

### Post by mehrdadm on 2008-11-25
> **Ayuthia said:**
> If you are also having problems with the wired connection, can you turn off KNetworkManager (right click on the network icon in the panel and select quit) and try the following in the Konsole:
```
sudo dhclient eth0
```

This is mainly to test and see if KNetworkManager is having problems with the connection or if it is something else.

I was tested this before!

Before i remove that file (/etc/network/interfaces) there isn't any "eth0" I think it was something else!
And after moving that file, there is just wlan0,wmaster0 and lo on ifconfig output! and there isn't any replacement for interfaces file! :-/

but anyway: on either before or after, "sudo dhclient XXX" doesn't work! :-/

---

### Post by mehrdadm on 2008-11-25
> **Ayuthia said:**
> If you are also having problems with the wired connection, can you turn off KNetworkManager (right click on the network icon in the panel and select quit) and try the following in the Konsole:
```
sudo dhclient eth0
```

This is mainly to test and see if KNetworkManager is having problems with the connection or if it is something else.

I check it again, it name is "pan0" :-/
and dhclient cannot get IP! :-/

---

### Post by Ayuthia on 2008-11-25
> **mehrdadm said:**
> I was tested this before!

Before i remove that file (/etc/network/interfaces) there isn't any "eth0" I think it was something else!
And after moving that file, there is just wlan0,wmaster0 and lo on ifconfig output! and there isn't any replacement for interfaces file! :-/

but anyway: on either before or after, "sudo dhclient XXX" doesn't work! :-/
If that is the case, please try the following:
```
sudo ifconfig eth0 up
sudo dhclient eth0
```
KNetworkManager might have turned off the connection.

---

### Post by mehrdadm on 2008-11-26
> **Ayuthia said:**
> If that is the case, please try the following:
```
sudo ifconfig eth0 up
sudo dhclient eth0
```
KNetworkManager might have turned off the connection.
this doesn't work, and it says that "ignore unknown interface eth0"

How can I reconfigure interfaces?

and:
finally i install a fresh Kubuntu 8.10 and a fresh Ubuntu 8.10, on another partition!
Now, on new systems, (new Ubuntu and Kubuntu) I could connect to my home network via eth0. and its OK.
but I cannot connect to Wireless network, in fact it connects to it, and after a while my connection gets dropped, cannot connect any more, even i restart NetworkManager service!

---

### Post by mehrdadm on 2008-11-26
Ethernet (eth0) problem fixed by removing Kernel backport modules pkg, as I found in bug tracker that it's a bug of that package!

Now, just I can't connect with my wireless card, after connection gets dropped as i said before! :-/

---

