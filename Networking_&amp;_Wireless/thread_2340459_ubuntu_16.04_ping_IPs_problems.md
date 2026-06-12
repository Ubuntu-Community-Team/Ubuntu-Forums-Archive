---
title: "ubuntu 16.04 ping IPs problems"
date: 2016-10-18
forum: Networking &amp; Wireless
---

### Post by ganl-140593 on 2016-10-18
Hello,

I've got ubuntu 16.04 on my machine and the sign of network seems ready to work.
But I cannot receive any webpages when searching an address. I thought there existed a DNS problem, so I tried to ping something, ping 127.0.0.1 is fine.
But ping other IPs, it shows:
```
ping 216.58.212.110
PING 216.58.212.110 (216.58.212.110) 56(84) bytes of data.

--- 216.58.212.110 ping statistics ---
84 packets transmitted, 0 received, 100% packet loss, time 83632ms
```

And If I ping addresses, it shows cannot find the host.
Anyone can help me out?

---

### Post by Bucky Ball on 2016-10-18
What does the IP 216.58.212.110 belong to? Ping this:

```
ping google.com
```

Try pinging the router which is probably this:

```
ping 192.168.0.1
```

... or this:

```
ping 192.168.1.1
```

Could be something different, unlikely, but check the router manual. If you can not ping the router, that is where you'd be starting on fixing this issue.

Please report all outcomes.

---

### Post by Skaperen on 2016-10-18
try: *traceroute 8.8.8.8*

---

### Post by ganl-140593 on 2016-10-19
Results for these three:
```
ping google.com
ping: unknown host google.com
```

```
ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(16) bytes of data.

^C
--- 192.168.1.1 ping statistics ---
16 packets transmitted, 0 received, 100% packet loss, time 83632ms
```

The same for pinging 192.168.1.1
```
ping 192.168.1.1
PING 192.168.1.1 (192.168.0.1) 56(16) bytes of data.


^C
--- 192.168.1.1 ping statistics ---
16 packets transmitted, 0 received, 100% packet loss, time 83632ms
```

> **Bucky Ball said:**
> What does the IP 216.58.212.110 belong to? Ping this:

```
ping google.com
```

Try pinging the router which is probably this:

```
ping 192.168.0.1
```

... or this:

```
ping 192.168.1.1
```

Could be something different, unlikely, but check the router manual. If you can not ping the router, that is where you'd be starting on fixing this issue.

Please report all outcomes.

---

### Post by nathan-linux-sa on 2016-10-19
Please send the output of

```
ping -c2  $(route -n | grep -A 1 Gateway | grep "0.0.0.0" | awk '{ print $2 }')
```

and as suggested, 
```
ping 8.8.8.8
``` 

also, 
```
sudo iptables -L OUTPUT -vn
```

---

### Post by ganl-140593 on 2016-10-20
Here are the results:
```
ping -c2 $(route -n | grep -A 1 Gateway | grep "0.0.0.0" | awk '{print $2}')
PING 0.0.0.0 (202.117.10.47) 56(124) bytes of data.

--- 0.0.0.0 ping statistics ---
2 packets transmitted, 0 received 100% packet loss, time 999ms 
```

```
ping 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
^C
--- 8.8.8.8 ping statistics ---
7 packets transmitted, 0 received, 100% packet loss, time 6047ms
```

---

### Post by ganl-140593 on 2016-10-20
And, 
```
sudo iptables -L OUTPUT -vn

Chain OUTPUT (policy ACCEPT 0 packets, 0 bytes)
pkt bytes target prot opt in out   source    destination
```


PS: I checked the interfaces file under /usr/etc/init.d/, but only to find that there is only lo existed. Should I add the static network configuration info into this file?
I've tried before but failed...

---

### Post by nathan-linux-sa on 2016-10-20
Hi

I would like to see the output of 
```
ifconfig
```
```
ip route list
```
```
ethtool eth0
```

What must your network settings be?

---

### Post by ganl-140593 on 2016-10-20
Here are some results updated:
[ATTACH=CONFIG]271703[/ATTACH][ATTACH=CONFIG]271704[/ATTACH][ATTACH=CONFIG]271705[/ATTACH]

---

### Post by nathan-linux-sa on 2016-10-22
Hi

If you believe you have dns issues, then the below commands will confirm this:

Open http to CNN's website using the command below:
```
nc -v -w1 151.101.16.73 80
```

This is the result on my machine
```
$ nc -v -w1 151.101.16.73 80
Connection to 151.101.16.73 80 port [tcp/http] succeeded!

```

If you have DNS issues, the below will fail
```
nc -v -w1 www.cnn.com 80
```

Below is the result from my machine
```
$ nc -v -w1 www.cnn.com 80
Connection to www.cnn.com 80 port [tcp/http] succeeded!

```

---

