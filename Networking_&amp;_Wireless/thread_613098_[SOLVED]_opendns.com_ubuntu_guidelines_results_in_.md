---
title: "[SOLVED] opendns.com ubuntu guidelines results in &amp;quot;interface eth0 not configured&amp;quot; err"
date: 2007-11-14
forum: Networking &amp; Wireless
---

### Post by koenbeek on 2007-11-14
Google have been having some dns problems in europe and asia lately [(see google problems)]("http://groups.google.com/group/GDSupdates/msg/f8df65d17fd182be")

So I decided to set-up the opendns dns server instead of those of my internet provider.
I followed the instructions on [this page]("https://www.opendns.com/start/ubuntu.php")

the last command they mentioned is : > sudo ifdown eth0 && sudo ifup eth0I get the following error for this command :
[COLOR=Red]> ifdown: interface eth0 not configured
Ignoring unknown interface eth0=eth0.[/COLOR]I am however sure that my network interface is eth0 so I'm not sure why it fails.
I have been googling and looking on the forums for about an hour now and can't figure it out.

I have a fresh install of ubuntu gutsy 64 bits and a dell E521 AMD64.

ifconfig -a shows :
```
eth0      Link encap:Ethernet  HWaddr 00:13:72:37:B8:B0  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:72ff:fe37:b8b0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:9600 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8301 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6657643 (6.3 MB)  TX bytes:1352810 (1.2 MB)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```


/etc/interfaces contains the following :
```
$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

$
``` 

should eth0 not be mentioned in the interfaces file ?
how do I stop and restart my network now ?

my internet connection works correctly but I don't understand why I get the interface eth0 not configured error.

I know it's also possible to execute 
sudo /etc/init.d/networking restart
but this simply does a ifdown -a --exclude=lo and then a ifdown -a --exclude=lo
so I don't think it does anything on my system as lo seems to be the only interface that is defined

---

### Post by noob12 on 2007-11-15
It is ok for eth0 not to be mentioned in /etc/network/interfaces; it means it is managed in roaming mode by NetworkManager

You can reboot or can disable and reenable networking via the NetworkManager applet. .

---

