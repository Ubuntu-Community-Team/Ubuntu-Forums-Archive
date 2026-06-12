---
title: "[SOLVED] Common web page access problem... Solutions?"
date: 2007-12-04
forum: Networking &amp; Wireless
---

### Post by Jeztastic on 2007-12-04
Hi

I am having a problem accessing some web pages. However, the problem is intermittent, and seems to only happen 'deep in' a site. Eg, it has happened attempting to post here, and on yahoo email.

This problem is mentioned Here:

[http://ubuntuforums.org/showthread.php?t=608524&highlight=web+pages+problem]("http://ubuntuforums.org/showthread.php?t=608524&highlight=web+pages+problem")

Here:

[http://ubuntuforums.org/showthread.php?t=608760&highlight=web+pages+problem](http://ubuntuforums.org/showthread.php?t=608760&highlight=web+pages+problem)

Here:

[http://ubuntuforums.org/showthread.php?t=526706&highlight=web+pages+problem](http://ubuntuforums.org/showthread.php?t=526706&highlight=web+pages+problem)

without a satisfactory solution, as far as I can see,

Does anyone have a fix? 

FYI, my girlfriends XP laptop has a similar problem on all browsers. My Vista dual boot on the machine does not have the problem. All through the same router.

---

### Post by 11hjpphty76lkjj on 2007-12-04
Not sure if I can help...but run:

```
ifconfig
```

and

```
hostname
```

and

```
cat /etc/network/interfaces
```

and 

```
cat /etc/issue
```

and

```
netstat -r
```

and post the output of each.

also install lynx

```
sudo apt-get install lynx
```

then run lynx

```
lynx
```

and as a test see if you can get to external websites using that.

A

---

### Post by Jeztastic on 2007-12-04
```
laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1B:38:17:1A:E7  
          inet addr:192.168.1.66  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:38ff:fe17:1ae7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12635 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10989 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11397314 (10.8 MB)  TX bytes:2096059 (1.9 MB)
          Interrupt:19 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```

```
hostname
hopjes-laptop

```

```
cat /etc/network/interfaces
auto lo
iface lo inet loopback
```

```
 cat /etc/issue
Ubuntu 7.10 \n \l
```

```
netstat -r
Kernel IP routeing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     *               255.255.255.0   U         0 0          0 eth0
link-local      *               255.255.0.0     U         0 0          0 eth0
default         home            0.0.0.0         UG        0 0          0 eth0

```

There you go!

Will try lynx, but have tried with Opera in the past to no avail...

---

### Post by 11hjpphty76lkjj on 2007-12-04
Okay run

```
sudo gedit /etc/network/interfaces
```

add

```
auto eth0
iface eth0 inet dhcp
```

then

```
sudo /etc/init.d/networking restart
```

That do anything? 

Everything else looks fine from my experience..

---

### Post by Jeztastic on 2007-12-07
> **kalosaurusrex said:**
> Okay run

```
sudo gedit /etc/network/interfaces
```



```
auto lo
iface lo inet loopback
```

> 


add

```
auto eth0
iface eth0 inet dhcp
```



```
auto eth0
bash: auto: command not found
iface eth0 inet dhcp
bash: iface: command not found

```


> 
then

```
sudo /etc/init.d/networking restart
```

That do anything? 

Everything else looks fine from my experience..

OK, still not liking Yahoo...

---

### Post by Jeztastic on 2007-12-07
It's really random - web pages will work fine at sometimes, but not others. I managed to view an email in Yahoo, but only after several tries. Now it's not responding. I'm sending OK on this forum, but the other day I had to switch over to Vista. Still no problems in Vista.

---

### Post by Jeztastic on 2007-12-09
Hi, can anyone else come in on this?

---

### Post by Jeztastic on 2008-01-10
Update:

The problem was the MTU settings on my router. Vista dynamically assigns MTU, so there was no problem there. XP does not, so my girlfriends laptop had the same problem.

I fixed this by working out optimum MTU for my girlfriends Laptop, and then changing the router MTU to match it. Changing the router settings also sorted my access problems, however, I didn't have to change anything in Ubuntu. 

Hope this helps someone.

I might add, no - one here was any help. Thanks to kalosaurusrex for trying, but I've found on these forums so many times - if it's not a simple fix yoi just get ignored.

---

