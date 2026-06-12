---
title: "Knowing which process or application transfering data"
date: 2009-09-21
forum: New to Ubuntu
---

### Post by ubfu on 2009-09-21
I'd like to know is there any command or application which shows which application or process transferring data ?

It's quite weird when everytime I start my pc , the network shows of data transfering download sometimes goes up to 100KIB/s .I wnated to know which application hogging the bandwidth.

Is there away to detect it ?

---

### Post by tomBorgia on 2009-09-21
Netstat is probably what you need... it'll show you active connections and the process using them.

---

### Post by MrWES on 2009-09-21
> **ubfu said:**
> I'd like to know is there any command or application which shows which application or process transferring data ?

It's quite weird when everytime I start my pc , the network shows of data transfering download sometimes goes up to 100KIB/s .I wnated to know which application hogging the bandwidth.

Is there away to detect it ?

From a terminal type:
```
netstat --inet
```
It should return something like this:
```
Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 bill-laptop:60471       vx-in-f102.google.c:www ESTABLISHED
tcp        0      0 bill-laptop:35949       yo-in-f101.google.c:www ESTABLISHED
tcp        0      0 bill-laptop:47318       ubuntu:microsoft-ds     ESTABLISHED
tcp        0      0 bill-laptop:58277       74.125.106.16:www       ESTABLISHED

```

you can add the -c flag, and netstat will refresh every second.

Bill

---

### Post by kpkeerthi on 2009-09-21
To see which process is using the socket/port include the --program switch as well.

---

### Post by ubfu on 2009-09-27
But I wanted it to display live speed kb downloading.

---

