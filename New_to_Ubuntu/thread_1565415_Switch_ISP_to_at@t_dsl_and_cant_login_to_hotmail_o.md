---
title: "Switch ISP to at@t dsl and cant login to hotmail or surf cnn"
date: 2010-08-31
forum: New to Ubuntu
---

### Post by MeTylerDurden on 2010-08-31
Can't think what changed as I only changed my Internet Service provider.

---

### Post by CharlesA on 2010-08-31
What do you mean by "can't login to hotmail or surf cnn" ?

You'd need to be a lot more specific to get any help.

---

### Post by MeTylerDurden on 2010-08-31
put your tool to work

---

### Post by CharlesA on 2010-08-31
What exactly happens?

You could try running this to see if DNS is working.

```
dig cnn.com
```

---

### Post by lkraemer on 2010-08-31
Try the following commands:
```

route
route -n
route -nee
netstat -r
ping yourgatewayIPaddress

```
If you can't ping the Gateway IP address then your Login & Password
for your ISP are incorrect.

lk

---

### Post by MeTylerDurden on 2010-08-31
The connection to the server was reset while page was loading   is error when logging into hotmail.      I can't reply on my other pc running ubuntu 10.04 it works once in 20 tries.   I'm starting to think that when they upgrade people in the city to highspeed internet it just bogs down the "average joe".

---

### Post by CharlesA on 2010-08-31
Sounds like something you should talk to yer ISP about. I've never had problems loading websites on high speed.

---

### Post by MeTylerDurden on 2010-08-31
> **lkraemer said:**
> Try the following commands:
```

route
route -n
route -nee
netstat -r
ping yourgatewayIPaddress

```
If you can't ping the Gateway IP address then your Login & Password
for your ISP are incorrect.

lk ****UNKNOWN HOST YOUR GATEWAY IP ADDRESS****  when I ping

---

### Post by v1ad on 2010-08-31
> **CharlesA said:**
> Sounds like something you should talk to yer ISP about. I've never had problems loading websites on high speed.

they will be like; Linux??? We only support windows and mac.

---

### Post by CharlesA on 2010-09-01
> **v1ad said:**
> they will be like; Linux??? We only support windows and mac.

Just tell them you have a mac.

@OP: Post the output of ***ifconfig*** please.

---

### Post by lkraemer on 2010-09-02
You keep avoiding any response that can help us help you.

What is your IP address from the route command?
EXAMPLE:
```

larry@larry-laptop:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.x.x     *               255.255.255.0   U     2      0        0 wlan0
link-local      *               255.255.0.0     U     1000   0        0 wlan0
default         **192.168.1.1 **    0.0.0.0         UG    0      0        0 wlan0
larry@larry-laptop:~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=1.46 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=0.774 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=0.779 ms
64 bytes from 192.168.1.1: icmp_seq=4 ttl=64 time=0.751 ms
^C

```
Then Ping the IP address located at the intersection of DEFAULT & GATEWAY as in:
```

ping 192.168.1.1

```

If you can't ping the Gateway IP Address Call your ISP and get the
LoginName & LoginPassword.....

Then VERIFY you have DNS Servers specified.
```

ping www.google.com

```

lk

---

