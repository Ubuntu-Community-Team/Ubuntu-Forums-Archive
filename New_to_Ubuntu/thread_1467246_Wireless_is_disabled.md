---
title: "Wireless is disabled"
date: 2010-04-30
forum: New to Ubuntu
---

### Post by lupirius on 2010-04-30
I just installed ubuntu and am really new to this. It seems like my computer isn't recognizing any wireless networks and it only says wireless is disabled. I know that wireless works perfectly on Windows 7 for sure. How can I fix this?

---

### Post by spiky001 on 2010-04-30
As you have just installed have you updated yet if not then you need to do that via an eth) cable this might sort out wireless, if not then you need to check if any drivers are availble check hard ware drivers

---

### Post by lupirius on 2010-04-30
I don't know how to update.

As for drivers, it says that I have a Broadcom STA wireless driver. It says that it is activated and currently in use.

---

### Post by spiky001 on 2010-04-30
you need to get an internet connection with a lead as your wireless is not working, then go systen administration update manager it will check for any updates

---

### Post by lupirius on 2010-04-30
ok, i did that and my system is up to date.

---

### Post by 3177 on 2010-04-30
i had the same problem on an acer laptop

what your looking for is under Hardware drivers

there should be 2 options to choose from:
*the free driver(works...like crap)
*the proprietary driver(wasnt able to install, computer froze)

I just use a belkin adapter at the moment

---

### Post by lupirius on 2010-04-30
i have a dell inspiron 1545 if that helps

---

### Post by spiky001 on 2010-04-30
type in terminal
```
ifconfig
```

then post output

---

### Post by 3177 on 2010-04-30
> **lupirius said:**
> i have a dell inspiron 1545 if that helps

no not really
I just have the same wireless card

---

### Post by lupirius on 2010-04-30
Output:
> 
eth0      Link encap:Ethernet  HWaddr 00:23:ae:3a:e5:f0  
          inet addr:169.229.82.142  Bcast:169.229.82.255  Mask:255.255.255.0
          inet6 addr: fe80::223:aeff:fe3a:e5f0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:50342 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19922 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:35329427 (35.3 MB)  TX bytes:2874740 (2.8 MB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:30 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1728 (1.7 KB)  TX bytes:1728 (1.7 KB)


---

### Post by spiky001 on 2010-04-30
try in terminal 
```
sudo ifconfig wlan0 up
```

---

### Post by lupirius on 2010-04-30
This is what comes up:

> wlan0: ERROR while getting interface flags: No such device

---

### Post by spiky001 on 2010-04-30
looks like you need a driver have a look here

[http://ubuntuforums.org/showthread.php?t=1305906](http://ubuntuforums.org/showthread.php?t=1305906)

---

### Post by 3177 on 2010-04-30
> **spiky001 said:**
> looks like you need a driver have a look here

[http://ubuntuforums.org/showthread.php?t=1305906](http://ubuntuforums.org/showthread.php?t=1305906)

kinda what I already said(i read the link)

---

### Post by 3177 on 2010-05-14
any luck?

---

### Post by 3177 on 2010-05-16
i used the quoted solution on the newest post. works fine again
[http://ubuntuforums.org/showthread.php?t=1369975](http://ubuntuforums.org/showthread.php?t=1369975)

---

