---
title: "cant configure my interenet connection"
date: 2010-03-25
forum: New to Ubuntu
---

### Post by r.sushant on 2010-03-25
hello friends i am new to ubuntu, using it on pen drive along with win7 on my laptop.
i am using cablenet, and very first time when i connected my cable, it was detected automatically and i was able to use internet. but later ubuntu never configure it automatically, n even i cldnt fix that!
so, if i want to use my internet i have to switch myself to win7.
please help me in this matter!
thank you!

---

### Post by 2hot6ft2 on 2010-03-25
If you right click on the network manager applet in the top panel and select Edit Connections what does it show under Wired?
Does it show "Auto eth0", or "ifupdown"?

---

### Post by r.sushant on 2010-03-25
it shows Auto eth0!

---

### Post by 2hot6ft2 on 2010-03-25
Ok, I take it that it's plugged into the router so let's see what you have with
Open a terminal
Applications > Accessories > Terminal
and run
```
ifconfig
```
And post the results
Looking for whether or not it's getting an IP Address, and whether or not it's getting one for both the ethernet adapter and wifi adapter at the same time.

---

### Post by r.sushant on 2010-03-25
ifconfig gave me following output!


   ubuntu@ubuntu:~$ ifconfig
  eth0      Link encap:Ethernet  HWaddr 00:24:e8:81:ea:39  
            inet6 addr: fe80::224:e8ff:fe81:ea39/64 Scope:Link
            UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
            RX packets:333 errors:0 dropped:0 overruns:0 frame:1
            TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:1000
            RX bytes:27461 (27.4 KB)  TX bytes:1016 (1.0 KB)
            Interrupt:16
   
  lo        Link encap:Local Loopback  
            inet addr:127.0.0.1  Mask:255.0.0.0
            inet6 addr: ::1/128 Scope:Host
            UP LOOPBACK RUNNING  MTU:16436  Metric:1
            RX packets:0 errors:0 dropped:0 overruns:0 frame:0
            TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:0
            RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by 2hot6ft2 on 2010-03-25
> **r.sushant said:**
> ifconfig gave me following output!


   ubuntu@ubuntu:~$ ifconfig
```
  eth0      Link encap:Ethernet  **HWaddr** 00:24:e8:81:ea:39  
            inet6 addr: fe80::224:e8ff:fe81:ea39/64 Scope:Link
            UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
            RX packets:333 errors:0 dropped:0 overruns:0 frame:1
            TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:1000
            **RX bytes:27461 (27.4 KB)  TX bytes:1016 (1.0 KB)**
            Interrupt:16

``` 

It's seeing the adapter and apparently there is no wifi adapter so the question is why isn't it getting an IP Address.
Since it works in win. a hardware problem can be ruled out.
You might try
```
sudo /etc/init.d/networking restart
```
if that doesn't help what do you get from
```
lspci
```
Looking for the Ethernet adapters info to search and see if others have had problems with it.

You can also try
```
cat /etc/network/interfaces
```
all it should come up with is
> auto lo
iface lo inet loopback
No need to post it unless it shows something else.

---

