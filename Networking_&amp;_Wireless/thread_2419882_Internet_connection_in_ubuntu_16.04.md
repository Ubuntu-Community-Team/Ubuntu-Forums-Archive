---
title: "Internet connection in ubuntu 16.04"
date: 2019-05-26
forum: Networking &amp; Wireless
---

### Post by AnupamMitra on 2019-05-26
Today I have installed Ubuntu 16.04 32 Bit OS in a new HP Laptop Free DOS with USB Stick. Thereafter I connected the wired network to the said Laptop. Connection is established but I can't open any site. It was my target that after installation of 16.04 OS, I would upgrade it to 18.04, but I couldn't due to lack of internet connection.

Need help to overcome the hurdle.

---

### Post by Rubi1200 on 2019-05-26
Before we get into the connectivity issues, why not just install 18.04 from the start rather than this upgrade?

Let's see the output of the following please:

```
ifconfig -a
```

and

```
netstat -nr
```

Thanks.

---

### Post by AnupamMitra on 2019-05-26
> **Rubi1200 said:**
> Before we get into the connectivity issues, why not just install 18.04 from the start rather than this upgrade?

Let's see the output of the following please:

```
ifconfig -a
```

and

```
netstat -nr
```

Thanks.

As because I was not having neither the ISO image of 18.04 OS or readily the USB stick with 18.04. 
However, the outcome is as under.

```

 sharmista@sharmista-hp-laptop-14q-cs0xxx:~$ ifconfig -a
 enp1s0    Link encap:Ethernet  HWaddr c4:65:16:85:77:f6   
           UP BROADCAST MULTICAST  MTU:1500  Metric:1
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:1000  
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
 
 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0
           inet6 addr: ::1/128 Scope:Host
           UP LOOPBACK RUNNING  MTU:65536  Metric:1
           RX packets:820 errors:0 dropped:0 overruns:0 frame:0
           TX packets:820 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:1000  
           RX bytes:60896 (60.8 KB)  TX bytes:60896 (60.8 KB)
 
 
 sharmista@sharmista-hp-laptop-14q-cs0xxx:~$ netstat -nr
 Kernel IP routing table
 Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
 sharmista@sharmista-hp-laptop-14q-cs0xxx:~$ 
  
```

Thanks.

---

### Post by Rubi1200 on 2019-05-26
I could be wrong but it does not seem to me that you are connected.

Have you tried some or all of the options here?
[https://www.pcworld.com/article/2455972/how-to-fix-your-internet-connection-in-ubuntu-linux.html](https://www.pcworld.com/article/2455972/how-to-fix-your-internet-connection-in-ubuntu-linux.html)

---

