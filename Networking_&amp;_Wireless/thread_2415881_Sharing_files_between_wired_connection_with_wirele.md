---
title: "Sharing files between wired connection with wireless network"
date: 2019-04-02
forum: Networking &amp; Wireless
---

### Post by jsjpandey on 2019-04-02
My system is connected to wireless connection with one system and the same is connected using lan with other one. I want to connect with both the end working making my computers a router. How to do it?

---

### Post by TheFu on 2019-04-02
The answer depends on which release of Ubuntu you have and the networks you want to route between.

[https://ubuntuforums.org/showthread.php?t=2410859](https://ubuntuforums.org/showthread.php?t=2410859) is about the simplest answer. Don't know if that is enough for your needs.

---

### Post by rsteinmetz70112 on 2019-04-02
I don't really understand what you are trying to do some more information would b e helpful. 

The most common situation would be one machine connected to a wired port on a router and the other connected to the same router wirelessly. In most cases the default settings of the router and Ubuntu should connect automatically. Unless I am missing something.

---

### Post by jsjpandey on 2019-04-06
My scenario is as following

  ```

Connected with Wifi Device

Computer A - wlx20e317024622     -->  192.168.0.104
Computer B - wlx20e317024622      -->  192.168.1.105And


Connected with LAN Wire
Computer B - ens33      -->  10.42.0.1
Computer C - ens33    -> 10.42.0.9
  
```


Now I want Computer A to get connected with Computer C with Samba.
How to make it possible.

---

### Post by jsjpandey on 2019-04-07
My scenario is as following

  ```

Connected with Wifi Device

Computer A - wlx20e317024622     -->  192.168.0.104
Computer B - wlx20e317024622      -->  192.168.1.105And


Connected with LAN Wire
Computer B - ens33      -->  10.42.0.1
Computer C - ens33    -> 10.42.0.9
  
```


Now I want Computer A to get connected with Computer C with Samba.
How to make it possible.

---

### Post by SeijiSensei on 2019-04-07
First thing you probably need to do is allow traffic to flow between the interfaces. By default, Ubuntu will not pass such traffic. To do so you need to uncomment

```
net.ipv4.ip_forward=1
```

by removing the hash mark at the beginning of that line in /etc/sysctl.conf. You'll need to use a text editor like nano with sudo.

---

### Post by TheFu on 2019-04-07
Which computer do you think should handle the routing?
And where is the internet connection?

There is an "Ars Technica" article about converting a computer into a router. Think it is 3-part.

---

### Post by jsjpandey on 2019-04-07
Thanks for reply.  I have forwarded the ip but how to find the ip of computer c.

---

### Post by SeijiSensei on 2019-04-08
Isn't it 10.42.0.9? That's what you have above.

Start by seeing whether you can ping all the hosts on both networks. For instance "ping 10.42.0.9".

You changed sysctl.conf on machine B, right? That's the one that is acting as a router.

You may need to add some routes on machines A and C as well.  On A, 

```
sudo ip route add 10.42.0.0/24 via 192.168.1.105
```

and on C

```
sudo ip route add 192.168.1.0/24 via 10.42.0.1
```

If it doesn't work, show us the result of running "route -n" on all three machines.

---

### Post by jsjpandey on 2019-04-08
I think computer B should handle routing, by the way there is no internet connection only router and land connections

---

### Post by coffeecat on 2019-04-08
Threads merged. Please do not create more than one thread about the same issue. This dilutes community effort.

---

### Post by jsjpandey on 2019-04-13
Not working. The ```
route -n
``` result is a follows

Computer A: 

```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    600    0        0 wlp1s0
10.42.0.0       192.168.0.104   255.255.255.0   UG    0      0        0 wlp1s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlp1s0
192.168.0.0     0.0.0.0         255.255.255.0   U     600    0        0 wlp1s0


```

Computer B:
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    600    0        0 wlx20e317024622
10.42.0.0       0.0.0.0         255.255.255.0   U     100    0        0 ens33
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlx20e317024622
192.168.0.0     0.0.0.0         255.255.255.0   U     600    0        0 wlx20e317024622


```

And last

Computer C:

```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.42.0.1       0.0.0.0         UG    100    0        0 ens33
10.42.0.0       0.0.0.0         255.255.255.0   U     0      0        0 ens33
10.42.0.1       0.0.0.0         255.255.255.255 UH    100    0        0 ens33
192.168.0.0     10.42.0.1       255.255.255.0   UG    0      0        0 ens33


```


I can ping on Computer B with 10.42.0.1 from Computer A but cannot on Computer C.

---

### Post by jsjpandey on 2019-04-17
Not working. Please help

---

### Post by SeijiSensei on 2019-04-17
```
10.42.0.0       192.168.0.104   255.255.255.0   UG    0      0        0 wlp1s0
```

Shouldn't the gateway be 192.168.0.**105**?

---

